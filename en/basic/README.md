# Why make Wox?

I always wanted to write a keyboard based launcher. I use hotkeys as often as possible, especially after I got used to the unix programmers editor [Vim](http://www.vim.org). I frequently used the `Win + R` shortcut to launch the Windows "Run" command, but "Run" doesn't have built in search or any other useful functions. The Windows 8 and Windows 10 `Win+S` "Search" menu are an improvement, but "Search" still isn't a fast, flexiable, reliable keyboard launcher. For a while I was using [Launchy](http://www.Launchy.net/), but updates are ever less frequent and it looks like it's becoming abandonware.

Back to 2011, I tried using `C` to write [fstart](https://code.Google.com/p/fstart/) and then [smartrun](https://code.Google.com/p/smartrun/) but I wasn't experienced enough in developing with `C` or perhaps `C++` just wasn't the right tool for me. Neither of these launcher projects really took off.

Then, toward the end of 2013, I came across an excellent Mac launcher called  [Alfred](http://www.alfredapp.com/), and thought "how unfortunate that this doesn't exist yet for Windows".

Naturally, I thought I should develop something for Windows similar to Alfred, initially I even wanted to name it *WinAlfred* and [posted on V2ex](http://v2ex.com/t/93922) about it. My post and initial code generated enough excitement to get the project moving, but that same excitement concerned the authors of Alfred about possible confusion over their existing trademark, so I decided to rename it "Wox".

# Introduction
  -----------------------------
Wox lets you keep your hands on the **keyboard**. You can use Wox to:
* **Launch applications** and files without lifting your fingertips off the keyboard
* **Quick Search the Web** with Google, Wikipedia, or your own custom searches
* Use the **built in Calculator** and built in DOS/Cygwin **shell command launcher**
* Use **plugins** for Power Management, Clipboard History, Browser Bookmarks, Filezilla, Password Generator, Spotify, Language Translation and even search *Everything*
* For **developers**, we also have plugins for Dash Docs, Shadowsocks, Putty or Kitty, Pidgin, caniuse,  Hosts File Editor or you can develop your own plugins with `JSON`, `C#` or `Python`

Wox is open source, you can contribute via
[github](http://www.github.com/qianlifeng/wox)


# Wox Settings

You can accesss the Wox settings by simply activating Wox and typing `Settings`.

![](http://api.drp.io/files/54ceea25620af.png)

Alternatively, you can right click on the Wox tray icon and choose settings.


# System Plugin
---------------

Internally, all Wox searches are handled via plugins, the built in system plugin and optional user plugins. System plugins don't need to be installed or uninstalled, they are part of Wox. With the exception of Web Searches, system plugins do not require an `Action Keyword` keyboard shortcut to activate.

User plugins, such as [Clipboard History](https://www.getwox.com/plugin/4) requires an `Action Keyword`, so you would type `cb` + space + *search terms* to search your clipboard history.


## Program Launcher (System Plugin)

![](http://api.drp.io/files/54ceeb5e30338.png)

The program launcher is the most basic feature of Wox. Each item Wox finds that matches your search has it's own search relevancy weight. Each time you select an item, the weight increases for the active search term. This way, Wox gets to know what you like to search for and results will get more relevant over time. Your favorites will be displayed at the top of the list.

*Note for Chinese Language Use, Wox will automatically use romanized Chinese (pinyin) or actual chinese characters for search as in the image below.*

![](http://ww2.sinaimg.cn/large/5d7c1fa4jw1elrx1jpdrij20m807m0tg.jpg)

Wox automatically searches for any programs with shortcuts in the `Start Menu`. Under the `Wox Settings` > `Plugin` > `Programs` tab you can also add your own list of folders to search.

![](http://ww4.sinaimg.cn/large/5d7c1fa4jw1elrwuw8m25j20m80go76k.jpg)

By default Wox "Programs" search will find: .exe files, .bat (batch files) .lnk (windows shortcuts), and .appref-ms (windows application reference files from ClickOnce manifests)

## Control Panel (System Plugin)

![](http://ww1.sinaimg.cn/large/5d7c1fa4jw1elrx9znjv9j20m803g3ym.jpg)

In addition to programs, Wox also searches for Control Panel Applets. For example, type `users` to open the "User Accounts" page of the Control Panel or type `pro fea` to open the "Programs and Features" Control Panel page that lets you uninstall any previously installed program. Don't forget to try `present` to open Windows excellent "Presentation Settings" tool.

## Folder (System Plugin)

![](http://ww4.sinaimg.cn/large/5d7c1fa4jw1elrxk3oir4j20m803g74c.jpg)

If there are folders you frequently open such as your Home folder or your Dropbox folder, just add them to the list here and you can directly open that folder or even browse the contents of it from inside Wox.

## Calculator (System Plugin)

![](http://ww4.sinaimg.cn/large/5d7c1fa4jw1elrxc7incnj20m803gglq.jpg)

Wox includes a very powerful calculator based on the internal `Python` math libraries. Even complex equations are quickly handeld by Wox, and the result copied to the clipboard.

## URL (System Plugin)

![](http://ww2.sinaimg.cn/large/5d7c1fa4jw1elrxeradmpj20m803ggln.jpg)

When wox detects something that looks like it could be a URL (*something.com*) you'll see the Open URL option in Wox. Note that you can also paste URL's directly into Wox and open them more quickly than by activating your browser and pasting into the address bar.

## Web Search (System Plugin)

![](http://ww4.sinaimg.cn/large/5d7c1fa4jw1elrxsgt1drj20m80aegm7.jpg)

Web search plugins are like the "Other Search Engines" feature of Chrome, "Search Providers" feature of Internet Explorer, or the "Manager Search Engine List" feature of Firefox.

The default web search is Google, activated with the `g` Action Keyword. You can create your own shortcuts for the search feature on any website that uses GET type requests. Just replace the serch query term with `{q}` so that Wox knows where to insert your custom queries. For example, to add your own `w` search for Wikipedia, inside the wikipedia.org search box type "wox". You'll see the following URL on the address bar:

```
http://en.wikipedia.org/wiki/Special:Search?search=wox&go=Go
```

Just replace the "wox" portion, so your custom Wikipedia search URL would be:

```
http://en.wikipedia.org/wiki/Special:Search?search={q}&go=Go
```

![](http://ww1.sinaimg.cn/large/5d7c1fa4jw1elrxwxd0xwj20m80goq5o.jpg)


## Shell (System Plugin)

![](http://ww1.sinaimg.cn/large/5d7c1fa4jw1elrtig5gbyj20m8090wez.jpg)


Wox offers a replacement for the Windows "Run" `win+r` Dialog. Since the core of Wox is fast search, you don't have to worry about perfectly memorizing the name of each command you need to run. For example, type `win+r` and then `reset` and you'll see both IISreset (reset Windows built in web server) or Vista's session reset. If you chose "iisreset", you wouldn't get an annoying dos box window popping up, IIS reset would just execute the command required and exit in the background.

The top five commands that you run via Wox's `win+r` will be displayed in the last as soon as you launch it.

## System commands (System Plugin)

![](http://ww1.sinaimg.cn/large/5d7c1fa4jw1elrxgqz5n1j20m803gaa4.jpg)

Optional shortcuts for:

* Shutdown the computer
* Log off the current user
* Lock the screen
* Exit Wox
* Restart Wox
* Wox Settings


## Color (System Plugin)

![](http://ww1.sinaimg.cn/large/5d7c1fa4jw1elrx7z54j7j20m803gq2y.jpg)

Input an HTML/hex color code and Wox will visually display that color value.

## User Plugins Icon

![](http://ww2.sinaimg.cn/large/5d7c1fa4jw1elrtg0ec9kj20m8068jrk.jpg)

Note the paintbrush icon in the screenshot above. If you choose to activate any of these User Plugin choices, then the corresponding plugin will be executed.


# User plugins
  ----------------------------

## Wox Package Manager (wpm)

User plugins are installed via the `wpm install` command inside Wox. Most users will want to install the plugins for Clipboard History, Browser Bookmarks, Password Generation, and *Search Everything*. The full list of plugins is always available at [getwox.com/plugin](http://www.getwox.com/plugin)

Most developers will also want to install the plugins for Dash Docs, Shadowsocks, Putty or Kitty, Pidgin, caniuse, and the Hosts File Editor or even develop [your own plugins](/en/plugin/create_plugin.html) with `C#` or `Python`.

To install the Clipboard History plugin, activate Wox and enter `wpm install clip`, and then choose "Clipboard History" Once installed copy and paste a few items on your clipboard, and then activate Wox and type `cb` and you'll see a list of all the items in your recent history. Of course this is Wox, so the list is searchable.

To install the Browser Bookmarks plugin, just enter `wpm install bookmark`. Wox will find "Browser Bookmarks", click `enter` and then you'll be asked to confirm your choice.

To install the "Search Everything" plugin, just enter `wpm install every` and you'll see the "Everything" plugin.

To see which plugins you've already installed, just type `wpm list` and you'll see each plugin with it's Action Keyword listed at the end.


# Themes
  -----------------------------

![](http://api.drp.io/files/544a461139f56.png)

Wox ships with four themes by default: Dark, Light, Metro Server and Pink.

If you want to build your own theme you can use the Wox online theme builder at [getwox.com/theme/builder](https://www.getwox.com/theme/builder). Make sure to save your file under the Wox root directory and save it with the `.xaml` file extension so that Wox recognizes it as a theme. Note that to activate the theme, you'll need to restart Wox, and then you'll see your new theme as a choice under the `Settings` > `Themes` menu.

# Hotkeys
  -------------------------------------

![](http://api.drp.io/files/544a4878cbb40.png)

The global "activate wox" hotkey is `alt + space` by default, but you may want to change this to `ctrl + space` or something else to avoid interfering with the default Windows Restore/Move/Size/Close window menu.

You can also define a hotkey that pre-enters defined text into Wox, such as a hotkey for `alt + g` to activate the `g` built in Google Web Search.

In the example below, we've created a hotkey `alt+t` for "translate" and mapped it to `yd ` (note the extra space at the end of the hotkey) to activate the youdao online English/Chinese translation tool.

![](http://api.drp.io/files/544a4b2c392df.png)

![](http://api.drp.io/files/544a4bed8e627.png)

Once you install the [Clipboard plugin](https://github.com/qianlifeng/Wox.Plugin.ClipboardManager), we suggest mapping the `Ctrl + Shift + v` to `cb ` so that you can quickly search through recent clipboard history and decide what to paste.

# Context menu
  -------------------------------------

![](http://api.drp.io/files/544a2c5b85f45.png)

If you see this small "menu" icon on the right edge of an item in Wox, there is a context menu associated with that menu item. You can use `shift + enter` to see the menu options or `Esc` to exit from those options and return to the main search interface.

![](http://api.drp.io/files/544a2d1e2758a.png)

The context menu item provides optional actions, for example opens the file with administrator privileges or open the directory that contains the file.


# Proxy
------------------------------------

![](http://api.drp.io/files/544a4243dc812.png)

In the settings window, users can set HTTP proxy for Wox. This feature may be necessary for some business users if their networks are connected through a proxy.

If the proxy is set, then the 'wpm' commands and all system plugins will use this proxy.

Note: If user plugin author did not take proxy information into account, then this user plugin is not support proxy. So, we recommend plugin authors always consider proxy settings when making your plugin.

