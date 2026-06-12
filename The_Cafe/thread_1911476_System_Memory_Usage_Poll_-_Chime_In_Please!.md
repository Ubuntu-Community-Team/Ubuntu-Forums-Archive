---
title: "System Memory Usage Poll - Chime In Please!"
date: 2012-01-18
forum: The Cafe
---

### Post by w201 on 2012-01-18
I'd like to do a quick poll if anyone cares to chime in. Just as a curiosity, I'm wondering how many megabytes of memory your system uses.

As an example, if I open up system monitor, my system is currently using 715 MiB (35%) of 2 GiB of memory.

Obviously ubuntu is resource heavy, which makes it a little slow on older machines. I'm just trying to get an idea if 700+- MiB of memory is standard across the board. What are you guys showing?

***Note*** For this comparison, I'm running ubuntu 11.10, firefox and system monitor were the only processes running and another 146 sleeping at the time I took the measurement. 

Peace!

---

### Post by carl4926 on 2012-01-18
My R61[URL="http://paste.opensuse.org/82301067/"]
[/URL]

---

### Post by QIII on 2012-01-18
Ubuntu is resource heavy?  Mmmmm.  Don't know about that, depending on what you are comparing it to.  Might be with a particular DE.  Are you comparing it to a minimal install of something?

1.2GiB of 24GiB on this machine.

I have a Bodhi (Ubuntu derivative) machine using 54MiB of 256Mib right now with the E17 DE running.

So yeah.  Pretty heavy compared to that!

---

### Post by w201 on 2012-01-18
> **carl4926 said:**
> [URL="http://paste.opensuse.org/82301067/"]http://paste.opensuse.org/82301067
[/URL]

Whatever you're trying to show me, that site is on strike because of SOPA and PIPA. I'll check again after midnight.

---

### Post by w201 on 2012-01-18
> **QIII said:**
> Ubuntu is resource heavy?  Mmmmm.  Don't know about that, depending on what you are comparing it to.  Might be with a particular DE.  Are you comparing it to a minimal install of something?

1.2GiB of 24GiB on this machine.

I have a Bodhi (Ubuntu derivative) machine using 54MiB of 256Mib right now with the E17 DE running.

I'm comparing it to debian which uses about 80 MiB of 2 GiB. So 700 MiB of memory for ubuntu is normal? I've always thought it was a little heavy on the resources. But I guess compared to debian its not a fair fight.

---

### Post by carl4926 on 2012-01-19
Remember 'top' can enlighten

```
top - 05:04:10 up 7 days, 23:44,  3 users,  load average: 0.04, 0.05, 0.26
Tasks: 148 total,   2 running, 146 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.0%us,  4.3%sy,  0.0%ni, 85.7%id,  4.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3063328k total,  1692860k used,  1370468k free,   100144k buffers
Swap:  2465940k total,    17240k used,  2448700k free,  1015128k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                
  865 root      20   0  124m  31m 6656 R  3.7  1.1  50:47.79 Xorg                                   
28522 kernelcr  20   0  124m  23m  15m S  2.3  0.8   0:00.77 konsole                                
 1690 kernelcr  20   0  300m  59m  30m S  0.7  2.0  10:57.27 plasma-desktop                         
26951 kernelcr  20   0  614m 174m  35m S  0.3  5.8   5:02.35 firefox-bin                            
    1 root      20   0  5136 2964 1512 S  0.0  0.1   0:01.48 systemd                                
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.04 kthreadd                               
    3 root      20   0     0    0    0 S  0.0  0.0   0:00.27 ksoftirqd/0                            
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                            
    7 root      -2  19     0    0    0 S  0.0  0.0   0:14.34 rcuc0                                  
    8 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 rcun0  
```

---

### Post by QIII on 2012-01-19
What DE are you using in each?  What's running?

I'm using KDE on this box, which is certainly heavier than E17.  It's also more feature rich.

Fired up a CentOS 6.2 box.  0.57GiB of 4GiB.

I guess what I am saying is that without some common controls, a comparison like this is of little value.

Unless you have your Debian box running the same DE and the same stuff in the background, the comparison is essentially meaningless.

Is Debian lighter out of the box than Ubuntu with Unity?  Certainly.

Both CentOS 6.2 and Bodhi are lighter than my KDE box by just raw memory used at idle after startup, too.

---

### Post by davethewave83 on 2012-01-19
I will agree, Ubuntu is resource heavy, but all OS are today. Not too long ago, about 12 years that is, I owned an Apple Macintosh (LC-575) it ran on 8Mb of RAM, still was able to launch SimCity 2000 and run SimpleText in the background. 8Mb! It had sound, color video and didn't lag out a bit. 
I did end up upgrading to 16Mb, and boy it made a big difference. 

