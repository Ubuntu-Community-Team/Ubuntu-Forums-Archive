---
title: "How much RAM does your system use?"
date: 2010-01-10
forum: The Cafe
---

### Post by samjh on 2010-01-10
Just wondering what everyone's memory usage is.

Here are mine on Arch x86_64 with 4GB RAM under Gnome 2.28 and KDE 4.3.

**Gnome, Compiz (minimum plugins enabled), Firefox (two tabs: Arch forum and YouTube), Gnome-Terminal, and Gnome System Monitor.**
296MB

Most memory is used by Firefox (76.6MB), Compiz (25.7MB), and Nautilus (13.3MB).

```
             total       used       free     shared    buffers     cached
Mem:          3959        668       3291          0         70        301
-/+ buffers/cache:        296       3663
Swap:         4102          0       4102
```

**KDE with KWin compositing (default settings), Firefox (two tabs: Arch forum and YouTube), Konsole, and KDE System Monitor.**
336 MB

Most memory is used by Firefox (76.6MB), X (26.8MB), and Plasma Desktop (22.2MB).

```
             total       used       free     shared    buffers     cached
Mem:          3959       1026       2933          0         68        621
-/+ buffers/cache:        336       3623
Swap:         4102          0       4102
```

---

### Post by mamamia88 on 2010-01-10
right now on my netbook running xubuntu 225mb of ram running firefox with 2 tabs and a instance of synaptic

---

### Post by ~sHyLoCk~ on 2010-01-10
Compiz standalone:
```
 ~ >  free -m
             total       used       free     shared    buffers     cached
Mem:          2007        618       1389          0          7        272
-/+ buffers/cache:        338       1669
Swap:         1906          0       1906

```

---

### Post by jwbrase on 2010-01-10
My system tends to start out around 290-something. Skype ends up taking about 50 MB more, then Opera with it's memory leak tends to start out small and grow. Sometimes it'll push the total usage over a gig, but that's rare. Compiz vs. Metacity seems to be a difference of about 30 megs.

Right now I'm running around 650.

---

### Post by x33a on 2010-01-10
my arch machine right after boot up uses about 120 MB of ram with gnome.

right now with firefox (2 tabs)(76 MB), gnome-terminal (screen -> 2 shells) (35 MB):
```
free -m
             total       used       free     shared    buffers     cached
Mem:          1009        765        243          0        105        440
-/+ buffers/cache:        220        788
Swap:         2055          0       2055

```

---

### Post by happyhamster on 2010-01-10
My jaunty desktop after a day of light use:

```

free -m
             total       used       free     shared    buffers     cached
Mem:          7990       7928         61          0         76       6789
-/+ buffers/cache:       1062       6927
Swap:         1921          1       1920

```

Firefox takes 430MiB right now (10 instances of Firefox running, ~30 tabs I guess. Funny thing is that the swap is actually being used :)

---

### Post by Warpnow on 2010-01-10
810 mbs, but I'm running about 40 apps, of which 2 are web browsers, some text editors with over 100 files open, 2 games (super tux and world of goo), an irc client, totem, with a video playing on my external monitor, pidgin, and I have about a dozen pdf files open preparing for my first day of classes tomorrow.

---

### Post by schauerlich on 2010-01-10
I never got why people with loads of RAM pride themselves on how little RAM they're using. If you've got 4GB, why not use it?

---

### Post by kk0sse54 on 2010-01-10
Htop says 1052 MB Ram in use and muse -m reports ```
Active:      292.863 MB
Inactive:    140.008 MB
Wired:      1057.949 MB
Reserved:      4.109 MB
Cache:         2.207 MB
Kernel:        0.133 MB
Interrupt:     0.008 MB
Buffer:       61.500 MB

Total:      3007.648 MB
Free:       1513.430 MB

```

and that's just with two terminals, one running screen with portmaster and four tabs in firefox :o

---

### Post by Warpnow on 2010-01-10
> **schauerlich said:**
> I never got why people with loads of RAM pride themselves on how little RAM they're using. If you've got 4GB, why not use it?

If I had 4gbs I'd load the entire OS into ram every boot.

---

### Post by standingwave on 2010-01-10
> **schauerlich said:**
> I never got why people with loads of RAM pride themselves on how little RAM they're using. If you've got 4GB, why not use it?Exactly! I wish it would use more memory. Only rarely does it ever exceed 1GB.

[IMG]http://i49.tinypic.com/2uzfs46.png[/IMG]

---

### Post by Psumi on 2010-01-10
Bleh...

