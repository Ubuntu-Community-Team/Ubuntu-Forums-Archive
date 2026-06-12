---
title: "Ubuntu Studio persistent USB installation"
date: 2013-04-17
forum: Ubuntu Studio
---

### Post by Octavarium on 2013-04-17
Hi everybody,

I've got an issue installing Ubuntu Studio on an USB stick.

I've used this tool: [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
With this version: [FONT=Lucida Grande][COLOR=#333333]Ubuntu Studio 12.04[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#333333]And  with about 3GO for persistent data.[/COLOR][/FONT]

[FONT=Lucida Grande][COLOR=#333333]It "works" as the stick is bootable, I can start Ubuntu Studio, but I cannot manage to have any persistence.[/COLOR][/FONT]
I mean : adding some shortcuts on the desktop, for example, in one session, is not "save" for the next one.

Does anyone here ever work with Ubuntu Studio in a USB stick or has any idea how I can solve the problem ?

Sorry if I haven't posted in the right place, and for my poor english.

---

### Post by TheFu on 2013-04-17
Running a full OS off any USB device, especially a USB2 device is less than ideal.  IME, USB has "queuing issues" when more than 2 or 3 items are requested simultaneously.  If you could partition the real machine HDD to make just 15G of storage available, then you could dual boot and have a 1000x better experience.

Sorry, but I don't have any  happy experience using that tool, I use **yumi** from the same folks and it almost always works well, but not always.

---

### Post by pfeiffep on 2013-04-17
> **Octavarium said:**
> Hi everybody,

I've got an issue installing Ubuntu Studio on an USB stick.

I've used this tool: [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
With this version: [FONT=Lucida Grande][COLOR=#333333]Ubuntu Studio 12.04[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#333333]And  with about 3GO for persistent data.[/COLOR][/FONT]

[FONT=Lucida Grande][COLOR=#333333]It "works" as the stick is bootable, I can start Ubuntu Studio, but I cannot manage to have any persistence.[/COLOR][/FONT]
I mean : adding some shortcuts on the desktop, for example, in one session, is not "save" for the next one.

Does anyone here ever work with Ubuntu Studio in a USB stick or has any idea how I can solve the problem ?

Sorry if I haven't posted in the right place, and for my poor english.

I'm not entirely certain my experience will help since I've only tried this with Ubuntu 12.10 and 13.04 but it probably will. 
Before you boot fully into Studio on the USB stick you need to 'instruct' the boot session to be persistent. This is achieved by depressing the F6 key at the time when a screen appears ([COLOR=#ff0000]**much before**[/COLOR] the options to choose whether to install or try. This should present a menu and F6 again is the key, if my memory is correct, there should be a command line presented on your screen - type the word 'persistent' (no quotes) and depress enter. 

Note - every time you boot you'll need to enable persistence
Below quote copied directly from this[ link]("https://help.ubuntu.com/community/LiveCD/Persistence")
> **[SIZE=4]Booting the Live CD in Persistent Mode[/SIZE]**

[COLOR=#333333][FONT=Ubuntu]Now we get to enjoy the fruits of our labor. Make sure your USB Stick is plugged into your computer and take the Live CD that you downloaded and burned earlier and put it in your CD drive (if it is not already there). Reboot your computer and boot up using this Live CD.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]**Before you reboot** there are only two things that you need to remember. When the Live CD menu gets displayed hit the <F6> key to enter “Other Options”. This will display the arguments that the Live CD passes to the kernel. At the end of this argument list just add a space and add the word “persistent”. This will instruct the Live CD to maintain and use persistence. That is all. Go for it![/FONT][/COLOR]


---

### Post by C.S.Cameron on 2013-04-17
A lot of people seem to have problems with Universal.
Try S5tartup Disk Creator from the Live CD or UNetbootin.

If pfeiffep's advice works for you, you can make persistence permanent by adding the word "persistent" to syslinux.cfg.

---

### Post by Octavarium on 2013-04-18
Hi !
Thanks for your help.
I've tried with "F6" and adding "persistent", but that didn't help.
So I've tried installing using Yumi, that didn't work too.

Then I've tried with **Lili**: [http://www.linuxliveusb.com/fr](http://www.linuxliveusb.com/fr)
And **ubuntustudio-12.10-dvd-amd64**, and it finally works !
I can boot with USB, and there's an start item "persistent", and now I can save my changes.

---

