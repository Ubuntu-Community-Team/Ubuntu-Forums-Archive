---
title: "Problem with oracle Virtual box 4.2.26"
date: 2014-09-27
forum: Virtualisation
---

### Post by prashant7526 on 2014-09-27
I have installed VirtualBox 4.2.26 and First Problem i see is ICON the icon is white for Vitualbox in my Ubuntu 14.04 as you can see:
[ATTACH=CONFIG]256731[/ATTACH]

Second problem what I have is, I have installed Linux Mint in virtualbox  and when i run it, Linux mint is not accessing any network. (Following is the network setting I have for Linux mint)
[ATTACH=CONFIG]256732[/ATTACH]

Third problem is when I run my Linuxmint from virtualbox it not installing Guest Adddition  following error it gives when I click on Install Guest Edition:
[ATTACH=CONFIG]256733[/ATTACH]

And Last problem What is this VBOX HARDISK? I cannot MOUNT it cannot remove it.. what is this in my Virtual OS?
[ATTACH=CONFIG]256734[/ATTACH]

---

### Post by ibjsb4 on 2014-09-27
VirtualBox 4.2.26?
I would start there by removing it.  Then go to the virtualbox site and download the latest (4.3.16).
v4.2 was released with 12.04 and if I remember right, it had problems with the Unity desktop.

---

### Post by prashant7526 on 2014-09-28
Thanks it all fixed except one problem left that is making the Virtual in full screen mode, as you can see

1. If I make full screen to my Virtual OS my Ubuntu side pannel and top   never disapear it always be there and my VitualOS start menu hide  behind  those as you can see. (please ignore the error box as it got solved).
[ATTACH=CONFIG]256764[/ATTACH]

2. The pink part is my Virtual OS mint.. and once I take it to the full  screen this pink screen of my Virtual OS remain like that and never  goes, till i dont shutdown anyhow my virtual box.
[ATTACH=CONFIG]256763[/ATTACH]

This is the problem which I faced and downgraded my Virtual OS to 4.2 :( 
Please suggest what is the issue with my VirtualBox Full screen.

---

### Post by rbmorse on 2014-09-28
Did you install the virutalbox extension pack?

---

### Post by prashant7526 on 2014-09-29
Yes, I have extension installed as you can see. but when i make full screen virtual box don't go completely full screen mode

[ATTACH=CONFIG]256803[/ATTACH]

---

### Post by slickymaster on 2014-09-29
*Moved to the ***Virtualisation*** sub-forum*

---

### Post by prashant7526 on 2014-09-29
still not solved sorry

---

### Post by slickymaster on 2014-09-29
Please run the following command in the guest OS:```
sudo apt-get install virtualbox-guest-dkms
```and once that's installed reboot the guest OS

---

### Post by prashant7526 on 2014-09-30
This is the error i got when I run the command you gave me. Please Help!

[ATTACH=CONFIG]256831[/ATTACH]

---

### Post by slickymaster on 2014-09-30
In order to install VirtualBox Guest Additions successfully, you need the linux-headers-generic, which might be missing in your case.

Open a terminal window and run:```
sudo apt-get install linux-headers-generic
```and afterwards try once again to install VirtualBox Guest Additions.

---