[http://i49.tinypic.com/i20ydg.png](http://i49.tinypic.com/i20ydg.png)

---

### Post by witeshark17 on 2010-01-10
When I have a lot of websites open, about 400 - 900 mb

---

### Post by xuCGC002 on 2010-01-11
```
             total       used       free     shared    buffers     cached
Mem:          3964       1022       2942          0         85        390
-/+ buffers/cache:        545       3419
Swap:         2910          0       2910
```

KDE 4.3, Firefox with 3 tabs open.

---

### Post by Warren Watts on 2010-01-11
```

warren@server-550:~$ uptime
 02:09:24 up 9 days,  5:19,  1 user,  load average: 0.29, 0.10, 0.02
warren@server-550:~$ sudo lshw -C memory,processor -short
H/W path                  Device     Class       Description
============================================================
/0/0                                 memory      128KB BIOS
/0/4                                 processor   Pentium III (Katmai)
/0/4/a                               memory      32KB L1 cache
/0/4/b                               memory      512KB L2 cache
/0/1f                                memory      512MB System Memory
/0/1f/0                              memory      128MB DIMM EDRAM
/0/1f/1                              memory      128MB DIMM EDRAM
/0/1f/2                              memory      256MB DIMM EDRAM
/0/1f/3                              memory      DIMM EDRAM [empty]
warren@server-550:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           503        477         26          0        133        246
-/+ buffers/cache:         98        405
Swap:          470         33        437

```

550 MHz PIII 512MB RAM - Set up as server with no GUI

---

### Post by phillychease on 2010-01-11
```
             total       used       free     shared    buffers     cached
Mem:          1444       1344        100          0        170        532
-/+ buffers/cache:        641        803
Swap:         4228          6       4221

```

hmmmm

---

### Post by insane_alien on 2010-01-11
when its idle, about 200MB. 

when it's doing what i built it to do, 8GB + 4GB of swap.

---

### Post by NoaHall on 2010-01-11
On GNU/Linux, when having a web browser + media player + file browser + aMSN open, around 500MB. On Windows Vista/7, it's about 700MB for me. When doing more powerful things, such as playing games, video editing, photo editing, it has free run of 16GBs. I usually run several games at once.

---

### Post by xpod on 2010-01-11
I have 2G in my desktop but the reality is i could have taken a Gig out and still got by just fine....Virtualbox asides.
This old laptop only has 512Mb at the moment and it does me just fine too.In fact, i spend more time on this than i do on the Desktop....which is only a click or two away regardless.

---

### Post by tom66 on 2010-01-11
My Pentium III running on Ubuntu 8.10 uses 180MB of memory idle, and 200MB word processing. It has no swap, and has 256MB memory available.

I have noticed that Ubuntu 9.10 is much more of a hog, on my laptop, using almost 1 GB with Chrome + Gedit + Apache running, compared to the 700 MB in 8.10. I'm not too upset, because I've got 3 GB to play with plus 2 GB swap, but it is interesting.

---

### Post by Nevon on 2010-01-11
Ubuntu 9.10 with Firefox, Caffeine, Dropbox and Deluge running.

```
nevon@loltop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1975       1825        149          0         30       1374
-/+ buffers/cache:        419       1555
Swap:         5820          0       5820
```

---

### Post by Exodist on 2010-01-11
My system uses all my RAM, either part is software running normally around 1-1.5GB and the rest is various OS/Software still pre-cached for faster access.

---

### Post by t0p on 2010-01-11
EeePC 701 Jaunty, using Firefox (7 tabs), 1 terminal, totem playing muzak, downloading some warez over http:

```

t0p@deimos:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2006       1929         76          0         14       1492
-/+ buffers/cache:        423       1583
Swap:            0          0          0

```

**EDIT:** Actually I don't get what that means.  According to System Monitor, I'm using about 420MB of my 2GB RAM.  Where does my misunderstanding lie?

---

### Post by realzippy on 2010-01-11
> **standingwave said:**
> Exactly! I wish it would use more memory. Only rarely does it ever exceed 1GB.

[IMG]http://i49.tinypic.com/2uzfs46.png[/IMG]


...run a remastersys backup.
More than 7 Gb in use.....

---

### Post by barnex on 2010-01-11
```

~> uname -a                                                                                                                                  
Linux karmic 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux                                                    
~> kded -version                                                                                                                    
Qt: 3.3.8b                                                                                                                          
KDE: 3.5.10                                                                                                                         
KDE Daemon: $Id: kded.cpp 711061 2007-09-11 09:42:51Z tpatzig $                                                                     
~> top                                                                                                                    
top - 13:50:11 up  5:03,  2 users,  load average: 0.09, 0.07, 0.02
Tasks: 156 total,   2 running, 154 sleeping,   0 stopped,   0 zombie
Cpu(s): 45.3%us,  4.0%sy,  0.0%ni, 50.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2030268k total,  1965292k used,    64976k free,   202156k buffers
Swap:  4192956k total,        0k used,  4192956k free,   925820k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 2925 arne      20   0  390m 109m  49m S    1  5.5   6:30.21 amarok
 2373 arne      20   0  282m 100m  61m S    0  5.1   1:04.89 soffice.bin
 2108 arne      20   0  237m  67m  23m S    0  3.4   0:46.46 thunderbird-bin
 7753 arne      20   0  152m  62m  14m R   66  3.1   0:19.74 exe
 1966 arne      20   0  319m  57m  27m S    0  2.9   0:31.91 plasma-desktop
 1060 root      20   0  104m  39m  14m S   23  2.0   9:00.04 Xorg
 3097 arne      20   0  171m  38m  20m S    1  1.9   0:56.41 chrome
 7743 arne      20   0  116m  36m  18m S    4  1.8   0:02.87 chrome
 7538 arne      20   0  136m  34m  12m S    0  1.7   0:06.64 chrome
 1996 arne      20   0 97.7m  33m  21m S    0  1.7   0:01.18 python
 1994 arne      20   0  101m  30m  19m S    0  1.6   0:01.17 python
 1965 arne      20   0  159m  27m  14m S    0  1.4   0:02.97 knotify4

```

---

### Post by samjh on 2010-01-11
> **t0p said:**
> EeePC 701 Jaunty, using Firefox (7 tabs), 1 terminal, totem playing muzak, downloading some warez over http:

```

t0p@deimos:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2006       1929         76          0         14       1492
-/+ buffers/cache:        423       1583
Swap:            0          0          0

```

**EDIT:** Actually I don't get what that means.  According to System Monitor, I'm using about 420MB of my 2GB RAM.  Where does my misunderstanding lie?

Using "free -m", the relevant figure is the one just to the right of "-/+ buffers/cache", which is 423 in your case.  So that means 423MB of RAM is being used.

Your effective RAM usage is calculated using this formula: used - buffers - cached.
In your case: 1929 - 14 - 1492.

---

### Post by Chris Edgell on 2010-01-11
> **Warpnow said:**
> If I had 4gbs I'd load the entire OS into ram every boot.

Can you explain to me why you'd want to do that?


> **tom66 said:**
> My Pentium III running on Ubuntu 8.10 uses 180MB of memory idle, and 200MB word processing. It has no swap, and has 256MB memory available.


I guess I don't understand swap, I thought you HAD to have it, or is that only when space is tight?

Thanks

---

### Post by Warpnow on 2010-01-11
Swap isn't necessary however not having any is unwise. Your swap doesn't get used until all of your RAM is used. So if you don't use all your ram, ever, you don't need swap. 

I don't think ubuntu has the toram option, but try booting the knoppix livecd with "toram" in the boot parameters. It loads everything into ram, meaning that the hard drive isn't even used...it is outrageously fast.

---

### Post by vikrant82 on 2010-01-11
Why is it that more RAM system uses, more sluggish system becomes ? For e.g. My system has 1.5G of RAM. As the usage approaches 1G, I can see noticeable sluggishness. Even when swap is almost untouched as yet. 

Also why is it that** after a** heavy disk IO system seems to be even more sluggish as if it is recovering from a shock ? :) This is more pronounced in windows, but I have also noticed it on Linux. 

