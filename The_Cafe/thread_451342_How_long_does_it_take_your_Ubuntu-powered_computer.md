---
title: "How long does it take your Ubuntu-powered computer to boot up?"
date: 2007-05-22
forum: The Cafe
---

### Post by loathsome on 2007-05-22
It takes around one minute for my Vaio laptop. It's really fast, I have even stopped using hibernate / suspension; I just turn it off (saves much more battery). One thing is for sure, it's a lot faster than my C2D @ 3.4GHz desktop running Vista. It takes from 2-5 minutes for that to boot up.

You can still vote if you're not using Ubuntu, but please specify which OS you're running then.

---

### Post by gnomeuser on 2007-05-22
I dunno.. 30 secs or so from grub to gdm is fully loaded. It's dead fast.

---

### Post by argie on 2007-05-22
I'm using the older init scripts, Dapper you see, it takes something like a minute 30 to two.

---

### Post by ThinkBuntu on 2007-05-22
30-40 seconds. For comparison's sake, Arch took about 20 once I tweaked the Daemons (no /etc/rc.conf file in Ubuntu. I'm lost!), 30 in Zenwalk, and 30-40 for just about everything I've tried. Sabayon and openSUSE took nearly a minute, and Mandriva took no less than 45 seconds.

---

### Post by Sunflower1970 on 2007-05-22
Probably about a minute, maybe more on the 2 P4's. Just over 2 minutes with the PII :D

---

### Post by godd4242 on 2007-05-22
Hah guess I'm the oddball here.

3-5 minutes to from when I hit the power button to when GNOME is completely loaded.

512mb RAM and a 1.76 ghz processor; anyone any ideas on why its so slow?

PS: XP SP2 took about 2 minutes to boot to desktop on this same laptop.

---

### Post by Spr0k3t on 2007-05-22
```
           |  XP |  Linux  |       Specs
- - - - - -+- - -+- - - - -+- - - - - - - - - - - - - - -
Primary    |  09 |    23   | AMD 4600 FX64 X2 2.6GHz 2GB +RAID 1
Secondary  |  11 |    25   | C2D 6300 2.3GHz 2GB
Laptop 1   |  35 |    41   | P-D 2GHz 2GB
Laptop 2   |  73 |   114   | P3 800MHz 512MB

```

Times are in seconds.  I haven't really done much to optimize the boot time on the Linux installs, but I'm sure I could get them down much further.

---

### Post by loathsome on 2007-05-22
> **godd4242 said:**
> Hah guess I'm the oddball here.

3-5 minutes to from when I hit the power button to when GNOME is completely loaded.

512mb RAM and a 1.76 ghz processor; anyone any ideas on why its so slow?

PS: XP SP2 took about 2 minutes to boot to desktop on this same laptop.

I think you might be a victim for the network boot bug. Post your /etc/network/interfaces file, please. Also, check where the booting hangs. (CTRL + ALT + F8 when booting).

---

### Post by JerseyShoreComputer on 2007-05-22
Always under a minute.... Much faster than Vista or XP.

---

### Post by tenzindorje on 2007-05-22
Between 1 and 2 minutes on a 2.8GHz Pentium 4. Noticeably faster than XP.

---

### Post by samjh on 2007-05-22
Approximately one minute from power button to gdm.

But for comparison, Windows XP was faster: around 30 to 40 seconds from power button to login screen.

---

### Post by fred the wise on 2007-05-22
My toshiba satellite has a strange attitude..during the startup, it takes about 30 seconds without loading (pressin alt+F1 I see system is "starting up...") and after then it goes on quickly...I don't know why..maybe some settings of the boot services (I used recently sysv-rc-conf..)?

---

### Post by ghostboy on 2007-05-22
On my Acer running WinXP SP2, it took about 4.5 minutes. 
 
Ubuntu 7.04, about 2 flat.

---

### Post by koenn on 2007-05-22
42 seconds from GRUB menu to gdm login. Then another 10-12 seconds for gnome to load. 
That's Dapper on a 1.8 Ghz cpu with 1GB RAM.

---

### Post by Pinger05 on 2007-05-23
32 seconds from Grub to logon, that includes the hunting and pecking I do logging in:lolflag:

Specs:
Compaq P3 2.5Ghz
400Mb of Ram
40Gb EIDE HD
Stupid Intel Graphics card
NO Pimpily Geekness of Beryl
Not dual booted with anything

Here are the exact specs of the computer.  Bought it a few years ago.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00047766&lc=en&cc=us&product=359576&dlc=en&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00047766&lc=en&cc=us&product=359576&dlc=en&lang=en)

Windows takes 2 min to get to log on, then 5 from logon to useable.

---

### Post by steven8 on 2007-05-23
> **Pinger05 said:**
> 32 seconds from Grub to logon, that includes the hunting and pecking I do logging in:lolflag:

Specs:
Compaq P3 2.5Ghz
400Mb of Ram
40Gb EIDE HD
Stupid Intel Graphics card
NO Pimpily Geekness of Beryl
Not dual booted with anything

Here are the exact specs of the computer.  Bought it a few years ago.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00047766&lc=en&cc=us&product=359576&dlc=en&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00047766&lc=en&cc=us&product=359576&dlc=en&lang=en)

