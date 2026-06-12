---
title: "Write Access trouble with second Hard drive"
date: 2011-09-01
forum: Server Platforms
---

### Post by henrybs on 2011-09-01
So I might be a slightly new user to command prompt in terminal but I'm getting there with guides on the internet for what I need,

So I've got my second hard drive a 500gb Western digital, the first guide I read said you mount using fdisk-l to the name and stuff which was /dev/sdb at the time and I changed the /etc/fstab file, That was sweet for ten mins, not sure if i even mounted it right, but i soon found out the device names change depending what the computer see's first when it boots up so I found the UUID method for mounting my hard drive, for some reason my server crashed so i reinstalled.

So I'm on a fresh install, ssh, static ip is set up,

sudo blkid gave me my UUID number to my hard drive and the hard drive type which is HTF+ which was formated on my mac book before I put it in, I restarted and I tried to use the touch command to the folder I mounted it to, but I get I have read only permissions, so I tried doing "sudo chmod -R 777 /Files" (files been the folder I mounted the drive to), still didn't work so I tried the same command on the device it was /dev/sdb2.

I thought since this didn't work that I'd look at my fstab file again, which was setup as, 
UUID followed by mount point /Files, htfplus(can't remember what I wrote but i got it from blkid) followed by defaults, 0 0
I tried changing defaults to is RW for rewrite access, but still no luck, just get the same problem of it saying I only have read access.

Some suggestions on ideas to try would be helpful, I might try format it to fat32 tonight and see where I go from there


I'm on ubuntu server 11. something   64bit amd
80gb install drive, 512mb ram, 2.7ghz duel core, 2nd hard drive 500gb western digital.

Using ssh from my mac book, but have a screen and everything I can use, I just like using ssh so I can sit it the lounge.

---

