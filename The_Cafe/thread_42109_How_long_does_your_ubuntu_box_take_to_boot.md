---
title: "How long does your ubuntu box take to boot?"
date: 2005-06-16
forum: The Cafe
---

### Post by tristan on 2005-06-16
Hi all

It'd make interesting reading to see what different people are getting in terms of boot time, as it relates to system specs, optimisations etc.

For me it takes **65 sec **from turning the computer on, to seeing the gdm login. This is with a 10 sec delay in grub, so it can be **55sec**. My gnome desktop loads in about 3 sec after that.

I'm running Hoary on a P4 2.6GHz box with 1Gb RAM and a Western Digital 160Gb drive 7200 rpm. 

I've stripped out all sorts of unwanted services (especially checkfs.sh which took 30+ sec to check my disks every boot) and enabled prelinking. I also edited /etc/init.d/rc to include an & after $i start , so as to start later services in parallel. 

The last few lines...  

```
	startup $i start &
				;;
		esac
	done
  fi
# eof /etc/init.d/rc
```

I'm running splashy, which might add a couple of seconds to boot time but is worth it for looks!.

Ubuntu certainly doesn't have the fastest boot time of any linux I've used, but I've also seen a lot slower. On the flip side, once it's up and running it seems pretty snappy to me!

---

### Post by Dragonfly_X on 2005-06-16
About 2 minutes! I'm running an 2200+ AMD Athlon xp with 256mb 266mhz DDR ram and 80GB 7200rpm seagate HDD. :roll:

---

### Post by poofyhairguy on 2005-06-16
49 Mississippis

---

### Post by weekend warrior on 2005-06-16
to boot? too long! 

hopefully will be improved

---

### Post by sapo on 2005-06-16
lol.. i almost forgot what "boot" means.. ubuntu is so stable that i almost never reboot... (last one was due to a power failure  ](*,) ) take a look:

[[IMG]http://img93.echo.cx/img93/2522/uptime5fj.th.jpg[/IMG]](http://img93.echo.cx/my.php?image=uptime5fj.jpg)

Maybe next month i can count the boot time...

---

### Post by SparkyDawg on 2005-06-16
[QUOTE=sapo]lol.. i almost forgot what "boot" means.. ubuntu is so stable that i almost never reboot... (last one was due to a power failure  ](*,) ) take a look:

[[IMG]http://img93.echo.cx/img93/2522/uptime5fj.th.jpg[/IMG]](http://img93.echo.cx/my.php?image=uptime5fj.jpg)

Maybe next month i can count the boot time...[/QUOTE]

You have one helluva cluttered desktop!  :) 

Next time I reboot, I'll count how long it takes. I have an AMD Athlon 2800+ with 512mb ram and a GeForce3 Ti500. I must say it boots up pretty damn quickly, even with all my gdesklets starting up. 

Heres my desktop, had to give a link because its pretty big

