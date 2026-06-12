---
title: "Linux Partitioning"
date: 2008-12-29
forum: Slackware and derivatives
---

### Post by DeadBolt on 2008-12-29
Ok I have a 160 gig hard drive and going to install Slackware 12.2 and wondering how big I should make my partitions. Can someone give me some sizes I am not sure how to make the sizes and how many. I was thinking partions for /boot, /home, /usr, /var, and /opt

Could someone give me some suggestions? :popcorn: :confused:

---

### Post by Superslobberface on 2008-12-29
I suggest you create at least 3 partitions:

/ and /home and a swap partition

If it were my system I would probably allocate the following:
[INDENT]
/ = ~36GB
/home = ~120GB
swap = ~2X available RAM (if you have 2GB ram create a ~4GB swap partition)
[/INDENT]
This assumes everything except your /home partition will be saved on / (or a child of /)

It is simple and allows you to persist your /home data even if you install a different distribution.

This is always up for debate.  It depends on how the system will be used.

You can read more:
[http://www.linuxplanet.com/linuxplanet/tutorials/4269/4/]("http://www.linuxplanet.com/linuxplanet/tutorials/4269/4/")

---

### Post by Bachstelze on 2008-12-29
36 GB for a root partition is WAY too much. 10 will already be more than enough.

---

### Post by nick192 on 2008-12-29
/boot 150mb
/  10gb
/var 5gb  (cuz all updates r downloaded in this directory. u can use them later if u've to reinstall os)
/home (remaining space - swap space)

now about swap. ive read on oracle guides that swap shud b:
upto 2gb ram == 2*ram
2 gb to 4gb ram == 1.5*ram
4 gb and 8gb ram == 1*ram
8gb and above == 0.75*ram
n 1 more thing is for performance dont make swap more than size of 2gb. if u want to create 4gb swap then make 2gb + 2gb..

n btw thats what written in that guide.. n not by me :mrgreen:

---

