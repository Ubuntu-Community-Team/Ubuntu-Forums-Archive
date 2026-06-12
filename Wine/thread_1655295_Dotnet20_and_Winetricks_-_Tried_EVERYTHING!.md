---
title: "Dotnet20 and Winetricks - Tried EVERYTHING!"
date: 2010-12-29
forum: Wine
---

### Post by Farrawr on 2010-12-29
I have been googling for about 6 hours now, and I'm about ready to give up. When I attempt to install Dotnet20 with Wine/Winetricks, I get this:
 
fagdedi:~# sh winetricks dotnet20
No protocol specified
No protocol specified
No protocol specified
No protocol specified
No protocol specified
------------------------------------------------------
Instaling .net 2.0 runtime.  Can take several minutes.  See [http://wiki.winehq.org/MicrosoftDotNet](http://wiki.winehq.org/MicrosoftDotNet) for tips.
------------------------------------------------------
prerequisite gecko already installed, skipping
DELETE - HKLM\Software\Microsoft\Windows\CurrentVersion SubVersionNumber 0 0 1
No protocol specified
Error: The system was unable to find the specified registry key or value
DELETE - HKLM\Software\Microsoft\Windows\CurrentVersion VersionNumber 0 0 1
No protocol specified
Error: The system was unable to find the specified registry key or value
DELETE - HKLM\Software\Microsoft\Windows NT\CurrentVersion CSDVersion 0 0 1
No protocol specified
The operation completed successfully
DELETE - HKLM\Software\Microsoft\Windows NT\CurrentVersion CurrentBuildNumber 0 0 1
No protocol specified
The operation completed successfully
DELETE - HKLM\Software\Microsoft\Windows NT\CurrentVersion CurrentVersion 0 0 1
No protocol specified
The operation completed successfully
DELETE - HKLM\System\CurrentControlSet\Control\ProductOptions ProductType 0 0 1
No protocol specified
Error: The system was unable to find the specified registry key or value
DELETE - HKLM\System\CurrentControlSet\Control\ServiceCurrent OS 0 0 1
No protocol specified
Error: The system was unable to find the specified registry key or value
DELETE - HKLM\System\CurrentControlSet\Control\Windows CSDVersion 0 0 1
No protocol specified
The operation completed successfully
Setting Windows version to win2k
Executing early_wine regedit c:\winetrickstmp\set-winver.reg
Executing cp -f /root/.cache/winetricks/dotnet20/l_intl.nls /root/.wine/dosdevices/c:/windows/system32
DELETE - HKLM\Software\Microsoft\.NETFramework\policy\v2.0 (null) 0 0 1
No protocol specified
Error: The system was unable to find the specified registry key or value
DELETE - HKLM\Software\Microsoft\.NETFramework InstallRoot 0 0 1
No protocol specified
Error: The system was unable to find the specified registry key or value
Executing wine /root/.cache/winetricks/dotnet20/dotnetfx.exe
No protocol specified
fixme:advapi:DecryptFileA "C:\\users\\root\\Temp\\IXP000.TMP\\" 00000000
No protocol specified
No protocol specified
No protocol specified
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:systray:initialize_systray Could not create tray window
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
------------------------------------------------------
Note: command 'wine /root/.cache/winetricks/dotnet20/dotnetfx.exe' returned status 43.  Aborting.
------------------------------------------------------
------------------------------------------------------
dotnet20 failed

------------------------------------------------------
 
I have completely removed and reinstalled Wine/tricks, cleared the config, changed the location of Wine/tricks, even loaded up the ol' NX No Machine and attempted to run it via Wine and the .exe. In GUI, I get this error:
 
[http://i54.tinypic.com/pwpd3.jpg](http://i54.tinypic.com/pwpd3.jpg)
 
I'm trying this on Debian 5.0, and I really need this done ASAP. Any help is very very much appreciated!
 
Happy Holidays!

---

### Post by marl30 on 2010-12-29
Try deleting "dotnet20" from .cache/winetricks/ and re-download it using Winetricks. If that doesn't work, it is possible that dotnet20 is having conflict with something else you installed in Wine. I always ensure that I install dotnet20 first before installing anything else in Wine, or it will be a pain to get to install.

---

### Post by marl30 on 2010-12-29
Also, make sure you are using a newer version of Wine (at least 1.2).

---

### Post by Farrawr on 2010-12-29
> **marl30 said:**
> Try deleting "dotnet20" from .cache/winetricks/ and re-download it using Winetricks. If that doesn't work, it is possible that dotnet20 is having conflict with something else you installed in Wine. I always ensure that I install dotnet20 first before installing anything else in Wine, or it will be a pain to get to install.
 
Done and done, twice. Neither work. Fresh install of Wine installing dotnet20 before corefonts and vcrun2008 still gives the error, so does removing the cache'd file and using the command again. Neither have worked.
 
> **marl30 said:**
> Also, make sure you are using a newer version of Wine (at least 1.2).
 
Am, but will recheck to be 100% sure. I am using wine-1.1.42 (Shown using wine --version), should I find a newer version? I thought this was the newest version on wine's site...
 
From what I can find on [http://www.lamaresh.net/binary.php](http://www.lamaresh.net/binary.php), for Debian, 1.1.42 is the newest version I can use.

---

### Post by marl30 on 2010-12-29
> **Farrawr said:**
> Done and done, twice. Neither work. Fresh install of Wine installing dotnet20 before corefonts and vcrun2008 still gives the error, so does removing the cache'd file and using the command again. Neither have worked.
 

 
Am, but will recheck to be 100% sure. I am using wine-1.1.42 (Shown using wine --version), should I find a newer version? I thought this was the newest version on wine's site...

No, that's an older version. The newest versions are 1.2.2 (Stable), and 1.3.10 (development).
You may want to add Wine PPA to get the latest version.


Here is also a complete rest command for Wine. Works on Ubuntu, not sure about Debian.
```
rm -rf $HOME/.wine && rm -f $HOME/.config/menus/applications-merged/wine* && rm -rf $HOME/.local/share/applications/wine && rm -f $HOME/.local/share/desktop-directories/wine* && rm -f $HOME/.local/share/icons/????_*.{xpm,png} && rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png} && rm -f $HOME/.local/share/applications/wine-extension*
```

---

### Post by Farrawr on 2010-12-29
> **marl30 said:**
> No, that's an older version. The newest versions are 1.2.2 (Stable), and 1.3.10 (development).
You may want to add Wine PPA to get the latest version.
 
 
Here is also a complete rest command for Wine. Works on Ubuntu, not sure about Debian.
```
rm -rf $HOME/.wine && rm -f $HOME/.config/menus/applications-merged/wine* && rm -rf $HOME/.local/share/applications/wine && rm -f $HOME/.local/share/desktop-directories/wine* && rm -f $HOME/.local/share/icons/????_*.{xpm,png} && rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png} && rm -f $HOME/.local/share/applications/wine-extension*
```
 
Command worked on Debian, however when I add the download links to my sources, I still get "wine is already the newest version". I'll try a manual download and dpkg right now.
 
EDIT: Alright the newest .deb package is what I had, but the newest release is a .tar.bz2. I can't use the dpkg -i command on it, so how do I use this downloaded updated Wine version and install it properly? :S
 
Also pointing out, wine-1.0.1-174-gc4039bd is the version that my other server is running that dotnet20 worked on.

---

### Post by marl30 on 2010-12-29
> **Farrawr said:**
> Command worked on Debian, however when I add the download links to my sources, I still get "wine is already the newest version". I'll try a manual download and dpkg right now.
 
EDIT: Alright the newest .deb package is what I had, but the newest release is a .tar.bz2. I can't use the dpkg -i command on it, so how do I use this downloaded updated Wine version and install it properly? :S
Does Ubuntu Tweak works on Debian? You could install it and use it to add Wine PPA and have it install the latest Wine: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

If that doesn't help, Playonlinux might be your solution, depending on what you want to install?

---

### Post by Farrawr on 2010-12-29
> **marl30 said:**
> Does Ubuntu Tweak works on Debian? You could install it and use it to add Wine PPA and have it install the latest Wine: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
 
If that doesn't help, Playonlinux might be your solution, depending on what you want to install?
 
I'm actually setting up a Dedicated Server for a game, therefore no GFX is actually needed. I just use the GUI since it's more "Windows" like than actually command line linux. I'm downgrading my Wine since my other dedi is running on "wine-1.0.1-174-gc4039bd" without any problems. If that doesn't work I'll find a .deb of the 1.2.2 and try that.

---

### Post by marl30 on 2010-12-29
> **Farrawr said:**
> I'm actually setting up a Dedicated Server for a game, therefore no GFX is actually needed. I just use the GUI since it's more "Windows" like than actually command line linux. I'm downgrading my Wine since my other dedi is running on "wine-1.0.1-174-gc4039bd" without any problems. If that doesn't work I'll find a .deb of the 1.2.2 and try that.

Ok, I see. Hope it works out for you.

---

### Post by Farrawr on 2010-12-29
Neither version worked, so it's not that. I wish I knew what it was though ;/

---

### Post by marl30 on 2010-12-29
> **Farrawr said:**
> Neither version worked, so it's not that. I wish I knew what it was though ;/

Try PlayonLinux. It has Dotnet20 under others. You would need to first create a bottle. You could do this with any random program. Then add Dotnet20 to that bottle from others. Afterwards, you can then install the program you wish to. PlayonLinux handles these extras quite differently from Wine on its on. So there is a great chance you will get it to work under it. [http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)

If you need help will PlayonLinux, I'll be glad to help.

---

### Post by dankegel on 2011-01-01
First - you shouldn't be running wine as root.
( [http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014](http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014) )

Second - wine requires graphics for a lot of stuff (possibly
including the app you want to run), you should probably try
getting X working before installing .net.  Make sure xeyes
or firefox work before trying wine.

---

