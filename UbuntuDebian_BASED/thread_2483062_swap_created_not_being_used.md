---
title: "swap created not being used"
date: 2023-01-19
forum: Ubuntu/Debian BASED
---

### Post by paul_red2 on 2023-01-19
Hi

I'm new with Linux OSes.. I installed it on an old intel core duo laptop (4gb ram)
but I forgot during installation to create the swap partition.. so I decided to follow a giude online:
[https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-22-04)

But using free -h I get this (swap not being uded at all:
```
               total        used        free      shared  buff/cache   available
Mem:           3,8Gi       1,6Gi       1,0Gi        21Mi       1,4Gi       2,2Gi
Swap:          4,0Gi          0B       4,0Gi

```

the graf on the desktop shows me the ram and cpu are not freeer after creating this swap.
I'm sure Ive done smth wrong.. can you guys help me?

---

### Post by TheFu on 2023-01-19
If the swap is showing up in 'free' output, then it is active. You can also use the 'swapon -s' command to see it.
But, if the system doesn't need any swap, then it won't be used.  You can check the system "swappiness" setting using 'sysctl' if you like.
```
$ sysctl -a |grep swapp
```

BTW, the buffers default to 20% of the RAM in the system.  With just 4GB of RAM, you might want to reduce those.

RAM requests by programs are the highest priority, so buffers will be dropped to the minimal amount automatically when program RAM requests require it and you'll see the virtual memory use increase.  Zero swap is a bit unusual for any Ubuntu install, but I can see where some VPS services might make that their default.  For a server, I try to minimize the swap available and needed. For desktops, that is much harder, with the bloat that is a modern browser.

---

### Post by paul_red2 on 2023-01-20
Thanks.

my swappiness is 80
> vm.swappiness = 80

Can you please tell me how can I do this:
> BTW, the buffers default to 20% of the RAM in the system.  With just 4GB of RAM, you might want to reduce those.

Also I wanted to know if it was better for me to have done the swap partition with Gparted and erase this swap I'm creating with a file.. Or maybe it's the same?

---

### Post by TheFu on 2023-01-20
If you are going to delve into the internal system settings on Unix, you'll need to learn to use manpages.  These provide details for how nearly every command works.  'man man' will teach about manpages.  They are organized in specific ways and in specific sections.  This is a basic skill for all Linux/Unix users to master.

So, the manpage for 'sysctl' says it can be used to modify any parameter.  This is only for a running system and last until the next reboot.  This is good to test things BEFORE making them permanent.  The manpage explains how to make it permanent, but always test any changes like this for a few hours, if not a few days, before.  Unexpected results are possible.

> 
Also I wanted to know if it was better for me to have done the swap partition with Gparted and erase this swap I'm creating with a file.. Or maybe it's the same? 
I don't know, since I haven't tested it on my systems.  The hardware involved would matter greatly.  For a number of reasons, I don't use swapfiles.  I actually don't use swap partitions either, preferring to use LVM2 Logical Volumes for my storage management.  There are different uses for swap and depending on the system and the users, those purposes can change.  

For example, I want to "feel" swap being used on desktops, because it means the system is running low on RAM and I need to close a few huge programs, typically the browser, but sometimes I'll shutdown a virtual machine.  With really fast storage, I'd likely not "feel" the sluggishness and when both RAM and swap are all used, the system will crash.  Here's  my main desktop, running 20.04:
```
$ free -mh
              total        used        free      shared  buff/cache   available
Mem:          3.8Gi       1.0Gi       126Mi        10Mi       2.7Gi       2.5Gi
Swap:         4.1Gi       9.0Mi       4.1Gi
```

On servers, I want to minimize the use of swap and allocate more RAM to the system so the workload it handles has just enough RAM to handle all expected/tested/known workloads.  About 4 yrs ago, the kernel code was changed so that having "some" swap would make the software run faster, even if it wasn't used.  Typically, for my well-tuned servers, I'll provide 500MB swap to enable the extra performance, with the expectation that swap will never get used, at least not much. For example, here's a small, family, old, nextcloud server running 18.;04:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           976M        419M        115M         26M        441M        376M
Swap:          1.0G        231M        790M
```
The new version (probably 20.04) will have less swap.  It does use all 1G of RAM occasionally. 

See how different systems have different needs for swap?

Both those systems above are virtual machines. They run on 2 different physical systems. 1 has 32G of RAM and the other has 16GB.
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:            30G         18G        1.5G        177M         10G         11G
Swap:          4.3G        1.8G        2.5G
```
and the other
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           14Gi       3.9Gi       653Mi       2.0Mi        10Gi        10Gi
Swap:         4.1Gi       1.8Gi       2.4Gi
```
I need to upgrade the 32G system. It needs a new OS before April. ;)

Sorry if this was more than you wanted.

---

### Post by paul_red2 on 2023-01-20
I don't understand all this. 
I could just type some code you tell me on the terminal and give you the result.

Can you help me?

I have this machine:
> CPU: dual core Intel Core2 Duo T6400 (-MCP-) speed/min/max: 1600/1200/2000 MHz
Kernel: 6.0.0-kali6-amd64 x86_64 Up: 2h 32m Mem: 2054.7/3922.0 MiB (52.4%)
Storage: 465.76 GiB (4.2% used) Procs: 190 Shell: Zsh


On a Windows 10 (which is on another hard disk) this same machine runs ok
now in Linux is very slow.

---

### Post by TheFu on 2023-01-20
I can't help with Kali kernels.  They aren't from Canonical.

---

### Post by paul_red2 on 2023-01-21
<snip>

Anyway.. for anybody else that wants to help: update of my situation:
now my swap is being used:
```
               total        used        free      shared  buff/cache   available
Mem:           3,8Gi       1,9Gi       317Mi        22Mi       1,9Gi       1,9Gi
Swap:          4,0Gi       1,0Mi       4,0Gi
```
 just 1Mb for the moment (xD lol) but I guess it's better than 0

Anyway from what I'm seeing Firefox is the issue. And it has to do with a particular tab I have to keep open to use internet (which is public hotspot that can be used only if you allow ads).
I have an adblocker ofc but it just stops the ad from showing.. the tap constantly refreshes and I think this uses much of the cpu + ram. As soon as I close that tap the cpu+ram use drops but internet can't be used. So I'm sure there must be a way to fix this.
I still don't understand why the computer doesn't start to use the swap I created when physical ram is at the max.

---

### Post by coffeecat on 2023-01-21
> **paul_red2 said:**
> Kernel: 6.0.0-kali6-amd64 x86_64 Up: 2h 32m Mem: 2054.7/3922.0 MiB (52.4%)

Kali Linux is not Ubuntu, nor is it one of the official flavours of Ubuntu, nor is it based on Ubuntu. You posted in the Officlal Flavours Support section of the forums.

*Thread moved to the appropriate sub-forum*

---

### Post by The Cog on 2023-01-21
I don't think you are short on memory - you are misunderstanding the output. Many new users do - it's different to what Windows displays. Here's an old page explaining: [https://www.linuxatemyram.com/](https://www.linuxatemyram.com/)

---

### Post by paul_red2 on 2023-01-21
Thanks The Cog.. I'll take a look (hopefully I'll understand)

---

### Post by TheFu on 2023-01-21
> **coffeecat said:**
> Kali Linux is not Ubuntu, nor is it one of the official flavours of Ubuntu, nor is it based on Ubuntu. You posted in the Officlal Flavours Support section of the forums.

*Thread moved to the appropriate sub-forum*

Not only is Kali not an official version of Linux, it is one of the least secure distros because it isn't meant to be used for daily use. It is a security tool, not a general purpose OS.  Worrying about swap use on a custom distro designed for a specific purpose really doesn't make sense.  I won't say that a web browser shouldn't be used, since part of security engagements is to see what websites appear and look for parts of those websites that shouldn't be generally available ... and looking for known flaws in the webapps after confirming the version of the app, web server or dbms running are susceptible to a method.
[https://www.systranbox.com/how-to-assign-swap-space-in-kali-linux/](https://www.systranbox.com/how-to-assign-swap-space-in-kali-linux/) seems to be written by a Kali guy. I only skimmed it, but he says that creating swap on Kali is different than other Linux distros.  Something about being a rolling release.

All that I know is that kali is a different animal, which is why I said I couldn't help.  I've used it on engagements with clients, but I'd never use it for a daily driver and have never needed to worry about swap with it.

---

### Post by paul_red2 on 2023-01-21
I'm trying to understand (if anyone can help) what's the difference of creating a swap with gparted and with a swapfile.. maybe if with the file is hard to do maybe I should just put a live version of gparted and just create a partition for swap and I'm done..
Again can anyone tell me what is the difference?

---

### Post by #&amp;thj^% on 2023-01-21
> **paul_red2 said:**
> what's the difference of creating a swap with gparted and with a swapfile.. 

Just methods used, I find, and I think the majority here find a swapfile easier, especially after a full install.
The Linux Kernel divides RAM into chunks of memories and the swapping process is when the Linux Kernel uses a hard disk space (swap space) to store information from RAM and thus releases some RAM space. That is why when you install a Linux distribution, the installation wizard usually asks you to assign some space for the system and another for the swap.
For a swap file:[https://discovery.endeavouros.com/storage-and-partitions/adding-swap-after-installation/2021/03/](https://discovery.endeavouros.com/storage-and-partitions/adding-swap-after-installation/2021/03/)
For a swap partition after install; [https://wiki.archlinux.org/title/swap](https://wiki.archlinux.org/title/swap)

---

### Post by TheFu on 2023-01-21
I don't know the current situation, but in prior Ubuntu releases swap  files couldn't be used for hibernation.  Also, swap files can run into fragmentation, if the size is changed or not contiguous.

A web search found lots and lots of answers.  One pointed out that a swap file on different file systems can have specific issues caused by the file system used. So, the answer isn't always simple, though the question seems like it would be.

For Linux, swap files are relatively new when compared to swap partitions which have been used for about 30 yrs now.

Of course, Kali isn't Ubuntu, so YMMV.

---

### Post by #&amp;thj^% on 2023-01-21
> **TheFu said:**
> I don't know the current situation, but in prior Ubuntu releases swap  files couldn't be used for hibernation.  Also, swap files can run into fragmentation, if the size is changed or not contiguous.
 yep i went the easy answer, Those are great points to consider.
> **TheFu said:**
> A web search found lots and lots of answers.  One pointed out that a swap file on different file systems can have specific issues caused by the file system used. So, the answer isn't always simple, though the question seems like it would be.
For Linux, swap files are relatively new when compared to swap partitions which have been used for about 30 yrs now.

another serious point to consider. after some self test's between the two and how i set my rigs up, I find swap partitions far better.
> **TheFu said:**
> 
Of course, Kali isn't Ubuntu, so YMMV.
+1

---

### Post by paul_red2 on 2023-01-22
Thanks for the help guys
I think I'll un do the swapfile and try to add a partition with Gparted (hoping I don't mess things up). It's still a mistery to me tho why on this same machine a Windows 10 would run faster than what I'm seeing with Linux (Kali in this case).
I would have expected Linux used better the low power hardware I have..
Anyway.. I'll try to add this swap partition and see if it improves.

---

### Post by TheFu on 2023-01-22
Kali is a very specific distro, unlike any other.  If you want to know about kali performance tuning, perhaps the best place to ask is on their forums?  

Kali does lots of things that Ubuntu and other mainstream distros don't allow. Most of the kali users I know - which is over 100  in my local DefCon groups, use kali on a dedicated system, just for security testing. None use it as a desktop. If Kali doesn't create swap as part of the Kali installation process, that speaks loudly to me.  TinyCore doesn't either.  It doesn't make them bad, just distros for a specific need.

There are many different distros designed to be used on less powerful hardware.  TinyCore will fly on almost any hardware that will boot today.  In the Ubuntu world, Lubuntu and Xubuntu are the low-end hardware distros to use.   It is up to the installer do choose properly.  If you have a motorcycle, but put a camper onto the same motor because you want a TV, fridge, bed, and microwave, you'll be disappointed.  The same applies to Linux distros.  I have a tiny linux device, no GUI, that runs off USB 5V power that is just a wifi storage server.  It makes microSD storage available to wifi clients. That's all it does.  Perfect for phones without a slot to add more storage, but not be force to use cloudy storage.

The right tool, for the right job. Matching the tool and hardware is up to the installer.

---

### Post by C.S.Cameron on 2023-01-23
> **TheFu said:**
> I don't know the current situation, but in prior Ubuntu releases swap  files couldn't be used for hibernation.  Also, swap files can run into fragmentation, if the size is changed or not contiguous.



I have had good luck activating hibernation in 20.04 and 22.04 using swapfiles. The secret is to use [B]resume_offset
[/B]
See: [https://askubuntu.com/a/1358453/43926](https://askubuntu.com/a/1358453/43926)

---

### Post by TheFu on 2023-01-24
> **C.S.Cameron said:**
> I have had good luck activating hibernation in 20.04 and 22.04 using swapfiles. The secret is to use [B]resume_offset
[/B]
See: [https://askubuntu.com/a/1358453/43926](https://askubuntu.com/a/1358453/43926)

Grandma needs a checkbox that handles everything, but the fact that it works at all seems to be progress.  That's excellent.
At least in that link, they use fallocate - not enough people remember/know that command. Very handy ... and I always forget about it myself.  There are lots of times where creating a specific sized file in under 1 sec is handy, even if just to play with block storage commands using it.

---

