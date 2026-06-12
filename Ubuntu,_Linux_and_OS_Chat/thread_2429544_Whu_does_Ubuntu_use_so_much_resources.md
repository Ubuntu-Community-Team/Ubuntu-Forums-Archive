---
title: "Whu does Ubuntu use so much resources"
date: 2019-10-19
forum: Ubuntu, Linux and OS Chat
---

### Post by RobGoss on 2019-10-19
I've just downloaded Ubuntu **19.10 **to give it a spin and notice it uses **2- GIG of Ram **just to keep this system going with noting running. is there any reason why it's using so much Ram with this release

I do think the system is a bit faster but am I willing to give up so much Ram resources not sure. I'm currently using Ubuntu mate and it only uses 726.31 MB   

I would like to switch back to Ubuntu but seeing it's consuming so much resource I'm not sure it's worth it

What are your thoughts?

---

### Post by Claus7 on 2019-10-19
Hello,

actually in ubuntu flashback it uses slightly less or the same which is ~1GB in my system. In ubuntu classic it goes higher than that and with a quick look ~ 1.2GB. Have you checked which is the resource hungry cause that uses so much ram? 
ps ux and system monitor will provide you more info.

Regards!

---

### Post by Artim on 2019-10-19
It's the reason I use Xubuntu instead!  Gnome 3 is a resource hog.  Even with 8GB of RAM there's a very noticable difference in speed loading applications and processing my projects.

There are plenty of very good alternative desktops and applications that use far less RAM and processor power.

---

### Post by RobGoss on 2019-10-19
Thanks for the tips. Yes I am aware of all the different distributions of Ubuntu I have many installed on different machines

I just don't understand why Ubuntu does not focus on this distro using less resources that's one of the reasons I moved away from it. I'll have to see what's using so much ram

---

### Post by TheFu on 2019-10-19
It is common for Windows computers to have 16-64GB of RAM, so Ubuntu wants to have all the "*cheese*" enabled they can for end-users who like the *cheese* to enjoy.  Every bell and whistle is enabled, even if you don't want them.  That uses RAM, CPU and gnome3 is a GPU hog.

For people like you and me, *cheese* for no purpose isn't worth it.  I prefer to begin with a lighter distro, then add anything I want.  I suppose some people would prefer to start with a bloated distro and remove things they don't want, assuming there isn't a "*just right*" distro for them.

The idea than any OS needs more than 512MB to run well freaks me out a little.

---

### Post by VMC on 2019-10-19
> **RobGoss said:**
> I've just downloaded Ubuntu **19.10 **to give it a spin and notice it uses **2- GIG of Ram **just to keep this system going with noting running. is there any reason why it's using so much Ram with this release

...
How did you check usage? using *vmstat* I get: 647824 K used memory, and *free*=6486376

---

### Post by uRock on 2019-10-19
I wish there was documentation explaining RAM usage. My system running 19.10 is only using 750MB of RAM at idle. It only has 2GB of RAM and nothing is currently being used in swap.

---

### Post by kmarsajith on 2019-10-19
when you use system monitor or top (vide terminal), which is the top memory hog application? web browsers these days could easily consume 1 GB of RAM, if several tabs are opened..

---

### Post by HermanAB on 2019-10-19
If you are concerned with speed, then you need to install either Slackware or OpenBSD with XFCE.  You will be blown away.

---

### Post by RobGoss on 2019-10-19
> **HermanAB said:**
> If you are concerned with speed, then you need to install either Slackware or OpenBSD with XFCE.  You will be blown away.

Hello HermanAB, well I'm am always concerned with the speed of my machines seeing a few of them are very old. Now when I was old I mean none of my machines have less then four GB of Ram, and the max machine is running 16-GB

I'm just concerned about Ubuntu 19.10 using so much Ram. I've always loved Ubuntu but when Gnome was introduced as the main desktop environment I had to move away from it to see if things gotten better 

It sounds interesting, **Slackware or OpenBSD **with **XFCE,** but I don't know much about it

---

### Post by RobGoss on 2019-10-19
> **uRock said:**
> I wish there was documentation explaining RAM usage. My system running 19.10 is only using 750MB of RAM at idle. It only has 2GB of RAM and nothing is currently being used in swap.

I would have to say your machine is doing well with Ubuntu 19.10. I have Mate installed on one of my machines and it's using about the same as yours

