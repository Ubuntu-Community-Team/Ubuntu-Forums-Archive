---
title: "Is nobody else using gnome-shell seeing ram figures like these?"
date: 2012-03-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Quackers on 2012-03-21
Really? Any ideas?
The system has an uptime of 19 hours. On reboot ram use is 114M for GS and total use is about 300M.
At the time this screenshot was taken I had nothing running except for 1 Firefox tab.

---

### Post by keithpeter on 2012-03-21
Hello Quackers

I'll leave my box on overnight and see what I get.

Gnome-shell is unusable for me at present because of the freezes when scrolling in LibreOffice docs.

I'm using stock 12.04 install updated to today with gnome-shell added, and an nvidia GT520 card with the proprietary drivers that Jockey installs. I have no ppas installed. Its an i386 system.

Are you on 64bit or i386?

Cheers

---

### Post by Quackers on 2012-03-21
64 bit here, no extra ppa's enabled. Video card as below.
I've been using GS from the start, as I prefer it to unity. I don't have cause to use Libreoffice as such, so am unaware of any problems in that area.
Gnome-shell is fine here apart from the mysterious ram use/leak (if that's what it is).

---

### Post by keithpeter on 2012-03-21
> **Quackers said:**
> 64 bit here, no extra ppa's enabled. Video card as below.
I've been using GS from the start, as I prefer it to unity. I don't have cause to use Libreoffice as such, so am unaware of any problems in that area.
Gnome-shell is fine here apart from the mysterious ram use/leak (if that's what it is).


Hello Quackers

Steps to reproduce

[LIST]
[*]Load LibreOffice and make a two or three page document by typing random stuff and adding a few pictures
[*]Scroll up and down the document quickly
[*]Await a total freeze (mouse arrow stuck, can't Alt-F2, can't log out)
[*]Escape by doing a Ctrl-Alt-F1 to get a tty then log in and sudo reboot, or by using the Shift-Alt-Printscreen chords
[/LIST]

I'll try on i386 first, then if no leaks, I'll try a usb boot into 64bit

Cheers

---

### Post by screaminj3sus on 2012-03-21
Gnome-shell is known to have memory leak issues, but they were supposed to be mostly fixed in gnome 3.2.

---

### Post by keithpeter on 2012-03-21
> **screaminj3sus said:**
> Gnome-shell is known to have memory leak issues, but they were supposed to be mostly fixed in gnome 3.2.

Hello screamin'

I had no issues at all like this with gs3.2 but I'll do a good 12 hours uptime with 3.3.x and see what happens.

---

### Post by Quackers on 2012-03-21
> **keithpeter said:**
> Hello Quackers

Steps to reproduce

[LIST]
[*]Load LibreOffice and make a two or three page document by typing random stuff and adding a few pictures
[*]Scroll up and down the document quickly
[*]Await a total freeze (mouse arrow stuck, can't Alt-F2, can't log out)
[*]Escape by doing a Ctrl-Alt-F1 to get a tty then log in and sudo reboot, or by using the Shift-Alt-Printscreen chords
[/LIST]

I'll try on i386 first, then if no leaks, I'll try a usb boot into 64bit

Cheers

keithpeter, I can't get it to freeze.
I created a 3 page document with 2 pictures in it and have been scrolling up and down like a madman! Nothing. Still working perfectly here :) 
This is on 64 bit though, not 32.

---

### Post by keithpeter on 2012-03-21
> **Quackers said:**
> keithpeter, I can't get it to freeze.
I created a 3 page document with 2 pictures in it and have been scrolling up and down like a madman! Nothing. Still working perfectly here :) 
This is on 64 bit though, not 32.

Hello Quackers, Screamin' and all

Well, you know, no freezing here either at present since today's updates, I'm scrolling 50 page documents with hundreds of formulas and dozens of screenshots. Might be sorted.

Thanks

---

### Post by Quackers on 2012-03-21
That's good then :-)
Let's hope so.

---

### Post by keithpeter on 2012-03-22
Hello Quackers and all

8 hours overnight with no actual activity gives this...

```
2122 Wednesday 21st

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
1643 keith     20   0  534m 111m  41m S   11  2.8   0:32.91 gnome-shell  

0639 Thursday 22nd

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
1643 keith     20   0 1037m 529m  43m S    3 13.1  17:15.45 gnome-shell
```

...so I think the memory leak is still in Gnome Shell, at least in 3.3.90-0ubuntu1

I'll update in a bit

---

### Post by kansasnoob on 2012-03-22
I get about the same thing with 64 bit and 2 GB of RAM. It starts out fine but after several hours memory usage is ridiculous:

