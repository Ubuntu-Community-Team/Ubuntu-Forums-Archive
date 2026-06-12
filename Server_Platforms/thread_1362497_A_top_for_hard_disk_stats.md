---
title: "A top for hard disk stats?"
date: 2009-12-23
forum: Server Platforms
---

### Post by jimxms on 2009-12-23
Hi All,

I'm running into some problems with my Ubuntu install where the disk performance seems to significantly degrade over the course of a couple of days.

Doing a hdparm after a fresh restart shows my disks at about 90mb/s (expected), however a day later they are at 15mb/s.

I'm wondering, is there a utility a bit like 'top' which will show what applications are using hard disk time so that I can maybe track down what is happening.

Thanks

---

### Post by BkkBonanza on 2009-12-23
I don't know of a top like program but you may get some diagnostic help using lsof. This will list open files and combined with various options and grep can be used to track certain programs or uses. See man page.

If you can narrow down a small group then you could use with the watch command to keep a monitoring screen you can view.

I think it does give you some usage stats for the files but I haven't explored all the multitude of options it has.

---

### Post by oneloveamaru on 2009-12-23
There are programs like this but I have only found them in Solaris.

What you can do though, is just use "top" and look at the "wa" number. That's IO wait. If that number is always high, then you know something is using a massive amount of disk IO.

If I find a good program to use, I'll let you know.

---

### Post by jimxms on 2009-12-23
Cheers for the replies.

onelove - unfortunately i don't have a WA column on top or ps :(

---

### Post by oneloveamaru on 2009-12-23
You are probably not looking in the correct place.

top - 16:03:44 up 2 days,  6:09,  1 user,  load average: 0.00, 0.00, 0.00
Tasks:  74 total,   1 running,  73 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  **0.0%wa,**  0.0%hi,  0.0%si,  0.0%st
Mem:   1028628k total,   687120k used,   341508k free,   167908k buffers
Swap:  1951888k total,        0k used,  1951888k free,   354212k cached

---

### Post by Jose Catre-Vandis on 2009-12-23
Install **htop**, its easier to read, use and configure

---

### Post by Mister.Vash on 2009-12-24
Use iotop 

That should do it for you.  Like top, but for I/O usage

---

### Post by BkkBonanza on 2009-12-24
Just installed iotop and it's great. The version in the repos has some issues though so you may want to update using the deb package (to 3.2-1). If you're on Lucid then it has this new version. In the repos 3.0 doesn't work properly for accumulated (-a) mode and only (-o) mode together. The update keeps accumulated info on display after the activity ends and it sorts correctly when accumulated data is listed. 

On the downside there is a message about SWAP IN and IO% not working due to kernel options. Oh well, I requested a feature to quiet the error message and columns when not available. 

Pretty nice tool though. Thanks for suggesting it.

---