Windows takes 2 min to get to log on, then 5 from logon to useable.

My exact time!

---

### Post by hard_i on 2007-05-23
28 seconds
Celeron 2.4 @ 3.0GHz , 1.25GB RAM, Hitachi Deskstar 40GB/7200/2MB
Here's my boot chart:

[[IMG]http://img513.imageshack.us/img513/403/feisty200705231jf1.th.png[/IMG]](http://img513.imageshack.us/img513/403/feisty200705231jf1.png)

---

### Post by insane_alien on 2007-05-23
about 2-5 minutes including login time and all the crap i start up at boot(firefox, XMMS, X-chat, GAIM etc.)

---

### Post by guitarmaniac on 2007-05-23
didn't bother counting, but probably a bit under a minute.
seems much faster now that Im using ubuntustudio, I think my computer likes the low latency kernel.
maybe its just placebo.
next time I reboot I'll count ;)

---

### Post by forcesofhabit on 2007-05-23
About five... XP doesn't take that long at all. GRUB takes a while to load, and then Ubuntu hangs at the boot screen for a bit, and then finally decides to load everything else up.

I wish I could make this thing go faster. I have Celeron D 2.8ghz w/256mb of ram. Not alot of RAM I know, but I still don't think it should be that slow!

---

### Post by Brinstar on 2007-05-23
I'm laughing at all you ubuntu guys with your 2-5 minute boots, on a 1.7 Ghz Pentium M w/ 1Gb RAM, i consistently get 35 sec boots. 

edit: should have added that i use Zenwalk 4.6 b 2

---

### Post by lakersforce on 2007-05-23
> **gnomeuser said:**
> I dunno.. 30 secs or so from grub to gdm is fully loaded. It's dead fast.

My Ubuntu boot takes a little under 2 mins from grub to fully booted and logged in. In comparison my XP boot only takes 15 seconds (with 5 of those being the splash screen). I might add that I do not game on my XP (nor Ubuntu) partition and except flash 8 only use open source software. So Ubuntu Is not exactly a speedhog.

---

### Post by PartisanEntity on 2007-05-23
I timed a while ago, if I remember correctly it took about 40 seconds from grub to gdm on my Asus A6K 1.6GHz Turion laptop.

---

### Post by dreadlord_chris on 2007-05-23
Pentium Celeron D 3.2GHz, 256MB = consistantly boot to login in 34 seconds (except for the occasional fsck, then it'll go up to 1 - 1.5 minutes)

---

### Post by TheMono on 2007-05-23
Bootchart tells me 22 seconds.

---

### Post by icechen1 on 2007-05-23
Near 50 seconds but sometime 2 min

---

### Post by Lucifiel on 2007-05-23
Sometimes around 20++ secs but often around 30++ secs.

---

### Post by discmaster on 2007-05-23
I wondered about this since I started using Ubuntu a couple mo. ago. I just now shut down & timed from a "cold" boot; It takes around 1 min. 10 sec from power button to desktop. It sure seems longer when you are sitting there waiting on it!

My PC Specs.
2.39 AMD 64
1 GB Crucial RAM
Seagate Sata 250 gb.
sda2 part is 30 gb. linux
sda1 part is 30 gb. empty now, might install xp..

In viewing the poll results, I see the majority boot in under a minute. What are the tips for a fast booting pc?

---

### Post by Lucifiel on 2007-05-23
> **discmaster said:**
> I wondered about this since I started using Ubuntu a couple mo. ago. I just now shut down & timed from a "cold" boot; It takes around 1 min. 10 sec from power button to desktop. It sure seems longer when you are sitting there waiting on it!

My PC Specs.
2.39 AMD 64
1 GB Crucial RAM
Seagate Sata 250 gb.
sda2 part is 30 gb. linux
sda1 part is 30 gb. empty now, might install xp..

In viewing the poll results, I see the majority boot in under a minute. What are the tips for a fast booting pc?

If I'm not wrong, there's this tip:

sudo tune2fs /dev/###

where ### = your Linux partition.

---

### Post by 71CH on 2007-05-23
so is there a way to speed up boot times?

---

### Post by Onyros on 2007-05-23
Wow... terrible boot times around here...

I once had a Mini ITX system with a Pentium III Tualatin 1.2GHz and 512MB of RAM (PC133) and it booted Breezy in under a minute (into Fluxbox), so I'm really surprised to learn that the options above 1 minute are pretty crowded.

I have 3 laptops around the house, and they all boot in under a minute with Feisty.

---

### Post by a12ctic on 2007-05-23
Somewhere around 30 seconds to a minute and 15 seconds. It's pretty speedy.

---

### Post by jperez on 2007-05-24
About less than a minute, which is WAY lass time than Windows takes.  ¬.¬

From the log on screen to the desktop, about 3-5 secs.  I'm in love all over again with Ubuntu.

Windows...from log on to full use of Desktop, 1 minute...

Yeah, I think Ubuntu wins hands down.

Jesse~

---

### Post by NikoC on 2007-05-24
About 41 seconds on a Sony Vaio VGN-S4HP lappy (Intel Mobile 1.73 Ghz with 512 Mb RAM and 60 Gb HD) running Feisty.

---

### Post by DarkN00b on 2007-05-24
36 seconds from cold boot to desktop with Feisty/Gnome. 

HP ze2000 laptop, 768 MB memory, 4200 RPM HD, Intel I855 mobile graphics - 32MB

Proof you say? Bootchart below.

---

### Post by PatrickMay16 on 2007-05-24
Whoa OH **** yeeeeeeeeaaaaaaaahhhhhhhhhhhhhhhhhhh it takes about 45 seconds for dapper on my computer to boot, after selecting it in the grub menu.

---

### Post by PartisanEntity on 2007-05-24
> **DarkN00b said:**
> 36 seconds from cold boot to desktop with Feisty/Gnome. 

HP ze2000 laptop, 768 MB memory, 4200 RPM HD, Intel I855 mobile graphics - 32MB

Proof you say? Bootchart below.

How do I get a nice chart like that?

---

### Post by Ram Crammer on 2007-05-24
About 60 seconds.  I'm running Feisty, out of the box.  No kernel optimizations (yet).  I really must get around to trying to optimize.  I'm sure I can shave off 15 or 20 secs.  As is, it's not too bad for the kind of hardware I'm running.  (See my sign-off)

---

### Post by loathsome on 2007-05-24
> **PartisanEntity said:**
> How do I get a nice chart like that?

I'd also like to know that.

On the other hand, are there any good tips speeding up the boot time? I'm pretty happy as it is, but I'd sure like to get 30-seconds like some of you guys 

:popcorn:

---

### Post by Somenoob on 2007-05-24
14-17 secs

---

### Post by headcronie on 2007-05-24
AMD K6-2 550mhz 256mb RAM: 2-3 minutes running Dapper Drake
PIII 866mhz 256 RAM: 1 minute running Feisty Fawn
Celeron 500mhz 160mb RAM: 1-2 minutes runnng Win2K
P4 1.8ghz, 1gb RAM: offline - dead harddrives.
Palm TE 32mb RAM: 5 seconds - Palm OS 5.2.1

---

### Post by DarkN00b on 2007-05-24
> **PartisanEntity said:**
> How do I get a nice chart like that?

```
sudo aptitude update
Sudo aptitude install bootchart
```

Bootcharts are stored at /var/log at boot time. They need to be deleted occasionally. :)

---

### Post by loathsome on 2007-05-24
> **DarkN00b said:**
> ```
sudo aptitude update
Sudo aptitude install bootchart
```

Bootcharts are stored at /var/log at boot time. They need to be deleted occasionally. :)

