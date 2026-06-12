---
title: "Virtual Box upgrade issue"
date: 2016-06-28
forum: Virtualisation
---

### Post by cmcanulty on 2016-06-28
I want to upgrade my virtual box windows 7 to windows 10. The tool says I don't have enough space. Needs 20GB and I have a 50GB virtual box drive and all but 500MB of it is the windows 7 system itself. This makes no sense. It is counting all the windows 7 installation as used space when most of it will be overwritten. Is there a tweak for this?

---

### Post by MAFoElffen on 2016-06-28
A good guide on how to do that: 
[http://www.howtogeek.com/124622/how-to-enlarge-a-virtual-machines-disk-in-virtualbox-or-vmware/](http://www.howtogeek.com/124622/how-to-enlarge-a-virtual-machines-disk-in-virtualbox-or-vmware/)

BUT also thinking that it the image file is 500 GB That you could also do one of two things.
(1) Add a vritual disk to the machine ands migrate some things to that disk to make room for the upgrade. If fact. Virtual Machines run betetter and have less chance of failure if you span the system over multiple smller images, rather than a single large image file.

(2) Inventory your content and do some disk cleanup. You might be surprised how much room you might be able to reclaim from caches and old downloads of old archived update files.

(3) I add more disk, but I (<-- This is just personal technique) also  point my own, both physical and virtual Windows installs,  to use a symbolic links in the C;/users/, C;/Programs, and C;/Programs-86, to point to corresponding directories on another disk, that I migrate all that content to. Just like creating a boot partition and home partition in Linux, it makes sense to move/spit out things that grow to places where they have room to grow.

Of course, it does not help you now with Windows 7, but with Windows version 8.1 and up, you can then use Storage Spaces, which is Windows version of Linux LVM. (To span data across multiple disks). So if you bit the bullet and found room now by cleanup, it will be easier for you for find room in the future..

---

### Post by cmcanulty on 2016-06-28
I got it going by deleting everything except the basics. Windows using 30GB for a very basic setup is nuts. But good news by downloading the latest VirtualBox from the web site rather than the repositories I was finally able to get around the graphic card won't allow win 10 upgrade issue. I really don't like win 10 but need to learn to get around it so I can provide support for our library patrons using it on their laptops. Linux forever. Installing and upgrading windows takes all day, ubuntu 20-30 min.

---

### Post by MAFoElffen on 2016-06-29
Happy to hear it's working for you.

If this is now solved, please revisit this thread to mark it as such. (Upper right of page > Slect link "Thread Tools" > Select "Mark thread as Solved"). This helps other to find answers to their similar problems.

---

