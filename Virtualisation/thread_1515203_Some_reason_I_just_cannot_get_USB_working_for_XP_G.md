---
title: "Some reason I just cannot get USB working for XP Guest on Virtual Box.."
date: 2010-06-22
forum: Virtualisation
---

### Post by morbidxbean on 2010-06-22
I have installed the CLOSED SOURCE version of Virtual Box,  enabled USB in the settings  and USB 2.0 EHIC controller....and also added the items I wish to be detected,   I found several guides on the net and alot of them say to add

## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=125,devmode=664 0 0

Or very similar to my /etc/fstab file

I still cant seem to get any luck of picking up my flash drive, external HD, Ipod, or USB Wireless adapter

---

### Post by Tylerjd on 2010-06-22
I have also had problems with USB devices. First, make sure you have the guest additions installed. 
I have never used Virtual Box on ubuntu let alone any version of Linux, but I know the Mac OSX version of vb, you have to unmount the flash drive/ device for VB to recognize and grab it. I don't know if you can do that to a wifi adapter, but I don't understand why you would need to mount it on VB b/c you already have to built in networking using NAT or bridging.

---

### Post by morbid_bean on 2010-06-22
well installed the guest additions and also tried the unmounting, neither worked  :confused:

---

### Post by revolverXD on 2010-06-22
go to system->adminstration->user and groups->add yourslef to the groups lp and vboxusers.

if it wont work try setting up a rule to VM type lsusb check the id of the device you try to connect go to setting->usb->add filter a put it the name of the device and the vendor device for example if i use lsusb i get:

Bus 002 Device 005: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/2/4GB Flash Drive
vendor id:0781
name: SanDisk Corp. Cruzer Micro 1/2/4GB Flash Drive

---

### Post by larry.said on 2010-06-22
I had the exact same problem. 

First add yourself to the group vboxuser as was said earlier. Install guest additions then reboot both the guest and the host. Start your VM and connect your USB thumb drive to your computer. 
In the bottom right of the virtualbox window click on the USB icon and select your thumb drive.

The thumb drive icon should dissapear from your ubuntu desktop and find its way into your VM

---

### Post by morbid_bean on 2010-06-22
Thanks revolverXD!  simply adding myself to the lp group fixed this issue, however I did have some mouse and CD drive complications....but I fixed those...

Again thanks for the help guys. ):P

---

### Post by revolverXD on 2010-06-23
my pleasure m8 :)

---

