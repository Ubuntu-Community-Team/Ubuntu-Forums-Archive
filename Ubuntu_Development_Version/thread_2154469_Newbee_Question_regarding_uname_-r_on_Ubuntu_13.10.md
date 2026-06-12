---
title: "Newbee Question regarding uname -r on Ubuntu 13.10"
date: 2013-06-14
forum: Ubuntu Development Version
---

### Post by mtbdrew on 2013-06-14
So have been regularly running software updater or sudo apt-get dist-upgrade and have seen Linux headers updates for both 3.9.0-5 and 3.9.0-6. However when doing uname -r it still shows 3.9.0-3-generic, should it be reading 3.9.0-6-generic?

---

### Post by arpanaut on 2013-06-14
Have you re-booted?
The OS would not be using the updated kernel until you do.

---

### Post by raimo on 2013-06-15
I have same problem with my 13.10 reboot did not help. But this helps me:
```
sudo grub-install /dev/sda
```and then reboot..

---

### Post by grahammechanical on 2013-06-15
Kernel updates usually require a restart. I just updated after missing Friday's update and kernel 3.9.0-6 came in. I had to restart and uname -a or uname -r says 3.9.0-6-generic. Kernel updates usually run update-grub and grub-install. On Thursday I was loading 3.9.0-5 and now (Saturday) I am loading 3.9.0-6.

Do you have another version of Ubuntu that controls Grub in the MBR? If so, you will need to load that other version of Ubuntu and run update-grub and grub-install. I just happen to have my saucy development version in control of the Grub in the MBR because I intend this install of Ubuntu to be a rolling development release.

Regards.

---

### Post by scradock on 2013-06-15
If you are using GRUB in the 13.10 install to start the machine it should not be necessary to run "grub-install" to get the new kernel; the installation process calls "update-grub", which will add the new kernel to the list and set it as the default.

However, if you are booting the machine using GRUB in another (more stable/reliable) install - which is a very good idea! - you will have to boot into that one and run "sudo update-grub" to add the new kernel for 13.10 to the list. Then, next time you boot, choosing 13.10 will boot with the updated kernel.

HTH

---

### Post by mtbdrew on 2013-06-15
I always reboot after updates even when it doesn't prompt me that should.
I did a standard install from USB drive of Ubuntu 13.10, there is no other OS on this system so the default grub that comes with the install should be in use. 
Okay now this is intersting, here is what I got on running command:

grub -version
The program 'grub' is currently not installed. You can install it by typing:
sudo apt-get install grub

Would seem Raimo as hit the nail on the head. Looks like the install did not install grub, is this normal or a bug with the iso install?

This is what I see running with this command:
rub-install -v
grub-install (GRUB) 2.00-14ubuntu1

Now I'm really confused, is grub installed or not? Okay so after some googling, is would appear I have Grub2 installed and the command Raimo gives is for legacy grub.

So back to my orginal issue, why is Grub2 not updating the kernel?

---

### Post by grahammechanical on 2013-06-15
You could trying installing Synaptic and using that to install or re-install kernel 3.9.0-6.

I have noticed that sometimes it takes a day or two for a kernel update to be completely installed. Kernel 3.9.0-5 came in two days running. But kernel 3.9.0-6 only needed on day's updates to activate. I think that sometimes some kernel packages are downloaded but not installed because other kernel packages are not yet in the repositories. It could be that the server repositories that you are using are a little out of sync with some of the other servers and so you are getting updates a little later than other people. I have noticed that this happens. Some come on this section saying that this or that has come through but I did not get it until I ran updates a second time and later in the day.

---

### Post by mtbdrew on 2013-06-15
I'm fairly sure the updates have been downloaded correctly already, they just are not being installed:

/usr/src$ ls -l
total 36
drwxr-xr-x 24 root root 4096 May 29 02:33 linux-headers-3.9.0-3
drwxr-xr-x  7 root root 4096 May 29 02:33 linux-headers-3.9.0-3-generic
drwxr-xr-x 24 root root 4096 Jun  5 18:28 linux-headers-3.9.0-4
drwxr-xr-x  7 root root 4096 Jun  5 18:28 linux-headers-3.9.0-4-generic
drwxr-xr-x 24 root root 4096 Jun 12 17:08 linux-headers-3.9.0-5
drwxr-xr-x  7 root root 4096 Jun 12 17:09 linux-headers-3.9.0-5-generic
drwxr-xr-x 24 root root 4096 Jun 14 17:55 linux-headers-3.9.0-6
drwxr-xr-x  7 root root 4096 Jun 14 17:55 linux-headers-3.9.0-6-generic
drwxr-xr-x  3 root root 4096 Jun  3 23:15 nvidia-313-updates-313.30



Installed Synaptic and saw that though the updates were downloaded and installed for kernel. The package linux-generic 3.9.0.6.7 was listed but not actually downloaded or installed. Marked this for installation and ran. Rebooted system and now get:

uname -a
Linux mythbox 3.9.0-6-generic #13-Ubuntu SMP Fri Jun 14 15:47:09 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Will be interesting to see if any future updates to the kernel get automaticall installed.

---

### Post by QDR06VV9 on 2013-06-15
> **grahammechanical said:**
> You could trying installing Synaptic and using that to install or re-install kernel 3.9.0-6.

 I think that sometimes some kernel packages are downloaded but not installed because other kernel packages are not yet in the repositories. It could be that the server repositories that you are using are a little out of sync with some of the other servers and so you are getting updates a little later than other people. I have noticed that this happens. Some come on this section saying that this or that has come through but I did not get it until I ran updates a second time and later in the day.


Glad to hear Im not the only one who has noticed this..
Thanks for posting grahammechanical

---

### Post by mtbdrew on 2013-06-15
So created a bug report for this and it was closed right away stating there is a difference in the headers and the kernel updates. According to the advice I have to set the linux-generic to automatic to get kernel updates installed using the updater. Question is how do I set this to automatic?

---

### Post by mtbdrew on 2013-06-16
Anyone know how to set the kernel updates for automatic?

---

### Post by zika on 2013-06-17
Go to Synaptic and check...
You should also have linux-kernel, linux-headers etc meta packages installed...
(As far as I know, bump-ing is not liked here... ;))

---

### Post by cariboo on 2013-06-18
> **zika said:**
> Go to Synaptic and check...
You should also have linux-kernel, linux-headers etc meta packages installed...
(As far as I know, bump-ing is not liked here... ;))

Bumping is fine here, as long as the op waits for 24 hours before doing so.

---

### Post by zika on 2013-06-18
> **cariboo907 said:**
> Bumping is fine here, as long as the op waits for 24 hours before doing so.):P So the times have changed... ;)

---

### Post by pfeiffep on 2013-06-18
> **zika said:**
> ):P So the times have changed... ;)

Wasn't there a song something like that --- The times   they are a changin:)

---

### Post by cariboo on 2013-06-18
<offtopic> We felt under the previous forum council that moderation was getting a little heavy handed, so we lightened up on things a bit.</offtopic>

---

