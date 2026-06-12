---
title: "Install of 14.04 server, RAID"
date: 2014-12-30
forum: Server Platforms
---

### Post by jason162 on 2014-12-30
Just built my first computer and installed 14.04 server.  During install from iso USB drive, I keep on getting stuck on partitioning/mounting drives.  I'm new to all of this and have spent countless hours trying to read and watch videos, but seems way above my level, so looking for any help.
I have 1 128GB SSD drive
I have 4 2tb wD red HD
16GB ram

I want to install OS on ssd drive and then set up raid 5 on wd hd's.

i watched videos on using "manual", and "guided with entire disk", etc but it never seems to work.  

I was told by a friend that I should use the ssd drive for additional swap memory.....  

I know this is vague, but anyone that can help me with the initial install onto ssd drive would be great

---

### Post by Bucky Ball on 2014-12-30
You should use a regular hard drive for /swap if you have space spare. It doesn't need to be more than 2Gb unless you hibernate often (unlikely with a server) in which case /swap should be the same size or bigger than your installed RAM. SSD wasted on on a /swap as /swap is rarely, if ever, used (depending on what you're doing, naturally). 

When you get to the partitioning section of the install, choose 'Something Else'. That will let you manually create partitions and tell the installer where to put the OS and everything else.

Just out of curiousity, you are installing the server version because you're intending the machine to act as a server? Might be a silly question, but just wondering ... ;)

---

### Post by jason162 on 2014-12-30
any suggestions greatly appreciated....  I was told to install server version and then use a minimal gui desktop to keep system from wasting resources.  I am really new to linux and have a lot to learn.  
I set up this system so I can store all my media from three computers  and two external NAS drives in one location.  I stream all of my media to a apple tv that i changed the certifications on to run plex through the trailers app on apple tv.  I would also like to run bit torrent programs and have the ability to put more programs etc and I learn about them.   


I was never given the  "something else," option.  it gave me 10 different choices such as:
manual, guided with lvm, guided using whole disk, etc.

Thank you again for your help.
jaosn

---

### Post by MAFoElffen on 2014-12-30
On the swap... Agreed. If you put that on another small disk, it will be faster when and if if needs to use that. Even if that is all that is there, or you split out your /boot (and possiibly your /home) to that, the rule of thumb for sswap size is 1.5 to 2 times the size of your installed RAM. (I have a bunch of 2-4GB SCSI 15k drives that I use for that).

GUI on server. That is controversial, depending who you talk with. Old-school diehards still argue to go console. I have to agree that GUI does take overhead and does open up possible security issues over just running console. But... I'm back in school doing certifications. Even on Win Server, they now concede that core (thier console) is more secure than their GUI version. But admin is faster and easier under a GUI Env. 

I like to install minimal X to mine. They all boot to console. You can log in and start a desktop, but when you exit out of the desktop, mine go back to the console. Do what I need to a get back out, without the overhead and security issues. I send XMessages to my management consoles and my management tools are remoted into my servers. Most my servers I use Openbox... A few I have LXDE. (Heck, I have LXDE install on my phone.)

Note on partitioning. How do you want it? Soem otpions won't shwo until you do "other" things... and I'm not really sure were those are documented. I just learned by doing. I always use manual. 

Beforehand, figure out what you want to do and use. If you want to play with Linux RAID or LVM... No hardware needed. But they take planning on how you want to lay them out. For instance RAID 6 will take 4 partitions and you might want a spare. You would prep 5 partitions. As some as you have over 2 partitions present, the mdadm RAID option will show in the partitioner menu... (funny how that works) Once selected you select how many partitions to the array, how many as spares... I have to admit that I was a old-school hardware RAID fan until about 4 years ago. (Until I tried Linux RAID) Now I'm a fan of Linux RAID.

LVM... Been using a little over a year. Forced myself to learn it. Now I love it. You can mirror volumes, span volume across physical disks... take snap shots for back ups... It's very flexibles and can add a layer of redundancy, buffer of error reporting before issues arise, etc. But again, you have to learn what it can do and how to use it.