Programmers these days program differently I guess, it's all OOP (Object Oriented Programming) which takes a lot more resources than if they were to program in Assembler. 

I tried to find the leanest desktop environment that was still enjoyable, but no matter what I did, I couldn't get it below 100Mb. 

100Mb, my old Apple Mac hard drive was a 250Mb SCSI drive, 100Mb Ram is, relatively insane. 

Sure the computers are faster these days, but imagine how fast it'd be if it were still programmed to run on 8-16Mb RAM using the technology of today. 

Anyways, right now I'm running firefox, Skype, truecrypt, terminal and have a bunch of windows open so this won't be a very fair or accurate reading but I've got 794.4MB consumed in Ubuntu Lucid Lynx (10.04) running Gnome 2

that wouldn't even fit on an old trusty CD, I wish someone would do something about the excessive memory usage used by software these days

Fresh Boot Edit: 350Mb fresh boot.

---

### Post by w201 on 2012-01-19
> **QIII said:**
> What DE are you using in each?  What's running?

I'm using KDE on this box, with is certainly heavier than E17.  It's also more feature rich.

Fired up a CentOS 6.2 box.  0.57GiB of 4GiB.

I guess what I am saying is that without some common controls, a comparison like this is of little value.

Unless you have your Debian box running the same DE and the same stuff in the background, the comparison is essentially meaningless.

Yea I guess I get what you're saying about the comparisons. Just to clarify, i'm not trying to compare debian to ubuntu, I'm trying to compare ubuntu on my box to other users that are also running ubuntu 11.10. I know different people will be running different processes, but just trying to get a general idea. 

On this box I'm running ubuntu 11.10. 700Mib of 2Gib. There's stuff running in the background. Firefox is the only major process I had running at the time I took the measurement. 

Running debian xfce on a separate box and it's lighting fast compared to ubuntu. Both systems are set up with the same hardware.

@carl4926- I'm glad you pointed out TOP. Do you know what zombie means? I've always wondered about that.

---

### Post by QIII on 2012-01-19
I would expect Xfce to be a lot lighter.  E17 even beats that.

By the way, weighing in at 0.750GiB at startup, at idle and with nothing running is openSUSE with KDE.  

This is the joy of Linux.  A la carte menu.  You can have a salad or a burger.

---

### Post by w201 on 2012-01-19
> **QIII said:**
> I would expect Xfce to be a lot lighter.  E17 even beats that.

By the way, weighing in at 0.750GiB at startup, at idle and with nothing running is openSUSE with KDE.  

This is the joy of Linux.  A la carte menu.  You can have a salad or a burger.

I haven't heard of E17- will look into that.

Did you read my earlier comment about zombie? Can you explain what it is?

---

### Post by QIII on 2012-01-19
> **davethewave83 said:**
> Sure the computers are faster these days, but imagine how fast it'd be if it were still programmed to run on 8-16Mb RAM using the technology of today.

You'd have Pong.

I hope you are not under the impression that we don't optimize our code.  Well, those of us who don't work for a certain large software company that shall remain unnamed.

:lolflag:

---

### Post by carl4926 on 2012-01-19
> **QIII said:**
> I would expect Xfce to be a lot lighter.  E17 even beats that.

By the way, weighing in at 0.750GiB at startup, at idle and with nothing running is openSUSE with KDE.  

This is the joy of Linux.  A la carte menu.  You can have a salad or a burger.

FYI:
Guess I'm messing up your poll because my stats were openSUSE 12.1 KDE4
I've not done a reboot for about a week and I just dropped out of a VM

Later when I have my eeepc to hand I'll post my Ubuntu info

---

### Post by QIII on 2012-01-19
A zombie process is essentially a child process spawned by another process that has completed execution but still shows in the process table so the parent can read its exit status.

---

### Post by w201 on 2012-01-19
> **carl4926 said:**
> FYI:
Guess I'm messing up your poll because my stats were openSUSE 12.1 KDE4
I've not done a reboot for about a week and I just dropped out of a VM

Later when I have my eeepc to hand I'll post my Ubuntu info

No worries. Killing firefox shaved off 200MiB lol.

> A zombie process is essentially a child process spawned by another  process that has completed execution but still shows in the process  table so the parent can read its exit status.

I'm not going to pretend to know what that means, but thanks for the explanation.

---

### Post by xyzzyman on 2012-01-19
I was keeping ubuntu 11.10 < 500MB's until I realized I was being stupid not enjoying having 4GB's of RAM. So I'm at 850MB's of RAM used, but I have chrome with lots of extensions, conky, docky, transmission, 4 indicators running, guake, pidgin, gwibber, shutter. Probably missing other stuff.

