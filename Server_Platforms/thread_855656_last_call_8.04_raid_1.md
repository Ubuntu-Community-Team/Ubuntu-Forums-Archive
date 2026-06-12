---
title: "last call 8.04 raid 1"
date: 2008-07-10
forum: Server Platforms
---

### Post by mspIggy on 2008-07-10
Issue: server will not run with drive missing, grub installed on both drives

this is the last call, before i have to dump ubuntu and look for another OS

i really like ubuntu, there is a alot to offer here

i need to use software raid, no way i can afford to buy a good raid controllor card, and time is of the essence..

i did post unsuccessfully with this problem earlier...

i will tru again hoping someonw will have some insite on how i can modify MY file so suit the sample i will post so that my server will run with a missing drive...

her is a suggested FIX for this and my axtual file contents which differ from the suggested FIX...

thoughts on how i can adjust my file so the server will actually RUN with a missing hard drive

thank you

................

and suggests this:
WARNING: There is a serious bug which makes the boot fail if one of the physical disks in the RAID1 set is missing. The following code in /usr/share/initramfs-tools/scripts/local should help. 

martti@ubuntu:~$ sudo vi /usr/share/initramfs-tools/scripts/local
# The following code was added to allow degraded RAID arrays to start
if [ ! -e "${ROOT}" ] || ! /lib/udev/vol_id "${ROOT}" >/dev/null 2>&1; then
# Try mdadm and allow degraded arrays to start in case a drive has failed
log_begin_msg "Attempting to start RAID arrays and allow degraded arrays"
/sbin/mdadm --assemble --scan
log_end_msg
fi
............. .............

however - the file on current server is different...

# If the root device hasn't shown up yet, give it a little while
# to deal with removable devices
if [ ! -e "${ROOT}" ] || ! /lib/udev/vol_id "${ROOT}" >/dev/null 2>&1; 2>&1; then log_begin_msg "Waiting for root file system..."

# Default delay is 180s
if [ -z "${ROOTDELAY}" ]; then
slumber=180
else
slumber=${ROOTDELAY}
fi

---

### Post by doogy2004 on 2008-07-10
first what hardware are you using and what is the configuration (e.g. primary master 10GB HDD, primary slave CD drive, secondary master 30GB HDD)

second, what where the steps that you took when setting up the OS and what where the steps you took when configuring mdadm (RAID)

third, what where you expecting to accomplish (e.g. RAID 0,1 with the os on the array)

---

### Post by mspIggy on 2008-07-10
hi ---

many thanks

it is an hp dl360 g4

2 drives 80gb sata

i followed this to setup raid:
[http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html)

