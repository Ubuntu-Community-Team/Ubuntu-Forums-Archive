---
title: "Ubuntu 9.10 and Virtual Box. USB Activation"
date: 2010-04-07
forum: Virtualisation
---

### Post by Dyffo on 2010-04-07
I have V Box 3.1.6 installed together with Guest Additions - All this is O.K. but I cannot get the USB support to function. In the VB settings menu I have my 4 USB devices labeled, the details menu says 4 filters are active. When I run VB these USB devices are shown but grayed out.Any advice please.

---

### Post by monicamaria on 2010-04-07
Yes, please help!  I am having the same trouble.  I checked and made sure that VB is NOT the OSE version.

---

### Post by vickoxy on 2010-04-08
Hi,
see here:
[http://forums.virtualbox.org/viewtopic.php?f=8&t=28178&p=125623#p125623](http://forums.virtualbox.org/viewtopic.php?f=8&t=28178&p=125623#p125623)

There are some problems with usb card readers and external hard drives-i can not use them. Only USB Sticks... and DVD Drive...

---

### Post by mkvnmtr on 2010-04-08
What guest do you have? In my experience clicking on install guest additions only mounts the ISO. Windows then automaticaly runs the installation file. On linux guests I have to run it myself.

---

### Post by vickoxy on 2010-04-09
Well, i have on my mac os installed few linux versions and win xp. I installed guest eitions on all of them, but mounting USB SD Readers, USB Hard Drives is impossible to me. Only (sometimes) i can mount USB Sticks...

---

### Post by Dyffo on 2010-04-09
Hi Guys - thanks for all your posts but so far I still cannot mount the U:S:B. All I want to do is run U.S.B off my stick to save messing about with CD/DVD.
My version of V.B. is from the Sun website, same with Guest Additions. I am not sure if I have the PUEL version as suggested.I believe that there is some way of activating the U.S.B thro' the ubuntu terminal, but I cannot remember or locate the commands.

---

### Post by wangsuda on 2010-04-09
> **Dyffo said:**
> I have V Box 3.1.6 installed together with Guest Additions - All this is O.K. but I cannot get the USB support to function. In the VB settings menu I have my 4 USB devices labeled, the details menu says 4 filters are active. When I run VB these USB devices are shown but grayed out.Any advice please.
The instructions you need are here: [http://ubuntuforums.org/showthread.php?t=1365287](http://ubuntuforums.org/showthread.php?t=1365287) But I will also post them here. This should get you up and running!

> **wangsuda said:**
> For those who run Karmic AND VirtualBox 3.1.2 and are having trouble getting your virtual systems to read and write to USB devices, here's an easy way to permanently fix that problem. This post is an addition to [http://ubuntuforums.org/showpost.php?p=6122145&postcount=4](http://ubuntuforums.org/showpost.php?p=6122145&postcount=4) by bodhi.zazen and is Karmic-specific.

1. Go to System>Administration>Users and Groups
2. Click on your user name and unlock
3. Click on "manage groups"
4. Scroll down until you see "vboxusers." Click on it and then on "Properties"
5. Click on any and all accounts you want to add to VirtualBox. This would generally be you. Don't click on root
6. Close everything
7. Reboot

TAH DAH! You are done! Now USB devices can be read and written to!

This will work for newer versions of VB as well.

---

### Post by mkvnmtr on 2010-04-09
If you downloaded from the Sun site you have the Puel version. As I said if your guest is a windows it should run the installation script when you mount the guest additions. If you have a linux guest open the guest additions and look for the file .sh autorun. Right click on it and you should be offered the option to execute. It will then run in its own little terminal. When it completes close the terninal and restart.
I suppose a windows that did not autorun the install script would work the same way but for me they always ran by themselves.
Sometimes when a linux distro did not offer me the option to execute the autorun file I have opened the terninal and typed sudo with a space and then draged the file to the terminal and pressed enter.

---

### Post by vickoxy on 2010-04-09
I am not of big help here-but i remember that sometimes under linux guests you can not run autoinstall.sh without sudo privileges. So, i opened terminal,  sudo -s, cd /home/desktop/VBox.../autorun.sh or something like that. And only after that i saw it install it.

BUT, on some linux distros -although i installed verything properly, guest additions were not there...
So, root privileges.

---

### Post by vickoxy on 2010-04-09
> **wangsuda said:**
> The instructions you need are here: [http://ubuntuforums.org/showthread.php?t=1365287](http://ubuntuforums.org/showthread.php?t=1365287) But I will also post them here. This should get you up and running!



This will work for newer versions of VB as well.

I know it is off topic, but is there some simple fix for mac os host to make it work?

---

### Post by wangsuda on 2010-04-09
> **vickoxy said:**
> I know it is off topic, but is there some simple fix for mac os host to make it work?
I don't know Mac OS, so sorry, I can't be of any help.

---

### Post by Dyffo on 2010-04-09
> **wangsuda said:**
> The instructions you need are here: [http://ubuntuforums.org/showthread.php?t=1365287](http://ubuntuforums.org/showthread.php?t=1365287) But I will also post them here. This should get you up and running!



This will work for newer versions of VB as well.


[COLOR="Red"]THANK YOU - BRILLIANT - ALL MY USB DEVICES WORK.[/COLOR]

You are a true Genius.:lolflag:

---

### Post by wangsuda on 2010-04-09
Glad to help. Genius? No, just half-way decent with VB! LOL

---

### Post by vickoxy on 2010-04-10
> **wangsuda said:**
> The instructions you need are here: [http://ubuntuforums.org/showthread.php?t=1365287](http://ubuntuforums.org/showthread.php?t=1365287) But I will also post them here. This should get you up and running!



This will work for newer versions of VB as well.

Just to say thanks-just installed win xp on ubuntu host and all my usb devices seem to work ok. Amazing how big difference is in ubuntu and mac os host. And i use only 256 MB Ram on virtualbox for win xp (ubuntu 9.10) and it looks like it works faster as on mac os host.

---

### Post by wangsuda on 2010-04-11
> **vickoxy said:**
> Just to say thanks-just installed win xp on ubuntu host and all my usb devices seem to work ok. Amazing how big difference is in ubuntu and mac os host. And i use only 256 MB Ram on virtualbox for win xp (ubuntu 9.10) and it looks like it works faster as on mac os host.Glad everything worked for you! Happy computing!

---

