---
title: "Help Reducing Memory Usage in Ubuntu Server 10.04"
date: 2010-10-03
forum: Server Platforms
---

### Post by Jesse B on 2010-10-03
I recently got my home server up and running using some spare hardware I had laying around.  It's been working just fine, and I have no complaints.  However, I've noticed that as time goes on, memory usage seems to creep up and up.  

First things first, is this a known issue?  It goes back down to practically no memory usage after I restart the server, but then as time goes on it goes up to over 50%. I've only got 2GB of RAM at this point in time, and can't afford to buy more.  I'd just like for it to have more uptime than it currently does, without the need for constant rebooting.  

Second, I need to eliminate processes that don't need to be running.  I have no GUI installed, so this needs to be done via the CLI.  Is there a list of processes that are fundamental to the operation of the operating system anywhere?

Thanks in advance,


- Jesse

---

### Post by nr1c0re on 2010-10-03
describe what services you need on that server
show ps ax
and top

---

### Post by P4man on 2010-10-03
Its called a memory leak.  "top" should be able to tell you which process is leaking. Just sort it by memory usage when the server has been running for a while. Older versions of Xorg have been known to be leaky, but since you're not running X, its gotta be something else :)

---

### Post by BkkBonanza on 2010-10-03
How are you checking memory use?

I suspect you are seeing the effect of normal linux caching. It will appear to be using memory which is actually fully available for program use.

Under normal circumstances your memory use should remain fairly stable. It may go up and down but with a typical set of services running it won't keep climbing.

However, if you use the **free** command to view memory then you will see more and more get used up as the kernel uses memory for disk caching. This is normal and does not mean the memory is allocated as the kernel will hand that memory over to any program that allocates it.

A more intelligent utility like **htop** gives you a better view of your running system and real memory use.

For cleaning up unwanted processes the output of **ps -ax** command would be helpful to see what you have running. **pstree** also gives a nice printout showing parent/child processes nicely.

There isn't a standard list as it always depends on your system. Some core programs like init (always), cron (usually) needed. But after that you can often cut down on others.

---

### Post by Jesse B on 2010-10-03
> **nr1c0re said:**
> describe what services you need on that server
show ps ax
and top

There's a rather long output from running 'ps -ax', so I'll just list the services which I'm running that are "mandatory".  I've attached a text file showing the output.

- Apache2 server w/ PHP5/MySQL
- Subsonic
- TorrentFlux
- VirtualBox

That's pretty much all I require of my server.  I haven't set up anything to stream video yet, so that will be added on eventually.

> **P4man said:**
> Its called a memory leak.  "top" should be able to tell you which process is leaking. Just sort it by memory usage when the server has been running for a while. Older versions of Xorg have been known to be leaky, but since you're not running X, its gotta be something else :)

It seems to max out at about 55% memory usage, and then drop down to around 50%-ish.  Normally the OS using 1GB of RAM wouldn't bother me, but this isn't exactly a memory-intensive installation.  Maybe I'm just asking too much, and this amount of usage is normal, I don't know.  'top' output has also been attached, as it honestly doesn't mean a whole bunch to me.

> **BkkBonanza said:**
> How are you checking memory use?

I suspect you are seeing the effect of normal linux caching. It will appear to be using memory which is actually fully available for program use.

Under normal circumstances your memory use should remain fairly stable. It may go up and down but with a typical set of services running it won't keep climbing.

However, if you use the **free** command to view memory then you will see more and more get used up as the kernel uses memory for disk caching. This is normal and does not mean the memory is allocated as the kernel will hand that memory over to any program that allocates it.

A more intelligent utility like **htop** gives you a better view of your running system and real memory use.

For cleaning up unwanted processes the output of **ps -ax** command would be helpful to see what you have running. **pstree** also gives a nice printout showing parent/child processes nicely.

There isn't a standard list as it always depends on your system. Some core programs like init (always), cron (usually) needed. But after that you can often cut down on others.

