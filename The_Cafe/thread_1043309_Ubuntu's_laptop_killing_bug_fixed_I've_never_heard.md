---
title: "Ubuntu's laptop killing bug fixed? I've never heard of this"
date: 2009-01-18
forum: The Cafe
---

### Post by sefs on 2009-01-18
[http://it.slashdot.org/article.pl?sid=09/01/17/2127254](http://it.slashdot.org/article.pl?sid=09/01/17/2127254)

How do i ensure i have the fix installed?

---

### Post by smartboyathome on 2009-01-18
> **sefs said:**
> [http://it.slashdot.org/article.pl?sid=09/01/17/2127254](http://it.slashdot.org/article.pl?sid=09/01/17/2127254)

How do i ensure i have the fix installed?

If you have installed all the recent updates, then you have the fix.

---

### Post by jrusso2 on 2009-01-18
Not according to slashdot.  They are saying the fix is not in the updates yet.

"Back in October of 2007 we discussed a bug that would dramatically shorten the life of laptops using Ubuntu. Ubuntu users will be glad to know that a fix has finally been released for Ubuntu versions 9.04, 8.10 and 8.04 (LTS). However, as this fix is not yet in the update repositories, anyone wishing to test it should follow these instructions for enabling the 'proposed' repository. Report your results on the original bug report. Happy testing!"

I am wondering why it took so long to fix but I am glad its finally fixed.  There are people still saying there was no problem.

---

### Post by Polygon on 2009-01-18
they arnt in the regular repos yet, you have to enable proposed.

and i hope this is really 'fixed' this time, the last few times they say it was fixed but not really

---

### Post by aceinthenight on 2009-01-18
Wow, hold on, how does it shorten the life of my laptop?

---

### Post by Cracauer on 2009-01-18
> **aceinthenight said:**
> Wow, hold on, how does it shorten the life of my laptop?

It's just parking and restarting the harddrive at a rate that the harddrive manufacturers don't like.

I seriously doubt this is as hot as people make it.

---

### Post by aceinthenight on 2009-01-18
Hmm... Ive had Ubuntu on my laptop since Dapper... I doubt this bug is serious.

---

### Post by Polygon on 2009-01-18
> **Cracauer said:**
> It's just parking and restarting the harddrive at a rate that the harddrive manufacturers don't like.

I seriously doubt this is as hot as people make it.

it really is a big problem. But the problem really stems from the hard drive manufactures themselfs, rather then ubuntu or any OS, but since they arnt going to fix it, we have to. 

and this can severely shorten the life of your hard drive to like less then a year (in theory)

---

### Post by FuturePilot on 2009-01-18
> **Cracauer said:**
> It's just parking and restarting the harddrive at a rate that the harddrive manufacturers don't like.

I seriously doubt this is as hot as people make it.

No actually it was using the power management settings that the hard drive manufacturers were specifying. The problem is not really with Ubuntu, but with the hard drive manufacturers using power management schemes that are way too aggressive.

---

### Post by OutOfReach on 2009-01-18
> **polygon said:**
> 
and i hope this is really 'fixed' this time, the last few times they say it was fixed but not really

+1

---

### Post by init1 on 2009-01-18
> **jrusso2 said:**
> 
I am wondering why it took so long to fix

There's another bug which is several years old which corrupts FAT32 partitions. I am shocked that they haven't fixed it yet.

---

### Post by chris4585 on 2009-01-18
whats the package in proposed that will fix this issue?  I don't want to update everything in that list... there's a lot of things in 8.10 I purposely downgraded for certain reasons, and rather not have them updated again

> **init1 said:**
> There's another bug which is several years old which corrupts FAT32 partitions. I am shocked that they haven't fixed it yet.

Would this effect my external hdd with fat32?

---

### Post by Cracauer on 2009-01-18
Why wouldn't you just run the drive without timeout stopping?

---

### Post by melojo on 2009-01-18
Isn't the title of this topic a bit misleading?

---

### Post by mcduck on 2009-01-18
> **aceinthenight said:**
> Hmm... Ive had Ubuntu on my laptop since Dapper... I doubt this bug is serious.

And I've been running Ubuntu on my laptop since 5.10.. Seems to be still working. ;)

Reducing the hard drive's lifetime to a year sounds unlikely, reducing it's lifetime *by* a year could be possible. And in that case it's also quite meaningless, as all computer hardware gets seriously outdated years before reaching end of it's lifetime..

Has anybody's laptop actually been reported as broken because of this bug? Years old bug that's supposed to kill laptops but which has never actually done that doesn't sound too serious. :D

---

### Post by xXx 0wn3d xXx on 2009-01-18
If I recall correctly and I have been away from Linux for a while only to return for tinkering, the bug was with laptop-tools. It was never a threat because I believe the service was disabled starting at dapper. The only way it could have caused any sort of damage is if a user enabled it. Besides I really doubt it was a large problem in the first place. It could shorten the life of the drive but I doubt it would kill it within a year. An old laptop has been running Ubuntu since Breezy and it is in excellent shape, works just fine.

---

### Post by jespdj on 2009-01-18
> **jrusso2 said:**
> Not according to slashdot.  They are saying the fix is not in the updates yet.
As far as I know, the bug **is** in the updates, I remember seeing it in the list of updates last week (or even the week before). I'm using 8.04.

---

### Post by mamamia88 on 2009-01-18
excuse me but is this the right fix?  [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)  and then i just install whatever updates show up in update manager?  i don't want to worry about ubuntu killing my harddirve

---

### Post by FuturePilot on 2009-01-18
> **xXx 0wn3d xXx said:**
> If I recall correctly and I have been away from Linux for a while only to return for tinkering, the bug was with laptop-tools. It was never a threat because I believe the service was disabled starting at dapper. The only way it could have caused any sort of damage is if a user enabled it. Besides I really doubt it was a large problem in the first place. It could shorten the life of the drive but I doubt it would kill it within a year. An old laptop has been running Ubuntu since Breezy and it is in excellent shape, works just fine.
That used to be the thinking that it was only a problem if you enabled laptop-mode, but it was later discovered that that wasn't the problem. As I said in my previous post, Ubuntu would use the default power management settings that were specified in the hard drive's firmware. This is the problem since it seems hard drive manufacturers don't know what *good* power management settings are because they were way too aggressive.

> **jespdj said:**
> As far as I know, the bug **is** in the updates, I remember seeing it in the list of updates last week (or even the week before). I'm using 8.04.

> **mamamia88 said:**
> excuse me but is this the right fix?  [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)  and then i just install whatever updates show up in update manager?  i don't want to worry about ubuntu killing my harddirve

Yes, if you have installed all updates you should already have the fix. There should be no need to enable Proposed.

---

### Post by treesurf on 2009-01-18
For what it's worth I do believe this bug killed my last laptop harddrive.  The harddrive died after about one year, and I could constantly hear it parking the heads every minute or so.  

I replaced it with a different brand harddrive which doesn't seem to have the same problem, fortunately.  Or at least it's doing it much more quietly!  

Hopefully this update fixes the problem.

---

### Post by GrouchoMarx on 2009-01-18
Isn't this update already available through the regular repos?

---

### Post by cdekter on 2009-01-18
I can confirm this came through over the last day or so. I believe the package it's in is called acpi-support. However, it does NOT appear to have been fixed properly. While things are fine when I boot my laptop on A/C power, if I use Suspend-To-RAM, when the system wakes up the settings are wrong again and the hard drive destruction starts all over again.

Disappointing. How can it take SO long to fix a simple power management issue. The main reason of course is the spaghetti-like cludge that passes for power management on Linux (seriously, multiple shell scripts, all running at different times and overwriting each others' changes?!)

(Dell Inspiron 1525 here by the way - problem seems to be common to most Dell laptops).

---

### Post by Mr. Picklesworth on 2009-01-19
The media's coverage of this bug misses one really, really important part: It affects **some** computers. Not all.

There is an astounding number of people who think they are affected by this bug but really aren't thanks to the FUD that passes as tech journalism these days.

Not that it isn't a *significant* issue for some people, but the way masses of people react to this whenever it comes up is ridiculous especially when it has been mentioned many times that the issue is deeper than just "fix it" since it involves a (possibly kludgey) workaround. On my end, I have a working laptop that handles hard drive power management just fine and I don't want Ubuntu to implement its own functionality on top. For those people with laptops that don't work very well by default, it's a different story.

And I hope that the people with dead hard drives realize that they tend to come with solid warranties, although the data is definitely gone.

---

### Post by ssam on 2009-01-19
> **init1 said:**
> There's another bug which is several years old which corrupts FAT32 partitions. I am shocked that they haven't fixed it yet.

do you have bug number?

---

### Post by Sealbhach on 2009-01-19
OK, ubuntu_demon has supplied a good explanation of the problem here

[http://www.uluga.ubuntuforums.org/showthread.php?t=805570](http://www.uluga.ubuntuforums.org/showthread.php?t=805570)

as well as a fix called the "ugly fix" (which I use because my hard drive was clicking loudly every 20 seconds or so). 

If you're worried your laptop is still affected by this, run the tests outlined in the thread. 

This is how to do the ugly fix:

[http://www.uluga.ubuntuforums.org/showpost.php?p=5031047&postcount=3](http://www.uluga.ubuntuforums.org/showpost.php?p=5031047&postcount=3)

I reapplied it after I installed 8.10 because my hard-drive was still clicking.

.

---

### Post by TheUnabeefer on 2009-01-19
I read about this bug and took care of it the George W. Bush way:

I preemptively smashed my laptop with a sledge hammer, just in case I may have had the bug.

All fixed now.  :twisted:

---

### Post by jespdj on 2009-01-19
> **GrouchoMarx said:**
> Isn't this update already available through the regular repos?
Yes it is (at least for Hardy); I do not have the 'proposed' repository enabled and I did get the update.

So, no need to enable the 'proposed' repository.

---

### Post by DMcA on 2009-01-19
> **cdekter said:**
> I can confirm this came through over the last day or so. I believe the package it's in is called acpi-support. However, it does NOT appear to have been fixed properly. While things are fine when I boot my laptop on A/C power, if I use Suspend-To-RAM, when the system wakes up the settings are wrong again and the hard drive destruction starts all over again.

Disappointing. How can it take SO long to fix a simple power management issue. The main reason of course is the spaghetti-like cludge that passes for power management on Linux (seriously, multiple shell scripts, all running at different times and overwriting each others' changes?!)

(Dell Inspiron 1525 here by the way - problem seems to be common to most Dell laptops).

Same problem for me. Fix works on startup but stops again after resuming from suspend

---

### Post by gn2 on 2009-01-19
> **melojo said:**
> Isn't the title of this topic a bit misleading?

It sure is.

The bug only affects some hard drives.

---

### Post by plamen_todoroff on 2009-01-23
Should I remove the ugly fix for Hardy that I applied according to ubuntu_daemon's instruction (I applied the Suse fix right after I installed my system)? And should I remove it before or after I do the acpi-support update?

---

### Post by DMcA on 2009-01-23
> Should I remove the ugly fix for Hardy that I applied according to ubuntu_daemon's instruction (I applied the Suse fix right after I installed my system)? And should I remove it before or after I do the acpi-support update?


I'm by no means an expert on this (really, like not at all, don't believe anything I say on the issue), but assuming you get the update it shouldn't matter when you remove the ugly fix. The update is pretty much just a slightly more elegant version of the ugly fix and, assuming you named the ugly fix 99-whatever, the update will get overridden by it anyway. This is my understanding of the issue at any rate

---

### Post by init1 on 2009-01-23
> **chris4585 said:**
> 
Would this effect my external hdd with fat32?
Probably not, only happens when Ubuntu attempts to autofsck a partition (even if the partition is not listed in fstab).

---

### Post by ebe326 on 2009-01-24
After the updates, my Dell laptop is worse than before. For the past year or so I've just disabled hard drive power management using the hdparm command in my rc.local file. It's always worked. Now I'm hearing the clicking again. It's not as often as before but somehow it's overriding my rc.local file. When I hear it I just re-issue the command and the clicking stops. I haven't tried to figure it out yet. I just want to get a solid state drive and be done with it.

david

---

### Post by Paqman on 2009-01-25
> **Polygon said:**
> 
and this can severely shorten the life of your hard drive to like less then a year (in theory)

If that was actually happening, it would be big news on the forums. We've got 8 million Ubuntu users, a lot of them with laptops. The fact that we just don't get actual reports from users to back up these scare stories is telling.

---

### Post by Polygon on 2009-01-25
> **Paqman said:**
> If that was actually happening, it would be big news on the forums. We've got 8 million Ubuntu users, a lot of them with laptops. The fact that we just don't get actual reports from users to back up these scare stories is telling.

hard drives have built in 'monitoring' called SMART. they put values in, such as the number of tmes the drive can safely park/unpark. once the drive goes OVER this number, then thats past teh saftey point and the drive will fail, how long after that is of course debated

a ton of people can go well over that point and their drives work fine. But still, the drive is not meant to be parking/unparking that fast, and the bug that was making the drives do that is bad for the hard drives. it doesn't kill them instantly, but its still a bad thing and it cant be good for the overall health of the  hard drive

---

### Post by GrouchoMarx on 2009-01-31
A word to the wise. The update doesn't necessarily fix the problem. Load_Cycle count is still increasing every 5 seconds on battery power.

---

### Post by butlins on 2009-01-31
Does this dreadful bug encompass kubuntu?

---

### Post by wstout on 2009-01-31
yes KUBUNTU also, but i have been running Ubuntu for years on a laptop and never had any problems.

---

### Post by jongkind on 2009-01-31
> **GrouchoMarx said:**
> A word to the wise. The update doesn't necessarily fix the problem. Load_Cycle count is still increasing every 5 seconds on battery power.

That is right (and on purpose): the update installed "90-hdparm.sh" in /etc/acpi/start.d. A quote of the comment of this file:
"
#
# This script adjusts hard drive APM settings using hdparm. The hardware
# defaults (usually hdparm -B 128 ) cause excessive head load/unload cycles
# on many modern hard drives. We therefore set hdparm -B 254 while on AC
# power. On battery we set hdparm -B 128, because the head parking is
# very useful for shock protection.
#
"
If desired you can tweak the script by changing the following line:
hdparm -B 128 $dev
to
hdparm -B 256 $dev

---

### Post by GrouchoMarx on 2009-01-31
> **jongkind said:**
> That is right (and on purpose): the update installed "90-hdparm.sh" in /etc/acpi/start.d. A quote of the comment of this file:
"
#
# This script adjusts hard drive APM settings using hdparm. The hardware
# defaults (usually hdparm -B 128 ) cause excessive head load/unload cycles
# on many modern hard drives. We therefore set hdparm -B 254 while on AC
# power. On battery we set hdparm -B 128, because the head parking is
# very useful for shock protection.
#
"
If desired you can tweak the script by changing the following line:
hdparm -B 128 $dev
to
hdparm -B 256 $dev

Thanks for this. "hdparm -B 128" is not a sane default on my system (Thinkpad x200, Seagate ST980817AS, Intrepid). The solution I came up with was to enable laptop-mode in /etc/default/acpi-support, and then change "BATT_HD_POWERMGMT=1" to "BATT_HD_POWERMGMT=220". This also properly set the APM setting.

Does anyone know of any reason to disable laptop-mode and go with the /etc/acpi/start.d fix?

---

