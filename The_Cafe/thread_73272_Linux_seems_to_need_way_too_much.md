---
title: "Linux seems to need way too much"
date: 2005-10-08
forum: The Cafe
---

### Post by Cirkus on 2005-10-08
I'm going to wait a day or two before making a final decision; but I'm getting pretty disgruntled with Linux. 

I have a newer computer with 256 megs of ram, and while doing normal tasks (web surfing, file browsing, the occasional edit in GIMP) in GNOME it's consistently hitting ~450 megs of swap. That's far too much, particularly compared to XP (which, at most, only hits 300 megs and even then only when I run memory intensive games or 3d apps).

The performance is crap because of this. It's not acceptable. Particularly to someone who remembers the days of Linux 2.0/2.2 when linux was something that "might not support new hardware, but runs great on older machines!" (No WAY would I put 2.6 on anything less than a p3.)

If I this keeps up, I'll try GNOME under FreeBSD 5.4 (it's been my experience that BSD handles swap pretty good, so it may be better than Linux at this point); and if that doesn't work, I'll just stick to XP.

Browsing files and the web shouldn't eat 450 megs of swap; if that's GNOME, then I can tell you right there why Unix will stay in the server room.

---

### Post by BWF89 on 2005-10-08
Why don't you try Xfce or Fluxbox? I'm pretty sure they are less resource intensive than KDE or Gnome.

---

### Post by GeneralZod on 2005-10-08
This is interesting; I'm often complaining about the memory usage, but I've never gone about 250MB swap (on my 256MB laptop).  I use KDE, by the way, with Kontact (a full-blown PIM suite), Firefox with at least 20 tabs open, Konversation, Konsole with 5 tabs, Kompose, Kopete, Kate with the FreeCiv source being edited, and random other stuff running.

And yes, I'd imagine it's the DE's that are causing the bloat; the kernel itself is *tiny*.  You'll see the same result under the *BSDs.

As BWF89 said, lighter DE's/ WM's make a huge difference.  Using Opera instead of Firefox, the same.

I'm also confused as to why you think OS X should stay in the server room (it has just as much claim to the title of "Unix" as Linux does, and is comparably memory-hungry).  I guess there's no accounting for taste! :)

PS 