If you want to know about something, just ask. There is a lot of people from the Server section, who have helped me learn and helped me when I got stuck. I'm here to pass it on and give back.

---

### Post by Bashing-om on 2014-12-30
jason162; Hi ! Welcome to the forum.

Raid as you know is a "different ball of wax" .
The guide I used years back to set up 'software raid 5' :
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
A bit dated, but with discretion still applies.
Pencil and paper here is required to lay out your partitions on each disk. Pay attention to how you want to use grub ( Grand Unified bootloader). No matter the method, you will sacrifice disk space .

also:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)


Depending on your hardware, and what you want to do.
The knowledge base here is impressive, what you do not know and can not figure out, ask.
Someone here will know and respond to a thoughtful question.

[INDENT][INDENT]ain't no business like server business
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-12-30
> **Bashing-om said:**
> 

[INDENT][INDENT]ain't no business like server business
[/INDENT][/INDENT]

And with that, might be better here. ;)

*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2014-12-31
And of course the required .... **RAID is NOT a substitute for backups.**  There are many RAID failure modes where having a backup is the easiest way to recover.  Doesn't matter if it is HW-RAID, SW-RAID or Fake-RAID .... we all need backups.

Any server with 16G of RAM can easily run an Ubuntu GUI if the GPU in the box is $20 or more.  I'm a CLI-only person for systems management and most of the server-things does not have any GUI tools, so loading X/Windows onto a server really only matters if you have to sit behind the server itself.  It lets you have multiple terminals open to select/paste between. I basically only sit behind a physical server for the 15 minutes needed to do the install, then never again. We are small and don't have console concentrators here. Using a desktop to remote into any server for management is how 99.9999999999% of the UNIX/Linux servers are managed in the world. Only people at home sit behind a server and type.

BTW, if all you want to do is share media and have a place to backup other systems, 16G of RAM in the server is 15G of overkill.  With 16G, I'd be temped to use ZFS and RAIDz2 for the storage. ZFS likes RAM and you have lots.  For samba and nfs, a 512MB RAM server can easily provide all the storage sharing needed in a home regardless of the CPU.  If you want to run Plex Server and transcode video for different devices on-the-fly, then a Core i3 or better CPU and 2G of RAM would be enough.

There are lots of partitioning layouts posted in forums here.  LVM is completely optional - with or without RAID it is not required.  I use it on physical servers always because of the flexibility, but the greatest data loss I ever had was due to mis-use of LVM. Lost 80% of my storage due to 1 HDD failing where I'd merged multiple disks into a single partition. I didn't have **backup religion** back then - it was a long time ago. There was nothing to be done to recover any of the data, even on the good drives, in the LVM LV. Bye-bye data.  Please learn from my mistake - backup.  Also, practice restoring before you need it.

---

### Post by MAFoElffen on 2015-01-02
> **TheFu said:**
> And of course the required .... **RAID is NOT a substitute for backups.** 
++1 

I learned the hard way on that also. (Shame on me.) Raid 5 3+1 disks. 1 disk failed. Added spare and another failed on the reassemble. A good proactive recovery plan.

IDK-- On RAM... Maybe I'm just old-school. I was taught to plan to balance factors, based on the server's job... Balancing between:
- OS + all apps + 25%... to try to prevent  excessive paging.
- Number of files x 1.5 k RAM
- 1GB RAM per TB storage.
-512MB-2GB RAM/1-2 cores per virtual server
Then for swap-- 1.5 to 2 times the installed RAM

I have 2 servers at 48GB RAM with 40TB storage each, 1 at 96GB and 80TB storage. (They don't upgrade evenly to 40GB or 80GB.) 16GB is allot for a web or average Home server. Not a lot for a hypervisor.

---

### Post by TheFu on 2015-01-02
> **MAFoElffen said:**
> 
IDK-- On RAM... Maybe I'm just old-school. I was taught to plan to balance factors, based on the server's job... Balancing between:
- OS + all apps + 25%... to try to prevent  excessive paging.
- Number of files x 1.5 k RAM
- 1GB RAM per TB storage.
-512MB-2GB RAM/1-2 cores per virtual server
Then for swap-- 1.5 to 2 times the installed RAM


I think you are really old school. ;)

