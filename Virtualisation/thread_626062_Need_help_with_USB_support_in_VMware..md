---
title: "Need help with USB support in VMware."
date: 2007-11-28
forum: Virtualisation
---

### Post by Calybos on 2007-11-28
I need the WINXP virtual windows to be able to detect when i connect a USB device to it. 
Anyone able to help with this? Any would be greatly appreciated.

---

### Post by handzmonkey on 2007-11-28
Not that this helps you, but I had a lot of problems with VMWare player.  When I tried to plug in usb drives, VMWare would crash.  I have looked around and it seems to be an issue with player, I think VMware server is more stable but I don't know.  Might have better luck with that.

---

### Post by Calybos on 2007-11-28
To be more specific, I'm using Kubuntu with VMware server console. I'm really new to this also. What i need is.... I need phones to be detected by vmworkstation virtual XP machine so i can load applications onto them.

Thanks.

---

### Post by fjgaude on 2007-11-28
To get USB devices to work with Gutsy you need to uncomment four lines in a file:

```
sudo gedit /etc/init.d/mountdevsubfs.sh
```

Lines 42-45 get uncommented, starting with #mkdir -p /dev/bus/usb/.usbfs.

That should do it. Feisty didn't have these lines commented out. I don't know why Gutsy does.

---

### Post by fjodork on 2007-12-01
hmm... 

i uncommented the lines, restarted vmware server console and the virtual os, but still, in the VM - removable devices - usb devices meny it says EMPTY... 