Grrrreat, thanks :KS

---

### Post by forcesofhabit on 2007-05-24
For those with a slow boot-up time. Consider trying LILO. It was taking 4-5 minutes before, and now takes just over 1.

[LILO Page]("http://users.bigpond.net.au/hermanzone/p4.html")

---

### Post by arbulus on 2007-05-24
I have:
HP Netserver E60
Pentium III Processor 500mhz
320MB RAM
Ubuntu 7.04

It takes 5-6 minutes for this thing to boot.  A good 2 minutes of that is just the BIOS, the rest is Ubuntu's boot time.  I wish there were a way to speed that up.  Rebooting is painful.

---

### Post by SlayerMan on 2007-05-24
The coolest thing about all Ubuntu releases after Dapper is their speedy bootup. No other (desktop) distribution boots as fast as Ubuntu (out of the box).

---

### Post by FuturePilot on 2007-05-24
Ooops I voted wrong:o
I'm meant 0-1 minutes. More like 45 seconds.:D

---

### Post by PartisanEntity on 2007-05-24
> **DarkN00b said:**
> ```
sudo aptitude update
Sudo aptitude install bootchart
```

Bootcharts are stored at /var/log at boot time. They need to be deleted occasionally. :)

Cool thanks very much here is my boot chart :)

---

### Post by loathsome on 2007-05-24
> **forcesofhabit said:**
> For those with a slow boot-up time. Consider trying LILO. It was taking 4-5 minutes before, and now takes just over 1.

[LILO Page]("http://users.bigpond.net.au/hermanzone/p4.html")

Grub takes like 3 seconds here.

---

### Post by Happy_Man on 2007-05-24
5 seconds from BIOS to GRUB.....

10 seconds from GRUB to Ubuntu boot.....

45 seconds from begin boot to login....

1 second for me to type my login stuff....

3 seconds to GNOME deskop. 

Total: 64 seconds. Not bad.....

---

### Post by rsambuca on 2007-05-24
> **Somenoob said:**
> 14-17 secs

???  What set-up do you have?

---

### Post by loathsome on 2007-05-24
Yeah, my Sony Vaio now takes exactly **34 seconds** to boot! Just installed the latest updates, and poof we go. :KS

---

### Post by DarkN00b on 2007-05-25
I had to go dig up the old bootchart thread [here]("http://ubuntuforums.org/showthread.php?t=241604"). Its not posted there, but I once had Dapper booting in 29 seconds.

---

