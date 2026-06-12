---
title: "starcraft 2 help??"
date: 2010-08-01
forum: Wine
---

### Post by jberrystl on 2010-08-01
i have ubuntu10.4 and a noob iv been following some tuorials i found through google but am getting no where, everytime i open installer.exe it says no install files found. i am using an external dvdrom via usb because my internal took a crap on me. i cant mount and unmount the drive through the terminal but i can through the drive utility still no help for me.
any help would be appreceiated, or even just point me in the direction of where to get help
thanks

---

### Post by cariboo on 2010-08-01
Moved to the Wine sub-forum.

---

### Post by robsoles on 2010-08-02
> **jberrystl said:**
> i have ubuntu10.4 and a noob iv been following some tuorials i found through google but am getting no where, everytime i open installer.exe it says no install files found. i am using an external dvdrom via usb because my internal took a crap on me. i cant mount and unmount the drive through the terminal but i can through the drive utility still no help for me.
any help would be appreceiated, or even just point me in the direction of where to get help
thanks

That's odd - I wonder if you are just double clicking it and not actually right-clicking it and choosing 'open with wine ..." option from that menu.

Get WINE (Just guessing but I reckon you probably don't even have WINE) and have a squiz at a thread I participated in recently [http://ubuntuforums.org/showthread.php?t=1534751](http://ubuntuforums.org/showthread.php?t=1534751)

---

### Post by dardack on 2010-08-02
> **jberrystl said:**
> i have ubuntu10.4 and a noob iv been following some tuorials i found through google but am getting no where, everytime i open installer.exe it says no install files found. i am using an external dvdrom via usb because my internal took a crap on me. i cant mount and unmount the drive through the terminal but i can through the drive utility still no help for me.
any help would be appreceiated, or even just point me in the direction of where to get help
thanks

You have to mount the drive with unhide command.

So your usb cdrom drive, you have to figure out the /dev/ device it's mounted on.  If you can mount with the drive utility, open a terminal after mounting and do a:

```
df -h
```

Once you figure out the device it's on, unmount it, then run this command:

```
mount -o ro,unhide,uid=1000 /dev/cdrom /mnt/cdrom
```

where /dev/cdrom is the device you determined in the step above. Also, make sure the directory /mnt/cdrom exists, or choose your own directory where you want it mounted.  Blizz uses some DRM on the dvd, but basically just hides the files or something.  The unhide lets you see them.

Also, for all your starcraft2/wine help:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882)

---

