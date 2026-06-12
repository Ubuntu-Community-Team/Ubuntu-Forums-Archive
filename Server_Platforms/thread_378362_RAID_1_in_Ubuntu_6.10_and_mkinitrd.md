---
title: "RAID 1 in Ubuntu 6.10 and mkinitrd"
date: 2007-03-07
forum: Server Platforms
---

### Post by raidlost on 2007-03-07
I am trying to set up software raid 1 on an IBM with 2 SATA drives in 6.10. all is well up to the point where I need to create a initrd for the new RAID. I have found tech docks and have gotten as far as this:


cd /mnt
mount -o bind /proc ./proc
# check if you see anything below /mnt/dev, if not:
mount -o bind /dev ./dev
chroot /mnt
# mkinitrd has more flavours, use one of the following two syntaxis (check manpage)
# syntax 1
mkinitrd -r /dev/md0 -o <the initrd-image-name from the grub config>-raid
# syntax 2 (a.o. Fedora FC3)
mkinitrd <the initrd-image-name from the grub config>-raid <kernel-version>

my image name is /boot/initrd.img-2.6.17-10-generic

to check if the image contains the necessary modules I execute the command

    gunzip -c /boot/initrd.img-2.6.17-10-generic-raid | cpio -it

and it returns with

    gunzip: /boot/initrd.img-2.6.17-10-generic-raid: not in gzip format
    cpio:  premature end of archive

:mad: :mad: :mad: 

:confused: what do I need to do to create the initrd so I can boot the new RAID & test....?????:confused:

---

### Post by raidlost on 2007-03-09
:frown: [http://ubuntuforums.org/images/smilies/frown.gif](http://ubuntuforums.org/images/smilies/frown.gif)
:frown:

is it the wrong question, have i not looked on the right forum for the answer, or does everyone have the same problem without a solution.....????


if i am missing something could someone please slap me in the face with it,,, it is for work and i would hate to revert to [MS]

---

### Post by raidlost on 2007-03-09
:popcorn: 
:popcorn: 

Fanks alot to all you !!

as a reward for all the help and the fact that I could not get a text mail client to send a mail to our support ++++++ the urgent need for the server 

        I now have to spend the weekend installing ms 2003 :guitar: 

so much for trying to get Ubuntu in to the company

please do not worry about this post any more

---

### Post by Aberrix on 2007-03-09
As far as a 'soft raid' in ubuntu 6.06/6.10 the only luck I have had is using the alternate install disk. I swear I tried everything else and couldn't get ANYTHING to work, popped in the alternate install disk and was up and running within the hour.

---

### Post by ghandi69_ on 2007-03-09
> **raidlost said:**
> :popcorn: 
:popcorn: 

Fanks alot to all you !!

as a reward for all the help and the fact that I could not get a text mail client to send a mail to our support ++++++ the urgent need for the server 

        I now have to spend the weekend installing ms 2003 :guitar: 

so much for trying to get Ubuntu in to the company

please do not worry about this post any more

lol that was a sweet response man.. I too have often had that feeling not getting a response to a thread... but never came up with as good of a "bow out" as that one.  I had a RAID thread that didn't get answered as well... I really don't think anyone on here knows anything about how to get a RAID setup working besides just using good luck.

---

### Post by raidlost on 2007-03-12
Without going in to my life story ----- I have been PRO LINUX for some time ___

but

all I need is a server with RAID 1 for the OS
a proxy for web access authenticating domain users
monitoring software that will log internet access and mail reports to the correct person

I SET THIS UP IN 3 HOURS ON MS2003

as for today I tried again on a spare pc,,,,,, it has been 8 days on Ubuntu and -- get this -- 3 re-installs ,,, and

do you think its working


NO

wait, lets hear that again 

NO NO NO

IS THERE A STEP BY STEP FOR EXPERT CONFIGURATION FOR DUMMIES 

or is that what windows is for ??????????

---

### Post by mvoorberg on 2007-03-14
raidlost, I feel your pain.  I too wanted a raid1 box to replace my Windoze server.   A simple box with 2 80G IDE drives, follow the install and the instructions found here:

[http://users.piuha.net/martti/comp/ubuntu/raid.html]("http://users.piuha.net/martti/comp/ubuntu/raid.html")

Oh, except it won't boot.

I was getting 
```

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

```

I saw all kinds of 'help' about making sure that the RAID module is loaded etc, but the fix was a simple edit to my /boot/grub/menu.lst to point to "/dev/md0" instead of "/dev/hda1".

Added that and all is good.  Naturally I added a section to boot from the mirror using 

"root (hd1,0)" instead of "root (hd0,0)" and then installing grub to the mirror but worry about that after the damn thing boots the OS!

-Cheers,
Mark Voorberg
[www.objectclarity.com](www.objectclarity.com)

---

