---
title: "a cleaner OS"
date: 2015-01-22
forum: Ubuntu, Linux and OS Chat
---

### Post by aliak-93 on 2015-01-22
hello everybody!
we all know windows gets dirtier and slower the more time passes as you use it. so I switched to ubuntu. I'm a newbie and I still wonder, is Ubuntu made to mantain itself clean? is ti simple not to get it filled with junk files? and useless, uncountable, processes that start everytime I turn on my computer slowing it down?

---

### Post by pfeiffep on 2015-01-22
I found that on my first Ubuntu install on a 32 bit Old Dell laptop (not the one in my signature) I had to keep my small hard drive 'cleaned up'. 
I tired of the tedious manual operations and installed [BleachBit]("https://apps.ubuntu.com/cat/applications/precise/bleachbit/") which is available in the software center. 
Please be careful because being overly agressive with this software might cripple your system.
[On Line Manual]("http://bleachbit.sourceforge.net/documentation")

---

### Post by aliak-93 on 2015-01-22
I'm still getting accustomed with ubuntu, but it behaves really well for now. Is it really so easy to cripple my system? Or Have I simply to pay attention to what I do, given the large range of possibilities it has?

---

### Post by PondPuppy on 2015-01-22
I believe that when Ubuntu updates the Linux kernel it saves the old version as well. These should probably be cleared out now and then. 

Disk fragmentation is not much of a problem with Linux. To understand why, here's on of many explanations: [http://www.howtogeek.com/115229/htg-explains-why-linux-doesnt-need-defragmenting/](http://www.howtogeek.com/115229/htg-explains-why-linux-doesnt-need-defragmenting/)

Yes, you can bork a Linux installation. I screwed up a server install while trying to disable certain power-off functions. (This was ignorance.) Seems I can't learn without making mistakes... call them "cognitive incentives"! Look at it this way: with power comes responsibility. Always wise to keep a backup of your music, photos, any other data.

I think probably OSX is the most secure from user tampering, and Linux the least. Windows is, I think, in between. (I'm not talking about security from external attacks. In that regard, I think Linux is usually quite secure, and can easily be made very secure indeed.)

---

### Post by mörgæs on 2015-01-22
The commands 

```
sudo apt-get update
sudo apt-get dist-upgrade
<maybe reboot>
sudo apt-get autoremove
```

are easy, safe and efficient in keeping a hard disk clean.

---

### Post by deadflowr on 2015-01-22
> **aliak-93 said:**
> I'm still getting accustomed with ubuntu, but it behaves really well for now. Is it really so easy to cripple my system? Or Have I simply to pay attention to what I do, given the large range of possibilities it has?

Well, if you decide not to pay attention to what you are doing, then the odds of crippling your system are greater.
It doesn't take a lot of your attention to keep it from falling a part.
But you do need to put some thought into what you do.

I would think that this would be rudimentary across all devices...

---

### Post by aliak-93 on 2015-01-22
I like this Os! It makes you use your mind! About those codes, what do they do?

---

### Post by deadflowr on 2015-01-22
If I may
the first command: apt-get update, updates the list of available packages for your system

the second command: apt-get dist-upgrade, uses the list of packages found after using the first command and actually installs the newest updates for whatever packages you have installed.
(It only updates those packages for the release(ie, 12.04, or 14.04, or 14.10), or which ever release of Ubuntu you are running;
 so do not worry that running it will change the system from one release to another; a common misconception)

the third command( skipping the reboot line) apt-get autoremove helps find and remove any packages that are no longer needed on the system.
Sort of like a quick cleaning tool.

Hope that helps.

---

### Post by mörgæs on 2015-01-22
Yes, please. Good explanation.

---

### Post by oldrocker99 on 2015-01-22
One thing to remember, since borking one's system was mentioned:

***[SIZE=4]The Linux shell assumes that you know exactly what you're doing.[/SIZE]***

---

### Post by ian-weisser on 2015-01-22
> **aliak-93 said:**
> is ti simple not to get it filled with junk files?
If you discover any application creating junk files, please file a bug report. Applications are expected to clean up after themselves.

> **aliak-93 said:**
>  and useless, uncountable, processes that start everytime I turn on my computer slowing it down?
Well, a process might seem 'useless' to you until you kill it...and then discover that your printing or networking or display was actually using it after all.
My desktop install might run up to 200 processes, 90% of which use almost no memory and 99% of which are sleeping.
Some of the processes are kernel threads. You cannot change those easily.
Others are services provided by the OS, and listed in /etc/init and /etc/init.d. You can start and stop most of those easily.
There are easy ways to turn off unused services (if you know what they are).

As an experiment, I turned off a *lot* of services about a year ago...and it made no difference to the responsiveness of my system.

---

### Post by mikodo on 2015-01-22
> **ian-weisser said:**
> Well, a process might seem 'useless' to you until you kill it...and then discover that your printing or networking or display was actually using it after all. Yep, I don't know what I am doing, and I tried shutting off a bunch of processes in a distro I was trying for a day, and broke it, (irreparable for me). No biggie though. It was to be gone that day any ways.

---

### Post by Irihapeti on 2015-01-22
I have an EeePC 900 with only 4GB for the OS, so I need to keep a close eye on how much free space is available.

All I've ever done are the commands that mörgæs listed, plus:

```
sudo apt-get clean
```

which removes all the downloaded .deb packages (they aren't needed after installation),

manually removing the previous kernel version,

and, of course, removing any programs that I've installed and decided I no longer need.

I've been following this routine for a few years now, and I've never had the need to use BleachBit or any other cleanup routine.

---

### Post by aliak-93 on 2015-01-30
Thank you! You really got my ideas clearer.

---

### Post by katabatic2 on 2015-01-31
I don't think Ubuntu will have much difference in this regard. However, low ram and a slow hard drive will slow you down a lot. Regular hard disc drives are slow at accessing lots of little files and configs, which as you mention, can build up on an older system, whereas SSD drives are very fast, which you can buy now.

---

