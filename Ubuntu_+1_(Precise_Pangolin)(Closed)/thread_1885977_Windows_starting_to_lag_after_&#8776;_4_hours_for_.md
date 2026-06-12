---
title: "Windows starting to lag after &#8776; 4 hours for you?"
date: 2011-11-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-11-24
For the last three days I am seeing that, after about 4 hours, if I try to move some particular apps on screen/between viewports, etc, they go slowly and I can see the redrawn process. The typical examples are Gedit, Terminal and Firefox, Chrome. I usually  have them opened all day, sometimes for a couple days when I don't turn  off the PC. 

The obvious line of thought would be that there's a leak in some lib they share, but I can't see change in system load: There more than 10GB of free RAM, CPU Cores are in less than 10% load, Nvidia GPU is running cold on adaptive mode, with almost 1GB free. Top, htop, etc show no signs of the system being under stress and the lagging apps are using normal memory/cpu amounts.

Closing and reopening the lagging apps makes them fast again.

Downgrading nvidia from 290.10 to up to 4 previous versions hasn't fixed it. Weird thing: It doesn't affect all apps. Eclipse, for example, continues to behave normally, no matter the number of hours.

There's nothing interesting in logs. I ran compiz from the terminal to have a look at compiz/unity warn./errors but nothing abnormal is shown.

I'm puzzled. Anyone else seeing this or knows of a workaround?

**EDIT: **

Software Versions:
Linux AL-DESK 3.1.0-2-generic #3-Ubuntu SMP Sat Oct 29 00:48:30 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux (not customized)
Unity 4.24.0
Compiz 0.9.6

Another indicators: 
CPU's are cold, less than 40ºC, with cooler running on silent mode.
I'm not swapping (swapoff), SSD/HDD are operating normally (r/w speed and s.m.a.r.t info)

---

### Post by PaulW2U on 2011-11-24
I have seen something like that with a couple of applications and they are noticeably faster the next time I use them, gvim with the cream add-on is one of them.

I don't know if this is related in anyway but if I have a lot of applications open I have trouble closing one of them, it's like it doesn't want to close. When it does, I lose Unity's default theme.

---

### Post by effenberg0x0 on 2011-11-24
> **PaulW2U said:**
> I have seen something like that with a couple of applications and they are noticeably faster the next time I use them, gvim with the cream add-on is one of them.

I don't know if this is related in anyway but if I have a lot of applications open I have trouble closing one of them, it's like it doesn't want to close. When it does, I lose Unity's default theme.

Do you see the app using too much cpu/ram resources (more than normal)  on top/htop/system Monitor? I see nothing unusual with my lagging ones, which is odd.

EDI: And I see you're on ATI, so I probably can't blame it on nvidia.

---

### Post by PaulW2U on 2011-11-24
> **effenberg0x0 said:**
> Do you see the app using too much cpu/ram resources (more than normal)  on top/htop/system Monitor? I see nothing unusual with my lagging ones, which is odd.

I haven't noticed anything so far.

I'm using Kubuntu at the moment where I haven't come across any such problem. The next time I boot into Ubuntu I think I need to be running Gnome Shell as I want to become more familiar with it. I'm pretty sure that that was what I was using when I first came across the problem of not being able to close an application.

---

### Post by MacUntu on 2011-11-24
AFAIK a known Compiz issue (and IIRC already resolved or at least worked on, just not uploaded).

---

### Post by VinDSL on 2011-11-27
> **effenberg0x0 said:**
> I'm puzzled. Anyone else seeing this or knows of a workaround?
Hrm...  Yes n' no.

I started a thread, a week or so ago, about this machine lagging out on me.

I seemed to be the only person in the threads having this problem.

I'll see if I can find it, and refresh my memory...

Okay, here's one:  [http://ubuntuforums.org/showthread.php?t=1866882](http://ubuntuforums.org/showthread.php?t=1866882)

Turned out to be a kernel problem.  But, that's not the one I was thinking about...