There are derivates of Ubuntu meant for older hardware, but 2-4GB's of RAM has been standard for a few years now and Ubuntu is geared towards those systems. It's just hard for alot of us to accept we have more RAM than we need. We live like depression era people 50 years later. With similar software running I've found Windows 7 would be using ~1-1.25GB's, even with unneeded background service turned off, etc..

EDIT: That's 4 indicators that I've added, not counting what is already running by default.

---

### Post by w201 on 2012-01-19
> **xyzzyman said:**
> I was keeping ubuntu 11.10 < 500MB's until I realized I was being stupid not enjoying having 4GB's of RAM. So I'm at 850MB's of RAM used, but I have chrome with lots of extensions, conky, docky, transmission, 4 indicators running, guake, pidgin, gwibber, shutter. Probably missing other stuff.

That helps a lot. We're running more or less the same processes. So I guess 700+- MiB is average for ubuntu 11.10

---

### Post by davethewave83 on 2012-01-19
> **QIII said:**
> You'd have Pong.

I hope you are not under the impression that we don't optimize our code.  Well, those of us who don't work for a certain large software company that shall remain unnamed.

:lolflag:

simcity 2000 running on 8mb ram with a GUI capable of internet browsing,networking, audio cd, mp3, mov file playing is a bit more than Pong in my opinion. 

I'm sure you could probably run pong on less than 128k

I didn't mean to imply there is no attempt at optimization in the code, it's just that todays optimization is not optimal. It's no secret that software is bloated, and wastes a lot of space these days. People take the space for granted because of the advancement in technology, instead of really using optimal code that would run 10x faster and cleaner. 

I am not one to complain too much though as I am not a programmer, and if I were, I am sure I would take a lot of the same lazy short cuts that are available today. 

so in the end, all is fair. :p

---

### Post by carl4926 on 2012-01-19
eeepc Ubuntu 11.10 _64 2D

```
top - 07:18:04 up 2 min,  1 user,  load average: 1.25, 0.64, 0.25
Tasks: 147 total,   1 running, 146 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.2%us,  2.5%sy,  0.0%ni, 92.2%id,  1.1%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2046748k total,  1010228k used,  1036520k free,    50356k buffers
Swap:  2313324k total,        0k used,  2313324k free,   485988k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1747 kernelcr  20   0  790m 162m  34m S   14  8.1   0:29.04 firefox            
  962 root      20   0  144m  11m 5648 S    6  0.6   0:07.45 Xorg               
 1645 kernelcr  20   0  308m  17m  11m S    3  0.9   0:02.49 gnome-terminal     
 1807 kernelcr  20   0 82784  13m 9608 S    2  0.7   0:00.74 npviewer.bin       
 1788 kernelcr  20   0  234m  17m  12m S    2  0.9   0:00.55 plugin-containe    
 1452 kernelcr  20   0 26900 2696  856 S    1  0.1   0:04.53 dbus-daemon        
 1545 kernelcr  20   0  374m  18m  10m S    1  0.9   0:02.70 unity-panel-ser    
 1496 kernelcr  20   0  426m  27m  19m S    1  1.4   0:01.28 unity-2d-panel     
 1710 kernelcr  20   0 21460 1384 1004 R    1  0.1   0:00.66 top                
   15 root      20   0     0    0    0 S    0  0.0   0:00.10 kworker/3:0        
  209 root      20   0     0    0    0 S    0  0.0   0:00.17 kworker/u:3        
  832 messageb  20   0 25208 2252 1072 S    0  0.1   0:03.25 dbus-daemon        
  953 root      20   0 15848  632  460 S    0  0.0   0:00.06 irqbalance         
 1485 kernelcr  20   0  198m  12m 9496 S    0  0.6   0:01.67 metacity           
 1491 kernelcr  20   0 20064  908  736 S    0  0.0   0:00.09 syndaemon          
 1513 kernelcr  20   0  335m  13m 9384 S    0  0.7   0:00.54 nm-applet          
 1575 kernelcr  20   0  220m 4796 3820 S    0  0.2   0:00.21 indicator-appli    

```

---

### Post by w201 on 2012-01-19
> **carl4926 said:**
> eeepc Ubuntu 11.10 _64 2D

