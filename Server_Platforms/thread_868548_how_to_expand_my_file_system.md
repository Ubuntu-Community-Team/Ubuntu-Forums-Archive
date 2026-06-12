---
title: "how to expand my file system"
date: 2008-07-24
forum: Server Platforms
---

### Post by soon82 on 2008-07-24
Hi, 

I have one samba server, and i have noticed that one of my file system was full. So i would like to install one hard drive and expand on it. Anyone of you can help me on this.


root@Aquasvr:/# df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             17781232   1869944  15008036  12% /
tmpfs                   485272         0    485272   0% /dev/shm
tmpfs                   485272     12588    472684   3% /lib/modules/2.6.12-10-386/volatile
/dev/sda5             29280176  29206768     73408 100% /Draft
/dev/sda6             29280176  10338688  18941488  36% /Project
/dev/sda1               466662     22879    418884   6% /boot

---

### Post by Traumadog on 2008-07-24
> **soon82 said:**
> Hi, 

I have one samba server, and i have noticed that one of my file system was full. So i would like to install one hard drive and expand on it. Anyone of you can help me on this.


root@Aquasvr:/# df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             17781232   1869944  15008036  12% /
tmpfs                   485272         0    485272   0% /dev/shm
tmpfs                   485272     12588    472684   3% /lib/modules/2.6.12-10-386/volatile
/dev/sda5             29280176  29206768     73408 100% /Draft
/dev/sda6             29280176  10338688  18941488  36% /Project
/dev/sda1               466662     22879    418884   6% /boot

Hello soon82,

Here is a quick web tutorial on how to partition, format and mount a second HDD that you might find useful: [http://www.idevelopment.info/data/Unix/Linux/LINUX_PartitioningandFormattingSecondHardDrive_ext3.shtml](http://www.idevelopment.info/data/Unix/Linux/LINUX_PartitioningandFormattingSecondHardDrive_ext3.shtml)

In your case, remember to create a mount point that is within the directory that you are using as your SAMBA share.

Hope this post is useful for you.

Best wishes, :)

Traumadog.

---

