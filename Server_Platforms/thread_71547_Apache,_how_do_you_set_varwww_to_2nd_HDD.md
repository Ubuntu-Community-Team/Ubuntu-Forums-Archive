---
title: "Apache, how do you set /var/www to 2nd HDD?"
date: 2005-10-03
forum: Server Platforms
---

### Post by waynejkruse10 on 2005-10-03
I have rebuilt my server computer, now with a P3 800mhz, 512mb Ram and 2 HDD's. I am doing a fresh install of Ubuntu Hoary on my small HDD (4gb) but i want instead of the /var/www to be on the drive the system is on, i want it to be on the other drive.

Thanks
Wayne

---

### Post by rockett15 on 2005-10-03
FYI

[http://www.ubuntuforums.org/showthread.php?t=22348]("http://www.ubuntuforums.org/showthread.php?t=22348")

---

### Post by waynejkruse10 on 2005-10-03
ok, but none of the other forums really is suited for configuration, its all application support.......

---

### Post by benplaut on 2005-10-03
[QUOTE=waynejkruse10]ok, but none of the other forums really is suited for configuration, its all application support.......[/QUOTE]

this forum is also not suited - it is for HOWTOs

in the installer's partitioner, it gives you options for setting various parts of / onto seperate partitions and drives. Your answer is probably just playing with the installer till you figure it out...

---

### Post by waynejkruse10 on 2005-10-03
> 	
Hoary 5.04 Customization Tips & Tricks (105 Viewing)
The place to Customization Tips & Tricks to help other users and to discuss them. 

It doesnt exactly make it clear its for HOWTO's.

---

### Post by cactus on 2005-10-03
You could optionally, just create another mount point, and have fstab mount it there.
/dev/hdb1 /var/www reiserfs defaults 0 0

I dont see why that wouldn't work.

This should probably go into one of the server forums though..
Mod move?

---

### Post by poofyhairguy on 2005-10-03
[QUOTE=waynejkruse10]It doesnt exactly make it clear its for HOWTO's.[/QUOTE]

The announcement is at the top of the how to forum.

Moved.

---

### Post by LordHunter317 on 2005-10-03
Either mount your new drive at /var/www, or change the DocumentRoot and add a Directory directive for it.  Tell me whichever you prefer and I can post more details.  The former is preferable, IMO.

---

### Post by waynejkruse10 on 2005-10-04
Thanks for all your help, i mounted my drive in /var/www and it worked very well.

Thanks everyone :D

---

