---
title: "Is there something wrong with grub/raid1"
date: 2012-03-02
forum: Server Platforms
---

### Post by Zookee on 2012-03-02
Hi All,

I made a post previously regarding software raid1 and grub and tried a few suggestions on there to no avail.  I also thought it may be the machine I was using, so I tried on a virtual machine - again, no luck.

The problem I am having is this:

When I come to test the raid1 setup I unplug the one of the physical drives to simulate a failure (while the power is off of course) and reboot.  If I unplug the second physical drive everything is fine and it boots in degraded mode.  However if I unplug the first physical drive problems occur - grub briefly flashes up and then the system reboots.  This cycle continues over and over.  Using VirtualBox the machine actually exceptions and VirtualBox ends the process.  On a real machine, it just exceptions and reboots over and over.

I am at a loss to what I'm doing wrong and have tried various things.  I've even followed the guide ([https://help.ubuntu.com/community/In...n/SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID")) to the letter and that doesn't work.

Is anyone able to humour me and try this on either a physical machine or a Virtualbox virtual machine?  It's driving me crazy.

For virtual box, I followed the above guide for software raid, set it all up and then just removed one of the disks from the virtual machine.  For a physical one, I unplugged it obviously.  In either case, the results are the same.  1st disk gone = exception and constant reboots. 2nd disk gone = boots into degraded.

Surely the machine should boot from either drive?

Any help would be very much appreciated.

---

### Post by kevinthecomputerguy on 2012-03-03
try this before your tests

grub-install /dev/sda
grub-install /dev/sdb
grub-install /dev/mdx      (replace x with the right number)
update-grub

then remove a drive
*make sure your bios is ok with booting off a secondary, or tell your bios 2 is now 1

---

### Post by Zookee on 2012-03-05
Here's the results;

grub-install /dev/sda
Installtion finished. No error reported.

grub-install /dev/sdb
Installtion finished. No error reported.

grub-install /dev/md1
/usr/sbin/grub-setup: error: unable to identify a filesystem in /dev/sda; safety check can't be performed.

I've checked and md1 is the correct array (ie, not my swapspace one).

I also did a sanity test (just to make sure) and tried this on debian and everything worked fine.  So I'm thinking there's a bug somewhere but I have no idea what to do or how to fix it.

---

### Post by Zookee on 2012-03-05
A bit of clarification here.....

I tried the above grub-install commands and received the above errors.  I then tried to go into grub by typing "grub" at the command prompt and was told it was not installed.  So I did;

sudo apt-get install grub

From this point on, if I now try;

sudo grub-install /dev/sda1

I get;

The file /boot/grub/stage1 not read correctly.

Therefore I'm not sure if I've just compounded the issue and made things worse by installing a different version of grub?  My confusion is that grub was installed, but I couldn't get into grub by typing "grub" so I apt-get it, and now I have a totally different error message.

The boot problem still remains of course, and now these on top of it.

---

### Post by Zookee on 2012-03-05
Right, I think I may have solved this after much pain, googling and reading, re-reading....

My problem was that my raid would not boot into a degraded state if the primary drive was dead (or removed for simulated failure).  In my travels I scuffled with grub and ensuring it was installed on both partitions which only added more confusion and compounded the issue.

I also tested debian 6.04 and ubuntu server 10.04 LTS and these seemed to work.  My main issue was with 11.04.

I _think_ I have now solved the issue.  For anyone else reading that wants to be spared the pain, read on....

I created a raid array for swap and / using the standard tool and guide during installation (linked on my first post).

To fix the problem with the array not booting, you need to edit /etc/mdadm/mdadm.conf and find the lines where the array is defined - something like;

ARRAY /dev/md0 level=raid1 num-devices=2 UUID=<insert big long uuid here>
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=<insert big long uuid here>

and change them to (or whatever your drives are defined as);

ARRAY /dev/md0 level=raid1 num-devices=2 devices=/dev/sda1,/dev/sdb1
ARRAY /dev/md1 level=raid1 num-devices=2 devices=/dev/sda2,/dev/sdb2

As you can see, the UUID has been replaced with the actual devices.

Save the file, then run;

 sudo dpkg-reconfigure mdadm

It does NOT  get re-create mdadm.conf, but the settings seem to be used for the initrd.img) and this obviously "refreshes" it.

I believe this is because the UUID that's put into mdadm.conf is that of ONE of the drives and not BOTH.  Some people have suggested using the UUID of the array here but since actually using devices= and putting my raid members in that - I'm happy!

I have repeated all my previous tests and the raid boots degraded and I can resync it happily.

I haven't been able to do this on my 11.04 machine as yet but hopefully that will do the trick.  I'm hoping this will be the case on the 11.04 distro and it's just down to a bug somewhere in 11.04 (since it seems to work ok on debian and 10.04lts)

References:

[http://lavezarez.blogspot.com/2011/01/raid-1-not-starting-and-mounting-on.html](http://lavezarez.blogspot.com/2011/01/raid-1-not-starting-and-mounting-on.html)
[http://ubuntuforums.org/showthread.php?t=1468064&page=4](http://ubuntuforums.org/showthread.php?t=1468064&page=4)
[http://ubuntuforums.org/showpost.php?p=9334317&postcount=8](http://ubuntuforums.org/showpost.php?p=9334317&postcount=8)
[http://ubuntuforums.org/showpost.php?p=10285279&postcount=34](http://ubuntuforums.org/showpost.php?p=10285279&postcount=34)

---

### Post by Monkey Nuts on 2012-07-17
Hi,

Did you manage to try this on your 11.04 machine and, if so, what happened?

I have an 11.04 machine with the same problem. I've built a version in VMWare Server to test and can recreate the problem exactly. I've tried applying your suggested fix but I still get the same problem - boot with degraded array if second drive is removed and "boot-loader and reboot" cycle if the primary drive is removed.

Any suggests would be most welcome!

---

