---
title: "Adaptec aacraid 6805 6405, v 1.1.7-28000"
date: 2011-06-22
forum: Server Platforms
---

### Post by Entilza on 2011-06-22
I'm building a new server with an Adaptec 6805 controller and ran into version problems with the current drivers on Adaptec and the current version of Ubuntu.

The drivers on the Adaptec website are for 10.04.01 (Kernel 2.6.32-24) However Ubuntu now released 10.04.02 (Kernel 2.6.32-28).  This makes using insmod aacraid.ko fail due to version differences.

I then downloaded the linux drivers source and was trying to figure out how to get the older kernel source.  Took forever but somehow I managed to get it to work by using "dkms" to build the module for the older kernel.

This worked for Step 1 of the installation to actually get Ubuntu to recognize the aacraid driver.  (insmod aacraid.ko) finally worked

However step 2 after Ubuntu is installed is to copy an old initrd from 2.6.32-24 again I would think this would be a problem.  So I used mkinitramfs to create a proper initrd.img-2.6.32-28-server with the new aacraid.ko driver.

I never tried this step because currently I just have the card I am still waiting for some hardware to continue the rest of the build so I am unable to test this, but I will monitor this thread and provide any info.

I've attached aacraid.ko that I was able to successfully detect on 10.04.02.

Here is the initrd:  [initrd.img-2.6.32-28-server]("http://www.2shared.com/file/-OfbIUCO/initrdimg-26.html")

If this works I'll link it to a better spot in future.  I should have the hardware next week so I will definitely be able to confirm this but if someone needs this right away then please let me know how it worked out.

*********************************************
UPDATE (Jun 23,11)

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)  contains Ubuntu 10.04.01  where you can download the exact version of Ubuntu that is currently supported for the Adaptec 6805 / 6405 / etc.  From here you can then upgrade to 10.04.02 but you would still have to compile the aacraid driver into the kernel.

I should be getting the remaining hardware for the server next week so I will post more info later.
*********************************************

**Note:  These are 64-bit versions**

---

### Post by Entilza on 2011-06-30
I finally got around to testing these drivers yesterday and they work!  So that will get you into the current 10.04.02 with your Adaptec 6805 / 6405 / etc.

Once there you can download one of the latest kernels but at least you will have a base system to start with and fall back to if there are any issues with compiling the driver into the kernel afterwards.

I'll have to blog about my server build somewhere it was truly a funny experience given everything that had occurred. Building a custom rack server from scratch with just common components works but you really have to research each and every component.

---

### Post by moprmac on 2011-07-11
So how did you get the 6805 working on 10.04.2?  Can you provide a little more detail, I have been fight with this for a few days and you seem to be the only one I can find.

I appreciate any help you can offer, but could use more detail as I am a linux noob:confused:

Also I am using the card for additional drives, not the os drives, so I already have 10.04.2 running.

Thanks!

---

### Post by Zonesa on 2011-07-12
Can you provide a little how-to about your fix : I'm trying to install Ubuntu with this card without any success. 

The following distros are not supported on this card (6405) : 

- Ubuntu/Debian
- CentOS 5.x
- VMware ESXi (Work on ESX but poor write performance)
- Citrix XenServer 5.x

Headhash.

---

### Post by Entilza on 2011-07-13
> **moprmac said:**
> So how did you get the 6805 working on 10.04.2?  Can you provide a little more detail, I have been fight with this for a few days and you seem to be the only one I can find.

I appreciate any help you can offer, but could use more detail as I am a linux noob:confused:

Also I am using the card for additional drives, not the os drives, so I already have 10.04.2 running.

Thanks!

Download my aacraid.ko  and try to use "insmod aacraid.ko" if it loads into memory you should be good to go.  if you do a "lsmod" you should see "aacraid" in the list.  You can then copy this to /lib/modules/2.6.32-28-server/kernel/drivers/scsi/aacraid/aacraid.ko   I believe you will need the initrd as well afterwards so copy that to /boot  but back up your old one.