Here it is:  [http://ubuntuforums.org/showthread.php?t=1878658](http://ubuntuforums.org/showthread.php?t=1878658)

And, the upshot:

> **VinDSL said:**
> Hrm...

I thought I'd better do an update.  This thread pops up high in Google Search results. ;)

I started playing around with kernel updates, last night, and nVidia 290.06.

Eventually, I succeeded in borking my UbuPP install.  LoL!  :D

After I put Humpty Dumpty back together again, I settled on:

Linux 3.1.0-2-generic, and nVidia-common & nVidia-settings 285.05.09

```
vindsl@Zuul:~$ dpkg-query -l | grep 3.1.0-2
ii  linux-headers-3.1.0-2                  3.1.0-2.3                               Header files related to Linux kernel version 3.1.0
ii  linux-headers-3.1.0-2-generic          3.1.0-2.3                               Linux kernel headers for version 3.1.0 on x86/x86_64
ii  linux-image-3.1.0-2-generic            3.1.0-2.3                               Linux kernel image for version 3.1.0 on x86/x86_64

vindsl@Zuul:~$ dpkg-query -l | grep nvidia
ii  nvidia-common                          1:0.2.36                                Find obsolete NVIDIA drivers
ii  nvidia-current                         285.05.09-0ubuntu1                      NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                        285.05.09-0ubuntu1                      Tool of configuring the NVIDIA graphics driver
vindsl@Zuul:~$ 
```

Everything is working great now!  Go figure...  ;)

Heh!  Now, I remember.

I totally borked my install, trying to get rid of the lagginess.

I can't tell you all the things I tried, or the sequence, but it was one of those 2-hour sessions in Recovery Mode - frantically doing a wash, rinse and restyle.

Eventually, I got it to boot into Unity, and everything has been fine ever since.

Sorry I can't be of more help.  Basically, I took a meat cleaver to this thing, from CLI.  I was about ready to do a fresh install, when all of a sudden it started working.

That said, I'm running Linux 3.1.0-2.3-generic, and nVidia 285.05.09-0ubuntu1, and haven't suffered any lagginess since that last occurence.

Actually, it's running great great!  Been on here for 8 hours, as I type, doing a lot of heavy-duty programming, with multiple windows open, on multiple desktops, blah, blah, blah.

**Edit**

You know... I was just sitting here thinking back...

I remember, once I got Unity to boot, it was still acting janky!

It turned out that the 290.06 nvidia-current-updates binary had somehow survived all my attempts at purging it.

Once I got rid of it, 285.05.09 started working great!

Just a thought...  ;)

---

### Post by Derek Karpinski on 2011-11-28
It's trying to tell us that 4 hours behind a computer screen.........after spending 8 hours at work behind a computer is just way too much.  Ubuntu wants us to get some fresh air.

---

### Post by effenberg0x0 on 2011-11-28
> **VinDSL said:**
> Hrm...  Yes n' no.

I started a thread, a week or so ago, about this machine lagging out on me.

I seemed to be the only person in the threads having this problem.

I'll see if I can find it, and refresh my memory...

Okay, here's one:  [http://ubuntuforums.org/showthread.php?t=1866882](http://ubuntuforums.org/showthread.php?t=1866882)

Turned out to be a kernel problem.  But, that's not the one I was thinking about...

Here it is:  [http://ubuntuforums.org/showthread.php?t=1878658](http://ubuntuforums.org/showthread.php?t=1878658)

And, the upshot:



Heh!  Now, I remember.

I totally borked my install, trying to get rid of the lagginess.

I can't tell you all the things I tried, or the sequence, but it was one of those 2-hour sessions in Recovery Mode - frantically doing a wash, rinse and restyle.

Eventually, I got it to boot into Unity, and everything has been fine ever since.

Sorry I can't be of more help.  Basically, I took a meat cleaver to this thing, from CLI.  I was about ready to do a fresh install, when all of a sudden it started working.

That said, I'm running Linux 3.1.0-2.3-generic, and nVidia 285.05.09-0ubuntu1, and haven't suffered any lagginess since that last occurence.

Actually, it's running great great!  Been on here for 8 hours, as I type, doing a lot of heavy-duty programming, with multiple windows open, on multiple desktops, blah, blah, blah.

**Edit**

You know... I was just sitting here thinking back...

I remember, once I got Unity to boot, it was still acting janky!

It turned out that the 290.06 nvidia-current-updates binary had somehow survived all my attempts at purging it.

Once I got rid of it, 285.05.09 started working great!

Just a thought...  ;)


There was definitely something wrong with 290.10 + previous kernel. As soon as I installed 290.10 and kernel 3.2.0-2 I could feel a sensible change in gui performance. The lagging is gone and video seems to be updating faster.

---

