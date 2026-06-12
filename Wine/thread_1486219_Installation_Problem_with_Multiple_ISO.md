---
title: "Installation Problem with Multiple ISO"
date: 2010-05-17
forum: Wine
---

### Post by echoforever on 2010-05-17
[SIZE="1"]I'm trying to install a game from 2 ISO files.
I mount the ISO1 and run setup program. 

```
$ sudo mount -o loop '/home/echo/Downloads/cd1.iso' /home/echo/virtualdrive/cd1
$ wineconsole cmd
Z:\> D:\Setup.exe 
```

It goes fine until the point where it asks for the second CD.
I try to eject the CD from a new terminal.

```
$ wine eject
Cannot open device for drive d:
$ sudo umount /home/echo/virtualdrive/cd1
umount: /home/echo/virtualdrive/cd1: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

I manage to unmount with -l option, mount the second CD and press OK to continue installation. I get the same prompt to insert the second CD.

I have tried a lot of commands from various forums. None of them worked. Can anyone help me out?
[/SIZE]

---

### Post by asdfoo on 2010-05-18
> **echoforever said:**
> [SIZE="1"]I'm trying to install a game from 2 ISO files.
I mount the ISO1 and run setup program. 

```
$ sudo mount -o loop '/home/echo/Downloads/cd1.iso' /home/echo/virtualdrive/cd1
$ wineconsole cmd
Z:\> D:\Setup.exe 
```

It goes fine until the point where it asks for the second CD.
I try to eject the CD from a new terminal.

```
$ wine eject
Cannot open device for drive d:
$ sudo umount /home/echo/virtualdrive/cd1
umount: /home/echo/virtualdrive/cd1: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

I manage to unmount with -l option, mount the second CD and press OK to continue installation. I get the same prompt to insert the second CD.

I have tried a lot of commands from various forums. None of them worked. Can anyone help me out?
[/SIZE]


Did you run lsof to see what the problem was?

---

### Post by echoforever on 2010-05-18
[SIZE="1"]Setup.exe is the file causing umount to fail.
To confirm, I killed the process holding it and tried unmount without -l option.
Ofcourse I can't continue the installation after killing the process.[/SIZE]

---

### Post by hikaricore on 2010-05-18
Try copying the contents of the CDs to the hard drive and installing from there.
This always worked wonders for the multicd games I've installed in the past.

---

### Post by echoforever on 2010-05-18
[SIZE="1"]I have tried copying the contents to HD. I get the same problem.

I have tried the following:

1. Copy CD1 to HD and mount CD2
2. Copy CD1/CD2 to HD on seperate folders.
3. Copy CD1/CD2 to HD on seperate folders. Copy the contents of CD2 (folder) to CD1 (folder) when prompted for next CD.
4. Copy CD1/CD2 to HD on seperate folders. Rename CD1 (folder) to CD1_1 and CD2 (folder) to CD1.

I have found something interesting in cases 3 and 4.
Although I change the folder's contents, the contents in wine's instance remain unchanged. The contents change in wine after cancelling setup program and refreshing the explorer.
[/SIZE]

---

### Post by echoforever on 2010-09-16
[FONT="Arial"]Gave up![/FONT]

---

