---
title: "Running WoW from Windows partition using Wine"
date: 2011-01-31
forum: Wine
---

### Post by tesseract1 on 2011-01-31
Hi,

I'm am new to Ubuntu.  I am using Ubuntu 10.04.

I searched for information regarding running WoW from Windows partition using Wine, but a lot of the sources seem to date years back.  I tried some of the methods, but I was hesitant because they were so old.  Perhaps things have changed with the new WoW expansion, such as editing the config file, etc.

So I'm not sure how to proceed with it or if there are more recent tutorials that I can't find.

Ultimately I want to run my current install from my Windows partition in Ubuntu using Wine.

Can anyone help direct me through the steps or perhaps show me a source that is recent and reliable?

Any help is appreciated.

---

### Post by Soulcage on 2011-01-31
[http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2]("http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2")

---

### Post by cwwilson721 on 2011-01-31
What is meant is this (From the winehq article)
> [COLOR="Red"]Wine is not designed to interact with an existing Windows installation[/COLOR]. If you have any data you need from a Windows installation, browse your Windows filesystems in your normal file manager and copy the data to another location.
[COLOR="Red"]WARNING: Do not try to configure Wine to point to your actual Windows C:\ drive. This will break Windows and require a Windows reinstall.[/COLOR] We have tried to make this hard to do, so you probably cannot do it by accident. If you do manage this, Wine may or may not continue to operate, but your Windows install will be 100% dead due to critical parts of it being overwritten. The only way to fix Windows after this has happened is to reinstall it.
The reason why is the way that wine works. It creates it's own 'registry', and that will foul up Windows faster than a Windows update.

DON'T DO IT. DON'T TRY TO DO IT.

As the winehq says, you can try to copy the program folder over to your .wine folder. It MIGHT work, it might not. (World of Warcraft, for example, works great, after you edit the config.wtf file).

Easiest way is to just copy your Windows WoW folder to your /home/<USER>/.wine/drive_c/Program Files folder (Or wherever you want to put it), then make a launcher with the following command edited for your setup:
```
env WINEPREFIX="/home/<USER>/.wine-wow" WINEDEBUG=-all wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl
```The preceding tells wine to use the "wine-wow' folder for running (I use different 'wine' folders for different windows programs. That way, a foul-up in one doesn't kill all of them. And if I need to delete a particular 'install', I don't lose ALL my wine programs), don't debug (loading speed for my system, optional), and to run Launcher.exe with 'opengl'(Not optional, if you want more FPS. If you prefer eyecandy, try D3D. Look at winehq on how to try to run WoW in wine with D3D)

I then delete the config.wtf file, and run the launcher. WoW will create a new one for you.

Good luck!

---

