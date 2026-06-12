---
title: "Steam crashes on start-up due to proxy fail"
date: 2011-03-02
forum: Wine
---

### Post by deesto on 2011-03-02
I have successfully installed Steam via Wine and have gotten it to run a few times, even got a few games running as well.  But now I notice that after the Steam client loads initially (which does fine). a few seconds later the client tries to pop up the additional "News" window, and I can see the outline of that window appear and then the app crashes completely and disappears.  I believe this is due to the client News window trying to connect back home, and then failing because it can't figure out how to get through my proxy.

I found an old thread on hacking the "registry" and adding a proxy definition there.  I can't remember whether I did this before or after recognizing the problem with the News pop-up window, but it hasn't helped with that problem.

Is there a way to get the latest version of the client to either use a proxy for all connections, or to keep the News window from appearing?

Sample output:
```
$ **env WINEPREFIX="/home/me/.wine" wine C:\\Program\ Files\\Steam\\Steam.exe**
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:urlmon:CoInternetSetFeatureEnabled 5, 0x00000002, 1, stub
fixme:urlmon:CoInternetSetFeatureEnabled 10, 0x00000002, 1, stub
fixme:dwmapi:DwmSetWindowAttribute (0x1009a, 2, 0x32d334, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x1009a, 3, 0x32d338, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x1009a, 4, 0x32d33c, 4) stub
fixme:mixer:ALSA_MixerInit No master control found on Camera, disabling mixer
fixme:dwmapi:DwmSetWindowAttribute (0x100a2, 2, 0x32d804, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100a2, 3, 0x32d808, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100a2, 4, 0x32d80c, 4) stub
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:wbemprox:wbem_locator_ConnectServer 0x1a2ae8, L"ROOT\\CIMV2", (null), (null), (null), 0x00000080, (null), (nil), 0x42bbee8)
fixme:dwmapi:DwmSetWindowAttribute (0x100aa, 2, 0x32d80c, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100aa, 3, 0x32d810, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100aa, 4, 0x32d814, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100b4, 2, 0x32d2e4, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100b4, 3, 0x32d2e8, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100b4, 4, 0x32d2ec, 4) stub
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:dwmapi:DwmSetWindowAttribute (0x100d0, 2, 0x32d94c, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100d0, 3, 0x32d950, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100d0, 4, 0x32d954, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x1010c, 2, 0x32da8c, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x1010c, 3, 0x32da90, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x1010c, 4, 0x32da94, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x10116, 2, 0x32d514, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x10116, 3, 0x32d518, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x10116, 4, 0x32d51c, 4) stub
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:win:EnumDisplayDevicesW ((null),0,0x32ce24,0x00000000), stub!
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
```

I assume the problem is here:
```
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
```

I have a system-wide proxy set (via bash and Gnome); not sure how to convince Wine/Steam to use it.

---

### Post by deesto on 2011-03-04
It looks like the only thing that can't navigate the proxy is the News pop-up, and if I run games directly and bypass the client window display entirely, it works with no problem.  

It looks like Steam calls this News window an "overlay", and I found a comment here that claims to fix the crash by adding a Wine library exception for `gameoverlayrender` but this didn't help in my case:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444)

Is there a Steam configuration file option somewhere where I can manually change whether this News dialog is launched?  I know there's a tick box in the Preferences, which I can disable on another OS, but client interface changes between OSes aren't synced centrally, and I can't get the client to stay alive long enough to get to a Preferences menu.

I also see comments everywhere to "Steam Community In-Game", but this only applies to games, not the client, and not all games have this option (Portal doesn't, for example).  Plus, I see as well that the latest client and Wine combo was supposed to fix this.  Regardless, if there's a way to disable this globally, please let me know.

---

### Post by pils92 on 2011-03-06
Bump! Same problem Ubuntu 10.10 fresh install.

---

### Post by lite1979 on 2011-03-15
From the winehq forums I was advised to add "-silent" to my command line and that's been working for me. Whenever a steam browser is called, though, it crashes steam, so when I exit half-life, for example, steam crashes when the advertisement tries to pop up. I hate when stuff that used to work fine suddenly stops working...

---

### Post by deesto on 2011-03-16
> **lite1979 said:**
> From the winehq forums I was advised to add "-silent" to my command line and that's been working for me. Whenever a steam browser is called, though, it crashes steam, so when I exit half-life, for example, steam crashes when the advertisement tries to pop up. I hate when stuff that used to work fine suddenly stops working...
OK, what you're calling the "steam browser" is what I've been calling a pop-up or News, correct?  If so, is this a known problem, and Linux users are just expected to run the games themselves straight without running the client?

---

### Post by Davidthewin on 2011-03-18
Just tried to install Steam and I'm getting the same problem, although I didn't get the error message presumably because I was running it straight through Wine rather than Terminal

---

### Post by lite1979 on 2011-03-24
No error message here, either. I usually use my desktop icon to start Steam, so I just added the "-silent" option to the command properties for that icon.

Steam continues to shut itself down after I finish playing a game, though, because a browser window attempts to open once I finish playing, crashing Steam.

---

### Post by deesto on 2011-03-24
Right: you won't see an error if you're not running from a terminal.  If you want to see it, copy the command from your app icon (or type 'wine ' and the command you're running) in a terminal.

---

### Post by Abacus Man on 2011-05-11
Is there a way to let me show the news window? because the terms and conditions for some of my games seem to share its properties, preventing me from installing them :(

---