You can actually tune the swappiness at run-time; see e.g. [here](http://kerneltrap.org/node/3000).

---

### Post by bugi on 2005-10-08
[QUOTE=Cirkus]Browsing files and the web shouldn't eat 450 megs of swap[/QUOTE]

It doesn't. Linux with KDE, Gnome on 256mb machine should not use swap at all (ok, maybe sometimes but not more than few mb). It has to be some problem with hardware, wrong configuration or something like that.

---

### Post by Cirkus on 2005-10-08
[QUOTE=BWF89]Why don't you try Xfce or Fluxbox? I'm pretty sure they are less resource intensive than KDE or Gnome.[/QUOTE]

XFCE is quite nice (I've used it under BSD), but it's not what I want. If I were to downgrade from a DE, I'd probably go for Windowmaker, but it's starting to show its' age (stylistically speaking).

---

### Post by Cirkus on 2005-10-08
[QUOTE=bugi]It doesn't. Linux with KDE, Gnome on 256mb machine should not use swap at all (ok, maybe sometimes but not more than few mb). It has to be some problem with hardware, wrong configuration or something like that.[/QUOTE]

That is what I was thinking; but other than some surface changes (installing a mac like theme for GTK and tweeking around with the panels) I really haven't done that much **to** misconfigure. I thought it was odd too, which is why I'm not throwing it out right away (I'm going to try to figure out WTF, **then** throw it out if I can't fix it).

---

### Post by Stormy Eyes on 2005-10-08
[QUOTE=Cirkus]XFCE is quite nice (I've used it under BSD), but it's not what I want. If I were to downgrade from a DE, I'd probably go for Windowmaker, but it's starting to show its' age (stylistically speaking).[/QUOTE]

If you've got the *cojones*, try E17. You could also try blackbox or openbox. Don't even think of using fluxbox; it's a mishmash.

---

### Post by Cirkus on 2005-10-08
[QUOTE=Stormy Eyes]If you've got the *cojones*, try E17.[/QUOTE]

I don't have them; enlightenment has always given me a screaming headache :p

---

### Post by poofyhairguy on 2005-10-08
Install XFCE. Run these programs one after the other in the run dialog:

> gnome-panel

gnome-volume-manager

nautilus

move the XFCE panel off to the side an make it autohide (or killall xfce4-panel).

There. XFCE will now act like Gnome in almost every way except it will use less RAM.

What you describe in a problem with Gnome. Yes Gnome ahs RAM problems- Breezy goes a long way to fix that. But its Gnome's fault, not Linux's.

---

### Post by Omnios on 2005-10-08
Ram in Linux may be slightly decieving. I learn't quite a bit about how Linux handles ram or rather shows it playing around with Kuramba dock apps. Counting on what sensor you are using it may show Used memory in megabytes + cache and "buffers" giving a very high total. Apperently this also holds true for buffer as  to why it would buffer and  cach in swap that I would like explained. Aslo if you are running a dock app that could take up a lot of resources counting on whay particular app you are using. I   think aa more  usefull measurment would be over all perfomance Gnome and even KDE totaly smokes WinXP.

---

### Post by Cirkus on 2005-10-08
[QUOTE=poofyhairguy]Install XFCE. Run these programs one after the other in the run dialog:



move the XFCE panel off to the side an make it autohide (or killall xfce4-panel).

There. XFCE will now act like Gnome in almost every way except it will use less RAM.

What you describe in a problem with Gnome. Yes Gnome ahs RAM problems- Breezy goes a long way to fix that. But its Gnome's fault, not Linux's.[/QUOTE]

Ok, I'll fire that up into a shell script ( I'm assming I can do 'killall xfce4-panel' as a literal command) and see how it goes.

Thanks! :)
[QUOTE=Omnios]Ram in Linux may be slightly decieving. I learn't quite a bit about how Linux handles ram or rather shows it playing around with Kuramba dock apps. Counting on what sensor you are using it may show Used memory in megabytes + cache and "buffers" giving a very high total. Apperently this also holds true for buffer as  to why it would buffer and  cach in swap that I would like explained. Aslo if you are running a dock app that could take up a lot of resources counting on whay particular app you are using. I   think aa more  usefull measurment would be over all perfomance Gnome and even KDE totaly smokes WinXP.[/QUOTE]
So far, Linux has been digging deep into my swap space and performance has turned to crud while I have to wait for redraws and swap read/writes. XP performance degrades over time but that's **expected** with XP; not with Linux.

I will try poofyhairguy's suggestion, though; and see how that works. :cool:

---

### Post by Kvark on 2005-10-08
There must be something wrong with your configuration. I got gnome with a nice theme and a couple programs running, 157MB ram and 2.8MB swap is used in total atm. That must be bad for all the people with 128MB ram but it should run like lightning on 256MB and at least an average CPU.

But there really is something funky about how memory usage is reported on a linux system. If I add up how much memory all my proccesses are using then they use 540MB memory. I wish it would report only the amount of memory that would be freed if the process in question was killed instead of all memory it shares with other processes.

---

### Post by cowlip on 2005-10-08
Does gimp store a lot of things in the swap?

---

### Post by -Rick- on 2005-10-08
[QUOTE=Cirkus]I'm going to wait a day or two before making a final decision; but I'm getting pretty disgruntled with Linux. 

I have a newer computer with 256 megs of ram, and while doing normal tasks (web surfing, file browsing, the occasional edit in GIMP) in GNOME it's consistently hitting ~450 megs of swap. That's far too much, particularly compared to XP (which, at most, only hits 300 megs and even then only when I run memory intensive games or 3d apps).

The performance is crap because of this. It's not acceptable. Particularly to someone who remembers the days of Linux 2.0/2.2 when linux was something that "might not support new hardware, but runs great on older machines!" (No WAY would I put 2.6 on anything less than a p3.)

If I this keeps up, I'll try GNOME under FreeBSD 5.4 (it's been my experience that BSD handles swap pretty good, so it may be better than Linux at this point); and if that doesn't work, I'll just stick to XP.

