---
title: "Black screen after running boot repair from bootable USB."
date: 2015-03-02
forum: Windows
---

### Post by Aaron_Pool on 2015-03-02
[COLOR=#000000][FONT=Calibri]Hey all,
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]So, I ran boot repair off a ubuntu bootable usb. Basically, I'm trying to resurrect windows on my computer, because I seem to have botched the boot sector really badly. Well, it claims it repaired the boot sector, but when I try to boot my computer now, I just get a perpetual black screen. Any assistance would be super appreciated
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]My boot repair log URL: [http://paste.ubuntu.com/10509675/](http://paste.ubuntu.com/10509675/)&#8203;
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]Thanks!
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]Aaron[/FONT][/COLOR]

---

### Post by ajgreeny on 2015-03-03
I am not sure if boot-repair is able to repair a Windows only computer; I thought it was for a dual boot or Linux only machines but I may be wrong.

Did you run the recommended Windows backup/repair utility when you first got the machine in order to have a DVD or however it works for Win7?

If not you may be able to simply run the installation of a basic Windows MBR using the Ubuntu live system and using lilo as detailed below.  That used to work for WinXP which was the last version I ever used, butI'm not certain about Win7

RESTORE WINDOWS MBR FROM UBUNTU LIVE OS

You can install a Windows equivalent MBR to your sda drive by doing the following from your Live CD:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```You will probably get one or two error messages which you can ignore as they refer to your use of a live system

Then you should be able to boot directly into Windows again if all goes well. Let me know how it goes or if you run into problems.

---

### Post by Aaron_Pool on 2015-03-03
Thanks greeny, I'll give that a go. I haven't run the basic windows repair yet because I don't have a cd drive on my computer. An, of course, I being the dufas that I am, removed the sticker with the windows key from the bottom of my computer, so I can't just download the ISO from Windows.

I'll get back to you tonight with whether or not that worked.

---

### Post by Aaron_Pool on 2015-03-03
Alright Greeny, here's what happened.

I ran lilo, and it said that the back up boot file already existed, so no new back up was written, but the boot WAS updated. I rebooted and this time the manufacturer logo came up, which is new, and then it went to a black screen, like last time, but with a blinking cursor this time. I thought this might have fixed something with the boot sector, so boot-repair might be able to do more than it could before. I ran boot-repair again and, this time, I don't get any errors. Which, you know, is great. But the computer still isn't booting. Any other ideas?

Here's my update log: [http://paste.ubuntu.com/10520554/](http://paste.ubuntu.com/10520554/)

Thanks!
Aaron

---