I was just going off the text that gets spewed out after ssh'ing into my server, like so:
[[IMG]http://i36.photobucket.com/albums/e19/jesse_braham/th_Screenshot-7.png[/IMG]](http://s36.photobucket.com/albums/e19/jesse_braham/?action=view&current=Screenshot-7.png)
Using the 'free' command outputs the following text:
> jesse@ubuntu-server:~$ free
             total       used       free     shared    buffers     cached
Mem:       1797284    1781384      15900          0       9708    1132236
-/+ buffers/cache:     639440    1157844
Swap:      5264376      20400    5243976

There's a high amount cached, so I assume that's what you were referring to?

Thanks for the help so far everyone.  I'm still getting used to this whole deal, as I just recently switched to Linux in general.  I'll start doing some research based on what you guys have suggested, and let everyone know how it goes.

Thanks again,


- Jesse

---

### Post by nr1c0re on 2010-10-04
Well, you should attach top with "by memory" sorting.

You can try ulimit and set max memory size for shell/process. Default is unlimited.

In top I see
smbd
nmbd
mysql
inetd
Do you use them?

---

### Post by BkkBonanza on 2010-10-04
```
total **used** free shared buffers **cached**
Mem: 1797284 **1781384** 15900 0 9708 **1132236**
```

This shows your actual memory used as 1781384 - 1132236 = 649148 or about 649 MB.
If this calculation result changes greatly over time then there may be an issue.
If the **cached** value increases along with the **used** value then it is just caches and means nothing regarding program memory use.

I don't know what calculation the landscape thingy shown during login uses but it seems to give a higher figure (unless it changed after login).

My home server usually runs between 80-100 MB, but then I started with a minimal install and removed things I didn't want there. Apache is a pig and I don't run it (I use nginx but not on this server anyway). 

Usually xinetd can be tossed unless you have something dependent on it, which usually people don't. It's a service for opening ports dynamically as programs request and personally gives me the heebies-jeebies having around, even if known to be ok.

smbd, nmbd, winbindd are all part of Samba so you can decide if you need samba running (for sharing storage on your network).

---

### Post by nr1c0re on 2010-10-04
Looking at top

Mem:   1797284k total,  1782124k used,    15160k free,     9624k buffers
Swap:  5264376k total,    20396k used,  5243980k free,  1133176k cached

We see, that at that momen all memory in use.
But I see 1gb used for cache - "1133176k cached" - that's ok. When there is free memory and high disk activity linux cache in RAM data from disk for performance reasons.
When application need some memory kernel will free it from cache and give it to application.

But I do not like 20M swap usage...

---

### Post by P4man on 2010-10-04
Since the OP has 2 gigs of RAM, 650 MB of actual use is good. Sure you can get this down, a lot, but there isnt a real need. If it aint broke, dont fix it :). Although if security is a concern (if the server is facing the internet) then stopping unneeded services is not a bad idea.

As for the 20 MB swap. Ive seen ubuntu do that on my machines as well. I have no idea why. There is probably a good reason, but even if not, hey, its just 20 MB. Still better than windows swapping gigabytes for no obvious reason.

---

### Post by Jesse B on 2010-10-04
> **BkkBonanza said:**
> ```
total **used** free shared buffers **cached**
Mem: 1797284 **1781384** 15900 0 9708 **1132236**
```This shows your actual memory used as 1781384 - 1132236 = 649148 or about 649 MB.
If this calculation result changes greatly over time then there may be an issue.
If the **cached** value increases along with the **used** value then it is just caches and means nothing regarding program memory use.

I don't know what calculation the landscape thingy shown during login uses but it seems to give a higher figure (unless it changed after login).

My home server usually runs between 80-100 MB, but then I started with a minimal install and removed things I didn't want there. Apache is a pig and I don't run it (I use nginx but not on this server anyway). 

Usually xinetd can be tossed unless you have something dependent on it, which usually people don't. It's a service for opening ports dynamically as programs request and personally gives me the heebies-jeebies having around, even if known to be ok.

smbd, nmbd, winbindd are all part of Samba so you can decide if you need samba running (for sharing storage on your network).

Alright, thanks.  I've recently been getting into web development, so I just like having a server around to be able to test things out on (I've been doing a lot of PHP).  I'll get rid of xinetd, and at this point in time I'm not needing Samba, so I'll get rid of that as well. 

> **nr1c0re said:**
> Looking at top