and this for the ubuntu:
[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

as to what i am hoping to accomplish? to reduce the chance of down time due to a drive failure.. and i want to be able to run and start with a missing drive
.................

---

### Post by doogy2004 on 2008-07-10
ok thanks, give this how-to a try [http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html)

the guide is fore 7.10 but it should work just the same in 8.04

---

### Post by mspIggy on 2008-07-10
ok - thank you

this looks very similar to the install i followed

i ask you a special request, please review the install link you posted twords the bottom, take heed to the WARNING posted after picture 16, this very same warning was in my directions...

indeed this WARNING reflected a true circumstance in my install, hence my post, which bings us full circle...
.................................................

this is a non ubunto bug, but a bug that relates to me being able to use ubuntu in my circumstance

i have the exact same server running with a different os, centOS - i can turn it off, yank out a drive and turn it on and it runs and serves sites just fine with a missing drive, i need this sort of performance from my ubuntu install, hands down, or i simply cannot use it, and this truly will be a shame as this is a very versitle OS and does all that we need, except this...

this it the link to this BUG, i posted the FIX for it in my top post... 

........................
[https://bugs.launchpad.net/ubuntu/+bug/120375](https://bugs.launchpad.net/ubuntu/+bug/120375)

my file is a bit different that the referenced, in the bug posted in this bug page - i need help making my file work with what is posted in thus bug report...

thank you

---

### Post by doogy2004 on 2008-07-10
after reading the launchpad page, it looks like it should be fixed for the next release, the last post [https://bugs.launchpad.net/ubuntu/+bug/120375/comments/61](https://bugs.launchpad.net/ubuntu/+bug/120375/comments/61) has directions for appplying a patch to make it work

try doing a fresh install using the directions in the launchpad link and then apply the patch

---

### Post by mspIggy on 2008-07-10
i have done all of that in the 'patch'

except this

# The following code was added to allow degraded RAID arrays to start
 if [ ! -e "${ROOT}" ] || ! /lib/udev/vol_id "${ROOT}" >/dev/null 2>&1; then
  # Try mdadm and allow degraded arrays to start in case a drive has failed
  log_begin_msg "Attempting to start RAID arrays and allow degraded arrays"
   /sbin/mdadm --assemble --scan
  log_end_msg
 fi
.............................

this is what i posted on top...

my file is different that the sample...

my end of the file are 

'fi'

is different 

so this is why i am asking how to meld this bit of 'fix' to my actual file which is this:

# If the root device hasn't shown up yet, give it a little while
# to deal with removable devices
if [ ! -e "${ROOT}" ] || ! /lib/udev/vol_id "${ROOT}" >/dev/null 2>&1; 2>&1; then log_begin_msg "Waiting for root file system..."

# Default delay is 180s
if [ -z "${ROOTDELAY}" ]; then
slumber=180
else
slumber=${ROOTDELAY}
fi

---

### Post by doogy2004 on 2008-07-10
if I understand correctly you just want to get the patch working for your specific file?

replace your file with

```
# If the root device hasn't shown up yet, give it a little while
# to deal with removable devices
if [ ! -e "${ROOT}" ] || ! /lib/udev/vol_id "${ROOT}" >/dev/null 2>&1; then log_begin_msg "Waiting for root file system..."

# Default delay is 180s
if [ -z "${ROOTDELAY}" ]; then
slumber=180
else
slumber=${ROOTDELAY}
fi

/sbin/mdadm --assemble --scan
  log_end_msg
 fi


```


If that doesn't work move 

```
/sbin/mdadm --assemble --scan
  log_end_msg
 fi
```

to the line above  ```
# Default delay is 180s
```

---

### Post by mspIggy on 2008-07-10
yes i am down to this file...

i will try this tomorrow - i wll have to go down to the data center...

thank you

---

### Post by doogy2004 on 2008-07-10
> **mspIggy said:**
> yes i am down to this file...

i will try this tomorrow - i wll have to go down to the data center...

thank you

ok, great sorry for the run around.  it looked like you had an extra redirect 2>&1 and you needed to add the line telling mdadm to scan then finish with a fi (end if).

---

### Post by mspIggy on 2008-07-10
:)

---

### Post by mspIggy on 2008-07-12
seems this is a complete failure -- i have tried both of the conditions you suggest...

after edits...

i bull primary drive out, turn server back on...

after grub loading lines...

next screen stops at loading, please wait.... for a very long time - then asks if i ant to boot with a degraded device...

i enter the cimands it says to do so... but says md1 not exists and drops to shell..

what is wrong?

i thought it would just run... maybe i need to learn more bout this?


here is screen

Id10

md2 inactive sda 3 [1] 69842496 blocks
md1 inactive sda 2 [1]489856 blocks
md0 inactive sda 1 [1] 7815488 blocks

a note about degraded drive and telle me to use this to boot

madam -R /dev/mdX use ..... so i use (0)

alert!  /dev/mdo does not exist dropping to shell

kernel alive

more lines...

create root not found
create group not found

then says

mdadm started /dev/mdo
(initrwmfs)

..........................

what is wrong here?

how do i get this blasted machine to boot with a missing drive?

---

### Post by windependence on 2008-07-12
When it asks you if you want to boot with a degraded device are you answering yes? in this case since you have a drive removed, you DO want to boot degraded.

-Tim

---

### Post by mspIggy on 2008-07-12
i understand this...

i put in what is asked for...

and i get what i posted -->

madam -R /dev/mdX use ..... so i use (0)

alert! /dev/mdo does not exist dropping to shell

kernel alive

more lines...

create root not found
create group not found

then says

mdadm started /dev/mdo
(initrwmfs)

.............

this is what appeard in command line when all the dust settles...

mdadm started /dev/mdo
(initrwmfs)

???

---

### Post by mspIggy on 2008-07-12
would it be possible to use webmin to setup raid 1 then install ubuntu?

[http://doxfer.com/Webmin/PartitionsOnLocalDisks#Introduction_to_RAID](http://doxfer.com/Webmin/PartitionsOnLocalDisks#Introduction_to_RAID)

??

would thsi solve my problems?

also i see a few raid cards on ebay

if i purchase one, and install it...

do i have to start over?

many thanks

---

### Post by doogy2004 on 2008-07-12
> **mspIggy said:**
> would it be possible to use webmin to setup raid 1 then install ubuntu?

[http://doxfer.com/Webmin/PartitionsOnLocalDisks#Introduction_to_RAID](http://doxfer.com/Webmin/PartitionsOnLocalDisks#Introduction_to_RAID)

??

would thsi solve my problems?

also i see a few raid cards on ebay

if i purchase one, and install it...

do i have to start over?

many thanks

webmin is a management tool, it must be installed after the os

---

### Post by mspIggy on 2008-07-12
i found this:

Why use Webmin?

While every aspect of the system can be managed through a shell, Webmin can save you time in certain areas. Personally, I created a software RAID array using Webmin in only a few minutes. 

..........

others have told me this can be done as well...

i will look futher into this and report back

---

### Post by doogy2004 on 2008-07-12
> **mspIggy said:**
> i found this:

Why use Webmin?

While every aspect of the system can be managed through a shell, Webmin can save you time in certain areas. Personally, I created a software RAID array using Webmin in only a few minutes. 

..........

others have told me this can be done as well...

i will look futher into this and report back

i'm not saying that it can't be done in webmin, i'm just stating that the order of operations is backwards.

---

### Post by mspIggy on 2008-07-12
ok...

what do you mean?

i found this:

[http://doxfer.com/Webmin/PartitionsOnLocalDisks](http://doxfer.com/Webmin/PartitionsOnLocalDisks)

and a video guide 
[http://www.fluffyducky.com/details/vid/41/Software-Raid-in-Webmin/](http://www.fluffyducky.com/details/vid/41/Software-Raid-in-Webmin/)

can i set this raid up this way so it will actually work then install ubuntu?

i guess i am confused now more than ever

many thanks

---

### Post by doogy2004 on 2008-07-12
> **mspIggy said:**
> ok...

what do you mean?

i found this:

[http://doxfer.com/Webmin/PartitionsOnLocalDisks](http://doxfer.com/Webmin/PartitionsOnLocalDisks)

and a video guide 
[http://www.fluffyducky.com/details/vid/41/Software-Raid-in-Webmin/](http://www.fluffyducky.com/details/vid/41/Software-Raid-in-Webmin/)

can i set this raid up this way so it will actually work then install ubuntu?

i guess i am confused now more than ever

many thanks

In order to use Webmin, you must have an Operating System already installed.  Webmin cannot be used without an Operating System.  So to get Webmin working you must do the following:
[LIST=1]
[*]Install Ubuntu
[*]Download the Webmin *.deb
[*]Install Webmin from the *.deb
[*]Use Webmin
[/LIST]

---

### Post by mspIggy on 2008-07-12
sorry -- i should have mentioned

i have webmin running...

i use it for mysql admin... (phpmyadmin times out in my big db's and crashes) 

i am confused, as to how i would use it for software raid when i set up failing raid 1 in ubuntu as i have outlined here... and have ubuntu and things running as they are now

---

### Post by mspIggy on 2008-07-13
this webmin > hardware > GRUB Boot Loader is pretty cool

shows 3 things

1) Ubuntu 8.04, kernel 2.6.24-16-server 
2) Ubuntu 8.04, kernel 2.6.24-16-server (recovery mode) 
3) Ubuntu 8.04, memtest86+ 

and global options
global options are Ubuntu 8.04, kernel 2.6.24-16-server fall back boot option - first on linst, which is Ubuntu 8.04, kernel 2.6.24-16-server

then it says timout b4 loading 3 seconds

then boot password none

then install GRUB on disk/ partition and the default is the whole drive - not any of the partitions in the select box...  shows disk a and b...


..............

now i exit out of this screen and am back to the > GRUB Boot Loader screen

looking at 1) Ubuntu 8.04, kernel 2.6.24-16-server shows 

Option Title 1) Ubuntu 8.04, kernel 2.6.24-16-server
Boot image (selected) partition SCSI Device A Partition A 1 (Linux RAID)

Operating system to boot  Kernel 
      path to kernel /boot/vmlinuz-2.6.24-16-server
      Kernel options root=/dev/md0 ro quiet splash
      Initial ramdisk file /boot/initrd.img-2.6.24-16-server

Other OS  From first sector of partition
Password locked? no

.................................................

now looking at 2) Ubuntu 8.04, kernel 2.6.24-16-server (recovery mode) 

Option title Ubuntu 8.04, kernel 2.6.24-16-server (recovery mode)

Boot image partition Selected SCSI device A partiton 1 (linux RAID)

Operating system to boot Kernel Path to kernel /boot/vmlinuz-2.6.24-16-server

Kernel options root=/dev/md0 ro single

Initial ramdisk file Initial ramdisk file

Other OS From first sector of partition
Password locked? No

......................................

and now my raid from the Hardware > Linux RAID menu

/dev/md0 Yes Mirrored (RAID1) /dev/sda1 | /dev/sdb1
 
/dev/md1 Yes Mirrored (RAID1) /dev/sda2 | /dev/sdb2
 
/dev/md2 Yes Mirrored (RAID1) /dev/sda3 | /dev/sdb3 
.......................................

in looking at all of this, i can see why my server will not boot with the missing drive... at least from my 'noob' (is this the word?) understanding of things...

when i yank out the primary drive and turn the server back on after the grub screen goes and the waiting.... screen stalls for several minns  the boot in degraded screen comes up and as i posted earlier... says "alert! /dev/mdo does not exist dropping to shell"

it seems this md0 is the primary drive - of course it does not exist - it is in my hand

................................

what piece of this puzzle is missing to allow this server to run with a missing drive?

................................

as you can see i am not ready to give up and go running back to centOS just yet...

:)

---

### Post by fjgaude on 2008-07-13
I haven't followed this thread but we know that we have to have **grub** on all raid1 drives, even three or four or however many there is in the raid1 array. Then the machine will boot from whichever drive there is left to boot from.

I'm sure the BIOS has something to say about this... so a failed drive being pointed to that doesn't exist can be the issue. <smile>

But still if the BIOS is setup in such a way that if the fist drive is not there then boot from the next. Most BIOSs have this feature.

---

### Post by hehe22 on 2008-07-13
hope these guys helped you out! lol!

---

### Post by mspIggy on 2008-07-13
> **hehe22 said:**
> hope these guys helped you out! lol!

why would you think this is funny?

as you can see i have been having a real problem with this

i simply am missing part of this picture...

i think i m pretty brave trying to do this myself, with absolutly no experience in this areana what so ever, do you have anything positive to contribute?

when i installed all of this, i did put grub onto the 2nd drive, at least i thought i did...

now i will try to do thsi again as it seems this is not the way it needs to be...

---

### Post by mspIggy on 2008-07-13
big problems

i reinsrtalled grub in drive 2

then tried to boot with drive i missing 

grub disk err was displayed no boot

so i now go back to restored file /usr/share/initramfs-tools/scripts

and amke it look like this:

# Default delay is 180s
if [ -z "${ROOTDELAY}" ]; then
slumber=180
else
slumber=${ROOTDELAY}
fi

/sbin/mdadm --assemble --scan
  log_end_msg
 fi

and run update-initramfs -u

go pull drive 1 and turn on server and to my horror, it will not boot up, gives this

init: scripts/local: 48: syntax error 'fi' unexpected (expecting "}"

kernal panic - not synching attempting to kill inet

...................................................

how do  into this file to try the other edit that was offered?

---

### Post by doogy2004 on 2008-07-13
> **mspIggy said:**
> big problems

i reinsrtalled grub in drive 2

then tried to boot with drive i missing 

grub disk err was displayed no boot

so i now go back to restored file /usr/share/initramfs-tools/scripts

and amke it look like this:

# Default delay is 180s
if [ -z "${ROOTDELAY}" ]; then
slumber=180
else
slumber=${ROOTDELAY}
fi

/sbin/mdadm --assemble --scan
  log_end_msg
 fi

and run update-initramfs -u

go pull drive 1 and turn on server and to my horror, it will not boot up, gives this

init: scripts/local: 48: syntax error 'fi' unexpected (expecting "}"

kernal panic - not synching attempting to kill inet

...................................................

how do  into this file to try the other edit that was offered?

in programming (scripting is programming)  you cannot have fi without being preceided by if.  you need to add the following before the /sbin/mdadm --assemble --scan

```
if [ ! -e "${ROOT}" ] || ! /lib/udev/vol_id "${ROOT}" >/dev/null 2>&1; then
log_begin_msg "Attempting to start RAID arrays and allow degraded arrays"
```

throughout this entire process you have been dead set on merging the patch with your current script, why are you so attached to the DELAY section?  Have you ever considered just to replace the entire script with the one suggested in the patch?

---

### Post by mspIggy on 2008-07-13
well ok... there is alot of of other lines in my file, the patch is written for a differnt version of ubuntu, i have no idea that it will cause problems so i would prefer to work with the original file

but if you say a file fro someother version of ubuntu will work i will try - u have this backed up...

now how do i get to the file being with as the server will not boot up due to this error?

is ther some way to get it to boot so  i can get to the file?

---

### Post by doogy2004 on 2008-07-13
> **mspIggy said:**
> well ok... there is alot of of other lines in my file, the patch is written for a differnt version of ubuntu, i have no idea that it will cause problems so i would prefer to work with the original file

but if you say a file fro someother version of ubuntu will work i will try - u have this backed up...

now how do i get to the file being with as the server will not boot up due to this error?

is ther some way to get it to boot so  i can get to the file?

please post the file in its entirety

---

### Post by mspIggy on 2008-07-13
i cannot post the file - no access  - the server will not boot up due to this error

how can i get it up with this error in the file?

is there another way to boot the machine?

---

### Post by doogy2004 on 2008-07-13
> **mspIggy said:**
> i cannot post the file - no access  - the server will not boot up due to this error

how can i get it up with this error in the file?

is there another way to boot the machine?

If it was booting correctly with both drives in place, put both drives in.

Is their important data on this server?  If not why don't you consider wiping the drives and starting over with the original tutorial that I sent you, try using 8.04 instead of the version that they use in the tutorial.  If that doesn't work try going back to the tutorial, use the version of Ubuntu that they use, get it working then upgrade to 8.04.

---

### Post by mspIggy on 2008-07-13
many thanks...

both drives are in it...

the tutorial u sent is for "This was done using Ubuntu 7.1 from the alternate disk"

i am on 8.04...

i missed the first part of the 'if'

i had no idea it was to go there..

literally...

i just put what u had in your post - the 3 lines...

i have a bit loaded and would hate to have to reload it...

it has teken me a very long time to get this far...

ther has to be some way to boot this?

---

### Post by doogy2004 on 2008-07-13
> **mspIggy said:**
> many thanks...

both drives are in it...

the tutorial u sent is for "This was done using Ubuntu 7.1 from the alternate disk"

i am on 8.04...

i missed the first part of the 'if'

i had no idea it was to go there..

literally...

i just put what u had in your post - the 3 lines...

i have a bit loaded and would hate to have to reload it...

it has teken me a very long time to get this far...

ther has to be some way to boot this?

using a live cd would be my guess

---

### Post by mspIggy on 2008-07-13
live cd?

u mean teh install disk?

---

### Post by doogy2004 on 2008-07-13
> **mspIggy said:**
> live cd?

u mean teh install disk?

the desktop cd is a live cd.  a live cd is one that boots directly from the cd, no hdd required.

---

### Post by mspIggy on 2008-07-13
no desktop cd here..

have to go home and burn it...

thank you

---

### Post by mspIggy on 2008-07-13
ok i have the desktop cd 

it seems i am out of luck...

the file is not the one installed on the server...

it must be on this desktop cd, for this disk only
.................................................


does anobody know of a way i can boot the server version with thie error in file /scripts/local?

thank you

---

### Post by mspIggy on 2008-07-13
well i am giving up...

i tried to 'rescue' from the cd rom... when all was said and done...

no boot file system not on md0

..........

i am trying to reload the whole system... lots of big red windows saying ERROR...

i have had enough of this.. going on 10 days, trying to get raid 1 to work...

...........


i give up...  doogy2004, i want to thank you for your help... 

thank you!!!
............

how can such a popular application fail in this manner?  no software raid1?  hard to imagine

...........

over and OUT!

---

### Post by windependence on 2008-07-13
OK, this proves my point earlier. Yes, this post is not helping the OP as I am sure someone will point out, but isn't that the point? Here we two threads where people are having trouble with software RAID and have spent HOURS and even DAYS tryong to fix it with expert help here.

I have just looked at one of my distributor's listings of SATA RAID cards and there are 808 listings, and 55 of them are under $100, most are below $50. Why oh why would someone want to do this when hardware RAID is available so cheap?

Here is an article from Tom's Hardware comparing several hardware RAID cards. It is quite old (2005) but even then they were performing very nicely, even the "software on a chip" cards.

[http://www.tomshardware.com/reviews/sata-spells-trouble-scsi-raid,1161.html](http://www.tomshardware.com/reviews/sata-spells-trouble-scsi-raid,1161.html)

I see no reason to punish yourself with software RAID when many cards are available for under $50.

Just my $.02

-Tim

---

### Post by mspIggy on 2008-07-14
what do you do if your raid card dies?

also i have been reading horror stories of hp dl360 users that have 360 g4 firmware raid updates and 3 months later have many problems...

also i have more that one of these servers to i could then take a software raid drive and simply put in onto another server and get in online in less than 5 minns...

there are many reasons why i want to use software raid....

sure your poits are valid - but not for me

i do not want to use debian...

i guess i will look to freeBSD...

when this, what i am feeling now is 'nonsense' is resolved i will come back

---

### Post by windependence on 2008-07-14
Jeez, why do you think large enterprises use hardware cards almost exclusively? If your card dies, you install another card. RAID is not a substitute for backups either. Hopefully you have a backup.

If you have a need to get back online that fast, you could always clone a drive and just plug it in with a hot swap bay. They are less than $20.

If you run your server on  VM, you could be on line even faster if yu have a copy of your VM. just start it on another machine and go.

-Tim

---

### Post by mspIggy on 2008-07-14
Hi Tim...

what in the world is VM?

........................

a little background on me...

we have been renting dedicated servers since 1999 for our flower business online -- 

we have never been happy - just varying levels of contentment

recently there has been horrible support - 4 hours to do a simple reboot - servers are down alot and they are lame 32 bit systems, we need alot more...

..............................

i have pulled the plug on these clowns, found 2 dl360g4 servers - have 1 running in emergency mode with our clietns and this one i am trying to get running well --

as you can see i am what i have learned, a complete 'noob' at this - the fellow at my co-lo center suggested ubuntu - it looks good except for this problem
..............................

also, i hear the word backup alot --

to me it is a bit like a thoat lozenge - something to make a person feel good --

i have no idea how to impliment any sort of backup/restore as of yet - any tutorials you can point me to? do i need some sort of extra hardware to store these backups on? 
.............................

i think i will look for an hp 6400 controller card and hope i can get it installed with our frying out the server :)

not ready to give up

i have a brand new dell 2950 in the box waiting for OS load once i get this figured out - that server will be my database server... not sure how i will set that up either... thoughts?

many thanks
...............................

---

### Post by windependence on 2008-07-14
Alright, that gives me abit better picture.

First I need to know what you are running on these servers. Is it a web site, or are you running an application you need for the business and if so what is it. In other words, tell me exactly what you had running before. I need to know why you are running a database, and what the front end is. We'll go from there.

For backups, I like to run a separate drive on the server that is not in a RAID array, just a lone drive by itself, and I mount it as /backup. Then, I copy all the data on the RAID array to the /backup drive and set up a cron job to rsync the data every so often. Could be every 15 minutes or it couls be once a day or once a week depending on your needs. Then, if you have a disaster, you can just restore ot back and have your server back up in less than an hour usually.

-Tim

---

### Post by mspIggy on 2008-07-14
well it is  a bit complicated...

it is many websites, 44 of them on this temp box now...

we serve them with software we develope that is installed on the server -- all of the data is stored in mysql database for each site plus there are databases for reference we go to for different reasons...

as to the backup then i should get anothe drive for the new dell 2950 server for backups...

i plan on using the 2 dl 360s to serve the sites and the 2950 for database's

---

### Post by windependence on 2008-07-14
No offense but are you sure you are up to this task yourself?

There are probably many people here who will flame me for this but for that many sites I would recommend running them on FreeBSD on several VMs (virutal machines) on two separate servers that are load balanced. The sites would exist on both machines and be mirrored. This way if one server fails, there is no interruption.

This is truly enterprise class stuff you have here. Do you have a UPS (uninterruted power supply)? In fact you should have dual UPSs in this case. You want to eliminate any single point of failure. Remember, if you web sites are down, you are losing serious money. this is not anything to worry about the cost of a RAID card on, don't you agree?

-Tim

---

### Post by mspIggy on 2008-07-14
-->No offense but are you sure you are up to this task yourself?

yes..

i have to learn and do this for myself to advance my business

time is what i have, and i can learn :)

i am at a datacenter in minneapolis that is very robust, they have a built in UPS and generator - they guy that runs the place told me the same thing (freeBSD etc..) and suggested i start with ubuntu to get my sites up and running, away from this horrible 32 bit blue quartz system that has nothing but problems for me -- so this is where i am starting

i will wind up using dell 1950 servers and 2950's once i get settled...

we hope to tripple our business in the next 9 months - so time is precious

i need to get thru this first...

................................

clients have no access to server dirs so we have control of sites - we pretty much know what is on the servers which makes backups / putting sites back on server not so bad - but none the less time consuming...

---

### Post by mspIggy on 2008-07-14
just wondering...

if i get a riad card.. and pull out a primary drive 

what will allow things to boot ?

how will adding a raid controllor have any impact on thsi raid 1 no boot with missing drive problem?

if i add a raid card will i be able to run the server with a missing drive? or am i going to have this same idioc problem?

many thanks

---

### Post by mspIggy on 2008-07-14
ok...

i have done research - it seems there is only one raid card on the planet that will work with my server / drive combo HP 347789-b21 and cable kit 398307-b21
............

wow this is getting out of hand -- then if something happens to the card? i have to scrounge for another?

..................

i think it is time to abandone raid ...

........................

how can i install and then do backups to the 2nd drive?

---

