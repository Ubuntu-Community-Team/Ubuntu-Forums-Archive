---
title: "Unable to install XP vm from cd/iso on shared partition"
date: 2008-10-31
forum: Virtualisation
---

### Post by mk4mzid on 2008-10-31
Hi all, having some trouble creating a new VM under Xubuntu 7.10 using VMWare Server 1.0.4.
So you have all the information, I dual boot Windows XP and Xubuntu. I have a second hard drive ( E: ) in XP that I mount as /winshare when I'm in Xubuntu. I spend 99% of my time in Xubuntu.

Now, I've been able to create an XP vm already using the default path for vm files, /var/lib/vmware/Virtua Machines, however I'd like to create a new one under the /winshare mount because I'm low on space under /. So I create the vm with no problems, it allocates the space fine. But when I try to boot the cd or iso to install Xp, the screen goes black, then just pops back out to the vm's summary page.

I've tested the iso and created a vm under the default path and it worked fine, but it just will not work when my vm is located on this shared partition.

I noticed that the share was mounted using umask=007, but changing to 000 didn't help, and actually makes things worse since now EVERYTHING under /winshare is wide open. I see /var/lib/vmware/Virtual Machines has sticky bit turned on, maybe that's it, but since I can't change the perms on the share's sub dir, I don't know how to turn it on for the share. So I'm stumped, hoping one of the guru's out there can help.

fstab
creating on this partition works
# /dev/hda5 (Linux)	
UUID=c6e84083-8b00-4a75-8a38-959d6dd1499e /               ext3    defaults,errors=remount-ro 0       1

creating on this partition fails
# /dev/hdc1 (Shared Drive)
UUID=7A2CB0002CAFB593 /winshare     ntfs    defaults,umask=000,gid=46 0       1

df,ls
/dev/hdc1             112G   53G   60G  47% /winshare
drwxrwxrwx 1 root plugdev 16384 2008-10-30 22:21 /winshare

After pasting the above, is the problem ntfs vs ext?

Thanks in advance for any info you can provide!

mk

---