Browsing files and the web shouldn't eat 450 megs of swap; if that's GNOME, then I can tell you right there why Unix will stay in the server room.[/QUOTE]
In my experience Gnome doesn't play nice with ram...the same with Firefox.
For me KDE+Opera works better(I have 256 mb ram too). And yes FreeBSD will make things better too :)

---

### Post by drizek on 2005-10-08
[QUOTE=Cirkus]XFCE is quite nice (I've used it under BSD), but it's not what I want. If I were to downgrade from a DE, I'd probably go for Windowmaker, but it's starting to show its' age (stylistically speaking).[/QUOTE]

why not upgrade to KDE then?

it uses less memory than gnome and it runs great on my old desktop with 192mb ram and integrated gfx. 

right now, im using my new desktop with kde,opera and amarok running and it is using about 180mb of actual memory(total of 400mb of cache, which wouldnt transfer over to swap if you run out of ram AFAIK). no swap is being used at all.

Edit:btw, on this same machine which has a gig of ram, windows xp uses 200mb of swap with just a web browser open.

---

### Post by Kyral on 2005-10-08
Yah, RAM info on Linux is very sketchy. I mean if I'm on IRC and I fire my sysinfo script it says I'm using 400 out of 512 MB. Yet at the same time I have GNOME System Monitor up and it says I'm using 184 MB RAM and maybe 2 MB swap...

---

### Post by drizek on 2005-10-08
thats because you are using 184mb of application data and the rest is just cache. once your ram starts running out, all that cache will be removed and replaced with application data. it will not be moved to swap. 

the "real" amount of ram you are using is still just 184mb.

---

### Post by -Rick- on 2005-10-08
Good info about linux memory managment: [http://forums.gentoo.org/viewtopic-t-175419-highlight-ram+usage.html](http://forums.gentoo.org/viewtopic-t-175419-highlight-ram+usage.html)

---

### Post by blastus on 2005-10-08
[QUOTE=-Rick-]Good info about linux memory management: [http://forums.gentoo.org/viewtopic-t-175419-highlight-ram+usage.html](http://forums.gentoo.org/viewtopic-t-175419-highlight-ram+usage.html)[/QUOTE]

Thanks for this link. A while ago I was trying to explain (in my own extremely limited amount of knowledge about this) to some morons on a Windows forum that Linux uses memory differently than Windows. They claimed that unless you have 512Mb of RAM, you can't run KDE, GNOME, and even Enlightment with acceptable performance. One guy even said he was an "administrator" who was responsible for overseeing all kinds of Linux machines running all kinds of desktop environments and based on his profound experience ALL the machines with less than 512Mb running Linux performed so slowly that they were basically unusable.

---

### Post by Cirkus on 2005-10-08
there's a difference between what utilities such as top report as being free, and what is actually available (and where it is coming from). 

Personally speaking, this is not my problem. My problem is that GNOME causes Linux to hit the swap like mad, and my system slows down to the point of being unusable. 

I'm trying out KDE, but I'm not liking it (most of the apps I use are gtk apps, and kde gives them a tiny, tiny font by default. :().

---

### Post by drizek on 2005-10-08
learn to use kde apps then. they are equal to or better than gnome ones. you will just have to get used to it. 

that said, gnome shouldnt be performing so badly. ive had it on 512mb systems before and it ran just fine.

---

### Post by Cirkus on 2005-10-08
[QUOTE=drizek]learn to use kde apps then. they are equal to or better than gnome ones. you will just have to get used to it. 

that said, gnome shouldnt be performing so badly. ive had it on 512mb systems before and it ran just fine.[/QUOTE]
I don't have to get used to kde as long as their are alternatives (gnome under BSD, or windows xp)

I have half that amount of ram; it makes a huge difference (apparently).

---

### Post by Efwis on 2005-10-08
actually makes me wonder if you have a different program running somewhere with a memory leak. I know memory leaks can make it seem like you are running more ram hence looks like you are using more swap then you actually are. 

Are you running any other programs at the same time that you are seeing this problem?

---

### Post by Omnios on 2005-10-08
KDE is a bit strange at first you realy have to play with it for a week or so to apreciate it.
 I realy wasn't all that impressed at first but with a few changes to desktop settings I found it rather pleasant to use and not a single crash as advertised lol. Basicly it does alot as a wm and is still fast on 1.6ghz P4 R with 256megs ram. Id still be using Gnome if it wasn't for the ram aand vidcard problems though :(my vid card bites) 

Other than click a icon to install I can say I prefer  it  over win xp, all the functionality but runs a hell of a lot faster.

---

### Post by aysiu on 2005-10-08
Can you post what pops up when you type ```
top
``` in a terminal? For example, mine says ```
top - 18:43:17 up 36 min,  1 user,  load average: 0.56, 0.82, 1.19
Tasks:  82 total,   1 running,  81 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.7% us,  0.7% sy,  0.0% ni, 92.7% id,  2.7% wa,  0.3% hi,  0.0% si
Mem:    451852k total,   428116k used,    23736k free,   117412k buffers
Swap:  1060248k total,    12476k used,  1047772k free,   104020k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8403 root      15   0  104m  22m 3536 S  2.3  5.1   0:50.42 Xorg
 8894 user     15   0 29708  16m  12m S  2.0  3.7   0:00.37 konsole
    1 root      16   0  1560  532  460 S  0.0  0.1   0:00.92 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.11 events/0
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  110 root      10  -5     0    0    0 S  0.0  0.0   0:03.70 kblockd/0
  138 root      15   0     0    0    0 S  0.0  0.0   0:00.02 pdflush
  139 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  141 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  140 root      15   0     0    0    0 S  0.0  0.0   0:00.53 kswapd0
  726 root      15   0     0    0    0 S  0.0  0.0   0:00.02 kseriod
  965 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0
 2414 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khubd
 2477 root      25   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
 2478 root      15   0     0    0    0 S  0.0  0.0   0:00.18 usb-storage

``` That's with Thunderbird, Firefox, and the terminal running.

---

### Post by Cirkus on 2005-10-08
[QUOTE=Efwis]

Are you running any other programs at the same time that you are seeing this problem?[/QUOTE]
The only culprits I can think of are:
**tdfsb** (a 3d file browser, I don't use it that much; but I know it's a hog)
**nautilus** (I think it may not free up memory after looking at a directory with tons of images in it)
**firefox** (a known memory problem :/)
**firestarter** (I don't know what kind of memory it uses or not, but I've noticed it seems to turn off by itself and I have no idea why).

gimp really isn't (or shouldn't be) a factor since I just load it, do a quick edit on an image and then close it.

---

### Post by Cirkus on 2005-10-08
[QUOTE=aysiu]Can you post what pops up when you type ```
top
``` in a terminal? [/QUOTE]
I logged out of KDE and I'm browsing here and browsed with the nautilus file browser (but not with tdfsb, obviously). At the moment I'm only 100 megs into my swap, I expect that to go up in a few hours of normal use, though. Here's what top shows:```

top - 19:20:03 up  1:47,  3 users,  load average: 0.52, 0.77, 0.73
Tasks:  96 total,   1 running,  94 sleeping,   0 stopped,   1 zombie
Cpu(s):  2.6% us,  2.8% sy,  0.0% ni, 94.4% id,  0.0% wa,  0.0% hi,  0.2% si
Mem:    255976k total,   251520k used,     4456k free,     6336k buffers
Swap:  1534196k total,   103212k used,  1430984k free,    80324k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6330 root      15   0  111m  22m 9036 S  4.2  9.0   4:21.77 Xorg
 8771 cirkus    15   0 38712  14m 9444 S  0.9  5.6   0:01.38 gnome-terminal
 7558 cirkus    15   0 13608 7104 5788 S  0.2  2.8   0:04.31 metacity
    1 root      16   0  1564  420  396 S  0.0  0.2   0:00.88 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.24 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.21 events/0
    4 root      14  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    5 root      19  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
   22 root      10  -5     0    0    0 S  0.0  0.0   0:00.19 kblockd/0
   68 root      15   0     0    0    0 S  0.0  0.0   0:00.03 pdflush
   69 root      15   0     0    0    0 S  0.0  0.0   0:00.11 pdflush
   71 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
   70 root      15   0     0    0    0 S  0.0  0.0   0:00.29 kswapd0
  657 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kseriod
 1857 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khubd
 1953 root      25   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
 1954 root      15   0     0    0    0 S  0.0  0.0   0:01.08 usb-storage

```

---

### Post by Efwis on 2005-10-08
from that it looks like you have a config issue.  Xorg is taking all your memory.

here is what my sys is looking like with ff open and terminal running. look at my Xorg compared to yours, and I'm running 512mb of Ram, it isn't touching my swap at all.

```
top - 22:14:39 up  2:21,  2 users,  load average: 0.06, 0.11, 0.09
Tasks:  75 total,   2 running,  73 sleeping,   0 stopped,   0 zombie
Cpu(s): 21.0% us,  1.0% sy,  0.0% ni, 78.0% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    516500k total,   354496k used,   162004k free,    19060k buffers
Swap:   265032k total,        0k used,   265032k free,   159540k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8396 edward    15   0  143m  82m  20m S 12.3 16.3   6:45.57 firefox-bin
 6877 root      16   0  109m  24m 6960 R  5.3  4.8   2:24.30 Xorg
 8812 edward    15   0 30008  12m 8268 S  2.7  2.5   0:00.98 gnome-terminal
 8356 edward    15   0 17500 9976 7668 S  0.7  1.9   0:03.11 wnck-applet
 8824 edward    16   0  2080 1040  820 R  0.7  0.2   0:00.47 top
 8019 edward    16   0 17392 8984 6956 S  0.3  1.7   0:00.98 x-session-manag
 8120 edward    15   0  7724 2716 2160 S  0.3  0.5   0:00.73 gnome-smproxy
 8122 edward    15   0 12652 7100 5648 S  0.3  1.4   0:03.39 metacity
 8126 edward    15   0 28112  12m 8980 S  0.3  2.5   0:03.10 gnome-panel
 8347 edward    16   0 16164 8192 6512 S  0.3  1.6   0:17.21 multiload-apple
    1 root      16   0  1552  508  444 S  0.0  0.1   0:00.52 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root       5 -10     0    0    0 S  0.0  0.0   0:00.07 events/0
    4 root      12 -10     0    0    0 S  0.0  0.0   0:00.01 khelper
   22 root      15 -10     0    0    0 S  0.0  0.0   0:00.00 kacpid
  111 root       5 -10     0    0    0 S  0.0  0.0   0:00.04 kblockd/0
  149 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush




```
You might want to take a look at your Xorg config and see what it might be.

---

### Post by Wide on 2005-10-08
As earlier stated, Linux uses memory on a reserved basis, memory is released by sleeping processes if need elsewhere.

You need to measure active process memory usage not 'top',  'ps', 'free' etc

There is a real good article on it [here](http://www.kdedevelopers.org/node/1445)


:cool:

---

### Post by Cirkus on 2005-10-08
[QUOTE=Efwis]from that it looks like you have a config issue.  Xorg is taking all your memory.

here is what my sys is looking like with ff open and terminal running. look at my Xorg compared to yours, and I'm running 512mb of Ram, it isn't touching my swap at all.

```
top - 22:14:39 up  2:21,  2 users,  load average: 0.06, 0.11, 0.09
Tasks:  75 total,   2 running,  73 sleeping,   0 stopped,   0 zombie
Cpu(s): 21.0% us,  1.0% sy,  0.0% ni, 78.0% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    516500k total,   354496k used,   162004k free,    19060k buffers
Swap:   265032k total,        0k used,   265032k free,   159540k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8396 edward    15   0  143m  82m  20m S 12.3 16.3   6:45.57 firefox-bin
 6877 root      16   0  109m  24m 6960 R  5.3  4.8   2:24.30 Xorg
 8812 edward    15   0 30008  12m 8268 S  2.7  2.5   0:00.98 gnome-terminal
 8356 edward    15   0 17500 9976 7668 S  0.7  1.9   0:03.11 wnck-applet
 8824 edward    16   0  2080 1040  820 R  0.7  0.2   0:00.47 top
 8019 edward    16   0 17392 8984 6956 S  0.3  1.7   0:00.98 x-session-manag
 8120 edward    15   0  7724 2716 2160 S  0.3  0.5   0:00.73 gnome-smproxy
 8122 edward    15   0 12652 7100 5648 S  0.3  1.4   0:03.39 metacity
 8126 edward    15   0 28112  12m 8980 S  0.3  2.5   0:03.10 gnome-panel
 8347 edward    16   0 16164 8192 6512 S  0.3  1.6   0:17.21 multiload-apple
    1 root      16   0  1552  508  444 S  0.0  0.1   0:00.52 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root       5 -10     0    0    0 S  0.0  0.0   0:00.07 events/0
    4 root      12 -10     0    0    0 S  0.0  0.0   0:00.01 khelper
   22 root      15 -10     0    0    0 S  0.0  0.0   0:00.00 kacpid
  111 root       5 -10     0    0    0 S  0.0  0.0   0:00.04 kblockd/0
  149 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush




```
You might want to take a look at your Xorg config and see what it might be.[/QUOTE]
I'm pretty far from being an expert. I'm using the (closed) nvidia drivers so I'll try switching back to the native xorg 'nv' driver. Maybe that will help?

---

### Post by Efwis on 2005-10-08
I too am far from an expert, but its someplace to look. which Nvidia driver are you using? I know they just came out with a new one not too long ago.

---

### Post by Cirkus on 2005-10-09
[QUOTE=Efwis]I too am far from an expert, but its someplace to look. which Nvidia driver are you using? I know they just came out with a new one not too long ago.[/QUOTE]
I'm not sure; it's the one that I installed after reading the how-to on ubuntuguides.org.

---

### Post by Cirkus on 2005-10-09
Ok, this is how top looks after running gnome for a while (I have the listing sorted by resident memory)> top - 22:06:40 up  2:09,  2 users,  load average: 0.45, 0.24, 0.26
Tasks: 109 total,   1 running, 108 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.6% us,  1.0% sy,  0.0% ni, 93.4% id,  0.0% wa,  0.0% hi,  
0.0% si
Mem:    255976k total,   251732k used,     4244k free,     4368k buffers
Swap:  1534196k total,   161712k used,  1372484k free,    71740k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8982 root      15   0  204m  65m 7776 S  2.3 26.1   2:18.36 Xorg
 9174 cirkus    16   0  123m  49m  16m S  0.0 19.7   2:49.91 firefox-bin
10493 root      15   0 36824  24m  14m S  0.0  9.8   0:16.76 synaptic
 9113 cirkus    16   0 26860  14m 8956 S  0.0  5.8   0:06.10 gnome-panel
11468 cirkus    15   0 31052  13m 8544 S  2.7  5.2   0:00.60 gnome-terminal
 9115 cirkus    16   0 30156  10m 8400 S  0.0  4.1   0:01.87 nautilus
 9317 root      15   0 19792 9960 7788 S  0.0  3.9   0:02.00 firestarter
 9160 cirkus    15   0 19376 9508 7712 S  0.0  3.7   0:11.96 wnck-applet
 9163 cirkus    15   0 19500 9232 7552 S  0.0  3.6   0:00.68 trashapplet
10737 cirkus    16   0 24288 9112 3444 S  0.0  3.6   0:00.11 gpbs
 9123 cirkus    16   0 18320 7684 6820 S  0.0  3.0   0:00.53 update-notifier
 9169 cirkus    16   0 22316 7636 6676 S  0.0  3.0   0:00.54 clock-applet
 9108 cirkus    15   0 13852 7568 6028 S  1.3  3.0   0:17.65 metacity
 9167 cirkus    15   0 19516 7316 6668 S  0.0  2.9   0:00.56 mixer_applet2
 9303 cirkus    15   0 26584 7020 6240 S  0.0  2.7   0:01.16 gaim
 9009 cirkus    15   0 18500 6540 6136 S  0.0  2.6   0:00.59 gnome-session
 9165 cirkus    15   0 17496 6240 5676 S  0.0  2.4   0:00.28 notification-ar



It apparently is a combination of 
a)xorg
b)firefox
c)a million and one memory chompin' (gnome-terminal takes 13 megs. wow.) gnome widgets

Since I can't figure out xorg.conf, I'm going to have to drop gnome and switch to another wm (probably window maker or xfce). 

Thanks to everyone for your help and advice!

---

