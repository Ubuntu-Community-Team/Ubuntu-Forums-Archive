---
title: "whats the best file format to host a Ubuntu Virtualbox inside Windows 7"
date: 2015-10-30
forum: Ubuntu, Linux and OS Chat
---

### Post by eival on 2015-10-30
i have 16 gigs of ram, so plenty of space to host the entire session just in ram, but I still want to be able to save updates and use that as my web browsing box, while the windows 7 shell is for my game streaming/capturing which doesnt have linux driver suppport.

i know VM's have different types of file systems other than just VDI, do any of them impact performance?

also if i were to migrate this to my SSD would doing this cause a lot of R/W on the drive or is it safer to just do it on my WDblack?

also is there any chance that windows viruses or malware in the VDI(or other type of file system) could talk to the windows 7 host or does it stay contained?

are there any articles that talk about the security of doing this, i'll still have QiHoo 360 on W7 with the bitdefender and avira engines protecting everything so its not a huge deal, but just wondering

---

### Post by TheFu on 2015-10-31
Lots of opinions below....

a) On SSD, the VM file container matters very little. Go with sparse.
b) On spinning disks, my most recent testing shows that sparse inside a VDI has a slight performance loss compared to fully pre-allocated containers. Most people would think that using sparse would be more convenient and worth a tiny hit.
c) If Windows is the HostOS - think of it as the beach - if  you lose the beach, you've lost everything when it comes to security.  You can run 20 AV tools and 15% of known viruses would still get onto the box. AV just isn't that effective, because it is always behind the current attacks. Our brains are the main AV tool we have.

SSD vs WD-Black.  Go to the numbers - SSDs have a longer predicted lifespan than any spinning disk, but all disks fail, so backups are absolutely required for anything you care about. Predictions are just guesses.  YOUR SSD or YOUR HDD could fail in 1 minute. Our goal is to move all our data off any disk *just before*  it fails. Guessing when a disk is about to fail is very difficult.  Nothing can replace *versioned backups*. Nothing. Versioning is very important.

VDI is actually just a container. It is not the file system.  If you want the highest possible disk performance, don't use virtualbox or Windows.  [https://www.phoronix.com/scan.php?page=home](https://www.phoronix.com/scan.php?page=home) just did a disk throughput test this month comparing 4 different virtualization tools. Interesting reading of you care.   [https://www.phoronix.com/scan.php?page=article&item=ubuntu-1510-hdd&num=1](https://www.phoronix.com/scan.php?page=article&item=ubuntu-1510-hdd&num=1) says XFS is faster than EXT4 and BTRFS. XFS can't do some things these other file systems can, which may or may not be important to you. Btrfs has some caveats when used with VMs.

I wrote a virtualbox performance tuning guide a few years ago: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox) May be of some help.

---

