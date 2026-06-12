---
title: "Create RAID 1 on running system"
date: 2011-10-23
forum: Server Platforms
---

### Post by YoshiHNS on 2011-10-23
Running Ubuntu server 11.04. I have everything mostly set up, but want to move everything to a RAID setup. I've been trying to follow a guide as a guideline, but it does not seem to work. The comments also suggest that there are a few errors in the guide. I've ran into two problems. One is that the files do not seem to copy over correctly from my original drive to the raid array. The other is that I cannot get it to boot on the first array (when the files did copy over correctly). Any chance someone can read through the guide and point out any mistakes?

My setup is with three partitions. First partition is OS with EXT4, second is swap, and third is ntfs. 

[LINK TO THE GUIDE]("http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04-p2")

---

### Post by YoshiHNS on 2011-10-23
I'm using EMACS to edit the config files. Don't see why this should cause any problems. I always remember to check and delete the file with the ~ at the end.

I understand everything the guide is explaining to do, so it's not really a matter of understanding the steps.

Everything works up to the point where you have to start editing the files.

---

### Post by darkod on 2011-10-23
I haven't worked much with Server but yes, the guide does sound straightforward. Just to make sure emacs has nothing to do with it, have you tried using nano editor?

Also, why do you think some of the copying is failing, do you have error messages?

And when you say it starts failing when editing the files, what exactly? The edit itself should not fail, do you mean the server doesn't boot afterwards?

---

### Post by YoshiHNS on 2011-10-23
No, I haven't tried using nano yet. That will be the next run through.

I'm pretty sure the file copy fails because when I  "ls -l -s" for each partition, they do not match. One instance the files and directories were all there, but the sizes did not match, and a second attempt only copied over half the files. This is using the "cp -dpRx / /mnt/md0" command.

When I say fails when it comes to editing the text, I do not mean that I cannot edit the files. The part that goes awry is when I reboot the system and hope that it boots off of md0 instead of sda1. When I reboot, I have to options now for linux server. The first one throws the
error: you need to load the linux kernel first
error. the second boots into sda1, but seems to use the RAID1 swap (md1).

Tempted to just modify the grub.conf file myself. It didn't look too difficult if I read it through enough times.

---

### Post by darkod on 2011-10-23
I have no idea about missing files/folders that should be copied.

As for the grub error, it sounds like the entry in the 09_raid_etc file is not correct. Make sure to adjust it for your system. This is just a temp entry anyway since they use it just to boot once to add the first disk to the new array and they delete it afterwards.

Using nano might look weird if you're used to graphics environment (I am mainly using Ubuntu and gedit) but once you look into it, it's no big deal to use.

---

### Post by darkod on 2011-10-23
PS. About that boot error. When editing the 09_swraid1_setup file did you take into account that the example has a separate /boot partition?

In this tutorial the final two lines of the menu entry are /vmlinuz... and /initrd.img.... while in a situation where you have your boot folder on your / (no separate /boot partition) it should be /boot/vmlinuz... and /boot/initrd.img... I believe.

Also, since you have noticed files missing after the copy, it's better to check if the kernel and the other boot files are in the /boot folder on /dev/sdb after the copy, where you would expect to find them. Even if the menu entry is correct it can't boot without the files in the correct location.

---

### Post by YoshiHNS on 2011-10-23
I did notice that he had a separate partition for /boot. Since I didn't, I ignored it and just edited for the root directory.

Not using a graphical interface, only command. Just like the general function of emacs.

I'll try the /boot/initrd entry to see if that works.

I read a comment in the guide how, in the 09_sw_raid_etc file that the entry for "set root='(md0)'" should actually be "set root='(md/0)'", but I have also seen where it was "set root='(md,0)'". Not sure which one of these formats is actually correct.

---

### Post by YoshiHNS on 2011-10-23
A thought. When I go to edit fstab and mtab files, do I need to add in the line declaring md0 as / AND md0 as /boot, or just declare root location?

the original mtab file only has:
/dev/sda1 / ext4 etc...

---

### Post by YoshiHNS on 2011-10-23
another attempt. Upon reboot, the errors I get for trying to load server from grub is:

error: file not found.
error: no such disk.
error: you need to load the kernel first.

I'll try searching around to see if anyone else has had those errors, but my search for just 'load the kernel first' didn't come up with too much helpful stuff.

I'll post up my files up later.

---

### Post by darkod on 2011-10-24
> **YoshiHNS said:**
> A thought. When I go to edit fstab and mtab files, do I need to add in the line declaring md0 as / AND md0 as /boot, or just declare root location?

the original mtab file only has:
/dev/sda1 / ext4 etc...

Only as /. You declare /boot only when it exists as separate. Otherwise there is only boot folder inside /.

And for the other question, I guess it should be root=(md0), or maybe (md0,1) to specify also the partition. The partitions start counting from 1 these days, not 0 like the old grub.

Make SURE you are pointing it to the right place. File not found, no suck disk and kernel not loaded means more or less, I'm not looking at the right place.

---

### Post by YoshiHNS on 2011-10-25
Just had a thought with what you mentioned about the raid arrays starting at 1. Somewhere along the line, I believe they start identifying RAID partitions on md125, md126... instead of md0, md1, md2. Going to try that later and see if I get anywhere with that.

---

### Post by YoshiHNS on 2011-10-27
I have given up. I've saved all my files to a spare hard drive and starting the complete RAID and OS install from scratch. It's just not worth wasting time on anymore.

Tried setroot=md/0, using commas instead, installing grub to md0, putting the /boot/prefix in front of the 09_swraid1_setup file. Nothing worked. Maybe someday someone will figure out where the issue is.

[Found another thread that dead ended.]("http://ubuntuforums.org/showthread.php?t=1681190")

---