Once the driver is in memory you should be able to access it with fdisk or other partition tools.  I never went with this method, but it should be easier this way.

As long as you can insmod the aacraid.ko then you are 99% there.

---

### Post by Entilza on 2011-07-13
> **Zonesa said:**
> Can you provide a little how-to about your fix : I'm trying to install Ubuntu with this card without any success. 

The following distros are not supported on this card (6405) : 

- Ubuntu/Debian
- CentOS 5.x
- VMware ESXi (Work on ESX but poor write performance)
- Citrix XenServer 5.x

Headhash.


Well because Adaptec is so awesome and give us the source code it's technically good for Any Linux Distro.

Here are the instructions from Adaptec:  (Note these are for 10.04.01) the files I provide are for 10.04.02  you'll know which one you have if you do "#uname -r" it tells you your kernel if it's 32-24 you have .01  if you have 32-28 you have .02 and need to use my files and change the instructions below to reflect 32-28.



[B]Ubuntu 10.04 Server x86_64 installation procedure:
[/B] 1. Write "initrd.img-2.6.32-24-server" and "aacraid.ko" on USB drive.
 2. Start installing Ubuntu 10.04 Server Linux by booting from the installation CD,
    Until a screen *Detect disks* said "No disk drive was detected"	
 3. Plug-in your USB-key, select for <Go back>, press enter on Detect disks
 4. Press "CTRL+ALT+F2" to enter into console 2
 5. fdisk -l   (scan for device, assume if USB drive is assigned to /dev/sda1)
 6. mkdir /mnt2 ; mount /dev/sda1 /mnt2
 7. uname -r (verify that your kernel is 2.6.32-24-generic)
 8. cp -f /mnt2/aacraid.ko /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/aacraid/aacraid.ko
 9. cp -f /mnt2/initrd.img-2.6.32-24-server /etc
10. umount /dev/sda1 and remove your USB drive from the installation system
11. Press CTRL+ALT+F1 to return to Ubuntu installer screen and select
    for <Go back>, press enter on Detect disks (Expect AACRAID driver get load and display disk partition)
12. Proceed to the installation as usual

 **************** Before rebooting the system, make sure you complete steps below ****************

13. Exit to console again (CTRL+ALT+F2) and check for kernel version
14. ls -l /target/boot   (expect to see kernel 2.6.32-24-server)
15  cp -f /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/aacraid/aacraid.ko /target/lib/modules/2.6.32-24-server/kernel/drivers/scsi/aacraid/aacraid.ko
16. cp -f /etc/initrd.img-2.6.32-24-server /target/boot/initrd.img-2.6.32-24-server

Press CTRL+ALT+F1 to return to the installer screen and REBOOT



*** Note:  after step 5 I had to plug in the USB key then use "Detect Disks" again in order to get the USB key to be recognized by fdisk -l  then I pressed "go back"

---

### Post by Entilza on 2011-07-13
Just a note the files I provided are for the **64 bit versions!**

One final note after I got 10.04.02 running with the above files I then switched to the latest stable kernel 2.6.39.x which now has support for the new aacraid driver.

---

### Post by Entilza on 2011-08-20
I've created a new set of drivers for the currently released 10.04.3  Version:

**This is only for a clean install of Ubuntu 10.04.3 64 bit.**

10.04.3 Comes with kernel 2.6.32-33-server

You follow the same steps as above.

Note I have not tested this one the .2 works 100%.  I have no means of testing this as my 6805 is now installed so if anyone is setting up a new one please give this a try.  If this is not working just download ubuntu 10.04.2  from [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)  and the above will work.

Here are the new files if someone would report back if this worked out.  Follow the same instructions as the top just replace with the new name of the kernel 32-33:

