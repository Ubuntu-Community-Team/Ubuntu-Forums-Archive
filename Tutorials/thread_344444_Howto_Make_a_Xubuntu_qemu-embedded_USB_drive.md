---
title: "Howto: Make a Xubuntu qemu-embedded USB drive"
date: 2007-01-22
forum: Tutorials
---

### Post by revoltism on 2007-01-22
Ok, guy's this is my first try to make a howto.. so bare with me..

I bought a cheap Transcend JetFlash V10 4 gig USB stick and decided to make it emulate linux. I needed this as I have Windows XP at work with a no install policy. 
First i tried an DSL-embedded install witch worked as a charm but I love Ubuntu so i decided to try Xubuntu. I could not find a howto so here it is.


#1#

First you need to download the latest 
[xubuntu-feisty-alternative-i386 herd2]("http://cdimage.ubuntu.com/xubuntu/releases/feisty/herd-2/")
[qemu-0.8.2-windows]("http://fabrice.bellard.free.fr/qemu/download.html")
[syslinux-3.31]("http://www.kernel.org/pub/linux/utils/boot/syslinux/").

#2#

I don't know if syslinux acctually is needed if you you only want to emulate as it is an alternative bootloader. Use only if you like boot from usb.
In the command promt (change X: to youre USB drive letter) and restart.
```
syslinux.exe X:
```


#3#

Format the USB to fat32 (right click on usb in explorer).
Extract and copy/paste the qemu folder to the USB flash drive and make a hda.img (virtual hdd).

In the command promt (win+r and cmd):
```
qemu-img.exe create -f qcow hda.img 3800M
```

Install Xubuntu to the virtual drive (hda.img)

Still in command promt:
```
qemu.exe -L \qemu -cdrom path-to-xubuntu-cd-img.iso -hda hda.img -m 256 -boot d
```

"-boot d" is only for booting the cdrom later you change it to "-boot c" whitch are to boot from the virtual hdd. I used a command-line system install to get it minimum (350 MB without X windows etc). This is all written [here]("https://help.ubuntu.com/community/Installation/LowMemorySystems?highlight=%28command-line%29%7C%28system%29"). I choosed Thunar, Dillo, Firefox and XFCE (ofcourse). I picked this cause i like blingbling and don't mind little lagg (if to much i go console). not rekommended for slower boxes. 


#4#

Make a xubuntu.bat file and put it in the root of youre USB.

In Notepad and rename to xubuntu.bat:
```
REM Start qemu on windows.
@ECHO OFF

START qemu\qemu.exe -L qemu\ -no-kqemu -localtime -hda qemu\hda.img -cdrom path-to-xubuntu-cd-img.iso -m 256 -boot c

CLS
EXIT
```

In the below Qemu link you can read what all the options means. If you get in to troubble delete the -cdrom with path and you might want to change -m 256 to 64 or 128 the "-m" indicates ram.


Sources i had help from:
[Qemu Official]("http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC12")
[QemuOnWindows]("http://kidsquid.com/cgi-bin/moin.cgi/QemuOnWindows#head-4d3f2df4b7b962a7c2e4110dd7d4a2850bbaa0d8")

---

### Post by austin on 2007-02-12
Great idea!!!

How much of your xubuntu and your hardware works under qemu actually? Have you used it intensively?

---

### Post by revoltism on 2007-02-12
Really good... 

I was just happy able to save when i did something at work. Save all the homepages to bookmarks and so on...

I have tried it some weeks and prefere installing at home cause i have a faster computer (core 2) home than at work (p4). I mostly just surf and talk to friend trough aMSN... I don't think Gimp and such will work.. oh well have to go

---

### Post by xwang on 2011-10-21
Hi, I would like to know if qemu must be installed on the hos system or if it is installed only on the USB driver.
Moreover I wasn't able to find the qemu windows version.
Can you help me?
Thank you,
Xwang

---

### Post by Ohwii on 2012-10-25
Can anyone post a updated Version of this Howto. The links are dead. that would be the bomb.

cheers 

Wii

---

### Post by Aphotic on 2013-04-25
> **Ohwii said:**
> Can anyone post a updated Version of this Howto. The links are dead. that would be the bomb.

cheers 

Wii

I was able to combine the information here with the files available for download at [this]("http://www.pendrivelinux.com/use-qemu-to-boot-linux-from-windows/") pendrivelinux tutorial to build my own crunchbang VM that loads from USB.

I removed all the stuff regarding kqemu from the StartLinux.BAT so it looked something like this:
```

@echo OFF
cls
echo. 
echo LINUX IS NOW RUNNING, Do not close this windows while linux is running!
echo Close only once Linux has shutdown (after the prompt to eject CD)
.\qemu\qemu.exe -L .\qemu\ -no-kqemu -hda hda.img -cdrom *.iso -localtime -m 256 -soundhw all  -boot d
pause

```

Just remember the steps by the OP to craft the HDD first and to change -boot d to -boot c after your first boot and OS install.
Also note that I have my cd iso and virtual hda.img in the same directory as the StartLinux.bat

---

### Post by Aphotic on 2013-04-26
Since the default QEMU NIC is dated and crunchbang wouldn't support it out of box I changed my load command to this:
```

.\qemu\qemu.exe -L .\qemu\ -no-kqemu -cdrom *.iso -hda hda.img -localtime -m 256 -soundhw all -net nic,model=rtl8139 -boot c

```

---

