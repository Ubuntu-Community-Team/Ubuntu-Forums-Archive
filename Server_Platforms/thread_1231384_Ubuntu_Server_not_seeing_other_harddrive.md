---
title: "Ubuntu Server not seeing other harddrive"
date: 2009-08-04
forum: Server Platforms
---

### Post by r8ermang on 2009-08-04
Hello,
 
My Ubuntu server is not seeing the second harddrive. How can I mount it and use it?
 
Thanks
 
raider@homer:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 9.04
Release: 9.04
Codename: jaunty
 
 
raider@homer:~$ uname -r
2.6.28-14-server

---

### Post by druhboruch on 2009-08-04
Is your disk already partitioned and is file system created?

---

### Post by hockey97 on 2009-08-04
what do you mean not seeing it? 

if you mean you don't see it on your desktop then you need to mount it every time. 

You should look under Places. You should see any 2nd or more hard drives listed under dvd creator.  If you see the name click on it and it will mount that hard drive. 

You should then see it on your desktop. You have to do this every time you restart your computer. 

If that's not the case. What type of filesystem is your 2nd hard drive?

is it ntfs or fat32?  If so you need to download a windows file system reader. This will read any windows formatted hard drives. 

If that is not the case. Then you have to figure out if it's formatted if you know for sure it has a partician and is formatted. 

Then you must open your computer and check the connections if it's loose.

These are what I can think of on top of my head hope this helps.

---

### Post by mohnkern on 2009-08-04
What does an fdisk -l from the shell show you?

---

