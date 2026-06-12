---
title: "WoW Launcher window not working and a possible Gecko problem."
date: 2009-06-02
forum: Wine
---

### Post by DarkSim on 2009-06-02
Today during maintenance I copied over my Windows WoW installation. I have the show launcher window on startup box checked but WoW goes straight to the login screen. 

Also when updating to newest patch I got a prompt to install Gecko for wine which I did. After that a box popped up which I think had either the changes from 3.1.3 or the ToS. It was whitened out with text at the top that said 'Javascript must be enabled.'

Other then those two problems the game runs much smoother than Vista. Wish I would have tried it sooner.Wintergrasp might have been much more enjoyable. :D

So in short can anybody help me get the launcher window to pop up first and get js working in Gecko so I can read patch changes and whatnot when those popups appear?

---

### Post by hikaricore on 2009-06-02
I don't advise running the Launcher as it serves no purpose.

However run:

wine Launcher.exe

instead of the normal:

wine WoW.exe

And the laucher should start.  :p
Assuming they havn't merged the binaries which I doubt.

---

### Post by lotsamuffins on 2010-03-05
haiving the same problem. just installed wrath of the lich king and the launch on the desktop and in the wow folder dont work but will launch wow with wow.exe. what gives. heres the code it gives me in terminal.

matthew@matthew-desktop:~$ wine "C:\Program Files\World of Warcraft\Launcher.exe"
fixme:shdocvw: PersistStreamInit_Load (0x13c470)->(0x32e0f4)
fixme:shdocvw:OleControl_FreezeEvents (0x13c470)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x13c470)->(0)
fixme:shell:IShellLinkA_fnGetPath (0x13ca18 ) : WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x13c9f8 ) : WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x13c9f8 ) : WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x13d370 ) : WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x13d370 ) : WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x13d370 ) : WIN32_FIND_DATA is not yet filled.
fixme:urlmon:URLMoniker_BindToObject use running object table
matthew@matthew-desktop:~$ wine "/media/windowsdrive/WorldofWarcraft/Wow.exe" -opengl
wine: cannot find '/media/windowsdrive/WorldofWarcraft/Wow.exe'
matthew@matthew-desktop:~$

---

### Post by Soulcage on 2010-03-05
lotsamuffins you're never supposed to run any program from you windows partition it will destroy some of those windows files. Also try pasting in a terminal:
cd ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft && wine Wow.exe -opengl

---