[http://dl.dropbox.com/u/37855661/ubuntu_10.04.3_amd64_install.zip](http://dl.dropbox.com/u/37855661/ubuntu_10.04.3_amd64_install.zip)

Final Note:  If you do install 10.04.2 do not upgrade the kernel with the package updates or you will lose your new aacraid driver.  The proper way is to download the new kernel source and copy the aacraid source from adaptec into the source directory and rebuild the kernel... Lot's of work but you can get this to work.

---

### Post by bennymak on 2011-09-28
I'm guessing that initrd is complied without LVM support? Worked fine through install on 10.04.3 till the time came to reboot the system. /boot was accessible no worries suggesting the driver got loaded but then failed to mount the main LVM volume.

Just tried 10.04.2 without LVMs and that's all good. apt-get upgrade to 10.04.3 with the -28 kernel and its happy enough. I'll compile my own kernel later.

Cheers for the module Entilza!

---

### Post by Entilza on 2011-09-28
The 10.04.02 version of this should work with LVM as I am using that one on my own server. Can you try that and see if that one works with LVM for you?

---

### Post by evil4ss on 2011-09-30
i just wanted to post here my way of getting it done. please forgive me for describing things in a funny way, because my english is not the best (i'm from germany).

so, previously i installed ubuntu server 10.04.03 lts with its standard kernel 2.6.32.33 i think.
after installing the controller with these commands everything worked fine:


[LIST=1]
[*]mkdir /home/administrator/downloads
[*]         cd /home/administrator/downloads
[*]         wget [http://download.adaptec.com/raid/aac/linux/aacraid-dkms-1.1.7-28000.tgz](http://download.adaptec.com/raid/aac/linux/aacraid-dkms-1.1.7-28000.tgz)
[*]         tar xvzf aacraid-dkms-1.1.7-28000.tgz
[*]         sudo aptitude install dkms
[*]         sudo aptitude install rpm
[*]         sudo bash
[*]         rpm2cpio aacraid-1.1.7.28000-dkms.noarch.rpm | (cd / ; cpio -idmu )
[*]         dkms add -m aacraid -v 1.1.7.28000
[*]         dkms build -m aacraid -v 1.1.7.28000
[*]         dkms install -m aacraid -v 1.1.7.28000
[*]         dkms status
[/LIST]
 
some today i updated my system and get the new kernel 2.6.32.34. after a reboot... :-?
because of a missing auto blah in the dkms.conf for the adaptec driver my mount where gone. but :-) ...
using just these commands helped me out, and after a restart everything was back at normal...


[LIST=1]
[*]sudo bash
[*]dkms build -m aacraid -v 1.1.7.28000
[*]         dkms install -m aacraid -v 1.1.7.28000
[*]         dkms status =: the matching driver / kernel version should now be listed
[*]         dkms uninstall -m aacraid -v 1.1.7.28000 -k 2.6.32-33-generic -a x86_64
[*]         dkms remove -m aacraid -v 1.1.7.28000 -k 2.6.32-33-generic -a x86_64
[*]dkms status =: the old driver should now be gone away.
[/LIST]
 for the last two commands please use YOUR old kernelversion and YOUR arch (x86_bla)
questions?

---

### Post by Entilza on 2011-09-30
The instructions you listed above are for installing the controller onto an existing system not a fresh install though just to be clear.

---

### Post by adeliciouspizza on 2011-09-30
Entilza many thanks to you for posting this information. It has been very helpful. Unfortunately I have not been able to successfully install Ubuntu yet follow your instructions. The first half goes ok - I can get Ubuntu to detect the card and install the operating system correctly. However the problem is when I try to do the second part just before reboot I find that the kernel version has changed. It seems that Ubuntu updates the kernel during the install even though I set the option for no automatic updates. So while I started off w/ kernel 2.6.32-28, at the end of the install it's always at 2.6.32-28. Also the initrd always says '-generic' at the end as opposed to '-server' like in your instructions. I'm also wondering, assuming I could get this installed correctly, is this going to break my system the next time it updates the kernel? Please note in my case the os would be on drives connected through the raid card, so if the driver doesn't load I would have no other way to boot the os to update the driver/kernel. Anyways I hope you are able to help me, and thanks again for your efforts. :D

~ADP

---

### Post by evil4ss on 2011-10-01
> **Entilza said:**
> The instructions you listed above are for installing the controller onto an existing system not a fresh install though just to be clear.

Exactly, i forgot that to mention.

---

### Post by Entilza on 2011-10-01
Ok so you are installing 10.04.2 good since this one is the one I know 100% works with the files I provided.

Make sure you dont have updates, if you don't do an update the kernel won't change.  Please re-edit your message you have a typo with the kernel versions so I am not sure how it's changing.

The other thing is -generic is correct for when it starts, ubuntu's config is a little strange in that after it's done installing it uses a different name for the final version.

After it's installed do not do a kernel update or it will poof your system.  I'm not sure if the previous poster's message means that if you install the dkms verison it will automatically update the kernel driver when you update the kernel. I haven't tried this so no idea how that really works.

There's a lot going here so let me know if you've gotten farther.

---

### Post by pythod on 2011-10-02
> **evil4ss said:**
> i just wanted to post here my way of getting it done. please forgive me for describing things in a funny way, because my english is not the best (i'm from germany).

so, previously i installed ubuntu server 10.04.03 lts with its standard kernel 2.6.32.33 i think.
after installing the controller with these commands everything worked fine:


[LIST=1]
[*]mkdir /home/administrator/downloads
[*]         cd /home/administrator/downloads
[*]         wget [http://download.adaptec.com/raid/aac/linux/aacraid-dkms-1.1.7-28000.tgz](http://download.adaptec.com/raid/aac/linux/aacraid-dkms-1.1.7-28000.tgz)
[*]         tar xvzf aacraid-dkms-1.1.7-28000.tgz
[*]         sudo aptitude install dkms
[*]         sudo aptitude install rpm
[*]         sudo bash
[*]         rpm2cpio aacraid-1.1.7.28000-dkms.noarch.rpm | (cd / ; cpio -idmu )
[*]         dkms add -m aacraid -v 1.1.7.28000
[*]         dkms build -m aacraid -v 1.1.7.28000
[*]         dkms install -m aacraid -v 1.1.7.28000
[*]         dkms status
[/LIST]
 
some today i updated my system and get the new kernel 2.6.32.34. after a reboot... :-?
because of a missing auto blah in the dkms.conf for the adaptec driver my mount where gone. but :-) ...
using just these commands helped me out, and after a restart everything was back at normal...


[LIST=1]
[*]sudo bash
[*]dkms build -m aacraid -v 1.1.7.28000
[*]         dkms install -m aacraid -v 1.1.7.28000
[*]         dkms status =: the matching driver / kernel version should now be listed
[*]         dkms uninstall -m aacraid -v 1.1.7.28000 -k 2.6.32-33-generic -a x86_64
[*]         dkms remove -m aacraid -v 1.1.7.28000 -k 2.6.32-33-generic -a x86_64
[*]dkms status =: the old driver should now be gone away.
[/LIST]
 for the last two commands please use YOUR old kernelversion and YOUR arch (x86_bla)
questions?

Thanks so much for posting these commands.

They helped me for my Adaptec 6445 after the installation was completed for kernel version:
Linux 2.6.32-34-server #77-Ubuntu SMP Tue Sep 13 20:54:38 UTC 2011 x86_64 GNU/Linux

---

### Post by adeliciouspizza on 2011-10-03
> **Entilza said:**
> Ok so you are installing 10.04.2 good since this one is the one I know 100% works with the files I provided.

Make sure you dont have updates, if you don't do an update the kernel won't change.  Please re-edit your message you have a typo with the kernel versions so I am not sure how it's changing.

The other thing is -generic is correct for when it starts, ubuntu's config is a little strange in that after it's done installing it uses a different name for the final version.

After it's installed do not do a kernel update or it will poof your system.  I'm not sure if the previous poster's message means that if you install the dkms verison it will automatically update the kernel driver when you update the kernel. I haven't tried this so no idea how that really works.

There's a lot going here so let me know if you've gotten farther.

yep, am installing ubuntu server 10.04.02 amd 64 from usb flash drive. sorry for the confusing explanation. :)

basically everything works per your instructions except for the last part. the installer is apparently updating the kernel during the install (without asking me for permission). so then at the end of the install before reboot i go to copy the files per your instructions but the kernel is at a newer version so it's incompatible with those files.

i think the solution is to do an 'offline' install so that it can't update the files/kernel during install. then after the reboot do an update (but don't reboot) and then compile the modules into the new kernel following the instructions from evil4ss. then reboot and it should work with the new kernel and i will need to do this process every time if i update the kernel.

if this works i will be sure to post back and let you know. and perhaps you should consider updating your instructions to let people know they need to do the install offline or it won't work. thanks again. :D

---

### Post by xerotm on 2011-10-07
At the moment I'm struggling in 11.04 to use a 6405 controller with  the latest 1.1.7-28000 driver, as the aacraid driver coming with  2.6.38-11-generic doesn't seem to do the job.
 
The step by step instructions from one of the earlier posts helped me with the first steps. But 'dkms build' always fails for me. So I manually tried to fix the problem. See the attached patch, which doesn't fix the problem completely. I had to replace ioctl with ioctl_unlocked and some mutex calls with sema_init

:!: But the resulting aacraid.ko triggers a Kernel oops. 

After applying the patch, I compiled the module with 
```
make KERNELRELEASE=2.6.38-11-generic -C /lib/modules/2.6.38-11-generic/build SUBDIRS=/var/lib/dkms/aacraid/1.1.7.28000/build modules
```

---

### Post by Narog82 on 2011-12-12
Just update your kernel.

The driver is included since kernel 2.6.39.

[http://www.adaptec.com/weblog/2011/11/18/linux-drivers-for-series-6-controllers/](http://www.adaptec.com/weblog/2011/11/18/linux-drivers-for-series-6-controllers/)

---

### Post by Entilza on 2011-12-12
Yes but it's not supported under 10.04 out of the box yet.  11.10 uses 3.0 so it will work.

When you are doing an installation from scratch with 10.04 it is still very difficult because 10.04 does not install 2.6.39+ as it's base kernel.  (Not yet anyway)

---

### Post by cinonet on 2012-01-09
hi;

i have bought Adaptec 6405 for my customer, and decidet to install Ubuntu 10.4 LTS; and as mentions before there was no support out of the box for this Adapter. So i have install OpenSuse 12.1.

**Question/Suggestion:**

On the Adaptec blog page [http://www.adaptec.com/weblog/2011/11/18/linux-drivers-for-series-6-controllers/](http://www.adaptec.com/weblog/2011/11/18/linux-drivers-for-series-6-controllers/) they write:

[COLOR=black][COLOR=black][FONT=Calibri]**"Canonical **- Ubuntu. [/FONT][/COLOR][COLOR=black][FONT=Calibri]With the recent release of Ubuntu 11.10, based on a 3.0 kernel, our 28000 driver is inbox."

So i have decided to install Ubuntu 10.04 LTS on a virtual environment and and Kernel upgrade to 3.0.0-14-server and then make a new Distro whith [B][remastersys]("http://remastersys.sourceforge.net/")

[/B]My new distro works very well; but i can not test it on the server because it is allready by my customer located and works as samba server.

Can one of you make a test whith new Distro (remastersys) and share us the experience please.

Not: You dont have to install the distro, you can use it as Live CD too.

Thanks :)

cinonet
[/FONT][/COLOR][/COLOR]

---