[http://img196.echo.cx/img196/6973/screenshot6tk.jpg](http://img196.echo.cx/img196/6973/screenshot6tk.jpg)

---

### Post by jsimmons on 2005-06-16
At what point do you start timing, from the second you hit the on/off switch, or after the system posts and you see the first line from the boot process?

---

### Post by somuchfortheafter on 2005-06-16
my amd 2800+ takes about 25 secs from the second i press enter for ubuntu...
my laptop takes closer to a minute with wireless networking configs and such...

---

### Post by tristan on 2005-06-16
> At what point do you start timing, from the second you hit the on/off switch, or after the system posts and you see the first line from the boot process?

OK here's the breakdown...

*Turn on power: 0 sec

*Grub menu appears: 17 sec

*Splashy gfx start: 35 sec (25 if I hit enter immediately at grub)

*Gdm appears: 65 sec (55 sec ")

So actually boot time from selecting OS and pressing enter at grub is between 38-48 sec. Not too bad, but we'd all love it to be quicker I'm sure. Anyone ever used BeOS? Booted to desktop in about 5 sec, on a P133!

---

### Post by jdong on 2005-06-16
On my system, about 30 seconds from GRUB loading the kernel to GDM's login screen. This is on an Athlon64 with a mixed IDE-SATA 5-disk RAID5, so your mileage may really vary!

As far as comparing it to other distros, Ubuntu's bootup speed is above average, if not exceptional. It's about in line with what I get with CentOS4 now and FC4 (but FC4 loads many more services than Ubuntu or CentOS4).

As someone else mentioned, I rarely reboot also. So I really don't care about the bootup speed if the OS can stay up.

---

### Post by Optimal Aurora on 2005-06-16
Mine usually takes about 30secs to about 40secs depending on if I got it restoring my last session... Now for fedora it took about 70secs...

---

### Post by sonny on 2005-06-16
I'll check out this weekend.. but I think it's about 40-50 secs.

---

### Post by Optimal Aurora on 2005-06-16
[QUOTE=sonny]I'll check out this weekend.. but I think it's about 40-50 secs.[/QUOTE]
If you all take that long to boot, what do you have running in the background...

---

### Post by bored2k on 2005-06-16
[QUOTE=sapo]lol.. i almost forgot what "boot" means.. ubuntu is so stable that i almost never reboot... (last one was due to a power failure  ](*,) ) take a look:

[[IMG]http://img93.echo.cx/img93/2522/uptime5fj.th.jpg[/IMG]](http://img93.echo.cx/my.php?image=uptime5fj.jpg)

Maybe next month i can count the boot time...[/QUOTE]
 Nice Rei Ayami avatar ;)

---

### Post by sapo on 2005-06-16
[QUOTE=bored2k]Nice Rei Ayami avatar ;)[/QUOTE]

;)

I have a lot of anime wallpaper, but i like this one cause is a little dark and its good to see the icons and the to run a transparent terminal :D

---

### Post by bored2k on 2005-06-16
[QUOTE=sapo];)

