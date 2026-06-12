---
title: "Installing Virtualbox Guest Add-ons"
date: 2008-06-10
forum: Virtualisation
---

### Post by Jidderstein on 2008-06-10
I've recently upgraded to the latest version of Virtualbox (1.6.2) and the upgrade took care of some of the previous issues i was having. The new problem is that the guest add-ons won't install. 

It worked perfectly on the older version but now nothing happens when i click "install guest add-ons" from the devices drop-down menu while the VM (windows xp) is running. I have a working internet connection both inside the VM and in Ubuntu.

Also, I have the virtual disk image for the VM on an external hard drive this time (it was on the internal disk previoulsly). Maybe that has something to do with it?

---

### Post by benhur99ph on 2008-06-10
The method that I used is a bit different. While my VM (winxp) is running, Click on Devices>Mount>Mount CD/DVD image  --  then I selected the ISO of the GuestAdditions. After that, I went to My Computer (winxp --VM) and the GuestAdditions is mounted on the CD drive. Double clicked it and installed. 

Hope this works for you. :D

---

### Post by Jidderstein on 2008-06-10
> **benhur99ph said:**
> The method that I used is a bit different. While my VM (winxp) is running, Click on Devices>Mount>Mount CD/DVD image  --  then I selected the ISO of the GuestAdditions. After that, I went to My Computer (winxp --VM) and the GuestAdditions is mounted on the CD drive. Double clicked it and installed. 

Hope this works for you. :D

Thanks for the reply. I tried your suggestion but still nothing happened. One thing to point out though, there were two images under the CD/DVD images tab:  

VBoxGuestAdditions.iso 
VBoxGuestAdditions_1.5.6.iso

The 1.5.6 is probably left over from my previous VM before I started over. I tried both but neither did anything at all

---

### Post by johnny5@5 on 2008-08-28
I tried your method which seemed to make sense to me and got:


A disk image with UUID {80fecff5-9a8a-4ecb-799e-fc522ff55720} or file path '/home/johnny5/.VirtualBox/VBoxGuestAdditions_1.5.6.iso' is already registered.


Result Code: 
0x80070057
Component: 
VirtualBox
Interface: 
IVirtualBox {76b25f3c-15d4-4785-a9d3-adc6a462beec}

 The whole point of me checking out this thread is to try to get my mouse captured, any other ideas or am I just going about this all wrong?

Any help would be greatly appreciated

Thanks

---

### Post by johnny5@5 on 2008-08-28
Interestingly enough my mouse is captured while using KDE, leads me to believe might be a dependency issue...any thoughts? Ive  already installed the following from virtualbox.org just for piece of mind:  :)

 gcc g++ bcc iasl xsltproc xalan libxalan110-dev uuid-dev \
 zlib1g-dev libidl-dev libsdl1.2-dev libxcursor-dev \
 libqt3-headers libqt3-mt-dev libasound2-dev libstdc++5 \
 libhal-dev libpulse-dev


If any other info needed, please inquire

Thanks again!

---