i got a software in xp that needs a e.gate cyberflex usb dongle to work... :( 

ideas?

---

### Post by fjgaude on 2007-12-01
You need to reboot to have it right. Or

```
sudo /etc/init.d/mountdevsubfs.sh start
```

That should do it too.

---

### Post by happyhappyRN on 2007-12-02
fjgaude

You're the BOMB! I looked everywhere for the fix to this and you had it! Thanks man. \\:D/\\:D/\\:D/

---

### Post by fjgaude on 2007-12-02
Bravo, and congrates. Now set this post to [SOLVED] whoever started it.

---

### Post by psypher on 2007-12-04
I also had this problem, although I followed this post:

[http://ubuntuforums.org/showthread.php?p=3879483](http://ubuntuforums.org/showthread.php?p=3879483)

which worked immediately. 

Does anyone know why this issue has suddenly started with Gutsy and has 2 different fixes?

---

### Post by fjgaude on 2007-12-06
Doesn't seem those who know will speak up.

I've put more "solutions" into my main box without troubles, so... I do think this will likely be fixed in Hardy in April '08. All this stuff is moving so fast. Virtualazation is moving into its own. Just wait until Xen gets there, likely with Hardy.

---

### Post by n1ght28 on 2007-12-06
hey I've tried both the solutions and they have partially worked,the first time i tried them it worked but now it doesn't,  when i go to VM---> removable devices ---> usb     i can see my removable hard drive but when i check the box windows doesn't detect it properly, it has the usb icon in the icon tray then it says unknown device  in port one and port 2 unused. any suggestions, i have tried multiple reboots,:confused:

---

### Post by psypher on 2007-12-10
thats weird. I've tried my solution on more than on host and guest with no issues. I did have the "unrecognized device" error once but a reboot of the vm fixed that. Has your windows got all the latest updates and the vmtools installed? is the usb device unmounted from your host?

---

### Post by fjgaude on 2007-12-10
> **n1ght28 said:**
> hey I've tried both the solutions and they have partially worked,the first time i tried them it worked but now it doesn't,  when i go to VM---> removable devices ---> usb     i can see my removable hard drive but when i check the box windows doesn't detect it properly, it has the usb icon in the icon tray then it says unknown device  in port one and port 2 unused. any suggestions, i have tried multiple reboots,:confused:

Do the devices work in Linux?

---

### Post by chinaski on 2007-12-19
> **fjgaude said:**
> To get USB devices to work with Gutsy you need to uncomment four lines in a file:

```
sudo gedit /etc/init.d/mountdevsubfs.sh
```Lines 42-45 get uncommented, starting with #mkdir -p /dev/bus/usb/.usbfs.

That should do it. Feisty didn't have these lines commented out. I don't know why Gutsy does.
nice one mate! brilliant! thanks ;)

---

### Post by sethtriggs on 2008-02-05
> **fjgaude said:**
> To get USB devices to work with Gutsy you need to uncomment four lines in a file:

```
sudo gedit /etc/init.d/mountdevsubfs.sh
```

Lines 42-45 get uncommented, starting with #mkdir -p /dev/bus/usb/.usbfs.

That should do it. Feisty didn't have these lines commented out. I don't know why Gutsy does.

Worked for me too! THANK YOU SO MUCH!

I didn't know this was the issue!

-Seth

---

### Post by Porter Doran on 2008-02-06
Thanks, Fjgaude! Your instructions worked great for me, once I'd also executed this command:

```
sudo rmmod ehci_hcd
```

which [this webpage](http://www.zune-online.com/news/zune/zune-on-linux-via-vmware.html) says disables a problematic USB 2.0 driver. (Well, it is problematic to VMWare, which only supports USB 1.1)


> **fjgaude said:**
> To get USB devices to work with Gutsy you need to uncomment four lines in a file:

```
sudo gedit /etc/init.d/mountdevsubfs.sh
```

Lines 42-45 get uncommented, starting with #mkdir -p /dev/bus/usb/.usbfs.

That should do it. Feisty didn't have these lines commented out. I don't know why Gutsy does.

---

### Post by Dev'olution on 2008-02-10
Don't mean to bump this old thread, but I have the same problem except when i type in that stuff into the console i get:


kristian@kristian-laptop:~$ sudo /etc/init.d/mountdevsubfs.sh start
[sudo] password for kristian:
ln: creating symbolic link `/dev/bus/usb/devices' to `.usbfs/devices': File exists

Help please?

---

### Post by fjgaude on 2008-02-11
That maybe okay... you already have the file.

Do you have something like this in your fstab file:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Have you tried to access any USBs from within vmware, VM/Removable Devices menu?

---

### Post by Dev'olution on 2008-02-11
> **fjgaude said:**
> That maybe okay... you already have the file.

Do you have something like this in your fstab file:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Have you tried to access any USBs from within vmware, VM/Removable Devices menu?
How do I access my fstab file?

---

### Post by fjgaude on 2008-02-12
> **WestAussieUbu said:**
> How do I access my fstab file?

```
gksudo gedit /etc/fstab
```

Then add this line at the bottom of the file if it doesn't already exist:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Reboot. Let us know what happens.

---

### Post by smittyinside on 2008-02-27
> **fjgaude said:**
> To get USB devices to work with Gutsy you need to uncomment four lines in a file:

```
sudo gedit /etc/init.d/mountdevsubfs.sh
```

Lines 42-45 get uncommented, starting with #mkdir -p /dev/bus/usb/.usbfs.

That should do it. Feisty didn't have these lines commented out. I don't know why Gutsy does.
This worked for me too. Rock on frank!

---

### Post by ediulia on 2008-04-21
one more solution that works at ubuntu 7.10 whith vmserver 1.0.5 !!!!!!!!!
you need to put this line in /etc/fstab:

    usbfs /proc/bus/usb usbfs auto 0 0


and reboot (bit drastic), or just issue this command:

    mount -t usbfs none /proc/bus/usb


thanks to this link

[http://red_techstuff.blogspot.com/2008/02/usb-devices-empty-in-vmware-host-under.html](http://red_techstuff.blogspot.com/2008/02/usb-devices-empty-in-vmware-host-under.html)

---

### Post by doug-M on 2008-04-22
I've tried all of the above suggestions but haven't had any luck.

If anyone has any suggestions for debugging the issues I would love to hear it.

More discussion on this issue.
[http://ubuntuforums.org/showthread.php?t=598523](http://ubuntuforums.org/showthread.php?t=598523)

---