[http://ubuntuforums.org/showthread.php?t=1890522](http://ubuntuforums.org/showthread.php?t=1890522)

I have no problem with i386 so that's what I use.

Edit: It doesn't matter what DE I use, even Lubuntu acts the same way so it's a 64 bit thing for me.

---

### Post by keithpeter on 2012-03-22
> **kansasnoob said:**
> I get about the same thing with 64 bit and 2 GB of RAM. It starts out fine but after several hours memory usage is ridiculous:

[http://ubuntuforums.org/showthread.php?t=1890522](http://ubuntuforums.org/showthread.php?t=1890522)

I have no problem with i386 so that's what I use.

Edit: It doesn't matter what DE I use, even Lubuntu acts the same way so it's a 64 bit thing for me.

Hello kansasnoob

My post above was on i386. Other memory use is normal, no issues with Unity, just gnome-shell.

---

### Post by jbicha on 2012-03-22
Could you give gnome-shell 3.3.92 a try? It was uploaded a few hours ago.

---

### Post by Quackers on 2012-03-22
Thanks guys.
Interestingly last night I re-installed from beta1 (64 bit again) and after running all night gnome-shell shows as using only 64MB. That's less than it was using right after startup :-)
On opening a FF page system monitor shows gnome-shell as using 114MB. I'll use it for a while and watch the figures.
kansasnoob I agree that it may not actually be GS using all the ram as sometimes there is serious cpu usage going on while the system is at idle (or there was in the older install).
We'll see.

---

### Post by Quackers on 2012-03-22
> **jbicha said:**
> Could you give gnome-shell 3.3.92 a try? It was uploaded a few hours ago.

Thanks jbicha, I'm updating now :-)

---

### Post by Quackers on 2012-03-22
Hmm, during the update all the window borders went awol, so I'm thinking GS crashed, or at least had a problem.
Actually, thinking about it, it seems to me that GS's crashing/stalling seems to be when something is using a lot of cpu activity. 
After updating GS to 3.3.92 system monitor shows it as using 95.9MB at the moment. I'll report back later.

---

### Post by dino99 on 2012-03-22
I'm not using GS but gnome-classic on i386, and today i get a whole system freeze: cant get menu, cant switch workplaces, cant get system monitor. Need to reset the session. This have happened while running an app via wine1.4

So one of the latest updates (packages recently uploaded, says in the last 8 hours from main server) have introduced this regression.
sadly nothing usefull got logged.

---

### Post by keithpeter on 2012-03-22
> **dino99 said:**
> I'm not using GS but gnome-classic on i386, and today i get a whole system freeze: cant get menu, cant switch workplaces, cant get system monitor. Need to reset the session. This have happened while running an app via wine1.4

So one of the latest updates (packages recently uploaded, says in the last 8 hours from main server) have introduced this regression.
sadly nothing usefull got logged.

Hello dino99

That is the kind of freeze I was having with largeish documents in LibreOffice. Where were you looking for the logs?

I'll do today's upgrade and leave it on again to see how the new version goes with the memory.

---

### Post by Quackers on 2012-03-22
I just took a screenshot and it crashed GS momentarily :-(
After GS came back it was using less ram :-)

---

### Post by lucazade on 2012-03-22
updated to latest version.. still some random hard freeze, mem usage is around 100mb and
 when the gshell session is loading the wallpaper appears shifted for some seconds (didn't happen with old gshell releases)

---

### Post by Quackers on 2012-03-22
Hmm I didn't see that, though I may be having some conky display issues - could be related perhaps. I'll reboot and watch carefully :-)

---

### Post by Quackers on 2012-03-22
My desktop was slightly mis-placed for just a second or so. No chance of a screenshot though - not long enough.
Approximately 90 minutes in to the new GS and ram usage seems much more stable now. Just one teeny crash so far. More of a hiccup than a crash really.

---

### Post by hotstovejer on 2012-03-22
I recall there being something about gnome-screensaver causing huge spikes in ram usage, because it happened to me. Right now, gs is using 77 mb of ram. Gnome-terminal and Chromium open. 64 bit updated 12.04 with 2 gb of ram and a Radeon 4350.

---

### Post by lucazade on 2012-03-22
> **Quackers said:**
> My desktop was slightly mis-placed for just a second or so. No chance of a screenshot though - not long enough.
Approximately 90 minutes in to the new GS and ram usage seems much more stable now. Just one teeny crash so far. More of a hiccup than a crash really.

desktop misplacement is due to nautilus desktop drawing.. it is reproducible via gnome-tweak-tool: 
"Have file manager handle the desktop"

---

### Post by Quackers on 2012-03-22
> **lucazade said:**
> desktop misplacement is due to nautilus desktop drawing.. it is reproducible via gnome-tweak-tool: 
"Have file manager handle the desktop"
That's what it's set at lucazade.
The desktop mis-placement is only very fleeting and just as the desktop loads. It's fine after a second.

---

### Post by Quackers on 2012-03-22
10 hours uptime now and GS is only using 111M of ram, so problem seems solved.
Thanks all :-)

---

### Post by cmccauley on 2012-03-23
> **Quackers said:**
> 10 hours uptime now and GS is only using 111M of ram, so problem seems solved.
Thanks all :-)

My GS (3.3.92) runs for days between reboots without any issues. Currently using 206M (down from 215M earlier). I think that's a lot but hadn't noticed it, wasn't worried about it but now that you guys have pointed it out - I'M ANGRY AS HELL!

Well, no not really, it is excessive but that's around 10% of resident memory. I guess it's all that Javascript goodness that has bloated it.

Chris

---

### Post by keithpeter on 2012-03-23
Hello All

Fine on i386 as well with yesterday's updated gnome-shell, package 3.3.92-0ubuntu1. Thanks to devs for squashing this one.

Now to see if I can provoke the freezing I was seeing with the previous version.

```
Thursday 22nd March 23:11
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1619 keith     20   0  544m 113m  45m S   16  2.8   0:15.81 gnome-shell  

Friday 23rd March 07:14

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1619 keith     20   0  559m 128m  45m S    6  3.2   1:20.87 gnome-shell
```

@cmccauley: Above with no extensions at all, and just with Firefox. What are you running when you see 200+ Mb of ram on Gnome Shell?

---

### Post by Quackers on 2012-03-23
Hmm, it seems that Xorg is now using 3 times the ram it used to :-)

---