---

### Post by RobGoss on 2019-10-19
> **Claus7 said:**
> Hello,

actually in ubuntu flashback it uses slightly less or the same which is ~1GB in my system. In ubuntu classic it goes higher than that and with a quick look ~ 1.2GB. Have you checked which is the resource hungry cause that uses so much ram? 
ps ux and system monitor will provide you more info.

Regards!

Thanks a bunch I'll have to check on that

---

### Post by RobGoss on 2019-10-19
**TheFu's ** I'm with you on that I don't need a lot on any system. I am a minimalist so I'm always getting rid of software that's not needed

---

### Post by RobGoss on 2019-10-19
> **VMC said:**
> How did you check usage? using *vmstat* I get: 647824 K used memory, and *free*=6486376

With system monitor it shows what using much of the Ram but I will have to take another look

---

### Post by mc4man on 2019-10-19
> **RobGoss said:**
> I've just downloaded Ubuntu **19.10 **to give it a spin and notice it uses **2- GIG of Ram **just to keep this system going with noting running. 

Don't see anything close. 
With gnome-shell/mutter around 600 MB used. 
With unityshell/compiz around 525 used.

---

### Post by Artim on 2019-10-19
Have you got some stuff running "in the background" that might be burning up RAM?  Like Bluetooth, Samba, network sharing, antivirus or daemons you don't need?

---

### Post by Tadaen_Sylvermane on 2019-10-19
Unused ram is wasted ram. These days computers have so much ram its stupid. Might as well use it for something. Post results of 

```
free -h
```

I'd post mine for comparison but I'm ripping dvds so my ram is fat right now.

Look at your actual available ram, not what's used. May be cache load. Linux uses ram like it's supposed to, doesn't let it sit and waste itself.

---

### Post by Skaperen on 2019-10-19
> **Tadaen_Sylvermane said:**
> Unused ram is wasted ram. These days computers have so much ram its stupid. Might as well use it for something. Post results of 

```
free -h
```

I'd post mine for comparison but I'm ripping dvds so my ram is fat right now.

Look at your actual available ram, not what's used. May be cache load. Linux uses ram like it's supposed to, doesn't let it sit and waste itself.

i like to see a low ram usage right after i boot up.  i like to see zero  swap usage because swapping is slow.  with ssd swapping will be faster  but ram is still the fastest so if it all can stay in ram that makes it  the fastest.  so why do i want to see the usage be a small fraction of  ram?  why do i use xubuntu so that it is?  why do i like to see so much  available ram?  do i get any benefit from that number?  so that i can  use that ram for myself!

```

lt2a/forums /home/forums 20> free -h
              total        used        free      shared  buff/cache   available
Mem:            15G        6.3G        454M        1.8G        8.9G        7.2G
Swap:           15G        2.3M         15G
lt2a/forums /home/forums 21>

```

---

### Post by QIII on 2019-10-19
I wouldn't use swap at all on an SSD.  That's a lot of read/write operations.  Swap was used back when RAM was precious and disk space was slightly less precious.  RAM is now dirt cheap.   4GB goes a long way.  8 GB is a lot.  16GB is probably overkill for the vast majority of users.  Someone running a heavily used server might want to use swap for scaling, but it's really unnecessary for a desktop user, IMO. 

You ARE using that RAM for yourself.  Linux maintains buffers and cache in RAM to make things faster.  Rather than having to re-read a file from disk, maintaining it in memory means the next time you want to work on it it is already in memory without having to be read from disk.  If the memory is needed later for some other task, the OS will sacrifice some memory from an older task to make room for something new.  