More so, why should system crawl while I am copying/writing a CD, even when there's plenty of RAM available and CPU is free ?

---

### Post by Grifulkin on 2010-01-11
Older laptop with 1GB of RAM.  Running Arch+Openbox
```
             total       used       free     shared    buffers     cached
Mem:           945        342        602          0          0        207
-/+ buffers/cache:        134        810
Swap:         1004          0       1004

```

And on my netbook running Arch+Openbox.

It starts at about 65mb and usually doesn't exceed 100 until I start a webbrowser with a couple tabs.


And for the life of me I have the same basic set up on ea ch and have found that my X server on the older laptop uses 2.5% of RAM while the X server on my netbook uses ~0.9% and I don't know why there is such a big change in the two.

---

### Post by SecretCode on 2010-01-11
> **vikrant82 said:**
> More so, why should system crawl while I am copying/writing a CD, even when there's plenty of RAM available and CPU is free ?

This is probably due to hardware interrupts, fighting with the keyboard and video let alone the hard disks. I find this is particularly bad on laptops.

---

### Post by NoaHall on 2010-01-11
> **Grifulkin said:**
> Older laptop with 1GB of RAM.  Running Arch+Openbox
```
             total       used       free     shared    buffers     cached
Mem:           945        342        602          0          0        207
-/+ buffers/cache:        134        810
Swap:         1004          0       1004

```

