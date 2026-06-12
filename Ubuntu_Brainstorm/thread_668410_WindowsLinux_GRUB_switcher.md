---
title: "Windows/Linux GRUB switcher"
date: 2008-01-15
forum: Ubuntu Brainstorm
---

### Post by zekopeko on 2008-01-15
Wouldn't it be nice to have a small applet in the panel with which you could 
set GRUB to switch on the next restart to Windows as the default OS and 
we should also have a small app in tray on Windows to switch to Ubuntu on the next reboot.
The application for Windows should be on the Ubuntu disk so that it can be easily installed.

Me thinks Mac's have that when you dual boot Win/OS X.

---

### Post by maybeway36 on 2008-01-15
Windows would need to have the ext3 driver installed.

---

### Post by zekopeko on 2008-01-15
or /boot as fat32 by default.

---

### Post by EXCiD3 on 2008-01-15
if /boot was fat32 then it would be awfully easy to whip up something like this. if i had the time i might look into doing something like that, but im pretty busy cuz between school and ladies, what free time could i possibly have? ;)

---

### Post by lexen on 2008-01-15
I am not a programmer, but you could simply have it so if you press shift then restart (or something like that) it would load your boot options.  When you click the option in GRUB that you like, it would write a temporary file in /boot that would change the default boot option in GRUB to what you chose.  Because it is a temporary file, it would change back when GRUB loads up so you don't have to worry about that the next time.  This would not work for windows, but I think you would need someone to write a windows program for that.

---

### Post by zekopeko on 2008-01-15
i think that we should look the way mac does it. i don't think that they set a special fat32 partition just so that they could switch between OSX and Win

---

### Post by smartboyathome on 2008-01-15
I don't get why... when my comp boots up I just choose what I want and then walk away. It only takes a few seconds to go from cold off to grub.

P.S. I haven't been in my Windows install in 3 months, so I don't use GRUB a lot anyway. :p

---

### Post by Tiekyl on 2008-01-15
It's definently a decent idea. A lot of my family members get kinda scared away when I tell them they have to select windows at startup to use it. It might be more hassle than its worth, but the benefit is definently there.

---

### Post by maybeway36 on 2008-01-15
An Ubuntu tray icon would be easy to program. A windows one might work but only it /boot is FAT (can you do this?)

---

### Post by zekopeko on 2008-01-15
> **maybeway36 said:**
> An Ubuntu tray icon would be easy to program. A windows one might work but only it /boot is FAT (can you do this?)

are you sure that it would only work with fat32? i would like to know how mac's do it because this idea is originaly from apple.

---

### Post by st4rdr1ft3r on 2008-01-15
You are going way too complex :)

```
grub-reboot <windows-entry-in-menu.lst>
```

Not 100% it works though.

---

### Post by zekopeko on 2008-01-16
> **st4rdr1ft3r said:**
> You are going way too complex :)

```
grub-reboot <windows-entry-in-menu.lst>
```

Not 100% it works though.

and what about the windows side of the deal? how would you boot from windows to ubuntu/linux?

---

### Post by Whiffle on 2008-01-16
I'm disappointed in yalls google skills:

[http://www.cs.unm.edu/~dmohr/grub.php](http://www.cs.unm.edu/~dmohr/grub.php)

---

### Post by smartboyathome on 2008-01-16
The problem with the windows side of the problem is that if you are running a 64-bit machine, there is no driver for EXT3, so you have to have your boot partition be FAT32. This can be a hassle for systems which are already installed.

---

