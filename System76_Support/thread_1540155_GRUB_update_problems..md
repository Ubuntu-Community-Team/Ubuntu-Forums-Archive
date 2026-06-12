---
title: "GRUB update problems."
date: 2010-07-27
forum: System76 Support
---

### Post by isantop on 2010-07-27
Attention System76 Users!!

A recent GRUB update has caused problems for a large number of users. THe update itself is fine, but the wording in the help text is very poor, and the suggestion there doesn't work.

If you haven't yet updated in a while, please follow these instructions:

1. Proceed to update normally.
2. When prompted to configure the grub-pc package, select to install grub to /dev/sda (not /dev/sda1) only. Do not install to any other device. It may suggest installing to every device, but this **will break your system.**
3. Finish the update.

If you have already updated, and now cannot boot, please go to [this page](http://knowledge76.com/index.php/Restore_Grub_Bootloader) and follow the instructions. You may need to connect to the internet for all of the commands to run correctly.

---

### Post by tully.foote on 2010-07-27
Hi , 
I definitely have hit this.  For reference, my computer just hangs after the POST with a black screen and a blinking curser in the top left.  I remember doing the update before I rebooted, and I let it install on all devices.  

I followed those instructions. However, I get the following error on the last step. 

{{{
warn: This msdos-style partition label has no post-MBR gap; embedding won't be possible.  
}}}

Any suggestions?  It offers to let me force it using --force but I'm a little worried about that due to the warnings that blocklists are UNRELIABLE.  

I do have an SSD which might make a difference?  I have the default install of 10.04 on my Serval/

Thanks,
Tully

---

### Post by isantop on 2010-07-27
Installing to blocklists shouldn't be a problem. I believe the default Ubuntu installer will install grub to blocklists as well.

---

### Post by tully.foote on 2010-07-27
Thanks, It worked fine after using the --force option.

---

### Post by Ron Burkey on 2010-10-12
By the time I tried this, the --force switch for grub-install no longer seemed to be supported ... no problem, I just left it out.  More seriously, grub-install failed with the message that /dev/sdb1 didn't exist or wasn't a block device (even though it was supposed to be writing to /dev/sda).  I found the following suggestion on a gentoo forum that fixed it for me:  Prior to running grub-install, run the command    grep -v rootfs /proc/mounts >/etc/mtab

---

### Post by guttmjo on 2010-10-13
oh no.  I just put GRUB in SDA1 !  Is a way to fix this without having a burned Ubuntu CD?

---

### Post by thomasaaron on 2010-10-14
Not that I'm aware of. Instructions, though, for restoring grub are here...
[http://knowledge76.com/index.php/Restore_Grub_Bootloader](http://knowledge76.com/index.php/Restore_Grub_Bootloader)

---

### Post by max127 on 2010-11-14
Thanks for sharing a great problem with us.

---

### Post by lapedestrienne on 2010-11-26
Okay, I was stupid enough to mis-install the GRUB update on my S76 Starling, and I can't figure out how to fix it. I burned a CD of Ubuntu 10.04 LTS 32-bit (someone stop me if I'm wrong), hooked up my external hard-drive to my netbook, and tried turning it on. The CD spins in its drive, but I still don't get any display--just a blinking cursor on a black screen. I can access setup utilities by pressing f2 on the start-up screen if I'm fast enough, but that's it. WHAT AM I MISSING???

PS--I tried it with a copy on a flash drive as well, but that didn't give me any better results. ARGGGH.

---

### Post by wilee-nilee on 2010-11-26
> **lapedestrienne said:**
> Okay, I was stupid enough to mis-install the GRUB update on my S76 Starling, and I can't figure out how to fix it. I burned a CD of Ubuntu 10.04 LTS 32-bit (someone stop me if I'm wrong), hooked up my external hard-drive to my netbook, and tried turning it on. The CD spins in its drive, but I still don't get any display--just a blinking cursor on a black screen. I can access setup utilities by pressing f2 on the start-up screen if I'm fast enough, but that's it. WHAT AM I MISSING???

PS--I tried it with a copy on a flash drive as well, but that didn't give me any better results. ARGGGH.

First start your own thread these problems may seem similar but hardly ever are.

In your new thread post the bootscript in my signature; link to it. Paste the text from the generated file by posting the script in code tags. To get code tags click on the # in the reply panel and paste the text in between. Feel free to PM me **if you start a new thread only, and have the script posted in code tags**.

---

### Post by bstoker on 2010-12-06
Avoided making this mistake last week. Wasn't paying attention today and installed it everywhere....

Came here first looking for help. Thanks for the sticky! You saved my bacon.

---

### Post by thc4ster on 2010-12-06
I fell victim to doing what the update manager suggested I do (select sda and sda1) and now my system is broken. I followed the directions at [http://knowledge76.com/index.php/Restore_Grub_Bootloader](http://knowledge76.com/index.php/Restore_Grub_Bootloader), but I cannot get past the first command:
 
sudo mount /dev/sda1 /mnt

 
I get the error message:
 
mount: no special device /dev/sda1 does not exist
 
I'd greatly appreciate any help. I really do not want to do a fresh install.

---

### Post by neophyte_of_linux on 2010-12-07
Hi, Unfourtunately I did not read this and followed the instructions.....but, my system is not "broken" as far as I can tell....

I am having a CD ripping problem, but I don't think that is qualifying for broken.

Do I need to do anything, even though I followed the wrong advice and installed it on the two things?

Its a bit disappointing because this resolution seems likely beyond my skill level.

---

### Post by isantop on 2010-12-08
If your computer is booting, then you're probably okay. If not, and the boot process halts at a flashing cursor, then you probably need to run the commands. You should only have to copy and paste.

---

### Post by neophyte_of_linux on 2010-12-08
Thanks Isantop.

I went ahead and followed the instructions, because one time it did act funny booting up.  I did get the messages about during the fix about something not recommended but then the next sentence said Installation complete and no problems.

I guess that did it.

BUT, what I need to know for the future is, where specifically should I go to find out if an update from the update manager is o.k. or not.  Is there a forum or a website?

Because unless I have personal advice, I am not experienced enough to tell if the update manager is asking me to do something ill advised.

I mean that message was pretty convincing that I should install the GRUb to both devices....

---

### Post by suzgould on 2010-12-12
Please help - I have the blank screen and blinking cursor on my 1st gen Starling.  I tried to do the restore Grub, but I got this message:
No configuration file found
No DEFAULT or UI configuration directive found!
When I tried to enter the commands, it gave me this message:
Could not find kernal image: sudo

---

### Post by suzgould on 2010-12-12
Problem solved.

---

### Post by neophyte_of_linux on 2011-02-02
This is goofy. And not in a happy way.  Once again the update manager in Ubuntu 10.04 wanted to do some updates.  So again, this update wanted to update the grub and install to mulitple devices.

I followed the instructions and did not allow (unchecked) sda1.

But it is goofy to me that the Ubuntu world still has this going on.  I wonder how many people today again just caused themselves problems???

---

### Post by isantop on 2011-02-02
I agree; this is not something users should have to deal with. Unfortunately, not even the documentation is very good, as it recommends installing to all devices (which breaks it).

---

### Post by scarey9 on 2011-02-03
Do you run all of the updates before you ship new systems?

---

### Post by isantop on 2011-02-03
We do, though sometimes new ones come down before the system arrives, and there may be a few for a new user to install.

---

### Post by bouncinglime on 2011-02-14
This wasn't quite what happened (I broke grub myself) but it definitely led me in the proper direction to fix it. Thanks! ^_^

---