Mem:   1797284k total,  1782124k used,    15160k free,     9624k buffers
Swap:  5264376k total,    20396k used,  5243980k free,  1133176k cached

We see, that at that momen all memory in use.
But I see 1gb used for cache - "1133176k cached" - that's ok. When there is free memory and high disk activity linux cache in RAM data from disk for performance reasons.
When application need some memory kernel will free it from cache and give it to application.

But I do not like 20M swap usage...

Alright, that's what I figured.  As for the swap usage, I was transferring some .iso's while I ran those commands, so that could be why?

> **P4man said:**
> Since the OP has 2 gigs of RAM, 650 MB of actual use is good. Sure you can get this down, a lot, but there isnt a real need. If it aint broke, dont fix it :). Although if security is a concern (if the server is facing the internet) then stopping unneeded services is not a bad idea.

As for the 20 MB swap. Ive seen ubuntu do that on my machines as well. I have no idea why. There is probably a good reason, but even if not, hey, its just 20 MB. Still better than windows swapping gigabytes for no obvious reason.

While I do admit it's "fine" how it is, I just wanted to get this rig to be as efficient as possible, just as a bit of a challenge/learning experience.  I just got VirtualBox with the phpVirtualBox web front-end installed, so I'd like to free up some more RAM for VM's :)

Thanks a lot everybody, you've all been quite helpful,


- Jesse

---

### Post by CharlesA on 2010-10-04
When that happens, try running this command:

```
free -m
```

That'll show how much memory is being used for caching and whatnot.

Also, you might want to check out htop, instead of top. I found that it can be a bit easier to deal with and understand.

---

### Post by SeijiSensei on 2010-10-04
Those processes in swap consists largely of kernel components that load at boot and swap themselves out immediately.  You'll see these processes if you run "ps ax" and look for the entries in square brackets.

There's practically no reason to try and manage memory better than the Linux kernel does already.  It aggressively caches the disk drives to improve performance, and reallocates those pages of memory to programs when needed.  Nearly every Linux box I run has almost all of the physical memory in use.  In most cases it's allocated to caching the disk drives.

You don't really need to free up memory for the VMs; Linux will handle that, too.  I just started up a Win7 Virtualbox VM and watched Linux reallocate the disk cache to the VM.

---

### Post by Jesse B on 2010-10-04
> **CharlesA said:**
> When that happens, try running this command:

```
free -m
```That'll show how much memory is being used for caching and whatnot.

Also, you might want to check out htop, instead of top. I found that it can be a bit easier to deal with and understand.

```
jesse@ubuntu-server:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1755       1738         17          0         11       1200
-/+ buffers/cache:        526       1229
Swap:         5140          0       5140
```

Quite a bit of memory cached.  I also did check out htop, it is indeed quite a bit easier to understand.

> **SeijiSensei said:**
> Those processes in swap consists largely of kernel components that load at boot and swap themselves out immediately.  You'll see these processes if you run "ps ax" and look for the entries in square brackets.

There's practically no reason to try and manage memory better than the Linux kernel does already.  It aggressively caches the disk drives to improve performance, and reallocates those pages of memory to programs when needed.  Nearly every Linux box I run has almost all of the physical memory in use.  In most cases it's allocated to caching the disk drives.

You don't really need to free up memory for the VMs; Linux will handle that, too.  I just started up a Win7 Virtualbox VM and watched Linux reallocate the disk cache to the VM.

I guess I wasn't really going at managing memory as much as eliminating unnecessary processes.    I didn't realize that the kernel was quite *that* good at managing memory, so that's good to know.

Thanks guys,


- Jesse

---

### Post by CharlesA on 2010-10-04
That looks about normal, cuz you've got over a gig of memory cached.

---

### Post by NightwishFan on 2010-10-04
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/) - A good read.

Also if you do not use any proprietary drivers (or any of these, make sure you do not need them) you can do this:
```
sudo nano /etc/default/linux-restricted-modules-common
```

Paste this:
```
DISABLED_MODULES="ath_hal fc fglrx fwlanusb ltm nv"
```

Reboot, or manually disable them.
```
rmmod *nameofmodule*
```


I actually find I get better performance using vm.swappiness=100. Follow this tutorial except use 100 instead of 10.
[https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?)

---