### Post by Atomic Dog on 2007-05-25
[http://noforclosures.com/temp/feisty-20070525-1.png](http://noforclosures.com/temp/feisty-20070525-1.png)

Can somebody figure out why feisty seems to hang for about 30 seconds on boot from this chart???  Feisty seems to take twice as long as Edgy did on the same machine.  TIA!!!

---

### Post by loathsome on 2007-05-25
> **Atomic Dog said:**
> [http://noforclosures.com/temp/feisty-20070525-1.png](http://noforclosures.com/temp/feisty-20070525-1.png)

Can somebody figure out why feisty seems to hang for about 30 seconds on boot from this chart???  Feisty seems to take twice as long as Edgy did on the same machine.  TIA!!!
Open up **/etc/network/interfaces** and clear out *everything* except the following: ```
auto lo
iface lo inet loopback

```

(backup the interfaces file first)

:)

---

### Post by insane_alien on 2007-05-25
just done a few quick optimizations and i got it down from 2 minutes to 39 seconds. not that it matters since this gets rebooted less times than bill gates boots into linux

---

### Post by jackmc on 2007-05-25
34 seconds at last count (Laptop)

---

### Post by Atomic Dog on 2007-05-25
> **loathsome said:**
> Open up **/etc/network/interfaces** and clear out *everything* except the following: ```
auto lo
iface lo inet loopback

```

(backup the interfaces file first)

:)


Well that seemed to make Feisty boot in about 15 seconds now.  What a dramatic difference :D

Thanks!  Seriously, THANK YOU!

So are there any negative effects to editing out all the other interfaces?  Everything still seems to work fine.  ????

---

### Post by j.miller565 on 2007-05-25
Well my OpenSUSE system took about 45 seconds to boot

---

### Post by guitarmaniac on 2007-05-26
50 seconds from the second I press the button. Bootchart says 35 so that must be from when grub loads I guess.

---

### Post by loathsome on 2007-05-26
> **Atomic Dog said:**
> Well that seemed to make Feisty boot in about 15 seconds now.  What a dramatic difference :D

Thanks!  Seriously, THANK YOU!

So are there any negative effects to editing out all the other interfaces?  Everything still seems to work fine.  ????

No, as far as I know, there's no negative effects at all. This 'bug' is present in Feisty only. Basically they added a bunch of stuff you don't need in the interfaces file that loads when you boot your machine.

Glad to help! :KS

---

### Post by Happy_Man on 2007-05-26
> **loathsome said:**
> Open up **/etc/network/interfaces** and clear out *everything* except the following: ```
auto lo
iface lo inet loopback

```

(backup the interfaces file first)

:)

How much of that stuff is important, though? And what does deleting it all do?

---

### Post by loathsome on 2007-05-26
> **Happy_Man said:**
> How much of that stuff is important, though? And what does deleting it all do?

The first two lines are important, the rest is unnecessary for most people.

---

### Post by picpak on 2007-05-26
A little over a minute, amazing for 500MHz, 128MB RAM.

---

### Post by pishcotec on 2007-05-29
hey,
my ubuntu lasts ages to  boot. please someone look at my bootchart and help me?
during boottime my display (syncMaster 710N) doesn't display image (not recomended resolution ...). any hint about that?
thanx!
_______________________
celeron 2.4GHz, 192MB RAM

---

### Post by loathsome on 2007-05-30
> **pishcotec said:**
> hey,
my ubuntu lasts ages to  boot. please someone look at my bootchart and help me?
during boottime my display (syncMaster 710N) doesn't display image (not recomended resolution ...). any hint about that?
thanx!
_______________________
celeron 2.4GHz, 192MB RAM
Did you try the tip I posted previously in this thread?

---

### Post by pishcotec on 2007-05-31
yes, i did comment it cout (#). don't tell me this is not allright(!)?

---

### Post by loathsome on 2007-05-31
> **pishcotec said:**
> yes, i did comment it cout (#). don't tell me this is not allright(!)?
Post the interfaces file so I can see :)

---

### Post by pishcotec on 2007-05-31
hej, now i already deleted those lines. it looks just the same as your's, and it doesn't help.
anyone can 'read' bootchartes :)?

---

### Post by Zero Prime on 2007-05-31
About 30 seconds for me, and that's with Beryl on startup.

---

### Post by blackened on 2007-06-04
Consistently 24 seconds from Grub to GDM. Athlon XP 2200+(1.8 GHZ) w/1GB of RAM.

This link should help alot of you out with your boot times: [http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml]("http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml")

---

### Post by loathsome on 2007-06-04
> **blackened said:**
> Consistently 24 seconds from Grub to GDM. Athlon XP 2200+(1.8 GHZ) w/1GB of RAM.

This link should help alot of you out with your boot times: [http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml]("http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml")
Sweet link, thanks! :KS

Will check it out later.

---

### Post by pishcotec on 2007-06-05
already tryed the link. didn' help.
i really ask for help - my boottime is just too long, (soffice also takes years) - , look at my BOOTCHART! (few posts ago).

thankyou :)

---

### Post by steven8 on 2007-06-05
> **pishcotec said:**
> already tryed the link. didn' help.
i really ask for help - my boottime is just too long, (soffice also takes years) - , look at my BOOTCHART! (few posts ago).

thankyou :)

I don't see anything on the boot chart that means anything to me, but I'd say it must be something to with your HDD.

---

### Post by sanderella on 2007-06-05
Fast, like a few seconds on my Dell Inspiron 1300 laptop.

---

