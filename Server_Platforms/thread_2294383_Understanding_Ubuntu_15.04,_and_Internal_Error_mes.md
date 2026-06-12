---
title: "Understanding Ubuntu 15.04, and Internal Error message, must restart server."
date: 2015-09-10
forum: Server Platforms
---

### Post by Joseph_Florio on 2015-09-10
Hello, and Thank you in advance for any help you can give me!

I am new to Linux Ubuntu, and I have Distribution 15.04 loaded on this server.  I am not in business, but after using Microsoft Vista for many years I grew to hate it on my last computer, so I decided to buy a server with several hard drives to store all of my video's, photo's and letters that I have accumulated over the years.

I bought a Lenovo Thinkserver TS440 with 4--2TB hard drives, and I did successfully set-up these hard drives with a Raid configuration in the first and second two hard drives, in a mirror set-up configuration.

However I have not been able to figure out how to use the second set of hard drives, the first two are 0 & 1 named System, the 3rd and 4th hard drives are named Data for videos and photos I would want to store.

In other words the first two hard drives are named System, which are for the operating system, and any pertinent information connected to it, the second set of hard drives named Data are empty, and I would like to store photo/video in files them.  
My question is how do I do that?

I think I have found these hard drives in my files folder, but trying to use them is another problem I have not figured out.

Just to let you know the system seems to be working fine, except the server has reported a few internal errors, and I am blaming these errors on the possibility of the newest (Beta) Ubuntu OS, (and I'm sure you know when they are new they have bugs)  
The second possibility is that the Bios is not set-up for Ubuntu, and is set-up mostly for MS 7 or 8, I may need to update the Bios if one is available for Ubuntu which so far there isn't one..

Please let me know if you have answers.
Thanks Again,
Joe

---

### Post by howefield on 2015-09-11
Thread moved to the "*Server Platforms*" forum for better support.

---

### Post by darkod on 2015-09-11
Hi Joe.

Few things to clear out, especially the ubuntu version/type.

1. Desktop or Server?
You said you "found the hard drives in my files folder". Does that mean you installed the Desktop version? Because that makes a difference, even if it's on server HW. The version type is more important than the machine.

2. Ubuntu 15.04.
If you look at [http://releases.ubuntu.com](http://releases.ubuntu.com) you will notice there are few releases with LTS in the name. That means Long Term Support and those are the recommended versions for servers and basically machines you intend to run stable for longer time. The non-LTS versions (like 15.04) have only 9 months support. The LTS versions have 5 years. The current LTS is 14.04 (the first number is the year, the second the month of release) that was released April 2014 and the next should be 16.04 in April 2016. They come out every 2 years (so far).
So it's more than recommended to use Ubuntu Server 14.04 LTS even for a home server.

3. RAID
The raid decision is very tricky. Linux and Ubuntu have a very good software raid which is done with the mdadm package. Most servers these days will offer you some type of raid levels, but I don't know if in your case that's a good dedicated HW raid controller or something built in into the motherboard. Sometimes built in raid still uses resources like the cpu because it has no dedicated cpu like HW raid cards have, and is called fakeraid. In such cases using SW raid with mdadm is much more recommended than using fakeraid. Even if you have HW raid, you can still decide not to use it (leave the disks to be presented to the OS as 4 single disks) and use mdadm instead. Some benefits of SW raid is that it will not depend on the HW (you can simply move the disks to a new machine and basically it will work as it is), and also often it has more flexibility and options.
Also, you need to think better about organizing your 4 disks in raid. When you say two raid1 arrays for System and Data, if by System you mean literary only the ubuntu server OS without using the root partition for big database files or personal files, asigning 2TB raid1 array for that is a waste. Note that basic ubuntu server install takes only about 2GB. In most cases, and I repeat without guarding big DB files and personal files on the root, a root partition of between 15-60GB is enough. On my home server I have 15GB root for example. The linux OS is not that hungry for space for root, if you have only the OS and configuration files on it.

So you might reconsider doing a raid5 of 4 disks, or for example doing a 100GB raid1 on disks1-2, then the rest 1900GB raid1 on disk1-2, and a 2000GB raid1 on disk3-4. After that you can use LVM to "join" the big arrays as one single continuos space and the OS will see 3900GB of space for the data.

Those are just few ideas...

---

