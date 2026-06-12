---
title: "Intalling Itunes on Wine"
date: 2011-04-23
forum: Wine
---

### Post by charlesbw on 2011-04-23
I just tried to install itunes on wine and keep getting blocked and then i tried other .exe files and kept getting the same blocked message.  Is there a specific way to install windows programs on wine.

```
The file '/media/Drive: D/Files/Downloads/HaloTrial.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.
```

I right clicked and chose to run it with wine when i got that message.

---

### Post by Joe of loath on 2011-04-23
You have to mark the program as executable before you run it, it's a security feature. Fine the .exe, right click it, click properties, and select 'Allow executing file as a program'. Alternately, you can run 'chmod +x /path/to/exe' in the terminal.

---

### Post by sikanderkhan on 2011-04-23
I tried to install it but my wine crashed. I had to reinstall wine.

---

### Post by Elfy on 2011-04-23
move to wine

---

### Post by cogadh on 2011-04-23
[iTunes doesn't really work in Wine]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347"). You'd probably be better off using a native app that will work with your iDevice, like Rhythmbox.

---

### Post by charlesbw on 2011-04-23
i already tried rythm box and it will not sync.  And do back ups and so on...people recommended amarok and banshee and neither worked so i have to see if itunes can be made to work with ubuntu

---

### Post by cogadh on 2011-04-23
It can't be made to work, Wine just doesn't have that capability (yet).

---

### Post by Joe of loath on 2011-04-23
You'd be better off spending your time getting Rhythmbox or Banshee to work.

---

### Post by cogadh on 2011-04-23
Or if you really must use iTunes, you can try installing Windows in a virtual machine, then installing iTunes in that. By all rights, that should work with no problems.

---

### Post by Nextgeneration on 2011-04-26
> **cogadh said:**
> Or if you really must use iTunes, you can try installing Windows in a virtual machine, then installing iTunes in that. By all rights, that should work with no problems.

To be honest I use my wifes laptop. She runs Win7 and has Itunes on there, download songs off youtube with a firefox addon then sound converter it and transfer. <--That and virtual box are the only real ways to do it, PlayOnLinux can't evan handle it. But I do agree spend your time with any of the free programs.

---

### Post by cogadh on 2011-04-26
> **Nextgeneration said:**
> PlayOnLinux can't evan handle it.
POL is just a front end for Wine, so it's really not surprising that it doesn't make a difference; POL can't do anything that Wine can't do.

---

