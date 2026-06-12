---
title: "RAID-5 mobo suggestions?"
date: 2009-05-14
forum: The Cafe
---

### Post by hambone79 on 2009-05-14
My old P3 file server running on Ubuntu finally decided to give out last night. It appears that part of the root parition became corrupt which wiped out part of /etc and the mdadm.conf file along with it. Because of this, my RAID 1 configuration got all screwed up.

The good news is that I was able to boot from a Knoppix CD and copy all the data over to a USB hard drive. The bad news is that I don't have a file server any more, so I've started looking at buying parts to build a bigger/faster file server. I'm not really concerned about CPU speed, memory, or graphics capability because this guy will be strictly for network storage. I want build something in a RAID5 configuration, but I want to do it cheap. I'm currently looking for a motherboard that offers on-board hardware RAID 5. Anyone know of a good motherboard like this?

---

### Post by handy on 2009-05-14
Are you operating on a multi-NIC gigabit speed LAN?

If not, why would you want RAID.

It is the fastest way to spread corruption on your drives.

Unless you have a huge network bandwidth, RAID is nothing but trouble.

Some people even think that RAID is a backup solution!!!

---

### Post by Delever on 2009-05-14
We recently looked into RAID 5, and found that it is mostly useful if you have MORE than 3 drives in array. Just have that in mind.

EDIT: also, most motherboards do not actually have "hardware" raid, it is still software.

---

### Post by hambone79 on 2009-05-16
> **handy said:**
> Are you operating on a multi-NIC gigabit speed LAN?

If not, why would you want RAID.

It is the fastest way to spread corruption on your drives.

Unless you have a huge network bandwidth, RAID is nothing but trouble.

Some people even think that RAID is a backup solution!!!

I'm not looking at RAID-5 for speed. I'm looking at it because I want a large fault tolerant file server.

> We recently looked into RAID 5, and found that it is mostly useful if you have MORE than 3 drives in array. Just have that in mind.

EDIT: also, most motherboards do not actually have "hardware" raid, it is still software. 

I don't mind if it is software or hardware based. I just want it to be transparent to the OS.

---

### Post by Delever on 2009-05-16
> **hambone79 said:**
> 
I don't mind if it is software or hardware based. I just want it to be transparent to the OS.

Yeah - what I am saying, many of them REQUIRE you to have drivers loaded to use it.

---

### Post by handy on 2009-05-17
> **hambone79 said:**
> I'm not looking at RAID-5 for speed. I'm looking at it because I want a large fault tolerant file server. 

So, I take it you will have some form of external backup?

> **hambone79 said:**
> 
I don't mind if it is software or hardware based. I just want it to be transparent to the OS.

Have you had a look at FreeNAS?

I use it (in a non-RAID form) it is very easy to set up, observe & maintain.  Once installed you use a client to access the brilliant browser based control panel.

FreeNAS handles soft & hard RAID, the FreeBSD handbook has all of the hardware supported.  

Great all round documentation too.

---