Unless it is due to a leak (which is NOT what most people think it is.  An application's use of excessive memory beyond what is really needed is not a leak.  The failure of an application to release memory when it dies is.  That memory cannot be recovered by the kernel and it can grow to the point where the OS fails.), you should be happy about the RAM being used.  That makes things faster for you.

It is a misconception to think that memory use is a bad thing in Linux.  It is a good thing.

With regard to RobGoss' question, your use may indicate something amiss.  All the forgoing notwithstanding, there are times when RAM use is excessive -- indicating that a lot of needless processes may be running or one process in particular may be running wild.

You can use 

```
top
``` 

to find out what is using all the memory.  It could be that the eye-candy is gobbling it, something that really is irritating.

---

### Post by Skaperen on 2019-10-20
actually i think i need even more than 16G.  so maybe 64G in my next one.  i use a lot.  i could run more things in the cloud.

---

### Post by RobGoss on 2019-10-20
> **Artim said:**
> Have you got some stuff running "in the background" that might be burning up RAM?  Like Bluetooth, Samba, network sharing, antivirus or daemons you don't need?

No nothing like that, I was trying to test 19.10 and using the USB drive so I don't know if that would make a difference

---

### Post by Artim on 2019-10-20
I think it does!  But I do the same thing when trying out a distro, I won't use virtualbox for that.  If it's slow Live, it'll be slow installed.

---

### Post by RobGoss on 2019-10-20
> **Artim said:**
> I think it does!  But I do the same thing when trying out a distro, I won't use virtualbox for that.  If it's slow Live, it'll be slow installed.

Yes I do all my installation in a live environment 

Thanks a bunch for that :)

---

### Post by uRock on 2019-10-20
> **RobGoss said:**
> I would have to say your machine is doing well with Ubuntu 19.10. I have Mate installed on one of my machines and it's using about the same as yours

I will add that that install is in a VM with only 2GB of RAM. From what I have noticed over the years, Ubuntu and others will use more or less RAM at idle depending on how much has been allocated. That is why I mentioned how nice it would be to have documentation explaining how the OS determines this, which would help folks who had questions on it. I am using Xubuntu as my primary on my desktop production machine and laptop used for testing and breaking. I have Debian Buster LXDE on a Netbook running as a server and it is only using 270MB of the 2GB RAM.

---

### Post by Tadaen_Sylvermane on 2019-10-20
[FONT=arial]```
ps aux --sort -rss
```

Try that. It will list your processes by highest usage from the top down. You can isolate it that way. Found here.