```
top - 07:18:04 up 2 min,  1 user,  load average: 1.25, 0.64, 0.25
Tasks: 147 total,   1 running, 146 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.2%us,  2.5%sy,  0.0%ni, 92.2%id,  1.1%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2046748k total,  1010228k used,  1036520k free,    50356k buffers
Swap:  2313324k total,        0k used,  2313324k free,   485988k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1747 kernelcr  20   0  790m 162m  34m S   14  8.1   0:29.04 firefox            
  962 root      20   0  144m  11m 5648 S    6  0.6   0:07.45 Xorg               
 1645 kernelcr  20   0  308m  17m  11m S    3  0.9   0:02.49 gnome-terminal     
 1807 kernelcr  20   0 82784  13m 9608 S    2  0.7   0:00.74 npviewer.bin       
 1788 kernelcr  20   0  234m  17m  12m S    2  0.9   0:00.55 plugin-containe    
 1452 kernelcr  20   0 26900 2696  856 S    1  0.1   0:04.53 dbus-daemon        
 1545 kernelcr  20   0  374m  18m  10m S    1  0.9   0:02.70 unity-panel-ser    
 1496 kernelcr  20   0  426m  27m  19m S    1  1.4   0:01.28 unity-2d-panel     
 1710 kernelcr  20   0 21460 1384 1004 R    1  0.1   0:00.66 top                
   15 root      20   0     0    0    0 S    0  0.0   0:00.10 kworker/3:0        
  209 root      20   0     0    0    0 S    0  0.0   0:00.17 kworker/u:3        
  832 messageb  20   0 25208 2252 1072 S    0  0.1   0:03.25 dbus-daemon        
  953 root      20   0 15848  632  460 S    0  0.0   0:00.06 irqbalance         
 1485 kernelcr  20   0  198m  12m 9496 S    0  0.6   0:01.67 metacity           
 1491 kernelcr  20   0 20064  908  736 S    0  0.0   0:00.09 syndaemon          
 1513 kernelcr  20   0  335m  13m 9384 S    0  0.7   0:00.54 nm-applet          
 1575 kernelcr  20   0  220m 4796 3820 S    0  0.2   0:00.21 indicator-appli    

```

Thanks for that!

---

### Post by dak0 on 2012-01-19
Hey,

I wonder what's wrong with my RAM Memory? 
It`s not that this is new PC its like 5 years, but i paid alot for it back in time, seems like 2GiG of RAM Memory isnt enough for this monster Ubuntu 11.10 ;).

Best Regards

[IMG]http://i43.tinypic.com/6rm1ax.png[/IMG]

---

### Post by carl4926 on 2012-01-19
Linux will use most of the available memory
But you should see, under normal load that most of it is in a buffer.
It can often look bad, when actually it isn't

---

### Post by Habitual on 2012-01-19
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by Dreamer Fithp Apprentice on 2012-01-19
450 mb for me right now. I rarely run into memory problems any more. When I do, it's almost always nautilus. It helps if you disable all previews in nautilus preferences.

---

### Post by ubiquitin.jf on 2012-01-19
1.3GB running Firefox and Banshee. I have 8GB so that's not an issue; Everything feels nice and snappy.

Crunchbang boots on this machine at 89MB.

---

### Post by CharlesA on 2012-01-19
Moved to CC.

I haven't really noticed Ubuntu being that much of a resource hog. My desktop box is running Firefox and Bluefish, but it is running as a VM with 512MB of RAM.

```
charles@Lucid:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           494        486          7          0          7         81
[COLOR="Blue"]-/+ buffers/cache:        397         96[/COLOR]
Swap:          894        265        629

```

Server box is running one VM, and a few other services:

```
charles@Thor:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          5981       5599        381          0        271       4339
[COLOR="Blue"]-/+ buffers/cache:        988       4992[/COLOR]
Swap:        17523          0      17523

```

---

### Post by bouncingwilf on 2012-01-19
10.4.3 with firefox and system monitor and its saying 327.0Mb  of 1.9 GB (16.8%) 

I never seem to get any memory problems 

Bouncingwilf

---

### Post by Dry Lips on 2012-01-19
**1.0** GB out of 3.6 GB (=4 GB) RAM. Firefox uses 273. megs, Thunderbird 59.

```
free -m
             total       used       free     shared    buffers     cached
Mem:          3709       2155       1554          0        155        824
-/+ buffers/cache:       1175       2534
Swap:            0          0          0

```

---

### Post by bodhi.zazen on 2012-01-19
My Gentoo install + Openbox + tint2 uses 66 Mb of RAM

[img]http://bodhizazen.net/img/thumb.gentoo.png[/img]

Unity uses about 225 Mb RAM. Of course with Ubuntu there is a bit more then just Unity running.

My VM has 1 Gb ram and us using 218 Mb (KDE)

```
free -m
             total       used       free     shared    buffers     cached
Mem:           998        780        218          0        166        385
-/+ buffers/cache:        [color=darkred]**228**[/color]        770
```

See : [linux ate my ram](http://www.linuxatemyram.com/)

It is all relative, but, considering anything resembling modern hardware comes with at least 1 Gb ram, 200-300 Mb seems rather reasonable.

---

### Post by cariboo on 2012-01-19
I'm running Precise alpha 1 so ram usage is a little higher than normal

```
free -m
             total       used       free     shared    buffers     cached
Mem:          2003       1889        113          0        137        882
-/+ buffers/cache:        869       1134
Swap:         1999          0       1999
```

---

