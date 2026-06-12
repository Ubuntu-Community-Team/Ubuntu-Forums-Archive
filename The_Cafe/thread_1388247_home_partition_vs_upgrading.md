---
title: "home partition vs upgrading"
date: 2010-01-22
forum: The Cafe
---

### Post by mamamia88 on 2010-01-22
is there any benefit to either?  which one would leave me with more of my settings in tact?  i know a separate home partiton would be much quicker and take at most 20 minutes to install new version where upgrading would take much longer on my internet connection

---

### Post by bxcrx on 2010-01-22
Pros of a home partition:

You retain your user/application settings for the most part during upgrades

You can go back from a bad upgrade


Cons:  

Maybe you made your home partition to small, or to large.

Too small - You run out of space to keep your data
Too large - You don't have enough room for updates etc in your other partition...


Pros of an upgrade

Hopefully all goes well and you can boot back into your desktop without anything changing

Cons

You can't go backwards from an upgrade


When you compare the two , keeping your settings on a separate partition and doing a clean upgrade is always the best answer.

---

### Post by mamamia88 on 2010-01-22
cool I think i will go with a separate home partition thanks.

---

### Post by The Real Dave on 2010-01-23
You should always use a seperate /home partition, it saves a lot of hassle between upgrades, and if you get filesystem damage to one partition, your data is still safe. I usually only give 8-10Gb to my / poartition, and then as much of the rest of the drive as possible to /home

---

### Post by llawwehttam on 2010-01-23
I have a 5 Gb /boot partition ( I know that much is unnecessary) , a 20 GB / partition and the rest as /home .

A clean install is always better than an upgrade.

---

### Post by slakkie on 2010-01-23
> **bxcrx said:**
> 
Pros of an upgrade

Hopefully all goes well and you can boot back into your desktop without anything changing

Cons

You can't go backwards from an upgrade


When you compare the two , keeping your settings on a separate partition and doing a clean upgrade is always the best answer.

Is that right?

---

### Post by oldfred on 2010-01-23
The only way you can go back is to copy all your data (/home) and reinstall. Part of a concern may be that newer versions of programs have newer slightly different settings that get saved into the hidden config files in /home that the older version may not recognize. Programs are generally configured for updates but not downdates.

I used the standard install of just root & swap for 3 years and updated every 6 months to the new version. I had issues with every update as some settings changed but my configs did not ( usually my choice as I was not sure if I would lose something I wanted). My clean install of Karmic was trouble free, but I did a lot of planning on conversion.

For Karmic I decided I wanted a clean install. I moved /home and created /data for all my data. I had a new drive so I had lots of room. I installed in a new partition and kept my old install just in case I wanted some old setting that was not in /home. I did find one or two things that I wanted to go back & find, but most was in /home. I did have to find all the applications and reinstall them. You can export from synaptic or with commands a list of all your apps and then reinstall all of them. My new install is only about 5GB with many applications, my new /home with some of the hidden partitions with the 3 years of history still is only 1GB, all my data is in a data partition linked into /home.

---

### Post by ssam on 2010-01-23
there is no need for a separate home partition, for doing installs.

if you use the manual partitioner in the installer, tell it to install onto a partition that already has ubuntu installed and dont tick the format box. then it will leave the /home folder intact.

i have used this to upgrade a machine from 8.10 to 9.10 in a quick step.

---

### Post by cguy on 2010-01-23
Separate /home partition for the safe, trouble free keeping of data. Use ext3 since it's "bulletproof".

10GB for / so I can install any program/upgrade the distro without concerns for space

a few hundreds MB for /var/log <- do yourself a favor and **create this partition**. When logging goes wild (I've had this happen twice) and your root partition gets filled, things aren't looking good.

/tmp - on a separate disk (I have an old, kinda slow, small capacity disk for this one)
It noticeably speeds up the system in *those* situations.
It is 6GB in size so it can fit the intermediary .ISO of a DVD I'm writing, along with the junk.

200MB - ext2 for /boot for a faster... well, boot.



This is the config I thought is the best after reading plenty on the subject.
It can get better if you have multiple disks.

---