[/FONT][https://unix.stackexchange.com/questions/92493/sorting-down-processes-by-memory-usage](https://unix.stackexchange.com/questions/92493/sorting-down-processes-by-memory-usage)[FONT=arial]
[/FONT]

---

### Post by RobGoss on 2019-10-21
> **uRock said:**
> I will add that that install is in a VM with only 2GB of RAM. From what I have noticed over the years, Ubuntu and others will use more or less RAM at idle depending on how much has been allocated. That is why I mentioned how nice it would be to have documentation explaining how the OS determines this, which would help folks who had questions on it. I am using Xubuntu as my primary on my desktop production machine and laptop used for testing and breaking. I have Debian Buster LXDE on a Netbook running as a server and it is only using 270MB of the 2GB RAM.

Thanks so much for the help and information on this issue

---

### Post by missmoondog on 2019-10-22
> **Tadaen_Sylvermane said:**
> Unused ram is wasted ram. These days computers have so much ram its stupid. Might as well use it for something. Post results of 

```
free -h
```

I'd post mine for comparison but I'm ripping dvds so my ram is fat right now.

Look at your actual available ram, not what's used. May be cache load. Linux uses ram like it's supposed to, doesn't let it sit and waste itself.

was looking for something else, sort of, and saw this topic. i'm using linux mint 19.2 with xfce and this is my memory usage as computer sets right now.

                   total        used        free      shared  buff/cache   available
Mem:           7.7G        761M        1.3G         33M        5.6G        6.7G
Swap:          2.0G          0B        2.0G


surprised as heck to see it only using 761M, but cool as heck. no wonder mint runs so well on everything i've put it on. used to use lubuntu, but that doesn't have nearly all the tools and stuff mint has that are very handy. wouldn't dream of using that bloated ubuntu, even on a very good machine!

---

### Post by uRock on 2019-10-22
> **missmoondog said:**
> <snip>.....wouldn't dream of using that bloated ubuntu, even on a very good machine!

I'm thinking Gnome is where the bloat is, not ubuntu. One of the reasons I dropped Debian Buster with Gnome from my desktop and put ubuntu on it, was because I always kept System Monitor open and constantly saw a lot of gnome stuff that didn't need to be running. Those processes were eating RAM. I installed Xubnutu on it and the difference was very obvious. Much less RAM utilization by background applications. Here's that command on my Xubuntu desktop before and after shutting down my video processing for Motion server and the RAM eater we call Firefox.
```
urock@urock:~$ free -h
              total        used        free      shared  buff/cache   available
Mem:           5.8G        2.2G        719M        112M        2.9G        3.2G
Swap:          7.8G        512K        7.8G
urock@urock:~$ free -h
              total        used        free      shared  buff/cache   available
Mem:           5.8G        580M        2.5G         17M        2.8G        4.9G
Swap:          7.8G        512K        7.8G

```
Take a look at your buff/cache output.

---

### Post by slickymaster on 2019-10-23
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by RobGoss on 2019-10-23
> **uRock said:**
> I'm thinking Gnome is where the bloat is, not ubuntu. One of the reasons I dropped Debian Buster with Gnome from my desktop and put ubuntu on it, was because I always kept System Monitor open and constantly saw a lot of gnome stuff that didn't need to be running. Those processes were eating RAM. I installed Xubnutu on it and the difference was very obvious. Much less RAM utilization by background applications. Here's that command on my Xubuntu desktop before and after shutting down my video processing for Motion server and the RAM eater we call Firefox.
```
urock@urock:~$ free -h
              total        used        free      shared  buff/cache   available
Mem:           5.8G        2.2G        719M        112M        2.9G        3.2G
Swap:          7.8G        512K        7.8G
urock@urock:~$ free -h
              total        used        free      shared  buff/cache   available
Mem:           5.8G        580M        2.5G         17M        2.8G        4.9G
Swap:          7.8G        512K        7.8G

```
Take a look at your buff/cache output.


I believe you're correct I should have made it more clear. I would say Gnome is the resource hog indeed. On this machine I have Xubuntu all ready to be installed I see how it runs, I had it installed awhile back and its was great. I never really liked Gnome for this reason

---

### Post by lammert-nijhof on 2019-10-23
DID YOU USE THE ZFS EXPERIMENTAL INSTALL? That would explain your memory usage, since ZFS reserves a large part of the free memory as cache and that is counted as used memory. It will free that memory again, if you load more programs, but that makes your system somewhat slower. I use ZFS since March 2018 and I boot from ZFS since Jan 2019. I maximize the cache size to 20-25% of my total memory in /sys/module/zfs/parameters/zfs_arc_max. By default it contains 0, no limit, but you can specify there a large number, specifying the maximum size of the cache in BYTES.

You can type: "arc_summary" to get a lists of all ZFS sizes and performances. It is a huge list, but in the first 10 lines you can see the cache (L1ARC) size. Somewhat further on it will give you even the cache hit rates.

---

### Post by kansasnoob on 2019-10-24
That seems unusually high even for the out-of-box GNOME 3 DE, although I do typically see high CPU usage the first few minutes after boot while unattended upgrades runs in the background. Even with Firefox open I typically only see RAM usage around 1.5 to 2 GB unless I have some very heavy web content loading. Of course it depends greatly on where I'm looking because some stats show cached RAM usage as actually USED RAM, but cached RAM is better thought of as reserved - not actually used because it'll be reallocated as needed as the priority of processes changes.

---

### Post by kansasnoob on 2019-10-24
> **lammert-nijhof said:**
> DID YOU USE THE ZFS EXPERIMENTAL INSTALL? That would explain your memory usage, since ZFS reserves a large part of the free memory as cache and that is counted as used memory. It will free that memory again, if you load more programs, but that makes your system somewhat slower. I use ZFS since March 2018 and I boot from ZFS since Jan 2019. I maximize the cache size to 20-25% of my total memory in /sys/module/zfs/parameters/zfs_arc_max. By default it contains 0, no limit, but you can specify there a large number, specifying the maximum size of the cache in BYTES.

You can type: "arc_summary" to get a lists of all ZFS sizes and performances. It is a huge list, but in the first 10 lines you can see the cache (L1ARC) size. Somewhat further on it will give you even the cache hit rates.

Good point. I hadn't thought of that. It should be noted that the release notes clearly state [Support for ZFS as the root filesystem is added as an **experimental** feature in 19.10]("https://wiki.ubuntu.com/EoanErmine/ReleaseNotes#ZFS_on_root"). Intentional emphasis on experimental.

---

### Post by bernard010 on 2019-11-27
My Ubuntu 19.10 Gnome is only using 1.3 GB of memory out of 8 GB. 
That is while reading and typing on this forum + Live streaming Video/Music in the background.
Kernel 5.3.0-23 
Something to remember how much you have going on the O.S. accounts for its Resources. True?

---

### Post by j2ee on 2019-12-18
Yeah this is so bad

---

