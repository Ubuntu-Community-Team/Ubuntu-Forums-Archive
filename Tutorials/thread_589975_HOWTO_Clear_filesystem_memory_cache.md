---
title: "HOWTO: Clear filesystem memory cache"
date: 2007-10-24
forum: Tutorials
---

### Post by jmarler on 2007-10-24
I have read several forum posts where people have asked "How do I clear/free/dump/purge the memory cache?"  A variation of the same answer is almost always given "You don't want to do that ... the Linux Kernel is smarter than you ... Don't try it ... Use dd to create a big file, then delete it ... etc ..."  I never could find an answer that just explained how to do it, so I kept searching elsewhere, and here it is.

**NOTE: This may cause you to lose data, it may make your system slower, it may kill your cat.  Do this at your own risk, and don't be surprised if it doesn't work out the way you wanted it to.**

With the CYA out of the way, here is how to free up as much memory as possible by dumping the cache.  Execute as root, or with sudo:

```
# sync
# echo 3 > /proc/sys/vm/drop_caches
```

That's it.  Not much to see here.  The first command writes any cache data that hasn't been written to the disk out to the disk.  The second command tells the kernel to drop what's cached.  Not much to it.  This invalidates the write cache as well as the read cache, which is why we have the sync command first.  Supposedly, it is possible to have some cached write data never make it to disk, so use it with caution, and ***NEVER*** do it on a production server.  You could ... but why take the risk?

As long as you are running a post 2.6.16 kernel, those commands will work.  I tested it on Feisty and Gutsy, and it worked perfect.

I got this information from [AP Lawrence]("http://aplawrence.com/Linux/buffer_cache.html").

Enjoy!

---

### Post by danbh on 2007-12-02
"This invalidates the write cache as well as the read cache, which is why we have the sync command first."
According to the documentation that you sited, this is not true.  

From the documentation cited in the cited documentation, "this is a non-destructive operation, and dirty objects are not freeable"

So, using the drop_caches command is designed to be safe, and running sync just ensures that ALL the cache is clear.  If you don't run sync, and unwritten data will stay in the cache. 

I hope its clear that I'm just getting this from the websites cited, and I can't personally verify this in anyway.

---

### Post by danbh on 2007-12-02
well, I tried it, nothing seems to have happened really, except now ubuntu is using less ram  :p

I had to ask to get a command that could be run with sudo, so I'm posting it here for reference:
sudo echo 3 | sudo tee /proc/sys/vm/drop_caches

---

### Post by Gen2ly on 2008-02-07
Cool tip.  I had to shutdown X server for it to really be effective.  For GNOME the GNOME display manager will need to be disabled.  I'm using Gentoo and the boot system is different for Ubuntu (Ubuntu uses RC, i believe?) but the xdm daemon needs to be stopped:

```
sudo /etc/init.d/xdm stop
```

ctrl-alt-del.

---

### Post by Copter on 2008-02-08
Hi!

Thanks jmarler. This is exacly what I was looking for :)

copter :]

---

### Post by cika.mancic on 2008-08-18
Thanks!
I have seen the other treads, and find this one very useful!
:)

---

### Post by bzz_ on 2009-08-10
Thank you for this. I need to clear the cached memory due to VBOX hogging cached memory, if I open/close multiple virtual machines, the cache does not clear, and once it hits 100%, when I try and start another my system crashes.

---

### Post by Inifekt on 2009-09-19
Just wanted to add a note to this. I have the system monitor on my panel, with memory enabled, and as soon as I typed the 2nd command the cached meter dropped instantly. Works great. :)

---

### Post by VipX1 on 2010-03-23
Sweet!
Works on Karmic. I use it after shutting down VBox XP machine. I must use *sudo -s* and then type the second command. Using only *sudo *doesn't work.

---

