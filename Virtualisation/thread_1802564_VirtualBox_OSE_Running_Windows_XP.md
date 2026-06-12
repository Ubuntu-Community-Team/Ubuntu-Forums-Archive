---
title: "VirtualBox OSE Running Windows XP"
date: 2011-07-12
forum: Virtualisation
---

### Post by NoFriends on 2011-07-12
Hi,

I'm running windows xp under virtualbox OSE, I am trying to connect my usb device to the virtualbox OSE instance, The application i am trying to run on windows xp does pick up the usb device, but it sticks on connecting, and generally does not finish connecting ?

I've left it a while to see if it just takes a long time, but 30 minutes later, still connecting.

Any help would be good.

Thanks in advance.

---

### Post by labinnsw on 2011-07-13
[You could try creating a share instead]("http://usablesoftware.wordpress.com/2010/05/21/virtualbox-share-folder-between-ubuntu-host-and-windows-xp-guest/"). This will give the added advantage of allowing you to access the USB simultaneously on Ubuntu and the virtual machine.

---

### Post by northwestuntu on 2011-07-13
> **NoFriends said:**
> Hi,

I'm running windows xp under virtualbox OSE, I am trying to connect my usb device to the virtualbox OSE instance, The application i am trying to run on windows xp does pick up the usb device, but it sticks on connecting, and generally does not finish connecting ?

I've left it a while to see if it just takes a long time, but 30 minutes later, still connecting.

Any help would be good.

Thanks in advance.

i think you need the full version for usb support.  go to main virtualbox site and download from there.

---

### Post by idlemind324 on 2011-07-13
As the previous poster put out you may need to upgrade your virtual box software.

What version of Ubuntu do you have and what version of Virtualbox specifically are you trying to use.

OSE was combined with the closed source version at 4.0 and beyond. They put all the closed source code in as extensions to the one version.

---

### Post by NoFriends on 2011-07-18
Sorry for the late response, I was away.

VIrtualbox is running version 4.0 and I'm currently running Ubuntu 11.04 the virtual xp instance can pick up the usb, and does try connecting, but it does not actually connect, just sticks at connecting for a very long time.

---

### Post by SeijiSensei on 2011-07-18
USB support only works in the proprietary version available from Oracle.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

You'll also need the "extensions pack."

If you follow the [instructions]("http://www.virtualbox.org/wiki/Linux_Downloads") to add the VB repository to your system, updates will be handled in the same way as they are for normal Ubuntu packages.

---

### Post by labinnsw on 2011-07-18
I use virtualbox OSE on Ubuntu 10.04 Host with Window 7 guest daily by sharing it on Ubuntu. I prefer it that way because I can access the USB driver simultaneously with Ubuntu and Windows. It is way easier to just share the drive.

---

### Post by SeijiSensei on 2011-07-18
> **labinnsw said:**
> I use virtualbox OSE on Ubuntu 10.04 Host with Window 7 guest daily by sharing it on Ubuntu. I prefer it that way because I can access the USB driver simultaneously with Ubuntu and Windows. It is way easier to just share the drive.

It sounds like you're talking about sharing a USB drive.  There are many other USB devices (cameras, keyboards, etc.) that I don't believe can be accessed other than via the proprietary version of VB.

---

### Post by CharlesA on 2011-07-18
> **SeijiSensei said:**
> It sounds like you're talking about sharing a USB drive.  There are many other USB devices (cameras, keyboards, etc.) that I don't believe can be accessed other than via the proprietary version of VB.

I think they can be accessed via VBox 4.0 that you get from the virtualbox site but I'm not sure if they work at USB 2 speeds since that needs the extension pack (the base package is open source.)

---

### Post by NoFriends on 2011-07-19
Thanks for your help, I will take a spend some time digging to see what i can find on their site.

---

### Post by John0009 on 2011-07-20
If you want to run the USB device with VirtualBox OSE then you need to udate the current version. I want to ask you that what's the version which you have been using. After updating this version then you will be able to connect the USB device.

---

### Post by NoFriends on 2011-07-20
As stated in my other posts, I'm running version 4.0 on Virtualbox

---

