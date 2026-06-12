---
title: "Does ubuntu damage your hard disk?"
date: 2008-09-13
forum: The Cafe
---

### Post by 7raTEYdCql on 2008-09-13
In our campus there is this rumor that is taking rounds, Ubuntu will damage your hard disk in the long run.

I was shocked when i heard it. Dont know how fat it is true. If this is true then it wasn't got up in the forums? That is the reason why i changed to suse. (Honestly, i want to come back). But i  want to get this settled for sure. Does ubuntu actually damage your hard disk in any repsect?

---

### Post by DrMelon on 2008-09-13
No, this is just a myth. The only damage Ubuntu can do to your hard disk is if you don't read the instructions and partition it wrongly.

---

### Post by Vince4Amy on 2008-09-13
There was a Kernel Problem in 7.04 which would cause some Hard Drives to shut off before parking, though this has been resolved. Also I'm not sure if ext3 would do anything but I use JFS.

---

### Post by 7raTEYdCql on 2008-09-13
I always format in ext3.

---

### Post by ronnielsen1 on 2008-09-13
> Official: Linux doesn't break laptops 
I knew I heard something like this before. Got a coincidence here. Today is 9/13/08 (also my birthday) and the date on the below is
> Thursday 13th September 2007

[http://www.pcpro.co.uk/news/124797/official-linux-doesnt-break-laptops.html](http://www.pcpro.co.uk/news/124797/official-linux-doesnt-break-laptops.html)

---

### Post by Joeb454 on 2008-09-13
I've had no issues with it so far. Running Ubuntu on my laptop since 7.10 when I bought it - now running 8.10

I think there's more disk chatter in XP/Vista than there is Ubuntu

---

### Post by DrMelon on 2008-09-13
Ubuntu is overall, much quieter.

---

### Post by fiddler616 on 2008-09-13
I'm pretty sure this is an urban legend, or else a simple Google would reveal hordes of people whining about what Ubuntu did to their HD.

---

### Post by spiderbatdad on 2008-09-13
Running Ubuntu on this laptop (I have the machine on about 15 hours a day) since Breezy Badger. First installed around June 2005. I have stayed current with releases.

---

### Post by flabdablet on 2008-09-13
It wasn't so much that drives would shut down without parking, as that some drives reacted noisily to being told to [shut down twice in quick succession]("http://article.gmane.org/gmane.linux.ide/17392").  Whether this was actually going to damage anything is anybody's guess.  In any case, it doesn't happen any more.

---

### Post by whazooo on 2008-09-13
I think you maybe thinking of bug #59695 at launchpad
Basicly its about overcycling the hard drive with over optimzation 
of battery settings, You can read about it here:

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

---

### Post by Pom2122 on 2008-09-13
Sorry, totally OT, 

ronnielsen1 Happy Birthday!

---

### Post by AlesUbu123 on 2008-09-13
I think this was related to aggressive power management of laptop hard-drives, which caused the drives head to be parked too often and subsequently causing deterioriation of harddrives (this is not that dramatic, AFAIK, some people estimated that your hard-drive would fail in 6 years if it was always on and suffered from this problem).

You should be worried if you hear loud clicks from your hard drive every few seconds or if the output of this command is showing rapidly increasing number (observe the number at the right side). 
> sudo smartctl -a /dev/hda | grep Load_Cycle_Count
(here, change /dev/hda to /dev/sda or other according name of your harddrive)

---

### Post by Vince4Amy on 2008-09-13
Yeah that's what I was talking about earlier, though this seems to have been long resolved.

Plus it obviously affected more than Ubuntu. There were some other distros at the time which caused the same problem.

---

### Post by Vince4Amy on 2008-09-13
Double Post.

---

### Post by Yannick Le Saint kyncani on 2008-09-13
> **AlesUbu123 said:**
> I think this was related to aggressive power management of laptop hard-drives, which caused the drives head to be parked too often and subsequently causing deterioriation of harddrives (this is not that dramatic, AFAIK, some people estimated that your hard-drive would fail in 6 years if it was always on and suffered from this problem).

You should be worried if you hear loud clicks from your hard drive every few seconds or if the output of this command is showing rapidly increasing number (observe the number at the right side). 

(here, change /dev/hda to /dev/sda or other according name of your harddrive)

Yeah, I had that in gutsy and had to "exec hdparm -B 255 /dev/sda" to prevent the disk from ever parking its heads. Beside a very high count of something I don't care to remember, the constant parking was very annoying anyway.

I've removed the hdparm fix from my boot sequence since I do not have this problem anymore in hardy.

---

### Post by SunnyRabbiera on 2008-09-13
truth is any OS can harm a hard disk if proper means are not taken.
Like using proper partitioning and the like, but aside from that I have seen windows kill hard drives

---

### Post by zmjjmz on 2008-09-13
Yeah, apparently this is old news.

---

### Post by bigbear2350 on 2008-09-13
The kernel 2.6.20 (the one fiesty uses) had problems with disks well my disk anyway it would make a popping sound on a clean shutdown. It didnt happen to me in gutsy +1.

---

### Post by morbid_bean on 2008-09-13
*In my opinion* Putting windows on a hard drive is just a virus itself...but then again...you do anything with the HD it will eventually die

---

### Post by Sealbhach on 2008-09-13
As far as I know, it's NOT been solved.

There is an awkward manual fix for it, but yes, installing Ubuntu can kill some laptop hard drives unless this fix is applied after installation.

See this thread for reference:

[http://ubuntuforums.org/showthread.php?t=591503&highlight=load+cycle+count](http://ubuntuforums.org/showthread.php?t=591503&highlight=load+cycle+count)



.

---

### Post by Polygon on 2008-09-13
the load cycle issue is not fixed in hardy, and im pretty sure not fixed in intrepid. its the reason i have to deal with vista on my laptop.

---

### Post by wolfen69 on 2008-09-13
> **Polygon said:**
> the load cycle issue is not fixed in hardy, and im pretty sure not fixed in intrepid. its the reason i have to deal with vista on my laptop.

what about other distros?

---

### Post by Polygon on 2008-09-13
it is a kernel / hard drive firmware issue, so unless it gets fixed in the kernel, every distro is effected.

---

### Post by bp1509 on 2008-09-14
d

---

### Post by Polygon on 2008-09-14
are you using ubuntu on a laptop? desktop hard drives never spin down (unless its one of those new 'green power' hard drives) so you don't have to worry about the load_cycle_count

---

### Post by fiddledd on 2008-09-14
> **Polygon said:**
> the load cycle issue is not fixed in hardy, and im pretty sure not fixed in intrepid. its the reason i have to deal with vista on my laptop.

I have to agree. In fact I've not used any version of Linux on a Laptop since I found out about the Load Cycle issue. 

And yes, I tested out a number of Distros, and compared the Load Cycle counts to Windows. However only certain makes of HDD seem to be affected, and it doesn't affect Desktops.

I'm actually quite surprised that more people here were not aware of this.

---

### Post by Polygon on 2008-09-14
at least for me in vista, the hard drive doesn't spin down for 3 minutes, and i'm not sure if its counting me being idle (not clicking/doing anything) or if it means the disk is being idle (no read/writes for 3 minutes)

if its the second one, then the hard drive never spins down, as vista is always reading/writing something

---

### Post by Sealbhach on 2008-09-14
Well, I'm using Linux on my laptop. I just did the ugly fix and it's fine.

Just if someone is not aware of the problem, that's where the danger is.


.

---

### Post by bp1509 on 2008-09-14
d

---

### Post by god0fgod on 2008-09-14
Isn't ext3 nicer for the hard disk?

---

### Post by Stefanie on 2008-09-14
I've been using Ubuntu on my laptop (Dell Latitude D510) for some months now and I have no problems at all. I observed the Load_cycle_count for a while and my only conclusion was that it increased much too slowly to damage my hard drive. I know some laptops are affected, but definitely not every one.

This is what the bug report on launchpad says:
> Symptoms of this bug are:
* Frequent HD clicks -- more than one per 3 minutes while idle, louder than the typical access sounds. Often more than twice per minute. On some disks, the click is very quiet
* Rapidly Increasing Load_Cycle_Count as displayed in the final number in "sudo smartctl -a /dev/hda | grep Load_Cycle_Count" (where /dev/hda is replaced with your own hard disk device)
* Early hard disk failure never stay parked, due to very frequent disk activity. Thus this cycle occurs often, thus wearing out the drive, and any comparative benefit is negligible (whereas, if the-- some disks are cut down to less than a year of actual uptime.

The problem is only present due to the existence of *all four* of the following factors:
* Hardware is set (default or otherwise) to aggressive power management, causing heads to park. (default behaviour of many drives and often the only user available type of power management)
* Disk is touched often, causing heads to unpark. (default behaviour of many distributions)
* Drives are spec'd to a limited number of these cycles. (600,000 is the most common, although some may be spec'd higher or lower).
* The OS not setting disk APM variables according to current disk access pattern.

Reasonable Limits / Criteria for a fix:
* There should be fewer than ~15 load cycles per hour, except during heavy usage while on battery.
* This provides a life expectancy of over four years, which is reasonable for a hard disk.



I have about 6 load cycles per hour which is not dangerous at all, and currently I'm only at 47.000 load cycles in total.

---

### Post by bigbear2350 on 2008-09-14
I do not think its a kernel issue with the unload cycle. My grandmas laptops harddrive has about 430k unload count and it is only a 1 year old. It has windows xp on it. So i think it is more to the harddrive you have not what kernel you have.

---

### Post by bigbear2350 on 2008-09-14
> **god0fgod said:**
> Isn't ext3 nicer for the hard disk?

not really, it commits to the journal every 5 seconds i dont know if it does it when idle but i think it does. JFS dosent have a commit interval although i dont know when it does commit its metadata to journal maybe right away. But i wouldnt recommened going to the other filesystems just for the sake of harddrive usage. NTFS commits every 5 seconds also.

---

### Post by jdong on 2008-09-14
I've got a laptop drive here with 1.5 million load cycles and it still works. Ubuntu does nothing to set the idle counter unless you specifically tell it to via an obscure configuration file. Some computers have hardware that specifically default to a low idle timeout. I dont' think Ubuntu should try to be smarter than the hardware it's running on, as there might be hardware configurations that handle these high load cycles properly and that is a desired effect.

Either way, if there's a reason not to use Ubuntu, this certainly isn't it.

---

### Post by gregphil on 2008-09-14
But lets not try to cover up the fact an earlier kernel did have such a bug, and it did in fact cause laptop hard drives to fail prematurely.

Some of the laptop hard drives are life rated in head park cycles as well as total hours powered.  The company I work for found the earlier kernels (in our case is was CentOS 4.4) would cause the type of laptop hard drives we were using, in a fan less mini-server, to fail after 3 or 4 months.   Once we figured this out, and turned of the hard drive power management head parking, the problem went away.  But we had a fair number of servers fail first, and it took a very obscure command line command to turn it off.

I turned out the head parking was happening *very* often, I think every 3 minutes, or something like that, and it would reach the rated head park life limit in about 3 months.  I was sort of surprised how LOW the rated number of hard drive head park cycles allowed actually was (something like 50,000), but under normal conditions (parking a few times a day) the drives would last a life time.

The newer kernels have eliminated this problem.

---

### Post by jdong on 2008-09-14
> **gregphil said:**
> But lets not try to cover up the fact an earlier kernel did have such a bug, and it did in fact cause laptop hard drives to fail prematurely.

Some of the laptop hard drives are life rated in head park cycles as well as total hours powered.  The company I work for found the earlier kernels (in our case is was CentOS 4.4) would cause the type of laptop hard drives we were using, in a fan less mini-server, to fail after 3 or 4 months.   Once we figured this out, and turned of the hard drive power management head parking, the problem went away.  But we had a fair number of servers fail first, and it took a very obscure command line command to turn it off.

I turned out the head parking was happening *very* often, I think every 3 minutes, or something like that, and it would reach the rated head park life limit in about 3 months.  I was sort of surprised how LOW the rated number of hard drive head park cycles allowed actually was (something like 50,000), but under normal conditions (parking a few times a day) the drives would last a life time.

The newer kernels have eliminated this problem.

Can you point to which commits of the kernel have had an effect on disk parking? I was unaware that the kernel messed with this setting at all.

---

### Post by Polygon on 2008-09-14
i still don't believe that this load cycle thing is nothing to be worried about. Im watching it while using xp and it only goes up if i put the computer into suspend or hibernate or just turn it off/on. Something is going on with ubuntu because windows isn't causing the count to go up 150 an hour like ubuntu does, and I personally don't want to have to replace my hard drive prematurely. 

also, the opensuse fix does not work for me. It works sometimes, but then other times it doesn't. The ugly fix works of course, but i do not want to enter a command every time i turn on my computer, sometimes i forget and 'oops! my load cycle has increased 100 counts"

---

### Post by Stan_1936 on 2008-09-14
I have read that the data-mode system of journaling is made available ONLY by ext3.  Apparently this gives the best protection to users (against loss of information) BUT, the hard drive can, as a result, experience a performance hit because the data is written TWICE this way!  Why would this option be selected by default then?  Shouldn't we be given the option to choose this option rather than having it forced down our throats if we are relatively new?

---

### Post by jdong on 2008-09-14
> **Stan_1936 said:**
> I have read that the data-mode system of journaling is made available ONLY by ext3.  Apparently this gives the best protection to users (against loss of information) BUT, the hard drive can, as a result, experience a performance hit because the data is written TWICE this way!  Why would this option be selected by default then?  Shouldn't we be given the option to choose this option rather than having it forced down our throats if we are relatively new?

This is not default. ext3 uses ordered metadata journaling by default, which in terms of disk activity is the same as metadata-only journaling. Data journaling is something that needs to be activated manually in fstab.

---

### Post by Stan_1936 on 2008-09-14
That's right.....my mistake.  I was getting data and meta-data mixed up.  Data journaling is NOT offered by default.  You're correct.

---

### Post by Polygon on 2008-09-14
there is a way around that though, im pretty sure if you do something with a 'relatime' flag, it delays the metadata writes for files until it hits an increment (like a minute or so) then writes all the metadata that its queued up at once, so it doesn't thrash your disk by writing everything twice

---

### Post by jdong on 2008-09-14
> **Polygon said:**
> there is a way around that though, im pretty sure if you do something with a 'relatime' flag, it delays the metadata writes for files until it hits an increment (like a minute or so) then writes all the metadata that its queued up at once, so it doesn't thrash your disk by writing everything twice

relatime only affects atime updates on files, not the other metadata that may be streaming in. 5-second metadata commits are done FOR YOUR SAFETY and every day you run a much higher risk of trashed/lost metadata causing data loss and corruption than load-unload cycles contributing to disk head wear and tear.

---

### Post by nick09 on 2008-09-14
It does not, just ignore the rumors and move on.

---

### Post by Sealbhach on 2008-09-15
> **nick09 said:**
> It does not, just ignore the rumors and move on.


Then what were all those bloody clicking sounds from my hard drive which only went away when I applied the ugly fix?


.

---

### Post by Sealbhach on 2008-09-15
> **Polygon said:**
>  The ugly fix works of course, but i do not want to enter a command every time i turn on my computer, sometimes i forget and 'oops! my load cycle has increased 100 counts"

You make it permanent by doing this:

> 1) revert any previous fixes. remove all 99-hdd-spin-fix.sh files if any. comment the lines you added in /etc/hdparm.conf to fix this issue if any.

2) make a file named "99-hdd-ugly-fix.sh". The important thing is starting with "99".