### Post by Rui Pais on 2007-06-05
> **pishcotec said:**
> hey,
my ubuntu lasts ages to  boot. please someone look at my bootchart and help me?
during boottime my display (syncMaster 710N) doesn't display image (not recomended resolution ...). any hint about that?

it looks that it stays a long time running vol_id. you may have some hardware issue with harddisk, some partition with problem (run e2fsck from a liveCD) or some incorrect setting on /etc/fstab. 
Do you add anything to /etc/rc.local?

But a better thing to do is open a thread with that problem. Maybe nothing simple to solve...

A good app is sysv-rc-conf (on repos). Allow turn on/off each boot service level by level. It's very useful for tweak and for find problematics services. You may try it to find exactly when thing happens.

_____________
I installed my using the mini.iso cd and add only what i need. That way i don't have some services (like avahi) that in fact i don't need. I tweaked a little further by turning off  some stuff i don't have any use (like restricted... the only one i use is nvidia and is loaded by X server). 
My boot time is consistently 18s according to bootchart :)

---

### Post by LightB on 2007-06-05
Not long from cold start, under a minute for me.

But more often when the computer is off I hibernate, which is faster. Sometimes standby, which is kind of instant.

---

### Post by w3bu53r on 2007-06-05
> **71CH said:**
> so is there a way to speed up boot times?
Compiling your own kernel, so you can minimize the amount of unnecessary items that are not related to your hardware.

---

### Post by Rui Pais on 2007-06-05
> **w3bu53r said:**
> Compiling your own kernel, so you can minimize the amount of unnecessary items that are not related to your hardware.

That will not make a great difference for boot times (but it will make the system feels snappier, if well done). 
Modules are loaded as needed, the fact that they are compiled didn't mean that they will be loaded. 
And you can always blacklist the ones that for some reason you don't want to use (i usually blacklist ipv6 and floppy, that i don't use). 
Of course you make your kernel lighter (and slight smaller) but that will only cut a few miliseconds on boot, before usplash appears. 
The thing for optimize boot times is simply don't start any service not essential.
[here]("http://ubuntuforums.org/showthread.php?t=89491") is an old thread (but actual) on how to optimize services.

