---
title: "RAID array wiped by fsck?"
date: 2009-06-10
forum: Server Platforms
---

### Post by legomind on 2009-06-10
Hello all,
I have searched the internet for a week now, and I must say that either my problem is so simple that no one bothers to post its solution online or my situation is fairly unique! 

I have a simple dell optiplex set up with hardy server and a software (fake) RAID 5 array using (3) 1 terabite drives, giving me roughly about 1.8 terabites of secure space formatted ext2. I have had this server set up since hardy came out. (about a year, I think) The server, despite a few kinks worked GREAT. :)

now let me fast forward to the bad part. :(

Last week my dad informed me that he had been given a legal copy of windows server 2008 that he wanted to try. (He is not a Linux fan, don't ask me why - It keeps him from buying software!;)) 

So, the poor Pentium III optiplex isn't going to cut it with vista, so I move the three terabite drives (yes, keeping them in order) and RAID controller to dell dimension 8200 after installing windows server 2008 and ext2ifs. Now here is the weird part. My ext2 formatted drive shows up in disk manager as unallocated. OK, so I figure instead of moving the drives back to the old computer to check it out, I install ubuntu next to vista, Install dmraid, and try to mount the RAID drive.

I get the following error:

Cannot find superblock on device /dev/md0

So I google it. Find a few commands to find backup superblocks.

it was something like:   newfs -n /dev/md0  -- Yes I DID use the -n switch!!!

It gave me a very lengthy reply about missing superblocks. -- Yes it couldn't find any. -- which is kind of confusing to me because as far as I understand this command dosen't look for any, it tells you were they would have been put.

so out of Ideas I run fsck on /dev/md0. Asks me a bunch of y/n questions about fixing block xxx on xxx. I choose yes to a whole lot of them. It finishes, I reboot. Now I try to mount the RAID disk again, but I get an error about /dev/dm0: wrong fs type, not ext2.......

I open up a terminal and type:
sudo dmraid -r

I get:
zero sectors on /dev/sdb
zero sectors on /dev/sdc
zero sectors on /dev/sdd
NO RAID DISKS.

In the bios of my fasttrack raid controller the array says:

2+1 RAID5 array   functional.


Now after my life story, what I want to know is:
(1) what I did wrong trying to fix the superblock
(2) how I zeroed my 600 gb of data
(3) can/how I recover my data

Thanks in advance

---

### Post by HermanAB on 2009-06-10
Howdy,

You should restore from backup.

In my experience a RAID array is a sensitive beast and should be hands off as far as possible.  Disks only go south once in a few years, so my experience with RAID repair is very limited and doing any sort of file system repair on a RAID has *always* resulted in total RAID loss to me, so I'm not surprised.

---

### Post by Vegan on 2009-06-10
Anytime you need to move a RAID array, you should back it up completely. This is because different machines will usually fail to recognize the array, even with a hardware card.

When I need to upgrade, I build whole new servers and just copy the files over the LAN.

Much safer as the old server becomes a defacto backup.

---

### Post by legomind on 2009-06-12
I wish that I had make a recent backup. I know it was stupid not to make one before moving the disks, but I did it anyway. :( Restoring the data I have has always been an option, but I need to know if there is any hope of recovering what I have lost.

Any other suggestions?

---

