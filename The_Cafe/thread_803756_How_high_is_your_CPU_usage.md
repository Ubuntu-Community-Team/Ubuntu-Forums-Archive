---
title: "How high is your CPU usage?"
date: 2008-05-22
forum: The Cafe
---

### Post by Ub1476 on 2008-05-22
Can be checked by running System Monitor, or in CLI:

```
top
```

```
sudo apt-get install htop
htop
```

htop is very good.

Mines 5% on a dual-core 2,4GHZ processor.

---

### Post by qazwsx on 2008-05-22
178.9/200 :)

---

### Post by Eisenwinter on 2008-05-22
Cycling between 2 - 5 for me, on an AMD Athalon XP 64bit 3800+, 2.4GHZ

---

### Post by buntunub on 2008-05-22
> **Ub1476 said:**
> Can be checked by running System Monitor, or in CLI:

```
top
```

```
sudo apt-get install htop
htop
```

htop is very good.

Mines 5% on a dual-core 2,4GHZ processor.

You need to be more specific with your post. At IDLE, my system uses almost no CPU. Under heavy loads, it uses more (duh!). What type of data are you trying to gather with this? 

*Do you want to know what people's CPU's are at under idle? Thats fine, but what about people who run just a single core with low RAM?.. What about people that run multiple cores and have alot of RAM?.. What about 64 bit systems? Do you want data on SPARC CPU's? Do you want data on CPU loads under Windows or MAC OSx?

*CPU loads under heavy conditions? Fine, then running what apps?.. Firefox 3b5?.. FF3b5+Compiz?.. 

*CPU's are finicky beasts. AMD acts differently than INTEL CPU's under certain conditions. Also, Bus Speeds and RAM type greatly affect CPU loading conditions as well, as does a 64 or 32 bit OS, under differing conditions - encoding being one prime example.

*CPU loads for how long? How long are we supposed to sample for to gather an average load under your conditions? For example, if the sample time is five minutes, and during that time (on a 64 bit OS) I am to encode a DVD, then my load average would be significantly different than if I were to encode the same DVD on a 32 bit OS. On Windows, under the same conditions, the data would also be much different.

Please do specify so that you can obtain useful data.

---

### Post by cookieforyou on 2008-05-22
I have an Intel Core2 Duo (E4500 @ 2.2 GHz) and one CPU peaks at about 5% and the other 2% (more or less) while posting here.  Thats on conky of course.
EDIT: While saving this message they seemed to peak at about 10% each.

---

### Post by Captain Oblivious on 2008-05-22
Going between 0% and 25% at the moment as I do different things.

---

### Post by Mhurst1 on 2008-05-22
Mine is at 6% with debian sid and kde 3.5.9.

---

### Post by NightwishFan on 2008-05-22
On Debian Lenny with kde, as long as I am not doing anything, (Music playing chat open and reading a forum post) it is always "100% idle". It barely goes over 10-20% to do anything like render a webpage or open a program.

---

### Post by Ub1476 on 2008-05-22
Not after any specific data. Just checking how good people take care of their CPUs;)

I suppose people are at least running Firefox if responding to this thread though.

---

### Post by Captain Oblivious on 2008-05-22
> **Ub1476 said:**
> Not after any specific data. Just checking how good people take care of their CPUs;)

I suppose people are at least running Firefox if responding to this thread though.

I'm running Firefox, along with several other programs at the moment.

---

### Post by NightwishFan on 2008-05-22
Konqueror, Amarok, Kget, Kopete, and a few programs/daemons like kpowersave and preload. Typing this and listening to Sandstorm JS16 Remix is using about 2-3% cpu. Generally I put it to good use with audio/video encoding though.

---

### Post by bufsabre666 on 2008-05-22
i ALWAYS have a torrent program running so to put my average usage it would have to be with that and its usually between 4-8%

---

### Post by nick09 on 2008-05-22
Strange I get around 30% usage on my parent's AMD Athlon 3200+ 64-bit.

Well the main reason is firefox is using 173 MB of ram(been browsing for 4 hours). Can I use the swap more somehow(so the computer uses less RAM)?

---

### Post by Rotarychainsaw on 2008-05-22
Run Boinc constantly, so 99% all the time lol.

---

### Post by EdThaSlayer on 2008-05-22
It fluctuates with me from 32.6% to 72.4% from time to time. So I guess 68.8% is my cpu usage.

---

### Post by vipergtsr on 2008-05-22
Im currently running a C2Q Q6600 @2.4GHz and 4GB of PC6400 800MHz Ram, :guitar: and somehow Im always using 100% of 1 of the cores(not always the same core) and 1% on the other 3 cores.
With Firefox 3 and pidgin, all the Ubuntu updates and the regular desktop (no animations), and when i run a virtualbox with Vista inside, 1 use 2 of the 4 cores at 100% and the other 2 at 1%, ram it uses about 512MBs with firefox and pidgin only or about 2.75GBs using virtualbox (2GB virtual ram for Vista)

How do you guys manage to run only 10% of the CPU with a dualcore???:confused:

Currently using Hardy Heron:KS

---

### Post by Bruce M. on 2008-05-22
Idle: 11%

Add Firefox and it goes between 20% and 60%

Frequently at 100% with a few apps open.

See sig and you'll know why.

---

### Post by freebeer on 2008-05-22
I run folding@home, so 100% on the single processor machine.  50% on the dual core (I only run one instance of F@H on each.)

---

### Post by kool_kat_os on 2008-05-22
0%-2% on Pentium 4 Hyper Threaded

---

### Post by Superkoop on 2008-05-22
About 0-5% running Firefox.(when using htop I automatically use 1.3% so I don't use htop, just the system monitor at on the task panel)
Specs:
Ubuntu 8.04 x86_64
GNOME 2.22.1
AMD Athlon(tm) 64 Processor 3200+
940 MB

---

### Post by NightwishFan on 2008-05-22
> **nick09 said:**
> Strange I get around 30% usage on my parent's AMD Athlon 3200+ 64-bit.

Well the main reason is firefox is using 173 MB of ram(been browsing for 4 hours). Can I use the swap more somehow(so the computer uses less RAM)?

You want your computer to use more ram.

---

### Post by DarkDancer on 2008-05-23
Right now I have Firefox and Deluge running on my single core AMD Athlon 64 3800+ Orleans 2.4GHz 512KB with L2 Cache. I also have fusion going pretty much full bore... ( ;) ) and I am running about 4%.

Oh, I always forget the background stuff, also running is Thunderbird, Amarok (though it's not playing) Pidgin, and that firewall thingie. 

If I start Amarok playing, it runs between 5 and 8% once it settles down.

---

### Post by Trail on 2008-05-23
About 6-10% when idleing on a Core2 2.2Ghz. Which includes 6 workspaces open with various stuff (firefox, kdevelop, pdfs, kate, mails, terminals etc)

---

### Post by ksennin on 2008-05-23
I am using now Xubuntu on a refurbished Pentium3-667mhz dell gx110, with 512mb ram, so my cpu hits 100% all the time. Minimum use is 17% with firefox open (couple of tabs).  AS I normally have several firefox tabs open+deluge+rapget in wine+vlc playing some mp3s, 75-100% is the active range.  Swappiness has dwindled to zero lately, thanks to the recent boost in ram.

---