```
sudo gedit 99-hdd-ugly-fix.sh 
```

make sure the file contains the following lines (fix it if you have PATA HDD):


```
#!/bin/bash
if on_ac_power; then
  # on AC so don't do any head parking
  hdparm -B 254 /dev/sda # you might need 255 or a different value
else
  # either on battery or power status could not be determined
  # so quickly park the head to protect the disk
  hdparm -B 128 /dev/sda
fi
```

4) copy this file to 4 locations:

```
$sudo install 99-hdd-ugly-fix.sh  /etc/acpi/resume.d/
$sudo install 99-hdd-ugly-fix.sh  /etc/acpi/start.d/
$sudo install 99-hdd-ugly-fix.sh  /etc/acpi/ac.d/
$sudo install 99-hdd-ugly-fix.sh /etc/acpi/battery.d/
```

By using install the file 99-hdd-ugly-fix.sh should have the x-bit set.

From: [http://ubuntuforums.org/showthread.php?p=5031046](http://ubuntuforums.org/showthread.php?p=5031046)


.

---

### Post by Polygon on 2008-09-15
i TRIED that but for some reason my hard drive load cycle counts kept spiking randomly. I don't know whats up with it. Anyway, i got fed up with it and just put vista back on my laptop, as ubuntu was causing me hell with the load cycle and touchpad/wireless/hibernate problems as well.

and seal: those clicking sounds are just your hard drive parking and unparking. its normal

---

### Post by 3rdalbum on 2008-09-15
My old Teac 20 gigabyte MP3 player used to click all the time when turned on and also when connected to the computer. Micro HDDs used in MP3 players can't take anywhere near as much punishment as the 2.5 inch HDDs in laptops. My MP3 player is still working fine.

I don't believe there's a problem with disk life on Ubuntu, but unfortunately it's one of those myths that will persist. In the late 1960, NASA found that **one** of their experimental batteries seemed to "remember" what charge level it previously had before being recharged. Forty years later, people **STILL** believe in "the memory effect".

---

### Post by jdong on 2008-09-15
> **3rdalbum said:**
> My old Teac 20 gigabyte MP3 player used to click all the time when turned on and also when connected to the computer. Micro HDDs used in MP3 players can't take anywhere near as much punishment as the 2.5 inch HDDs in laptops. My MP3 player is still working fine.

Yes, portable player HDDs are **supposed to** park the second they become idle. That way if you move around or drop it, the disk head doesn't come grinding down on actual data. In this case it's **safer** for your data to park the disk as soon as it's idle than to have it hovering over data platters for minutes.

---

### Post by ShaunByres on 2008-09-15
I've never had any major problems with Ubuntu on my HDD's and I've been using it for a couple of years now.

The only problem I've had was with a disk partitioning process gone wrong and my linux swap playing up on the side.  I've since then fixed those problems and have had no problems since.

---

### Post by Bucky Ball on 2008-09-15
I advise all to read this. At the end of the day, you can actually extend your hard drive&#347; life.

[http://colorfulcuriosities.blogspot.com/2008/05/ubuntu-hard-drive-cycle-linux-only.html](http://colorfulcuriosities.blogspot.com/2008/05/ubuntu-hard-drive-cycle-linux-only.html)

The load cycle problem is definitely not a rumour and is about aggressive power management more than anything else. Thus is not an issue with desktops, only laptops which do just that, especially on battery power.

---

### Post by Sealbhach on 2008-09-15
> **Polygon said:**
> 
and seal: those clicking sounds are just your hard drive parking and unparking. its normal


Yeah, but about every 20 seconds?  I only hear it now when I shut down.


.

---

### Post by Bucky Ball on 2008-09-15
I get one load cycle a session! I was getting a ridiculous amount before I ran the fix. I did the calculations at the time and my drive theoretically would have been dead in about 8 months from brand new.

---

### Post by uberdonkey5 on 2008-09-15
> **3rdalbum said:**
> ...
I don't believe there's a problem with disk life on Ubuntu, but unfortunately it's one of those myths that will persist. In the late 1960, NASA found that **one** of their experimental batteries seemed to "remember" what charge level it previously had before being recharged. Forty years later, people **STILL** believe in "the memory effect".

I know this is diverting slightly, but battery memory is true, surely? I have experienced the phenomena myself (I believe). I mean, wikipedia talks about it in some detail:

[http://en.wikipedia.org/wiki/Memory_effect](http://en.wikipedia.org/wiki/Memory_effect)

Given that people here HAVE had problems, and the reasons have been given, it does seem there is a problem with Ubuntu (at least earlier versions) on certain computers. Personally I have had it on my lap top (7.04 then 8.04) for 1 year and it works as good as ever. (infact better than ever cos I've penalised windows in my dual boot set up by giving it much less HD space :) )

---

### Post by plb on 2008-09-15
I've been using Linux for the past 10 years and have no hard drive problems..ever.

---

### Post by DMcA on 2008-09-15
Like the others have been saying, there certainly is an issue with some laptops. I believe it is actually I bios issue that Ubuntu does not provide a work-around for (windows does). This still affects me with Gutsy and I believe it has not yet been solved in later versions. Although it is not technically an ubuntu problem I believe that it is absolutely critical that something is done about this as soon as possible since many people simply don't know about it and so cannot implement the manual hack.

---

### Post by Polygon on 2008-09-15
> **Sealbhach said:**
> Yeah, but about every 20 seconds?  I only hear it now when I shut down.


.

yeah, thats the ubuntu (or linux in general) over aggressive power management at work, it parks the drive when its idle for like 3 seconds, but then something needs to use the disk and then it unparks and reads....waits three seconds, then parks....repeats

and each of these parks counts as one load cycle, which is the problem which is still going on.

---

### Post by OldDirtyTurtle on 2008-09-15
OK,  I'm now simultaneously confused and paranoid.  I'm ordering a laptop soon and going Ubuntu (I'm a complete newbie).

Is this a concern with Hardy overall, isolated/specific laptop HDD's, or even more isolated individual setups?

I'm waaaay too green to be doing serious fixes.

---

### Post by Sealbhach on 2008-09-15
> **OldDirtyTurtle said:**
> 
Is this a concern with Hardy overall, isolated/specific laptop HDD's, or even more isolated individual setups?

I'm waaaay too green to be doing serious fixes.

It affects some laptops. There's a list of the known ones here:

[http://ubuntuforums.org/showthread.php?t=795327](http://ubuntuforums.org/showthread.php?t=795327)


.

---

### Post by OldDirtyTurtle on 2008-09-15
Oops.  I guess a quick search could've answered my question.  Thanks for the pointer to the list.

---

### Post by gjoellee on 2008-09-15
If you want to damage your HDD you have to use a hammer ;-)

---

### Post by Stan_1936 on 2008-09-15
> **Bucky Ball said:**
> ...**The load cycle problem is** definitely not a rumour and is about aggressive power management more than anything else. Thus is not an issue with desktops, **only laptops** which do just that, especially on battery power.

**Whew!  That was a close one!**

---

### Post by billgoldberg on 2008-09-15
Yes, I have to buy a new one (hdd) every two weeks. But that I happily pay that price to get to use the best OS in the world.

---

### Post by billgoldberg on 2008-09-15
> **OldDirtyTurtle said:**
> OK,  I'm now simultaneously confused and paranoid.  I'm ordering a laptop soon and going Ubuntu (I'm a complete newbie).

Is this a concern with Hardy overall, isolated/specific laptop HDD's, or even more isolated individual setups?

I'm waaaay too green to be doing serious fixes.

Don't worry about it. You'll be fine.

---

### Post by phrostbyte on 2008-09-15
> **Yannick Le Saint kyncani said:**
> Yeah, I had that in gutsy and had to "exec hdparm -B 255 /dev/sda" to prevent the disk from ever parking its heads. Beside a very high count of something I don't care to remember, the constant parking was very annoying anyway.

I've removed the hdparm fix from my boot sequence since I do not have this problem anymore in hardy.

Wouldn't that be dangerous in it's own right? I've lost laptop HDDs drives before and it's always because of moving the laptop while there is a complex I/O. I mean it might be safer to just let it park when it's not in use.

---

### Post by medic2000 on 2008-09-15
> **i.mehrzad said:**
> In our campus there is this rumor that is taking rounds, Ubuntu will damage your hard disk in the long run.

I was shocked when i heard it. Dont know how fat it is true. If this is true then it wasn't got up in the forums? That is the reason why i changed to suse. (Honestly, i want to come back). But i  want to get this settled for sure. Does ubuntu actually damage your hard disk in any repsect?

Yeah,yeah,yeah... And did you know Windoze rapes your graphics card?

---

### Post by Bucky Ball on 2008-09-16
[quote=i.mehrzad]If this is true then it wasn't got up in the forums?[/quote]

[http://ubuntuforums.org/search.php?searchid=48091911](http://ubuntuforums.org/search.php?searchid=48091911)

Um, yes it was.

Once again:

Load cycle count = aggressive power management, specifically laptops, not desktops. Drive will park every three or so seconds without running the fix then when you do something, drive unparks = 1 load cycle. Average 2.5" hard drive lifespan = 600, 000 load cycles. Do the math and make your decision whether to run the fix or not.

Finally, running the fix can actually increase the life of your drive (not load cycle count - lifetime) as you are slashing the count drastically. If you decide to run the fix, here it is:

[http://colorfulcuriosities.blogspot.com/2008/05/ubuntu-hard-drive-cycle-linux-only.html](http://colorfulcuriosities.blogspot.com/2008/05/ubuntu-hard-drive-cycle-linux-only.html)

For info on machines and drives affected:

[http://ubuntuforums.org/showthread.php?t=795327](http://ubuntuforums.org/showthread.php?t=795327)

You will be stunned when you load smartmonitortools, use your lappy for and hour (or 5 minutes), then check how many load cycles your drive has performed. bobnutfield, run the fix man because that is probably your problem. Because ...

To everyone: Don't just save your pocket, think about resources and the environment! Most computer equipment is really not friendly in the manufacture and creates nasty c**p. Go RoHS standard and power efficient (something I say often but most computer users don't seem to give a toss - hardware falls off trees and blends back into the environment when you're done, obviously!). These standards exist for a reason and eventually you will have no choice anyway. The technology is there, use it. You will be doing yourself and all of us a favour (and saving money - if nothing else seals the deal that usually does!).

:)

---

### Post by Matymoo on 2008-10-11
I asked the opposite of this question on another forum website, (overclockers.com.au). "Does Windows wear out your hard drive faster than Linux or Mac OS X". 

I was, without warning, and subsequently, without any explanation, (despite several requests), banned from their forums indefinitely!

My reason for asking the question? I regularly test different operating systems on my desktop PC (AMD 64 Athlon, 3200+, 1G Ram, PLENTY of HDD space allocated to each O/S). I have run every distro of ubuntu from 6.04 to present (8.10b), PCLinuxOS, OpenSUSE, XP32, XP64, Vista32, OS X Leopard. 

When running XP and to a greater extent, Vista, my hard drive works HARD. Constant HDD light activity, constant HDD noise. In Linux and OS X, I barely even notice a sound from the hard disk!

Does ubuntu damage your hard disk? From my experience, not at all.
Does Windows damage your hard disk? From my experience, I honestly believe that windows would seriously shorten the life of your hard disk.

Can't understand why my above observations had me indefinitely banned from overclockers. :confused:

---

### Post by RATM_Owns on 2008-10-11
Yes. It almost destroys the hard disk.

BSD, Lunix, Debian and Mandrake__ are all versions of an illegal hacker operating system__[]("http://www.lunix.com/"), invented by a Soviet computer hacker named Linyos Torovoltos, before the Russians lost the Cold War. It is based on a program called "xenix" , which was written by Microsoft for the US Government. These programs are used by hackers to break into other people's computer systems to steal credit card numbers. They may also be used to break into people's stereos to steal their music, using the "mp3" program. Torovoltos is a notorious hacker, responsible for writing many hacker programs, such as "telnet", which is used by hackers to connect to machines on the internet without using a telephone.

[/Hilarious Fakeness]

---

### Post by azangru on 2008-10-11
Erm, take a look at [[COLOR="Blue"]this ubuntu brainstorm entry[/COLOR]]("http://brainstorm.ubuntu.com/idea/288/"). Apparently, the hard drive wearying bug was fixed just a couple of days ago, and the fix is going to be included in Intrepid.

I can hardly believe my eyes!

---

### Post by bigbear2350 on 2008-10-11
Its proably ext3.

Every 5 seconds it writes to the journal.

---

### Post by Sealbhach on 2008-10-11
> **Matymoo said:**
> 
Does ubuntu damage your hard disk? From my experience, not at all.
Does Windows damage your hard disk? From my experience, I honestly believe that windows would seriously shorten the life of your hard disk.


This discussion refers to a particular problem on some laptops due to the Agressive Power Management which causes the disk heads to park very frequently. This will kill the hard drive in these cases unless the "ugly fix" is applied.

[Ugly Fix]("http://ubuntudemon.wordpress.com/2007/10/26/laptop-hardrive-killer-bug/#comment-31234")

It's not caused by Ubuntu but needs to be fixed. The upcoming intrepid release has a fix for it.

I think it's very important that anyone using Ubuntu on a laptop is aware of it.



.

---

