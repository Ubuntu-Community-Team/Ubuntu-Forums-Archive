---
title: "Gparted slow opening"
date: 2012-08-06
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by GreatDanton on 2012-08-06
Hi, as you can see in the title I am wondering if anyone has same problem as me. I installed Gparted and whenever I want to open it, I have to wait for about 9 minutes (stopwatch did the job, haha, 9minutes 35 seconds to be precise). Does anybody have the same problem or it's just my hardware?

Regards.

---

### Post by cariboo on 2012-08-06
I haven't used Gparted since last week, when I formatted a USB thumb drive, but it preformed the way it should. Have you had the problem from the start of the development cycle, or Is this something new?

---

### Post by GreatDanton on 2012-08-06
> **cariboo907 said:**
>  Have you had the problem from the start of the development cycle, or Is this something new?

Actually I am new in this section (started from alpha3-current release). So it's from the start of development cycle :).

---

### Post by ronacc on 2012-08-06
on my AMD64 sys gparted seems to take about the normal amount of time to open . a few seconds , finding the drives seems a bit slow ( I've got 6 in this box ) but not more than a minute .

---

### Post by oldfred on 2012-08-06
A while back (years) I had issues with gparted being very slow and then not showing sda. It turned out that even though my XP on sda booted, it needed chkdsk. Once I ran chkdsk Windows booted a bit faster (4 min instead of 5) and gparted then worked very quickly. I have many partitions on sdc and it does take a bit but not excessive to review everything.

So is there an issue on another partition with a need for chkdsk or e2fsck?

---

### Post by GreatDanton on 2012-08-07
> **oldfred said:**
> 
So is there an issue on another partition with a need for chkdsk or e2fsck?

No. My Hard disk is empty. I created few partitions, but there is nothing on it. Maybe I wasn't clear&#8594;Gparted open right after I click on, but it takes 9 minutes to scan for devices.

---

### Post by oldfred on 2012-08-07
That was the issue I had. Is there something unique about your 'empty' partitions that may make them difficult to scan?

Once gparted does open do any of those other partitions have red or yellow icons as warnings?

---

### Post by GreatDanton on 2012-08-07
Here is the screenshot of current partitions. Quantal Quetzal is on /dev/sda8 and home partition is on sda9.

Screenshot is taken from Xubuntu 12.04 (yes I need one stable system) on /dev/sda5. sda6, sda7 are reserved for other distributions, Unallocated space is reserved for Windows7.

Gparted opened in 2 seconds without any problems, so I guess problem is with QQ.

Thanks for your help.

Regards.

P.S the second picture is taken from QQ. I can't see any warnings.

---

### Post by sammiev on 2012-08-07
This screen shoot took about 9 seconds. Last week I did 2 HD's with gparted and changed the HD's to how I wanted them and each took no more than 1 min.

---