All this RAM is overkill, unless you are running ZFS or some cluster file systems.  All other file systems simply don't need that much.  ZFS needs GB and all others need MB.

Swap - there are new ways to design swap.  2G is generally considered enough for well behaved servers where RAM for processing has been properly sized.  The goal is to never swap and accomplishing that is easy.  In fact, I don't usually allocate **any** swap to my VM servers. Their workloads are extremely well understood - no need at all for swap.  Swap for desktops is different - 4G is my minimum after experiencing system lockups thanks to modern browsers hogging RAM for little good reason.  Of course, if you hibernate, swap needs to be 1.0001x the amount of RAM or 4G (whichever is larger).  I only hibernate on netbooks, never servers.  The purpose of swap is to let users feel the server getting slower so RAM hogging processes can be removed.  I suppose if there are thousands of tiny processes which you want to have swapped out of RAM, but still appear in the process table, having a little more swap is desired.  That just doesn't fit the processing model for my systems.  We don't have thousands of end-users logged in sitting idle for days.

The number of files on a system has ZERO to do with how much RAM is needed ... unless ZFS or something new has been discovered. I'd love to learn.

Of the 30 VMs running here, only 2 get 2 vCPUs. All the rest get 1 and are oversubscribed on the physical system cores.  CPUs are so fast these days that more than one just isn't necessary for common workloads.  It is also important to leave 1 vCPU and 1G of RAM for the hostOS (if it runs a hypervisor) to have resources available to manage the VM workloads. I don't get the feeling the OP is doing any virtualization.  Of course, if you are running geospatial workloads at home RAM and CPU requirements are probably higher.  For a blog or media database, very little RAM is actually needed.  Most will be put towards disk buffers and after 1-2G, it just isn't needed, IMHO.  I have a few servers here with excess RAM that gets used for disk buffers.  Moving around a 2G file generally goes at wirespeed, but moving around a 22G Hidef TV recording eventually has to be written to disk and will slow down to reflect full disk buffers.  That's fine.  I just wouldn't spend the money on all that RAM to be used just for disk.  In my enterprise server sizing job (former day job), we never worried much about RAM for disk buffers - until it was an issue. Fortunately, by the time that happens, the buffers are on storage arrays and connected via 10G fibre so all is well.  EMC storage usually has plenty of buffers on their size, so the OS doesn't need to consider it.

So - I'd love to be educated on what my sizing is doing wrong.  Server performance is excellent here as is.  Generally the slowdown is not CPU (except when transcoding), but WAN bandwidth.  Could really use some 1G fibre to the house about now for $80/month. ;)

I hope this prompts discussion on server architectures, how to get the most from limited HW, and how to know when a monster server really is necessary.  I certainly don't have all the answers, just a decade of professional systems architecture, technical architecture and enterprise architecture work with mostly unlimited budgets across over 250 projects. That can lead to lazy solution designs.  At home, my budget is much tighter. None of my systems has more than 4 cores and most only have 8G of RAM - though 1 has 16G which is completely underutilized for useful purposes.

Hopefully, Jason will guide us towards his needs.

---

### Post by MAFoElffen on 2015-01-02
I would follow that discussion with very much interest!!!

1G Fiber to my house and I would be in Heaven. (I have the routers for them here.) Not going to happen here in any near future. (sticks)

Mostly for VM's. Only VM's I give 2 vcpus are some Solaris instances. Solaris instance seem real power hungry... They are they only ones the seem to benefit from that.  I'm wondering if giving up those resources for them is really worth it. They don't use swap. 

Been playing with using less swap for other VM's and allocating RAM for them dynamically, instead of a static numbers-- start on this amount, limit at this.. That is working out better. I used to set at what was recommended statically, but I think they must plan for the what-if max scenarios on those. That's when I started allocating 512MB as minimum... and was fine. Seems like the consistent big hit, is when a VM initially boots, then it levels off until it's actually getting hit hard with use. In between all that, a lot of idle ticks.

---

