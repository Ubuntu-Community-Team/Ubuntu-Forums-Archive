---
title: "why do linux programs generally use so much ram?"
date: 2007-01-19
forum: The Cafe
---

### Post by Choad on 2007-01-19
[[IMG]http://img260.imageshack.us/img260/7074/lowmemusageac7.th.png[/IMG]](http://img260.imageshack.us/my.php?image=lowmemusageac7.png)

i have yet to find a media player that uses up less than 20mb of ram with my music collection, and "isten" was using >60mb. foobar2k however uses just 2mb. utorrent as well, yet most torrent clients in linux use upwards of 10mb

im not trying to attack linux, im genuinely interested why this might be

everything in linux seems to use substantially more ram than its windows equivilent. dont even get me started on nautilus lol.

---

### Post by ComplexNumber on 2007-01-19
maybe because most of them are written in either python or c#. the ones written in C or C++ tend to be leaner in resources.

---

### Post by Lord Illidan on 2007-01-19
On my pc, firefox is by far and far away the hungriest..

---

### Post by zerhacke on 2007-01-19
You guys must be running a lot of extensions in Firefox.  For me, Firefox eats less than 30MB.  After that the biggest RAM eater is Gnome-Panel at just under 9MB.

---

### Post by bunabattoir on 2007-01-19
It is probably because they can. Linux's memory management is better than Win32's, so more RAM is made available when needed. It will then be reclaimed by the OS when needed elsewhere.

It could also be an accounting thing (the way the different platforms report mem usage, etc.).

---

### Post by sloggerkhan on 2007-01-19
My edgy system takes up way less RAM than windows. At any given moment it seems to be using between 120-260 mb of RAM, on extreme occasions, up to about 400mb. I have NEVER seen it use more than 12mb of swap (usually it uses 0). I admit it will often use unused RAM as cache, but it stops that as more memory becomes used for programs...

Even on my system running beryl, I tend to use about 250-300 mb of RAM.

On windows I easily use 300mb, and when I run games and such, that would skyrocket. And windows always had significant swap file usage, too.

i can't comment on App by app comparisons, though.

---

### Post by po0f on 2007-01-19
[Link](http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html), explains it pretty well.

---

### Post by sporx on 2007-01-19
I never learned python and I don't know much about it. I only know two people that know how to use it.

---

### Post by Choad on 2007-01-19
> **po0f said:**
> [Link](http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html), explains it pretty well.
ahh! that makes alot of sense

so if gedit, gnome baker and a game all used gnome_lib_x/y then the memory that gnome_lib_x/y takes up is added to each of the process' memory values, even tho gnome_lib_x/y is only loaded in to memory once.

kind of wierd, but at least it explains it.

however, the sys monitor shows my ram "x used out of 1024mb total" or whatever. if it ever got to 1024/1024, surely that would mean that there is still ram that i can use left over. because there would likely be alot of shared libraries in there, so the output would be inacurate. does that mean (according to the sys monitor) that (ignoring swap for the moment) i could have MORE than 1024mb of ram in use? do you even understand what im asking here?

---

### Post by ComplexNumber on 2007-01-19
> **Choad said:**
> ahh! that makes alot of sense

so if gedit, gnome baker and a game all used gnome_lib_x/y then the memory that gnome_lib_x/y takes up is added to each of the process' memory values, even tho gnome_lib_x/y is only loaded in to memory once.

kind of wierd, but at least it explains it.

however, the sys monitor shows my ram "x used out of 1024mb total" or whatever. if it ever got to 1024/1024, surely that would mean that there is still ram that i can use left over. because there would likely be alot of shared libraries in there, so the output would be inacurate. does that mean (according to the sys monitor) that (ignoring swap for the moment) i could have MORE than 1024mb of ram in use? do you even understand what im asking here?i  thought you were comparing media players(on linux) that take up a lot of ram with those that don't (on linux).

---

### Post by po0f on 2007-01-19
Choad,

Which system monitor are you using to get your RAM usage?  `free -m` (from a terminal) gives a more accurate reading of RAM usage.

---

### Post by MkfIbK7a on 2007-01-19
its true quod libet my music player is the top memory user then epiphany
(screenshot)
as you can see i use icewm

---

### Post by K.Mandla on 2007-01-19
I was going to mention the explanation of Linux memory use in the Gentoo wiki, but the link above is helpful as well.

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by po0f on 2007-01-19
K.Mandla,

Yeah I thought I had that link bookmarked but I don't or I would have posted that as well.  It must be bookmarked on my Linux box.

---

### Post by shining on 2007-01-19
other articles about memory usage:
[http://ktown.kde.org/~seli/memory/](http://ktown.kde.org/~seli/memory/)

---

### Post by rev_b on 2007-01-19
It's pointless to compare diferent programs. To me, Ubuntu with dual-monitor, 2 taskbars, running gnome, with qt libraries intalled and loaded, beryl 0.2 svn with pretty much all plugins loaded, with firefox opening 5 tabs and with 3-4 extensions gives me a memory usage of 279 Mb. That's 13.8% of my whole 2 Gb! And the used swap is, as expected, 0.

Booting into windows XP desktop with Nvidia drivers, twinview, antivirus, firewall, windows defender, and so on, opening firefox, and I never get away with much less than 500Mb used. That's fine for my actual RAM, but what drives me crazy is that windows always seems to do some file swapping even with 3/4 of free RAM!

So, comparing the same system, 2 diferent OS, I find Linux memory management way much more efficient than windows. So yes, I think a good answer to the question is "because they can" ;)

---

### Post by digTro on 2007-01-19
> **Choad said:**
> 
everything in linux seems to use substantially more ram than its windows equivilent. dont even get me started on nautilus lol.

My experience is quite the opposite. For me, the measure of RAM usage is the amount of swap space being used. Right now I have Firefox, Auzreus, Eclipse, Amarock and Gaim open (and some server processes - Apache, Tomcat, MySql, CVS). My RAM is 1 GB and the swap space used is a measly 18 MB. If I were to have the same programs running in Windows, the page file usage would be a minimum of 150 MB (I'm too lazy to login to XP right now. But I wouldn't be surprised if that estimate is on the lower side). Hell, even with no programs running, the page file usage would be a few tens of MB.

---

### Post by Mateo on 2007-01-19
i don't agree with the premise of this thread at all!  the reason i came to linux is because the programs launch faster, my computer doesn't slow down when I have multiple stuff open at the same time.

---

### Post by kripkenstein on 2007-01-19
The GNOME System Monitor has a field called "Writable Memory" for processes (this is a fairly recent addition). It tells you the amount of memory the process can write to, and since shared libraries cannot be written to, this is a fairly good measure of the 'real' memory usage of a process.

Speaking of music players, xmms is using 1.3MB here, very reasonable. However, Firefox **with NO extensions** is using 90MB right now, and often I see it above 100. Other high-RAM things are GNOME-panel and Nautilus, which after a day or so of constant uptime start to be fairly large (20-30 megs). All of this stuff leads to me having to restart GNOME once a day or two (I never turn off my computer) - I have 512MB, and once 300MB of RAM and 250MB of swap are being used, things get somewhat slow. It's a little annoying, but not too bad I guess.

---

### Post by saulgoode on 2007-01-19
Engaging in some speculation (I am not that familiar with Windows and am not inclined to investigate deeply), while both the Windows and Linux memory stats include shared library routines (and in neither case is this a true reflection of the situation), I am thinking that the Windows routines for the GUI interface exist in the kernel and therefore are not represent under memory usage; whereas Linux's GUI toolkit is in userland and its shared libraries are represented.

---

### Post by macogw on 2007-01-19
According to free -m, I'm always using up over 900 mb of ram.  That's Beryl, Firefox, Gaim, and XChat.

---

### Post by sloggerkhan on 2007-01-19
do you subtract your buffers/cache or include them?

---

### Post by pichalsi on 2007-01-19
If you wonder why Firefox takes so much RAM, read this :) 
[http://weblogs.mozillazine.org/ben/archives/009749.html](http://weblogs.mozillazine.org/ben/archives/009749.html)

---

### Post by RandomJoe on 2007-01-20
Wow...  I just enabled the "Writable Memory" field in System Monitor.  I wonder what that memory upgrade cost me?!? :biggrin: 

As an example, it says firefox-bin has 7,310,569,757.7 GiB writable memory!!!  Um...

Almost all of the processes listed say things like that!  There are only a handful that have more sane values, like 30KiB or such.

The Resident Memory value seems reasonable - 49MiB for firefox-bin.  Shows 137MiB for virtual memory.

As others have mentioned, I too find that Linux is far more efficient with memory usage than Windows.  Except for buffers, which in Linux will eat up all available RAM just because it's sitting there, I have a hard time on most systems getting over 256MB.  On my new system - thanks to having tons of screenspace to spread things out and leave them on - I might get near 512MB.  I don't think I've ever seen my swap used, other than a few kB, on any system with more than 256MB RAM.

Windows on my previous dual-booting work laptop (512MB RAM) would hit swap almost before it got finished starting up.  It's not too bad on the 1GB machine I have now, though.

---

### Post by rai4shu2 on 2007-01-20
I just think it's disturbing that I have 1 zombie (netstat).

---

### Post by kripkenstein on 2007-01-20
> **RandomJoe said:**
> Wow...  I just enabled the "Writable Memory" field in System Monitor.  I wonder what that memory upgrade cost me?!? :biggrin: 

As an example, it says firefox-bin has 7,310,569,757.7 GiB writable memory!!!  Um...

Almost all of the processes listed say things like that!  There are only a handful that have more sane values, like 30KiB or such.

The Resident Memory value seems reasonable - 49MiB for firefox-bin.  Shows 137MiB for virtual memory.


Wow, that sounds very wrong... can you post a screenshot?

---

### Post by macogw on 2007-01-20
> **sloggerkhan said:**
> do you subtract your buffers/cache or include them?

i ignored that column completely

..................total.......used.........free....shared.....buffers...cached
Mem:------1002-----941-----60-------0--------167------316
-/+ buffers/cache:----457-----544
Swap:-------0----------0-------0

---

### Post by jvc26 on 2007-01-20
Putting mine up ;)
             total       used       free     shared    buffers     cached