I have a lot of anime wallpaper, but i like this one cause is a little dark and its good to see the icons and the to run a transparent terminal :D[/QUOTE]
 **Off topic: **[http://www.animenfo.com/animetitle,1582,wkkkkd,bleach.html](http://www.animenfo.com/animetitle,1582,wkkkkd,bleach.html)
Bleach owns :-P

Ok, it's not better than one sick Kid owning a gazillion Angels and "get sick" at the very end (EOE Ova), but It's something fresh :D

---

### Post by vega44 on 2005-06-16
i dunno? 50 secs 

[[IMG]http://img179.echo.cx/img179/1978/ll29za8ft.th.jpg[/IMG]](http://img179.echo.cx/my.php?image=ll29za8ft.jpg)

---

### Post by bored2k on 2005-06-16
[QUOTE=lowlux]i dunno? 50 secs 

[[IMG]http://img179.echo.cx/img179/1978/ll29za8ft.th.jpg[/IMG]](http://img179.echo.cx/my.php?image=ll29za8ft.jpg)[/QUOTE]
 [QUOTE=The Forum FAQ]
6. Go easy on the images, they may help to explain something more clearly or indicate a problem you are experiencing better but you have to remember that not everyone has the same amount of bandwidth to waste on downloading large image files. If you feel you have to post images, make sure that they're properly compressed and no more than 80KB at the absolute most.[/QUOTE]
I am not sure why your sshot is necessary, but dialup users don't appreciate that. [-X

---

### Post by vega44 on 2005-06-16
[QUOTE=bored2k]I am not sure why your sshot is necessary, but dialup users don't appreciate that. [-X[/QUOTE]
56k died out? who in the world is still using 56k? i use 56k when my internet goes out.

---

### Post by sapo on 2005-06-16
[QUOTE=bored2k]
I am not sure why your sshot is necessary, but dialup users don't appreciate that. 
[/quote]

I think that he saw my screenshot, but i just posted that to show my uptime.. i should had cut just the terminal out of the image  ](*,) 

[QUOTE=bored2k]**Off topic: **[http://www.animenfo.com/animetitle,1582,wkkkkd,bleach.html](http://www.animenfo.com/animetitle,1582,wkkkkd,bleach.html)
Bleach owns :-P

Ok, it's not better than one sick Kid owning a gazillion Angels and "get sick" at the very end (EOE Ova), but It's something fresh :D[/QUOTE]

**[offtopic]**
hehe... I m an anime addicted... i have all the bleach eps.. and so goes for naruto, one piece, monster, and a lot of finished (and unfinished) series.. i have a lot of dvds full of animes  :grin: 
**[/offtopic]**

---

### Post by weekend warrior on 2005-06-17
> Originally Posted by **sapo**
I think that he saw my screenshot, but i just posted that to show my uptime.. i should had cut just the terminal out of the image  But he's not even running ubuntu, or even linux for that matter  :roll:   
And to top it off a totally useless (and quite horrid) XP screenshot on a *nix forum - uhmm... ok     :confused:

---

### Post by Optimal Aurora on 2005-06-17
Get back on topic will you...

---

### Post by bored2k on 2005-06-17
[QUOTE=sapo]
**[offtopic]**
hehe... I m an anime addicted... i have all the bleach eps.. and so goes for naruto, one piece, monster, and a lot of finished (and unfinished) series.. i have a lot of dvds full of animes  :grin: 
**[/offtopic]**[/QUOTE]
You are definitely a friend.


Back on topic. About 2 minutes and a few seconds I'd say. 2.4ghz PIV Box

---

### Post by psoleko on 2005-06-17
About 30 seconds from loading grub to GDM login.
Sempron 3100+
512MB Kingston HyperX PC3200
160GB Seagate HDD 7200RPM 8MB 
Shuttle SN85G4 V3

---

### Post by UbuWu on 2005-06-18
[QUOTE=tristan]I also edited /etc/init.d/rc to include an & after $i start , so as to start later services in parallel. 
[/QUOTE]

Is it safe to do this?

I tried to install initng a few weeks ago, which gave quite a fast boot time but also a lot of errors. Maybe I will try again sometime, but if this is all it takes to start everything in parallel....

---

### Post by tristan on 2005-06-18
[QUOTE=UbuWu]Is it safe to do this?

I tried to install initng a few weeks ago, which gave quite a fast boot time but also a lot of errors. Maybe I will try again sometime, but if this is all it takes to start everything in parallel....[/QUOTE]


Well it's nowhere near as sophisticated as initng, but it definitely works for me, shaves about 10 sec off bootup time. As long as the services you're starting in parallel don't depend on each other (most of these later services don't), it should work fine. And because it only affects later services which are not critical to the system starting, you shouldn't end up with a fatally unstable box.

I guess like everything you see posted on ubuntuforums - try at your own risk :)

---

### Post by drummer on 2005-06-19
from grub to gdm for me is 43 seconds, from gdm to gnome is 17 seconds (this seems slower recently but i don't know why :( )

---

### Post by xmastree on 2005-06-19
[QUOTE=drummer]from grub to gdm for me is 43 seconds, from gdm to gnome is 17 seconds (this seems slower recently but i don't know why :( )[/QUOTE]
 About one minute from selecting which drive to boot from, up to the login screen.
Athlon 2400+, Asus A7V8X-X, 512MB, 256MB GeForce4.

---

### Post by FLeiXiuS on 2005-06-22
It takes roughly 25 seconds to reboot, then a good 10 seconds to boot.

If you counted the time that I push the power button it'd be, hmm roughly 20.

---

### Post by CoriolisSTORM on 2005-06-22
Hmm, about a minute and a few seconds after GRUB.  But then again I lose a few at a PNP error I haven't worried about fixing yet.  
AMD Athlon XP 2800+ (2.0GHz) 512 MB RAM, integrated geforce 4 MX not bad at all.

---

### Post by Ride Jib on 2005-06-22
I think this should be the standard reply to this thread


[SIZE=7]TOO LONG[/SIZE]

My windows partition boots and is usable in about 1/4 the time it takes Ubuntu to load. It is the one thing that I like better about winblows.

---

### Post by poofyhairguy on 2005-06-22
[QUOTE=Ride Jib]I think this should be the standard reply to this thread


[SIZE=7]TOO LONG[/SIZE]

My windows partition boots and is usable in about 1/4 the time it takes Ubuntu to load. It is the one thing that I like better about winblows.[/QUOTE]


Let me guess....its hanging on the network part?

---

### Post by Hagen Kaiser on 2005-06-23
Yes Windows is much faster in booting

Hope that will improve, because with a laptop i hav to reboot often.
Using Suspend to disk doesnt make system going ready much faster

Does anyone have tips on how to improve bootuptime?

---

### Post by somuchfortheafter on 2005-06-23
ok when it goes to networking and hangs so to speak just press ctrl c
problem solved for ya...

---

### Post by compmodder26 on 2005-06-23
Never timed it but I would have to say less than a minute.  For me, it boots faster than Windows.

---

### Post by derrick1985 on 2005-06-23
50 sec to get to GDM
1:05 to get to Gnome-Desktop

---

### Post by elocal on 2005-06-25
Well, it is definetly too long.  From when I hit enter in grub to the time GDM appears it takes around 1:30, to load Gnome, it takes around 30 seconds. There is a delay about 20 seconds when the kernel is probing for ide1 (dvdrw and dvdrom).  Otherwise it looks all right, after the kernel hits init, it takes some time too even tough i disabled the obious services that i do not use...  I am not happy with the boot speed of ubuntu...

I run: 
Athlon 64 3000+@2250
Soltek K8TPRO-939(VIA K8T800 Pro)
1Gig of ram PC3200
Geforce 6600GT AGP 
Ubuntu Breezy Amd64, Custom (CK2) kernel.

---

### Post by cyanideoverdose on 2005-07-03
45 seconds from nvidia bios screen to gdm
15 seonds from gdm to desktop.

seems ok to me..

---

### Post by sapo on 2005-07-03
my ubuntu is with a strange problem.. when i boot up for the first time.. it always stop in a certain point.. something as "volume manager" i dont remember cause it was a few weeks that i ve rebooted it... btw..

then i reset using the reset button and in the second time it works.. but NEVER in the first time... if i reboot now.. it would crash in this part.. and after the reset stuff it would work...

very weird  ](*,)

---

### Post by roots on 2005-07-08
ok..i just recently switched from suse9.3 to ubuntu, one of the reasons was overall performance and startup time...
i compared startup and shutdown times of winxpsp2, suse9.3 and ubuntu5.04...

from choosing the os in grub to the login screen:

win 32s, ubuntu 39s, suse 46s

from login to ready desktop:

win 13s, ubuntu 16s, suse 25s

from clicking shutdown to poweroff:

win 16s, ubuntu 18s, suse 35s


all that happened on my travelmate 382tmi, 1.6ghz, 512mb, 80gb hdd, wlan + wpa enabled

---

### Post by KiwiNZ on 2005-07-08
since I reboot my Ubuntu box about twice per month I have never really noticed how long.
My Suse box is about 32 seconds.

---

### Post by elocal on 2005-07-28
[QUOTE=elocal]Well, it is definetly too long.  From when I hit enter in grub to the time GDM appears it takes around 1:30, to load Gnome, it takes around 30 seconds. There is a delay about 20 seconds when the kernel is probing for ide1 (dvdrw and dvdrom).  Otherwise it looks all right, after the kernel hits init, it takes some time too even tough i disabled the obious services that i do not use...  I am not happy with the boot speed of ubuntu...

I run: 
Athlon 64 3000+@2250
Soltek K8TPRO-939(VIA K8T800 Pro)
1Gig of ram PC3200
Geforce 6600GT AGP 
Ubuntu Breezy Amd64, Custom (CK2) kernel.[/QUOTE]

Switched back to Gentoo Linux now, from grub to gdm in about 0:45 seconds and from gdm to gnome in about 0:12 seconds. awesome.

---

### Post by Sam on 2005-07-28
Ok, I admit that Windows starts faster than Linux (if it's a fresh Win install, otherwise if the registry is old (read corrupted) it take more time; Linux do not that). But what is the difference between 30 sec. or a minute ? You are not restarting your box every ten minutes ! I switch on my box twice or three times a day, and I really don't care how much time it takes, statup time is less than 0.5% of my whole computer usage time....

---

### Post by byen on 2005-07-29
Well... ive been wondering for a while if it was only me....or if ubuntu did take so much time.... My boot time is usually abt 3-5 minutes( i guess i hold the record here)...most of it being spent on " loading ndiswrapper"...i guess it strying to find a network or something,,,, but i wish i could get it down as my ATiand linux standby dont get along well so its kind of a drag to have a restart and wait.....oh well...!

by the way I have a AMD 2800+768Mb, ati radeon U1 using the 7500 chipset!

---

### Post by bored2k on 2005-07-29
[QUOTE=byen]Well... ive been wondering for a while if it was only me....or if ubuntu did take so much time.... My boot time is usually abt 3-5 minutes( i guess i hold the record here)...most of it being spent on " loading ndiswrapper"...i guess it strying to find a network or something,,,, but i wish i could get it down as my ATiand linux standby dont get along well so its kind of a drag to have a restart and wait.....oh well...!

by the way I have a AMD 2800+768Mb, ati radeon U1 using the 7500 chipset![/QUOTE]
 Disable the network load service on boot-up, wich should solve things. Go to /etc/init.d/ and chmod -x any services you don't want (like ntpdate, wich tries to synchronize your clock). You could also install BUM wich is in our third party projects forum.

---

### Post by jerome bettis on 2005-07-29
50 seconds from pressing enter in grub to when everything is done.  i have auto login on and it spent about 4 seconds finding the wireless network.

---

### Post by jerome bettis on 2005-07-29
[QUOTE=KiwiNZ]since I reboot my Ubuntu box about twice per month I have never really noticed how long.[/QUOTE]

excellent i agree.  if i had a desktop the only time i'd notice would be a power failure.  i'd rather have an os that allows me to do that versus one that loads quick but needs to be reloaded often.

---

### Post by doclivingston on 2005-07-29
For me it's about 50 seconds from the bootloader to the dektop - but I do have Apache and MySQL starting on boot.

Windows (same machine) only takes about 15 seconds from the bootloader to the desktop - however it's around 20 seconds after the desktop appears for it to be usable (finishing loading Window services and anti-virus).

---

### Post by angkor on 2005-07-29
46 seconds from off->gdm, 40 if booting to console. hotplug taking the longest time of all processes being started. I think I'll give it a go without it. I haven't disabled any services yet. 

I think that's quite fast running a Sempron 2800, 1G ram and the standard k7 kernel. Of course windows 'boots' fasters cause it presents you with your desktop halfway during boot.

edit: gdm->gnome in under 5 seconds...

---

### Post by NeoSNightmarE on 2005-07-29
I'm surprised at the longer times in here. My computer with 256mbs of RAM and an AMD 2400+ does the entire bootup process in about 30 seconds tops. Can't really explain it but that's what it does. Lucky in a way I guess because my windows that I had on here took like 10 minutes to fully load. HUGE difference there in favor of Linux for me. ;)

---

### Post by nascent16 on 2005-08-02
I'd say mine boots faster with Ubuntu than with Windows.... but who cares? What are you guys rebooting for?

---

### Post by ghostintheshell on 2005-08-02
Windows users need to boot fast because they need simply to reboot often ;)

Ok ... My Ubuntu boot up sequence takes about 30 to 40 secs.

Cheers.

[EDIT] PIV 2Ghz with 512 Mo RAMBUS [/EDIT]

---

### Post by JayCnrs on 2005-08-03
Well decided to give this a try:

Takes 50 secs to GDM
Takes 15 secs to Gnome

I have a Dell Inspiron 2650, 256 MB RAM, 1.6 Ghz. Starting at bootup is ndiswrapper for wireless which loads in the background. I use ifplugd for this that way I can change from wireless to wired or back without rebooting or going into network properties.

---