### Post by crazy17 on 2010-05-08
Hi guys! This doesn't seem to work in 10.04. I get ```
bash: /proc/sys/vm/drop_caches: Permission denied
``` I am not well versed in the terminal and have only been using linux for a couple of months now. I am using PAE with 6 gb of ram. Hope you guys can help. Oh, and the system monitor shows full memory cache use.

---

### Post by Anduu on 2010-05-09
> **crazy17 said:**
> Hi guys! This doesn't seem to work in 10.04. I get ```
bash: /proc/sys/vm/drop_caches: Permission denied
``` I am not well versed in the terminal and have only been using linux for a couple of months now. I am using PAE with 6 gb of ram. Hope you guys can help. Oh, and the system monitor shows full memory cache use.

I had the same problem...even sudo wouldn't let me.

This worked however...
```
sudo su
echo 3 > /proc/sys/vm/drop_caches
```

---

### Post by bhavin mehta on 2010-05-13
> **crazy17 said:**
> Hi guys! This doesn't seem to work in 10.04. I get ```
bash: /proc/sys/vm/drop_caches: Permission denied
``` I am not well versed in the terminal and have only been using linux for a couple of months now. I am using PAE with 6 gb of ram. Hope you guys can help. Oh, and the system monitor shows full memory cache use.

sudo su  
sync
echo 3 > /proc/sys/vm/drop_caches

---

### Post by CylnZ on 2010-05-16
Thanks, this worked a treat. :)

---

### Post by darshana on 2010-06-02
don't use [HTML]sudo[/HTML] to run it as root. Log in to the system as root, then this works fine
> sudo sync; echo 3 > /proc/sys/vm/drop_caches
[sudo] password for darshana: 
bash: /proc/sys/vm/drop_caches: Permission denied

---

### Post by petteriIII on 2010-06-02
> **darshana said:**
> don't use [HTML]sudo[/HTML] to run it as root. Log in to the system as root, then this works fine

I hate to 'sudo su' and it's ilk. I use: 
sudo sync; echo 3 | sudo tee /proc/sys/vm/drop_caches

---

### Post by lakosshoots on 2010-06-05
sudo sh -c "sync; echo 3 > /proc/sys/vm/drop_caches"

this worked for me on 10.04. i used the memory system monitor and it went down right away

---

### Post by Maxei on 2010-06-11
I tried these proposed solutions in Lucid lynx. No errors displayed. But the System Monitor showed no changes after, and I am having 37% of used memory and swap history. Is that normal?

---

### Post by Astrals on 2010-06-12
> **lakosshoots said:**
> sudo sh -c "sync; echo 3 > /proc/sys/vm/drop_caches"

this worked for me on 10.04. i used the memory system monitor and it went down right away


This worked great for me, thank you.

I have 8gb 800 corsair (4x2gb)
One of my issues with 10.04.
Fresh reboot and watch a video using the default totem movie player and after about an hour my cache went up to about 68% after an hour.
9.10 did not give me this issue with the same user setup profile.
Also my cache would go up even using firefox.
It seems to me the cache is not being cleared.
If anyone has an answer to why this happens and what the causes are please post it here and also pm me, i always want to understand and learn.
Thank you.

---

### Post by guvnr on 2010-06-14
that's cos ya need to be root ya crazyhorse :P

sudo su root
sync
blah or whatever can't remember but it worked now it's a bash alias, thank you  Sir.

---

### Post by psusi on 2010-06-14
As someone already mentioned, drop_caches is perfectly safe, there is no risk of data loss, however, the ONLY reason to do this is because you are doing performance benchmarking and want to time how long it takes to read something with a cold cache.

> **Astrals said:**
> This worked great for me, thank you.

I have 8gb 800 corsair (4x2gb)
One of my issues with 10.04.
Fresh reboot and watch a video using the default totem movie player and after about an hour my cache went up to about 68% after an hour.
9.10 did not give me this issue with the same user setup profile.
Also my cache would go up even using firefox.
It seems to me the cache is not being cleared.
If anyone has an answer to why this happens and what the causes are please post it here and also pm me, i always want to understand and learn.
Thank you.

That is SUPPOSED to happen.  The cache is not supposed to be cleared.  It is supposed to use all of your free ram to cache data you have accessed in case you need it again.


> **guvnr said:**
> that's cos ya need to be root ya crazyhorse :P

sudo su root
sync
blah or whatever can't remember but it worked now it's a bash alias, thank you  Sir.

Use sudo -s instead of sudo su.

---

### Post by airdao on 2010-08-02
> **crazy17 said:**
> Hi guys! This doesn't seem to work in 10.04. I get ```
bash: /proc/sys/vm/drop_caches: Permission denied
``` I am not well versed in the terminal and have only been using linux for a couple of months now. I am using PAE with 6 gb of ram. Hope you guys can help. Oh, and the system monitor shows full memory cache use.


I have the same issue with the vbox and hogging all of the memory, in 10.04 you need to be root using the SUDOERS privilege is not enough.

sudo su
then try the command to drop the cache
echo 3 > /proc/sys/vm/drop_caches

it worked for me.

---

### Post by phantom.lord on 2010-08-08
**sudo echo 3 | sudo tee /proc/sys/vm/drop_caches**

this works ....

---

### Post by mektek69 on 2010-12-12
Just found this thread and command works great in 10.10 Maverick. Cache usage instantly dropped from 77% to 5% of 2Gb RAM.
Thanks for the tip :D

---

### Post by Dead Angel on 2010-12-20
Thanks for the running as root suggestion!! (Works like a charm!)

Here is a screenshot of my sysmonitor! (It monitors RAM, I have a memory problem, not enough!)

---

### Post by psusi on 2010-12-21
Once again for those who didn't read the whole thread: clearing the cache is not a good thing.  Caching files in memory that otherwise would be empty helps system performance.  As soon as it is needed, it will be reallocated, but until then it may as well be put to good use.

To put it another way, cache memory is, for all intents and purposes, free memory, with a bonus side effect.

---

### Post by sor on 2011-01-24
lol @ people upset that cache refills ;-)

There are actually two things you can clear, and they're both read caches. Write caching is a different thing entirely, and is referred to as 'dirty memory'.  1 is file *data (contents)*, 2 is file *metadata(time, date, permissions, names, etc)*, and 3 is both.  So for example, if you do a 'find /' looking for a file, and then read a 1GB file, and want to evict the 1 GB of data, but not lose the cached 'find' info, you can echo 1.

man /proc and look for drop_caches for the exact details. None of this is Ubuntu specific, by the way.

---

### Post by waffletten on 2011-02-14
I have ubuntu 9.10 server X86 setup with SMB shares as a headless media server in my basement network cabinet.  It has been running 24/7 for about a year (with the exception of a few power outages from storms) and when it has been heavily used (in my case three computers streaming for a couple of hours) I notice that up to %30-47 of the memory will be cached (in this case checking from ssh remotely on network with no streaming occurring 20 minutes after peak activity).  Streaming isn't negatively affected, but I will notice some "hesitation" when logging into the shares from a computer to browse to the file I wish to use after heavy multicomputer use of the shares. A reboot of the server clears the memory usage to normal (3% of 2 GB) and this is how I have dealt with it when it occurs.

Thanks so much to the OP and suggestions of others.  A quick login via ssh, dropping to root and

```
sync; echo 3 > /proc/sys/vm/drop_caches
```has made it much quicker to restore the snappiness of my samba media server without having to restart it remotely

---

### Post by the_jaykay on 2011-02-19
I just wanted to add my 2 cents.

I woke up my laptop which I last night put to sleep and it had around 30% SWAP that's over 1GB.
I have only 2GB of memory. Computer was 'useless' (meaning it felt like the old WinXP - almost there... almost there).

I found Ubuntu clear swap info page and this page. I needed to clear my 1GB cache to fit swap back to ram. So after these two scripts I'm back in business! No restart needed.

I don't know if there is another way to do this. But at the moment I have 40% free memory with no swap. Feels low amount considering I only run FireFox, scribes and gnome-term or whatever.

I would really love to get some real info about memory usage in linux and ubuntu. Modern I mean. Since gwibber alone takes 25MB per each process coming to around 100MB all together !!!

Really! 100MB for MSN :)
UbuntuOne-sync also 30MB and nm-applet 30MB. 
But these are ALL extra programs and I can shut them down if need to so can't complain. They got great usability.

But still would love to understand better about memory usage and need.

---

### Post by psusi on 2011-02-19
> **the_jaykay said:**
> 
I woke up my laptop which I last night put to sleep and it had around 30% SWAP that's over 1GB.
I have only 2GB of memory. Computer was 'useless' (meaning it felt like the old WinXP - almost there... almost there).

Hibernation dumps all ram to swap so that it can be preserved without power.  When you resume, most of it is only brought back to ram on demand, so things are slow while they keep having to wait to be swapped back in.  I've not tried it myself, but I think I read that TuxOnIce fixes this by reading everything back in right away when you resume.

---

### Post by The Unofficial on 2011-03-09
> **crazy17 said:**
> Hi guys! This doesn't seem to work in 10.04. I get ```
bash: /proc/sys/vm/drop_caches: Permission denied
``` I am not well versed in the terminal and have only been using linux for a couple of months now. I am using PAE with 6 gb of ram. Hope you guys can help. Oh, and the system monitor shows full memory cache use.

You must become root by entering

```
# sudo -s
```

Then putting in your password.

Hope this helps
The Unofficial

---

### Post by The Unofficial on 2011-03-09
Oh, and this works on 10.10 Maverick. Went from 77% cache to %5 cache.

---

### Post by psusi on 2011-03-09
> **psusi said:**
> Hibernation dumps all ram to swap so that it can be preserved without power.  When you resume, most of it is only brought back to ram on demand, so things are slow while they keep having to wait to be swapped back in.  I've not tried it myself, but I think I read that TuxOnIce fixes this by reading everything back in right away when you resume.

I have been using the swsusp package lately, which fixes this.  It writes everything out to disk ( and compresses it so it goes faster ), and reads it all ( or at least most, if you aren't using more than 50% of your ram ) back in when you resume.  You even get a little progress indicator during the process.

---

### Post by tg3793 on 2011-05-01
No mater what I do (other than reboot)  my memory starts out at about 30% and gradually creeps up to about 80%+ after a few hours.

I would really think if a reboot does it then a cache somewhere should be clearable (is that a word :-) ) to get it to drop to that magical 30% number.

I'm on Ubuntu 10.04 Lucid and I've tried all of the following:


# sync
# echo 3 > /proc/sys/vm/drop_caches
• This seems to be the most basic one that was written a few years ago in 2007. I got these answers from [http://ubuntuforums.org/showthread.php?t=589975](http://ubuntuforums.org/showthread.php?t=589975) and it seems that the following solutions were fixes that worked on later releases of Ubuntu.

- - - - - - - - - - - - - - - - - - - - - - - - 
sudo -s
echo 3 > /proc/sys/vm/drop_caches
- - - - - - - - - - - - - - - - - - - - - - - - 
sync; echo 3 > /proc/sys/vm/drop_caches
- - - - - - - - - - - - - - - - - - - - - - - - 
sudo sync; echo 3 | sudo tee /proc/sys/vm/drop_caches
- - - - - - - - - - - - - - - - - - - - - - - - 
sudo sh -c "sync; echo 3 > /proc/sys/vm/drop_caches"
- - - - - - - - - - - - - - - - - - - - - - - - 

Thanks in advance for any help :-)

---

### Post by psusi on 2011-05-02
> **tg3793 said:**
> No mater what I do (other than reboot)  my memory starts out at about 30% and gradually creeps up to about 80%+ after a few hours.

Where are you getting that figure?  Look at the output of the free command in a terminal.  Pay attention to the line with +/- cache, not the totals.

---

### Post by tg3793 on 2011-05-04
> **psusi said:**
> Where are you getting that figure?  Look at the output of the free command in a terminal.  Pay attention to the line with +/- cache, not the totals.

Sorry for the late reply. Busy last couple of days.

But yup that's the one. Been using "free -m" and looking that line two columns to the right of the "buffers/cache" spot. ... Maybe I'll just grab a couple more gigs of RAM in a few days; but it still hits me that I should be able to clear anything from the CLI that is clear-able after a reboot.

---

### Post by rg4w on 2011-05-04
> **psusi said:**
> Once again for those who didn't read the whole thread: clearing the cache is not a good thing.  Caching files in memory that otherwise would be empty helps system performance.  As soon as it is needed, it will be reallocated, but until then it may as well be put to good use.

To put it another way, cache memory is, for all intents and purposes, free memory, with a bonus side effect.
Agreed, but in my case I've been doing performance testing on various file I/O routines, and without clearing cache it was impossible to get good measurements other than by rebooting.

This thread has been a godsend for me - thanks to the OP!

---

### Post by vagrale13 on 2011-05-04
[B]@[tg3793]("http://ubuntuforums.org/member.php?u=1135669")
[/B]I think this is not normal, to uses *80% RAM* after some hours!
Maybe you must see why happen this. 
A simple test, is to boot with *livecd* *Ubuntu Lucid 10.04 LTS*, 
and see if this happen from there!
If yes, then test with newer version *Ubuntu Natty 11.04* and see the differences.

---

### Post by tg3793 on 2011-05-05
> **psusi said:**
> Once again for those who didn't read the whole thread: clearing the cache is not a good thing.  Caching files in memory that otherwise would be empty helps system performance.  As soon as it is needed, it will be reallocated, but until then it may as well be put to good use.

To put it another way, cache memory is, for all intents and purposes, free memory, with a bonus side effect.

Yup read it. To which I have to respond ... when it works it works, and when it doesn't work; well, it doesn't work.

There is the theoretical and then there is the actual. I say this as a guy that used to push device drivers and memory resident programs into upper memory before memmaker did it for you in DOS ... Not that it takes that kind of experience to know when it works and when it doesn't; but it helps :-)

---

### Post by psusi on 2011-05-07
> **tg3793 said:**
> Yup read it. To which I have to respond ... when it works it works, and when it doesn't work; well, it doesn't work.

As it is, this statement is a tautology and handwaving.  Can you be more specific?  What doesn't work?  After clearing the cache you are not better off, but worse off than before, because applications do not have access to any more memory than they did before, but file IO will be slowed due to the cache being cold.

> **tg3793 said:**
> There is the theoretical and then there is the actual. I say this as a guy that used to push device drivers and memory resident programs into upper memory before memmaker did it for you in DOS ... Not that it takes that kind of experience to know when it works and when it doesn't; but it helps :-)

So did I.  Good old dos debug ;)

---

### Post by tg3793 on 2011-05-08
> **psusi said:**
> As it is, this statement is a tautology and handwaving.  Can you be more specific?  What doesn't work?  After clearing the cache you are not better off, but worse off than before, because applications do not have access to any more memory than they did before, but file IO will be slowed due to the cache being cold.


To be more specific, programs stop responding, and the GUI freezes up from time to time. I know that the problem is tied to firefox; perhaps a plugin. However if I disable all of the plugins and restart firefox, I don't get 'all' of my memory back. 

In other words, if I start off at 30% of Ram and it creeps up to 80% after a few hours, if I disable all plugins (other than google talk) and restart firefox I might now be at 55%.

I finally made it down to PCExpress and just bought a couple more Gigs of DDR2 800 RAM. We'll see what happens in a few hours. I started out at 20% about two hours ago and now I'm at 28%. Now 'that's' nothing to be concerned about.

I'll keep watching it though. Maybe 10.04 just doesn't like hanging out with less than 4Gigs of RAM :-)

---

### Post by matt_symes on 2011-05-08
Hi

> **tg3793 said:**
> To be more specific, programs stop responding, and the GUI freezes up from time to time. I know that the problem is tied to firefox; perhaps a plugin. However if I disable all of the plugins and restart firefox, I don't get 'all' of my memory back. 

In other words, if I start off at 30% of Ram and it creeps up to 80% after a few hours, if I disable all plugins (other than google talk) and restart firefox I might now be at 55%.

I finally made it down to PCExpress and just bought a couple more Gigs of DDR2 800 RAM. We'll see what happens in a few hours. I started out at 20% about two hours ago and now I'm at 28%. Now 'that's' nothing to be concerned about.

I'll keep watching it though. Maybe 10.04 just doesn't like hanging out with less than 4Gigs of RAM :-)

Maybe you have a memory leak. 

That would be a different issue than the issue highlighted by psusi. I like my caches flaming hot. I would prefer my memory refresh cycles to refresh data that i might need as opposed to refreshing it for data that i definitely won't need as it's not there.

I have 3GB ram on my laptop and 10.04 flies along.

Kind regards

---

### Post by psusi on 2011-05-08
> **tg3793 said:**
> 
In other words, if I start off at 30% of Ram and it creeps up to 80% after a few hours, if I disable all plugins (other than google talk) and restart firefox I might now be at 55%.


As measured how?  If you are counting the cache in that figure, then that is perfectly normal.

---

### Post by tg3793 on 2011-05-09
> **psusi said:**
> As measured how?  If you are counting the cache in that figure, then that is perfectly normal.

I wouldn't disagree that it "creeping up" to 80% or more isn't normal. But it's the not being able to flush it in any way shape or form (other than a reboot) that I wouldn't consider normal. 

And, as I had mentioned before, I'm measuring the memory usage with "free -m".

---

### Post by tg3793 on 2011-05-09
I mostly continuing this thread out of a curiosity to learn at this point. Ever since I added an extra 2Gig memory module I haven't had a problem Nice snappy system with several hours of use going from 20% usage to 53% usage.

Still a problem that I can't "flush the memory" to get back down to the pre-boot 20% usage. But since the system continues to be nice and snappy I have no really need to now :-)

This latest development seems to validate my general statement of "when it works it works, and when it doesn't it doesn't" ... Ok, well that's not very scientific so I'll "frame" it another way. It seems that there is a memory leak in firefox (most likely one of the plugins) that gradually eats up memory even when pushing the upper limit as hight as 95% to 98% memory usage. And when it starts to get that high the system really starts to choke.

I'm using Ubuntu 10.04 and I understand that the memory management 'should' prevent this by pushing some of this to SWAP (how much or when I haven't researched yet).

Now that I've added 2Gig of RAM (total of 4Gig now) I am still having the memory leak issue but the speed of the memory leak has remained stable. This has allowed me to continue operating at a nice snappy speed even at eighteen hours of operation. I'll continue monitoring usage and see if the memory leak grows at this steady rate thereby eating all of the four gig (just taking longer to do so).

Again I don't know if it will eat the additional memory, I'm simply going to continue watching it. I'll report back here later for the edification of anyone interested :-)

---

### Post by matt_symes on 2011-05-09
Hi

@tg3793

This is old but the general principles still apply.

[http://tldp.org/LDP/tlk/mm/memory.html](http://tldp.org/LDP/tlk/mm/memory.html)

BTW: It just works on my machine. Have a look at the kernel source if you want to know how memory management is handled now.

Kind regards

---

### Post by tg3793 on 2011-05-09
> **matt_symes said:**
> 
This is old but the general principles still apply.
[http://tldp.org/LDP/tlk/mm/memory.html](http://tldp.org/LDP/tlk/mm/memory.html)


Thanks; good information.

> **matt_symes said:**
> 
BTW: It just works on my machine. 

:-)

---

### Post by psusi on 2011-05-09
> **tg3793 said:**
> I wouldn't disagree that it "creeping up" to 80% or more isn't normal. But it's the not being able to flush it in any way shape or form (other than a reboot) that I wouldn't consider normal. 

And, as I had mentioned before, I'm measuring the memory usage with "free -m".

But which column?  The +/- cache or not?  If it is not the +/- cache, then you can clear it as this thread describes, but shouldn't because that "used memory" is doing good.  If it is the +/- cache line, then check the system monitor or top to see what program is hogging it all and kill it.

             total       used       free     shared    buffers     cached
Mem:          3939       3537        402          0         60       2035
-/+ buffers/cache:       1441       2497

The 3537 might look like a lot, but since 2035 of it is cache, there is not a problem.  It is the 1441/2497 numbers you want to look at.

---

### Post by Catalyph on 2012-02-22
My NAS server was running very slow and slow transfer speeds over the network was getting 30 - 40 MB/s when i usually get 90+ MB/s when I ssh into the machine it indicated 96.8 % mem usage out of 2GB RAM.

I used the command by logging in as root.

sudo su
sync
echo > 3 /proc/sys/vm/drop_caches

now my system is working as normal and mem usage is back down to only 12%

Thanks!

---

### Post by pooneh2201 on 2012-06-25
> **crazy17 said:**
> Hi guys! This doesn't seem to work in 10.04. I get ```
bash: /proc/sys/vm/drop_caches: Permission denied
``` I am not well versed in the terminal and have only been using linux for a couple of months now. I am using PAE with 6 gb of ram. Hope you guys can help. Oh, and the system monitor shows full memory cache use.

use sudo command at first of the line ,

---

### Post by sayed100100 on 2012-10-06
hello  my frinds  ihave  some  problem Clearing cached memory on Linux system
 
 
ineed script  auto clean 
 
:KS

---

### Post by rubeni on 2013-02-18
hi to all. is my first post so hello to all freinds.

i have dhis problem just on vmware server

i try a lots time but same 

```
root@ns1:~# sudo su
root@ns1:~# echo 3 > /proc/sys/vm/drop_caches
bash: /proc/sys/vm/drop_caches: Permission denied
root@ns1:~# sync
root@ns1:~# sudo su
root@ns1:~# sync
root@ns1:~# echo 3 > /proc/sys/vm/drop_caches
bash: /proc/sys/vm/drop_caches: Permission denied
root@ns1:~# sudo sync; echo 3 | sudo tee /proc/sys/vm/drop_caches
tee: /proc/sys/vm/drop_caches: Permission denied
3
root@ns1:~# echo 3 > /proc/sys/vm/drop_caches
bash: /proc/sys/vm/drop_caches: Permission denied
root@ns1:~# sudo -s
root@ns1:~# echo 3 > /proc/sys/vm/drop_caches
bash: /proc/sys/vm/drop_caches: Permission denied
root@ns1:~# sync; echo 3 > /proc/sys/vm/drop_caches
bash: /proc/sys/vm/drop_caches: Permission denied
root@ns1:~# sudo sync; echo 3 | sudo tee /proc/sys/vm/drop_caches
tee: /proc/sys/vm/drop_caches: Permission denied
3
root@ns1:~# sudo sh -c "sync; echo 3 > /proc/sys/vm/drop_caches"
sh: /proc/sys/vm/drop_caches: Permission denied
root@ns1:~#

```

on real server work fine.

drop_caches iam sure dont work on virtual servers

---

### Post by benerivo on 2013-03-10
> **rubeni said:**
> hi to all. is my first post so hello to all freinds.

i have dhis problem just on vmware server

i try a lots time but same 

[CODE]root@ns1:~# sudo su
root@ns1:~# echo 3 > /proc/sys/vm/drop_caches
bash: /proc/sys/vm/drop_caches: Permission denied
...

I use this command but i get the same error when trying it with sudo. I have to log in as root (which is disabled by default in ubuntu) and then it works fine. This happens to me as a 'sudo' user in other distros as well.

Ben

---

### Post by kevashcraft on 2013-04-30
This command has been so useful!

Use free to see how the memory situation looks, then sudo su, sync, echo 3 > /proc/sys/vm/drop_caches, exit, and I'm home free =)

---

