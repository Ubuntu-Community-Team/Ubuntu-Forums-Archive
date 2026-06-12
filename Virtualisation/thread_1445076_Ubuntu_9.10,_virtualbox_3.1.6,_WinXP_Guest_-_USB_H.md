---
title: "Ubuntu 9.10, virtualbox 3.1.6, WinXP Guest - USB Harddisk diabled"
date: 2010-04-02
forum: Virtualisation
---

### Post by henrik23 on 2010-04-02
Hi,

I'm running a x64 ubuntu 9.10 with virtualbox 3.1.6.

I configured and installed a windows xp guest and activated the usb controller.
Then I added a filter for my western digital external harddisk.

But I can do anything and the entry in the USB menu will be diabled. I can not mount my usb harddisk to the virtual machine.

I tried:
- unmounting the harddisk from ubuntu --> entry diabled
- I started the virtual machine and then I plugged in the hdd --> entry diabled

What ca I do that the entry will be selectable?

Greets
Henrik

---

### Post by JustinR on 2010-04-03
Hi,

I've had this problem before.
In Ubuntu click Systems > Administration > Users and Groups

Unlock the Dialog

Click your username and click the button, "Properties"

Go to User privileges and check "Use VirtualBox"

Goodluck

---

### Post by henrik23 on 2010-04-05
I tried it- nothing.

Just to make it cleaar:
I **can** use USB devices. Just my external USB harddrive is gray.

---

### Post by teonghan on 2010-04-05
Hi henrik23,

When you said you can use USB devices, does that include printers and USB storages? Have you download and install the virtualbox guest addition in virtualbox?

---

### Post by henrik23 on 2010-04-05
It does include printer and card reader but no storage devices at all.

Edit:
GuestAdditions are of course installed.

---

### Post by teonghan on 2010-04-05
No sure this helps or not but last time what I did is go to System -> Administration -> Users and Groups, unlock it and go to "manage groups", find a group called "vboxusers" and add yourself to it. Restart and try using the USB storage and see. One more thing, I did not create filter for any of my USB devices in virtualbox and I can use all of them, no problem. I am not sure if this step is the same suggested by JustinR though.

---

### Post by henrik23 on 2010-04-07
I just looked and I was already member of this group

---

### Post by teonghan on 2010-04-07
Sorry, I am running out of idea...

---

### Post by eegerda on 2010-04-08
I've got a similar issue with centos 5.4 host and windows xp guest. I can't attached any usb devices (ipod nano, Nike+ wrist band) It used to work before I installed Virtualbox 3.1.6. I might just downgrade to and older version.

---

### Post by henrik23 on 2010-04-11
I heared from a friend that there might be a problem with AppAmor.
How do I deactivate AppAmor for VirtualBox?

---

### Post by eegerda on 2010-04-22
I'm not using Ubuntu but maybe this may help. I solved my problem by adding the following to line to my /etc/fstab file 

 ```
"none           /sys/bus/usb/drivers     usbfs devgid=501,devmode=664 0 0" 

```The devgid=501 is the group id of my vboxusers group. I rebooted my computer and everything worked which can be obtain by```
 cat /etc/group |grep -i box
``` In my case is 501 for you it may be different. 

This worked for me on Centos 5.4.

I found a post on a virtualbox forum that may be of help:
[http://forums.virtualbox.org/viewtopic.php?f=7&t=29356](http://forums.virtualbox.org/viewtopic.php?f=7&t=29356) 
Good luck

---

### Post by JohnnyAlpha8 on 2010-04-22
I had exactly the same problem and fixed it with these 5 steps:-

Step 1. Check that the user group ID vboxusers exists. If not, create the user group vboxusers using YaST -> System settings -> Advanced -> User Management.

Step 2. Discover the group ID (GID) number for group ID vboxusers. You can do this using -> System settings -> Advanced -> User Management ->  Groups and check show system accounts.  Scroll down to near the bottom of the list, where you should see the group name vboxusers with its group ID number to the right of vboxusers. Alternative way: grep vbox /etc/group as user root.

Step 3. Add the desired user ID (e.g. john) to the user group vboxusers. Click the button in the lower-right-hand corner labeled Finish.

Step 4. Add the following to the end of the file /etc/fstab:

none /proc/bus/usb usbfs devgid=XXX,devmode=664 0 0

where XXX is the group ID number you discovered in Step 2.

Also you should add the following to /etc/fstab and delete any other lines with usb:

/sys/bus/usb/drivers /proc/bus/usb usbfs devgid=XXX,devmode=664 0 0

and add following line to /etc/init.d/boot.local

mount -a

Step 5. Reboot.

---