Another optimize options:
[http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)
check "Concurrent Booting" part if you have dual core cpus (NOTE it's danger to use this with a single cpu even with SMP)

---

### Post by loathsome on 2007-06-05
A good tip in general, is to always remember to shut your computer off **properly**. I just did a test here. I did an Alt+SysRq+O for an immediate  power off, and got a **37 second boot time**. Then I went to GNOME &#8594; System &#8594; Quit, and the result: A **30 second** boot time.

---

### Post by Onyros on 2007-06-07
After profiling the startup on my Thinkpad X31, I get a 29 second boot.

And I blame the HDD (4200 rpm...), 'cos it could get much better ;)

---

### Post by issueperson on 2007-06-08
37 seconds from hitting the power button to a login screen (including 5 seconds for BIOS).  22 seconds from login to fully loaded desktop with beryl on and emerald theme, firestarter firewall, GAIM, and WPA encrypted wireless connection.  Total: 59 seconds.

I have a dell latitude D610 with a CentrinoM 1.86 GHz processor, and 1 gig of RAM.

---

### Post by nutz on 2007-06-08
Even booting from an external drive it takes me less than a minute.

---

### Post by Isaac_x on 2007-06-08
Windows XP is usable in under 20 seconds from cold start, Ubuntu under 90. I have no idea what's taking so long, I should check it out.
The CPU is a dual T2250 at 1733MHz.
--edit--
I optimized it for threading and memory usage, Ubuntu's usable in under a minute. Bootchart says booting takes 41 seconds. Still more than twice as long as Windows, and I have no idea why.
[[IMG]http://img57.imageshack.us/img57/1818/feisty200706081po6.th.png[/IMG]]("http://img57.imageshack.us/img57/1818/feisty200706081po6.png")

---

### Post by kerry_s on 2007-06-08
vaio pcg-f430 450mhz 256 ram 20gig 4200rpm hd

---

### Post by DarkN00b on 2007-06-10
> **DarkN00b said:**
> I had to go dig up the old bootchart thread [here]("http://ubuntuforums.org/showthread.php?t=241604"). Its not posted there, but I once had Dapper booting in 29 seconds.

I found the chart I was looking for. It just wasn't Dapper - it was Edgy.

[IMG]http://img.photobucket.com/albums/v191/DarkN00b/Bootcharts/edgy-20061201-2.jpg[/IMG]

---

### Post by Papi-KB7VGW on 2007-06-10
My Inspiron E1705 used to take over 2 minutes.  It would always hang at about 40% on the grub splash screen.  I didn't know about ctrl-alt-F8 then so I changed grub to NOSPLASH and now my boot time is definitely under 45 sec.  I just installed boot chart so I will find out later.

---

### Post by eddieb on 2007-06-10
two minutes 15 seconds. AMD 3200+ 64 bit. 250 sata, 1 gig ram. Nvidia 5200.
I also run Puppy which boots from grub to desktop in 20 seconds.
Here is my log.
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
Would appreciate how to make it boot faster.

---

### Post by iceportal on 2007-06-10
Damn...

You guys all suck. I got  about 8 seconds from boot to good-to-go...

In FreeDOS...

Nah, just playin.

My actual Ubuntu boot time is about 30-35 seconds, max. On my desktop it's about 30 seconds consistantly, but my laptop takes slightly longer.

Hell, if I'm already booted and running, then I restart, from the time I click "reboot" to the time I'm back in Gnome again is only about 1 minute to 1:10.

(I've got auto-login, so I don't have to type user/pass.)

Meanwhile, my XP box takes about 5 minutes to load up. Go figure.

---

### Post by ninthforce on 2007-06-10
Very fast. 25-30 seconds

---

### Post by darth_indy on 2007-06-10
About 2 1/2 minutes, but I'm running a computer that came with Win98, so it's ollllllld. I've figured that one real year = 20 computer years (since a computer usually lasts around 4 yrs, or 80 computer years). So, this thing is over 140 years old.

Compared to the XP tho, it's blazing fast. I'm sure the XP takes at least 8 minutes to boot, from power button to useable. 'Course, it had only 256 RAM and it's running Norton, so that helps it crawl. I've upgraded to a gig of RAM, so it's much better now.

---

### Post by macogw on 2007-06-10
22 seconds

---

### Post by loathsome on 2007-06-11
> **eddieb said:**
> two minutes 15 seconds. AMD 3200+ 64 bit. 250 sata, 1 gig ram. Nvidia 5200.
I also run Puppy which boots from grub to desktop in 20 seconds.
Here is my log.
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
Would appreciate how to make it boot faster.

Remove everything except the two first lines and try again.

---

### Post by Shadow Jolteon on 2007-06-11
One minute. It takes about five-ten for Windows to boot on the same computer.

---

### Post by southernman on 2007-06-11
definatly less than a minute with stock generic kernels.. from the power button to login screen.

XP 2800+
1024 pc3200 ram

---

### Post by dkaddict on 2007-06-11
Just timed mine at 1min 30secs.

It ain't always that long though. For reasons way beyond my understanding, sometimes it loads pretty lively and other times it is pretty slow. The first Ubuntu screen with the bar that fills up from left to right is where it differs. Again, sometimes the bar fills up in a few seconds and sometimes it hangs for a while. The one I just timed was a hanger m8. 
The time it takes whence I have entered my psswd is pretty consistent though. At the end of the day, a couple of minutes isn't too long. 
I have an aversion to booting into XP so can't be bothered to compare them. The end result of the XP boot process is pretty dismal when compared to my pretty little Linux environment. If i could get WINE to run my BT Softphone so I could send text messages to my friends and family, and if there was a mobile phone sync app that I could connect to my N73 and grab the photos etc, I doubt I would keep XP on its partition. They're the only reason I still need it.
Maybe I should start a post with a view to solving these 2 issues.
Nothing is perfect.
PEACE

dk

---

### Post by Rigrig on 2007-06-14
About 20 seconds from GRUB to GDM login running Feisty on a AMD Sempron 2800+ cpu(2GHz) with 512MB RAM.

---

### Post by happy-and-lost on 2007-06-17
I'm a lazy autologin freak.

My Gutsy install takes about 47 seconds to boot to the full desktop (granted I haven't stripped it down 'cos removing ubuntu-desktop from GG at this stage is asking for trouble!), which is fast considering it's a 2 year old laptop (1.73Ghz PM 1GB RAM), but that's a crawl compared to Debian Sid on the same box which takes a grand total of 21 seconds to reach a full desktop. :D

---

### Post by anthonyp on 2007-06-19
well my boot chart says 29 seconds but i swear its a lot longer. takes approx 57 second from pushing the power button to usable GUI (auto login here, i am lazy and don't need to see it).

B4 i edited the interfaces file it took exactly 60 seconds, so that saved 3 seconds... not much.

I was hoping to have the total boot time (from pushing power button) down to 40odd seconds.

I think the 29 seconds listed in boot chart is from the Ubuntu load not including Grub, cause from power button to Grub is only 5 seconds, and Grub is another 5 seconds and if I calculate that I have a total of 39seconds (which would be ideal) but it def takes 57 seconds to load all up :S

Weird eh

Cheers
Anthony

EDIT: I just profiled my boot and now my boot chart is down to 27seconds... but it still seems longer :S

---

### Post by Xummoner on 2007-06-20
Here's my bootchart and I have no idea on how to reduce the boot time, it used to be 40 seconds before the kernel update, now it takes forever. 

Hope someone can find what's the problem.

---

### Post by Ultra Magnus on 2007-06-20
Around 20 seconds - Ok I just got my new laptop today - I've got  vista/Ubuntu dual boot - Vista can take almost a minute to boot up!

---

### Post by steven8 on 2007-06-20
> **Ultra Magnus said:**
> Around 20 seconds - Ok I just got my new laptop today - I've got  vista/Ubuntu dual boot - Vista can take almost a minute to boot up!

That's one minute of your life you can never get back.  :p

---

### Post by adityakavoor on 2007-06-20
20 secs 

Booting Ubuntu on Core2Duo 2.4 Ghz ..1Gig Ram

---

### Post by kamaboko on 2007-06-20
Less than a minute, much like my Vista install.

---

### Post by bootslap on 2007-06-20
It takes 3-5 minutes for my laptop with Intel Celeron M 1.4 Ghz, 1 GB ram, 120 HDD with 20 for root, 60 for home and rest for XP. When I first installed Fiesty it was pretty fast when compared to XP. Now XP seems faster. It hardly takes a minute. While loading applications also it takes a lot of time, maybe 30 seconds to 1 minute for my home folder to open, or mail box to open, but once it is open, then is really fast, and that's the reason why I use Ubuntu coupled with the fact that we do not need to think about security when we are working on Ubuntu. But booting and application opening times are definitely on the higher side.

But I love my Ubuntu!!

---

### Post by pikul on 2007-07-24
Here is my bootchart 27 sec , i did a few diferent mods, not the runlevels one, but i cant get less then that :( i think it could be better for a dual core procesor .

[img]http://img231.imageshack.us/img231/2255/27segio8.png[/img]

---

### Post by Rui Pais on 2007-07-25
> **pikul said:**
> Here is my bootchart 27 sec , i did a few diferent mods, not the runlevels one, but i cant get less then that :( i think it could be better for a dual core procesor .

A quick look to the pic and seems that the main slowers of your boot are dhcp client and ntfs-3g. 

If your network has only 1 or 2 box+router/gateway theres no need for dhcp. Just set static IPs and you will not waste either those time as any resources.
About ntfs, are you sure you need your ntfs always mounted and accessible? 
You can remove that that from boot service and run it only when you need it.

Some other services that may not be needed: lrm-manager/linux-restricted (if the only restricted module is the one of your graphics card), ahavi-daemon (if you don't have or connect to MACs), hplip (if you don't have HP printers).


You can use sysv-rc-conf to turn services on/off.
[Here ]("http://ubuntuforums.org/showthread.php?t=89491")a thread with nice tips on boot services (a little old, but useful).

---

### Post by stalker145 on 2007-07-25
Funny thing this: I look at the chart and it says that I am booting in 41-46 seconds. I look at the ticker on the wall and it says that it's taking ~1:10. Either way, I'm much happier with Ubuntu's boot time than with Win2K, which *used* to be on this machine.

Note: the :46 is under battery power and the :41 is on A/C power.

---

### Post by doodaad_1 on 2007-07-25
AMD 4000+  2G ram 

Right on 1 minute with 5-10 seconts of that is my bios splash screen.

---

### Post by pikul on 2007-07-26
> **Rui Pais said:**
> A quick look to the pic and seems that the main slowers of your boot are dhcp client and ntfs-3g. 

If your network has only 1 or 2 box+router/gateway theres no need for dhcp. Just set static IPs and you will not waste either those time as any resources.
About ntfs, are you sure you need your ntfs always mounted and accessible? 
You can remove that that from boot service and run it only when you need it.

Some other services that may not be needed: lrm-manager/linux-restricted (if the only restricted module is the one of your graphics card), ahavi-daemon (if you don't have or connect to MACs), hplip (if you don't have HP printers).


You can use sysv-rc-conf to turn services on/off.
[Here ]("http://ubuntuforums.org/showthread.php?t=89491")a thread with nice tips on boot services (a little old, but useful).

Thanks for your reply :) it help me save 6 seconds, i disable de ntfs auto mounting and something on my dhcp thing, i looked for more info on that i dont remember rigth now what i did, but it make a lot of difference , if i found that mod ill post it, thanks.

---

### Post by buixuanduong1983 on 2007-07-26
Some time my Ubuntu 7.04 startup quite fast (<1min), but sometime it seems to be hang with the screen of loading nautilus, update manager... (the small screen after enter username and password). When it happend, this screen last until all icon, menu has appear. It would be very apreciate if you can help me point out the problem.

---

### Post by Anim8or666 on 2007-08-15
It takes me about 20-25 minutes to boot up Ubuntu. My computer is a Toshiba Satellite 5005-S504, with a 30 gigabyte hard drive, and 512 megabytes of RAM. It has a pentium 3 processor running at 1.33ghz:confused::(  Why does it take so long?

---

### Post by iPower on 2007-08-15
30minutes to 1hr (bios is allmost dead)

---

### Post by EXCiD3 on 2007-08-15
Before I tweaked my computer it would boot in a good 3-5 mins, spending much of the time haning on configuring my wireless card. Once I tweaked the settings using a tutorial, and some various information from some posts i read, i can easily get it booted in <1 min. I guess i should also note that i use Autologin as i am the sole user of my computer and see no point in having to login upon boot up.

---

### Post by kerrymorgan1 on 2007-08-15
a few days ago it took about 4 mins to boot up, or more (in that case i would restart my computer out of frustration. i went into the bios and set everything to default and from there it seemed to sort it self out....... good luck maybe? it's pretty fast now less than a minute.

---

### Post by Giggity on 2007-09-16
* post deleted -- it was eventually going to look like a hijacker post *

---

### Post by terry_gardener on 2007-09-16
1 min 15 secs from pressing the power button to desktop fully loaded 
2 min 14 secs for vista home premium

---

### Post by eljoeb on 2007-09-16
Five minutes from the press of the button to the desktop.  This has to do with running KDE and GNOME libraries, doesn't it?

Windows is easily under a minute, at 45 seconds.  Wassup with that?

---

### Post by K.Mandla on 2007-09-16
~37 seconds on a 1Ghz 512Mb PC133 7200rpm machine. 27 with Arch.

~1:10 on a 450Mhz K6-2 256Mb PC100 5400rpm machine. 40 with Arch.

I don't use Gnome or KDE. I build the desktops myself. Just like Chuck Norris.

---

### Post by aninaiian on 2007-09-16
Around 20-23 seconds to boot to the terminal and another 8-12 seconds to get to xfce4 w/ compiz-fusion on my laptop,

I'm not too sure how long it takes for my desktop as I haven't rebooted in awhile.  However, if I remember correctly it's still under a minute.

---

### Post by Packrat1947 on 2007-09-16
I just upgraded from the live CD to the desktop.   Bootup is VERY slow, on the  order of 2-3 minutes.  Heck, the CD booted up almost that fast.

This lappy is 1.6 gHz. dual core, and 2 gig of ram.

The orange "caterpillar" hangs about 1/2 way across the screen.

Maybe 7.05 will be better.

But anyhow, at least the wireless works.  Maybe that is what is loading in the background.   When the desktop comes up, it is ready to go.

BTW, I can connect to a campground's wireless system which is about 1/2 mile away.  This is over on the next country road.  Amazing.  

Packrat1947

---

### Post by markp1989 on 2007-09-16
My laptop takes 31 seconds to boot up (timed using boot chart), and me desktop takes around 25 seconds

---

### Post by nikef on 2007-09-16
Boot up time 30 to 40 seconds
just wish i could get it to boot straight to the kununtu loading screen instead of the txt first  :confused:

---

### Post by markp1989 on 2007-09-23
the laptop in my sig, its boot time is 23 seconds
the Desktop in my sig takes about 25-27 seconds

---

### Post by Black Mage on 2007-09-23
MacBook Pro, 2.2ghz 2 gigs Ram...boot time. around 30 seconds. Sometimes Linux is so fast on my Mac, it bends time and reacts to commands before I even type anything.

---

### Post by Carbon Tiger on 2007-09-23
From grub to the gdm about 25 to 30 seconds. GNOME boots up in about 10-15 seconds as well and Openbox seems to fully boot up in about 5 seconds. I have an HP dv6000 w/ AMD 64X2.

I'm not surprised its fast I'm just surprised its this fast.

---

### Post by jpyanowski on 2007-09-23
Push the power button to GRUB screen - 10 secs.

From select kernel to GNOME login - 27 secs.

From enter password to complete desktop - 22 secs.

Total - 59 secs.  Life is good.

---

### Post by conehead77 on 2007-09-23
27 seconds according to the bootchart.

from power button to desktop its 45-50 seconds

edit: 1GB RAM and sthg like Intel duo core 2xxxMHz. anybody knows how i can get the exact data of my CPU?

---

### Post by danny joe ritchie on 2007-09-23
From power button to desktop =45 seconds!  No modifications.

---

### Post by Scruffynerf on 2007-09-23
28 Seconds according to bootchart.

From Power On to Desktop... about 45-50 seconds, including a 5 second pause at Grub before default entry boot.

---

### Post by roachk71 on 2007-09-24
My computer is a brand new HP Pavilion s3020n with a dual-core AMD Athlon 64 X2, running Ubuntu exclusively. It typically takes around **35 seconds** after the BIOS startup routines finish to boot Ubuntu (64-bit version)!!

It used to have Vista installed (until a fatal crash :mad: ), and that took at least two minutes! :)

---

### Post by tsumiro on 2007-09-24
its definately faster on my mac than the OSX was.

---

### Post by boast on 2007-10-07
1 min 14 secs.

Anybody see anything I could tweak?

[[IMG]http://img489.imageshack.us/img489/6742/feisty200710061lx7.th.png[/IMG]](http://img489.imageshack.us/my.php?image=feisty200710061lx7.png)

---

### Post by vishzilla on 2007-10-07
Yup, i compared both my boxes
Windows: 76 secs
Ubuntu: 57 secs

---

### Post by CWayne on 2007-10-07
Very Fast!!!!
About 20 to 30 seconds from button push to up and ready.
Win XP was a real dog on this.
I have a Toshiba A74 Laptop.
Cliff

---

### Post by hessiess on 2007-10-07
around 30 seconds, ive never timed it tho

---

### Post by RAV TUX on 2007-10-07
> **loathsome said:**
> It takes around one minute for my Vaio laptop. It's really fast, I have even stopped using hibernate / suspension; I just turn it off (saves much more battery). One thing is for sure, it's a lot faster than my C2D @ 3.4GHz desktop running Vista. It takes from 2-5 minutes for that to boot up.

You can still vote if you're not using Ubuntu, but please specify which OS you're running then.

In Xubuntu 7.10 with e17 I use "Suspend" and it takes about 2 seconds to boot up, but I have never actually timed it.

---

### Post by revolve on 2007-10-09
it takes about....10 minutes for 7.10 to boot for me on my dell inspiron 8600 notebook


that's if it actually boots at all.

---

### Post by glupee on 2007-10-09
30-40 secs from the button to the login screen. Then it depends on whether i'm loading kde or fluxbox.

---