And on my netbook running Arch+Openbox.

It starts at about 65mb and usually doesn't exceed 100 until I start a webbrowser with a couple tabs.


And for the life of me I have the same basic set up on ea ch and have found that my X server on the older laptop uses 2.5% of RAM while the X server on my netbook uses ~0.9% and I don't know why there is such a big change in the two.

Better graphics cards and better graphics drivers and support for the netbook, would be my guess, not to mention other drivers.

---

### Post by Chris Edgell on 2010-01-11
Please go on with your topic, I just had to get in here and say that the negative is so miniscule and the positive so immense that I got amazed that there ever was the discussion of the miniscule.

So many gracious, thoughtful, helpful and truly caring people...never ceases to amaze me.
People stop what they're doing and answer the many little questions that pop up during the topic that's still ongoing.  I just love it!

So here's to you all
Cheers
(Well, I do have a coffee in my hand...(for people who ask if you really laugh when you write) lol.)             LOL

Christine

---

### Post by realzippy on 2010-01-12
> **Warpnow said:**
> Swap isn't necessary however not having any is unwise. *Your swap doesn't get used until all of your RAM is used*. So if you don't use all your ram, ever, you don't need swap. 




....only if swappiness is set to 0.

[B]cat /proc/sys/vm/swappiness
[/B]

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Khakilang on 2010-01-12
Old laptop with 512MB RAM. Use mostly Firefox and Open Office.

---

### Post by pwnst*r on 2010-01-12
> **schauerlich said:**
> I never got why people with loads of RAM pride themselves on how little RAM they're using. If you've got 4GB, why not use it?

^this.

I have 8 and the couple of times I've bothered to look at RAM usage I laughed.

---

### Post by pookiebear on 2010-01-12
crunchbang (openbox)
idle at 127mb
with firefox, RDesktop and pidgin going it is at 289mb

---

### Post by alex_o on 2010-01-26
```
             total       used       free     shared    buffers     cached
Mem:          3959       3810        148          0        249       2760
-/+ buffers/cache:        800       3159
Swap:         4996          0       4996
```

2760mb's of cache hehehehe :p that shure beats running 512mb's

Firefox:200MiB
Totem:42.7MiB
python(screenlets):27.8MiB
compiz.real:19.6MiB
pidgin:19.1MiB
nautilus:9.4MiB

---

### Post by SuperSonic4 on 2010-01-26
Arch x86_64: Amarok, Firefox (3 tabs), KWin, Konsole, KMess

```
             total       used       free     shared    buffers     cached
Mem:          7994       1757       6236          0        117        975
-/+ buffers/cache:        664       7330
Swap:        12997          0      12997

```

unsurprisingly no swap is being used

---

### Post by Zoot7 on 2010-01-26
As I type right now, I'm at 223MB as per conky. That's with Nautilus, Banshee and Firefox open in Debian with gnome atop openbox.
> **pwnst*r said:**
> I have 8 and the couple of times I've bothered to look at RAM usage I laughed.
Agreed. I've 4 in my main rig and whilst I've seen 64bit Windows 7 go up to maybe 2-2.5GB of usage the few times I've looked, I really don't care how much RAM it uses as long as the OS itself doesn't "chug" or "stutter" in any way while I'm using it.

---

### Post by Bartender on 2010-01-26
Bog-standard Ubuntu 9.04 install.  Compiz, firefox, and whatever :)

```

             total       used       free     shared    buffers     cached
Mem:          2011        554       1457          0         30        228
-/+ buffers/cache:        295       1716
Swap:         1937          0       1937

```

---

### Post by scouser73 on 2010-01-26
```
free -m
             total       used       free     shared    buffers     cached
Mem:     1002        920         81          0        216           296
-/+ buffers/cache:  407        595
Swap:    2933          1        2931
```

---

### Post by SuperSonic4 on 2010-01-26
> **schauerlich said:**
> I never got why people with loads of RAM pride themselves on how little RAM they're using. If you've got 4GB, why not use it?

^ this

Unused RAM is wasted RAM. I have 8GB and it means my system doesn't slow, I can enable even more of KDE eyecandy, rip 4 CDs at once, create a DVD and even edit video

---

### Post by gnomeuser on 2010-01-26
1.7 gigs of ram used out of 3 gigs available.