Mem:        515888     504556      11332          0      10396     239628
-/+ buffers/cache:     254532     261356
Swap:       979956         80     979876

Of which:
Xorg and Firefox are the biggest memory hoggers.
Il

---

### Post by zerhacke on 2007-01-20
> **kripkenstein said:**
> However, Firefox **with NO extensions** is using 90MB right now, and often I see it above 100.

I'm willing to bet you have java and flash 7 or 9 enabled.

---

### Post by RandomJoe on 2007-01-20
> **kripkenstein said:**
> Wow, that sounds very wrong... can you post a screenshot?
Alrighty, here it is - I now have a few more things running, including a long-running CivCTP game.  (The screenshot only shows one entry, there are actually six identical entries for Civ!)

Ubuntu 6.06 32-bit on a Core 2 Duo w/ 2GB RAM...

---

### Post by kripkenstein on 2007-01-20
> **zerhacke said:**
> I'm willing to bet you have java and flash 7 or 9 enabled.

Flash 9, yeah. Not sure about Java (do any websites still use that nowadays, anyhow?)

So, without Flash, Firefox is much leaner?

---

### Post by kripkenstein on 2007-01-20
> **RandomJoe said:**
> Alrighty, here it is - I now have a few more things running, including a long-running CivCTP game.  (The screenshot only shows one entry, there are actually six identical entries for Civ!)

Ubuntu 6.06 32-bit on a Core 2 Duo w/ 2GB RAM...

Hmm, looks like the "Writable" column is corrupt, or isn't showing the right units... it just doesn't make any sense to me.

---

