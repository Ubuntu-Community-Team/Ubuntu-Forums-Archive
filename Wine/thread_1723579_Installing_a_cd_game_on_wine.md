---
title: "Installing a cd game on wine"
date: 2011-04-07
forum: Wine
---

### Post by darknuts on 2011-04-07
How do I install a CD program into wine? I'm trying to run this game and I figure out how to get it to run and install. I'm running ubuntu 10.4. Thanks for your help.

---

### Post by IHeequ5i on 2011-04-07
It would help if you gave us more details:

What game are you trying to install? 

What are you doing to try to install it?

Have you checked WineHQ AppDB to see if anyone else has worked on it?

In general:
Put the CD in the drive
Open a Terminal and cd to the cd drive.
Do an "ls" to get the exact name of the installer.
Launch the installer with "wine nameofinstaller.exe"

Remember that Linux is case sensitive, so Setup.exe and setup.exe are two different things.

---

### Post by darknuts on 2011-04-12
Well, the problem is pretty general. I just want to know the process for installing from a CD. I have the same problem with all of my cd programs. I open the cd file and right click setup and select 'open with wine'. Then I get an error message. The game I wanna install is need for speed undercover and It is on the wine website.

---

### Post by darknuts on 2011-04-12
I tried to cd and install and this is what i got. 

```

bearcat@bearcat8f:~$ cd /media
bearcat@bearcat8f:/media$ wine setup.exe
wine: cannot find L"C:\\windows\\system32\\setup.exe"
bearcat@bearcat8f:/media$ 

```

Not sure what I'm doing wrong.

---

### Post by Hairy_Palms on 2011-04-12
i very much doubt your cd drive is under just /media, it will be /media/cdrom0 or somthing similar, you can install nautilus-open-terminal from synaptic and it will open at ur location.

> wine: cannot find L"C:\\windows\\system32\\setup.exe"

means theres nothing called setup.exe so wine is looking inside its fake windows directory but of course the file isnt there its on the disc. so first make sure your actually in the disc's directory and that your spelling setup.exe correctly case-wise.

---

### Post by cogadh on 2011-04-12
You shouldn't need to change directories to the CD/DVD to run the setup and honestly, you really shouldn't do that if the install involves multiple CDs, as being "in" the the CD/DVD directory will prevent you from properly ejecting and mounting the new CD. All you should need to do is identify the correct directory and run it from outside it:
```
wine /media/cdrom0/setup.exe
```
Obviously, replace that "cdrom0" with the correct mount name.

---

### Post by darknuts on 2011-04-12
Thank you for the information. I was able to download open-nautilus-terminal. How do I use it? I tried to find out my device name via the terminal and I came up with this:

```

bearcat@bearcat8f:~$ [COLOR=SeaGreen]ls /dev/disk/by-label -lah[/COLOR]
total 0
drwxr-xr-x 2 root root  80 2011-04-12 23:47 .
drwxr-xr-x 6 root root 120 2011-04-10 22:30 ..
lrwxrwxrwx 1 root root  10 2011-04-10 22:30 Maxtor\x20External -> ../../sdb1
lrwxrwxrwx 1 root root   9 2011-04-12 23:47 [COLOR=Blue]Starry\x20Night\x20Ent -> ../../sr0[/COLOR]
bearcat@bearcat8f:~$ [COLOR=Red]cd /media/sr0[/COLOR]
bash: cd: /media/sr0: [COLOR=Red]No such file or directory[/COLOR]
bearcat@bearcat8f:~$ cd /media/sr0/
bash: cd: /media/sr0/: No such file or directory

bearcat@bearcat8f:~$ [COLOR=SeaGreen]ls /dev/disk/by-id -lah[/COLOR]
total 0
drwxr-xr-x 2 root root 320 2011-04-10 22:30 .
drwxr-xr-x 6 root root 120 2011-04-10 22:30 ..
lrwxrwxrwx 1 root root   9 2011-04-10 22:30 ata-ST31000340NS_5QJ025JX -> ../../sda
lrwxrwxrwx 1 root root  10 2011-04-10 22:30 ata-ST31000340NS_5QJ025JX-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2011-04-10 22:30 ata-ST31000340NS_5QJ025JX-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2011-04-10 22:30 ata-ST31000340NS_5QJ025JX-part5 -> ../../sda5
lrwxrwxrwx 1 root root   9 2011-04-10 22:30 scsi-SATA_ST31000340NS_5QJ025JX -> ../../sda
lrwxrwxrwx 1 root root  10 2011-04-10 22:30 scsi-SATA_ST31000340NS_5QJ025JX-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2011-04-10 22:30 scsi-SATA_ST31000340NS_5QJ025JX-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2011-04-10 22:30 scsi-SATA_ST31000340NS_5QJ025JX-part5 -> ../../sda5
lrwxrwxrwx 1 root root   9 2011-04-10 22:30 usb-Maxtor_6_L300R0_00001914-0:0 -> ../../sdb
lrwxrwxrwx 1 root root  10 2011-04-10 22:30 usb-Maxtor_6_L300R0_00001914-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root   9 2011-04-10 22:30 wwn-0x5000c5000289f920 -> ../../sda
lrwxrwxrwx 1 root root  10 2011-04-10 22:30 wwn-0x5000c5000289f920-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2011-04-10 22:30 wwn-0x5000c5000289f920-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2011-04-10 22:30 wwn-0x5000c5000289f920-part5 -> ../../sda5
bearcat@bearcat8f:~$ 

```

The starry night/sr0 thing is what I am trying to open. I typed in cd /media/sr0 and I got a 'directory not found' message.

---

### Post by cogadh on 2011-04-12
You shouldn't have needed to download anything, Ubuntu already has a terminal app under "Accessories" in the Applications menu that can do everything you need, though I can see how the "nautilus-open-terminal" package might be useful. As for actually using it, all that does is add an "Open in terminal" option to your right-click menu, so you just need to find the right directory in Nautilus, then right-click on it.

The actual CD mount point should simply be /media/<whatever label your CD has>. If you open a terminal and type "cd /media/St" then hit TAB, it should auto-fill the rest of the mount point name correctly (assuming that it is named something like "Starry Night"). Alternatively, if you allow the disk to mount normally then browse through Nautilus to the /media directory, you should see the actual mount name there.

---

### Post by darknuts on 2011-04-13
I tried typing part of the cd name and hitting tab but it didn't work. I also tried the wine command  'wine /media/Starry Night Ent/setup.exe' but it couldn't find the directory. Starry Night is the name of the CD I'm trying to install. The nautilus-terminal thing isn't working for me either. This is so frustrating. Is there a terminal command that will just list your device names for you?

---

### Post by cogadh on 2011-04-13
The problem is the spaces in the name, the terminal can't recognize them on its own. If the CD actually mounted using "Starry Night Ent" as the mount name (that would honestly be a surprising name for a CD), then you need to run the command like this:
```
wine /media/Starry\ Night\ Ent/setup.exe
```
The backslashes before each space will allow the terminal to recognize the spaces.

As for identifying the name, you seem to be making it far too complicated. If you insert the CD and allow it to mount, it should both create a shortcut on your desktop as well as a directory within the /media directory with the same name. That is the name you need to use in the command path. For example, when I put my Freelancer install CD in, it creates a shortcut on my desktop and a directory in /media called "FL_v1". If I were to try to install the game with Wine, I would simply run this command:
```
wine /media/FL_v1/setup.exe
```
For each CD/DVD I use, the directory name will be different, but the usage is the same.

---

### Post by darknuts on 2011-04-13
LOL!!! Thanks! It worked! 8-)  The problem was the spaces. And Starry Night Ent was the actual CD name. Thanks again for the help! This problem is officially solved!\\:D/

---