I rather think that is wasteful, I would love for any excess RAM to be used for precaching the most used files or something. RAM is much faster than disk, saving the IO would probably greatly enhance the system performance. Of course that is just a thought, it could be insane.

Regardless the machine is running Compiz, Banshee (doing some heavy lifting bpm detection, downloading podcasts and processing for Mirage), VLC playing a movie (curse you Fluendo DVD for not working properly anymore now I am stuck with this poorly designed UI). A couple of Nautilus windows, Empathy, aMSN, a gnome-terminal and finally gnome-system-monitor which got me the data in the first place. Oh and plenty of Chromium tabs.

I rather think the system is holding up nicely given it's low specs (dual core Atom 330)

---

### Post by llawwehttam on 2010-01-26
```
llawwehttam@Joe-Pineapples:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3960       1117       2843          0         71        519
-/+ buffers/cache:        525       3434
Swap:         4769          0       4769

```4 GB DDR3 Ram with 2.0 Ghz dual core 64 bit processor.

Running conky, firefox 2 tabs, gnome-terminal, rhythmbox, thunderbird.

EDIT: this is a laptop with an nvidia geforce gt130m so it uses some of the ram.

---

### Post by proxess on 2010-01-26
```
proxess@PRXSS-Laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2009       1509        499          0         93        633
-/+ buffers/cache:        782       1227
Swap:            0          0          0
```

---

### Post by Paqman on 2010-01-26
> **gnomeuser said:**
> I would love for any excess RAM to be used for precaching the most used files or something.

Sounds like you want to install preload ;)

---

### Post by lotharmat on 2010-01-26
Firefox with 3 tabs open and Compiz

```
             total       used       free     shared    buffers     cached
Mem:          3014       1429       1584          0        124        867
-/+ buffers/cache:        437       2577
Swap:         6236          0       6236

```

---

### Post by Hallvor on 2010-01-26
[IMG]http://4333762010312117005-a-1802744773732722657-s-sites.googlegroups.com/site/privacyosproject/home/ram.png?attachauth=ANoY7cp0p0h_HbU94XCqF-J2PRaUGpcN4VuC4bE3nRVvE54WI43WQ-ALfgNzS4GqtnpV5Yo2nRYrLou2DwuUutZCwOEKMRkTvNe72RR6skSXqhnsYTJj5bmUy4BueIIfLaikHvI9E27dNYuyXG368d0R4iHUDqo77jbuQeh2mhcZvfp2VMoWV-4AJxNKO9G-gNLVn1fQmDspGBp1qBUPI8cVD9UzLoinAA%3D%3D&attredirects=0[/IMG]

This is from a virtual machine. I think memory usage is a little higher on a HD install.

My Debian Lenny (64 bit) starts at 120 MB, I think. When I have used it for a few days and have a few browsers, IM and Bittorrent open it usually stabilizes at +-400 MB out of 2 GB.

---

### Post by etnlIcarus on 2010-01-26
Ubuntu 9.04 minimal 32bit, on my Athlon 2800+ w/ 512mb of RAM.

Single tty login: 20-23mb of RAM usage.
X w/ HAL & Xfce 4.6: 110-112mb of RAM usage.
X w/ HAL, Xfce 4.6 & Compiz 0.8.2: 130-140mb of RAM usage.

Currently, with X, HAL, Xfce, Compiz, Pidgin, Galculator, Thunar, Pragha and 3 Firefox windows open (separate windows use more RAM than tabs, unfortunately), I'm sitting at about 275-285mb of RAM usage.

---

### Post by Paqman on 2010-01-27
```
             total       used       free     shared    buffers     cached
Mem:          3962       2313       1648          0        116       1111
-/+ buffers/cache:       1085       2876
Swap:         3223          0       3223
```

This is with /tmp and browser cache loaded into RAM, and preload enabled, running Chrome, Empathy, Skype, Gwibber and some other nicknacks. 

I mostly got 4GB for running VMs. 2GB wasn't quite enough, and i've only got 2 DDR3 slots, so 3GB wasn't an option.

---

### Post by Grifulkin on 2010-01-27
```
             total       used       free     shared    buffers     cached
Mem:           998        169        828          0          0        101
-/+ buffers/cache:         67        930
Swap:          956          0        956

```

On my netbook running LXDE and Midori and a Terminal.

---

### Post by Grifulkin on 2010-01-27
```
             total       used       free     shared    buffers     cached
Mem:           998        169        828          0          0        101
-/+ buffers/cache:         67        930
Swap:          956          0        956

```

On my netbook running LXDE and Midori and a Terminal.

---

