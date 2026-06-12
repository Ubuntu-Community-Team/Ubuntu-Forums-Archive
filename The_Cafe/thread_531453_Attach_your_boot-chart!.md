---
title: "Attach your boot-chart!"
date: 2007-08-21
forum: The Cafe
---

### Post by st33med on 2007-08-21
Everybody, attach your boot charts!

---

### Post by Arwen on 2007-08-21
Well no problem doing it but how?

---

### Post by st33med on 2007-08-21
To attach a file: click on the paper-clip in the advance Reply to topic. A window pops-up. Click the browse button, and browse to the file, namely /var/log/bootchart/*. Then click 'Upload' and close the window. It is now attached to your reply.

Or, if you mean you don't have bootchart:
```
sudo apt-get install bootchart
```
Then reboot and look in /var/log/bootchart

---

### Post by Arwen on 2007-08-21
Thanx for both :-)
I'll post tomorrow ,I feel too sleepy know zz :-P
Goodnight :-D

---

### Post by Paul820 on 2007-08-21
Here's mine:

---

### Post by st33med on 2007-08-21
Paul, do you use any restricted packages? Or ALSA?

---

### Post by Paul820 on 2007-08-21
Restricted packages? I use the ATI restricted graphics driver, as for ALSA, that's sound isn't it? I don't know about that, sound just works so i don't mess with it. My laptop 'just works' with ubuntu so i don't mess with any settings in case i break it :)

---

### Post by Paul820 on 2007-08-21
So.....why did you ask :confused:

---

### Post by st33med on 2007-08-21
Eh. You could make it go a little faster.
[http://ubuntuforums.org/showthread.php?t=89491&highlight=faster+boot]("http://ubuntuforums.org/showthread.php?t=89491&highlight=faster+boot")

---

### Post by Obor on 2007-08-22
Here is mine

---

### Post by synthaxx on 2007-08-22
Here's mine (before boot optimization). 
Keep in mind though, it's running from a 2.5" laptop HD since its an HTPC and it needs to be as quiet as possible.

Now to do some tweaking! Anybody have any tips?

---

### Post by PartisanEntity on 2007-08-22
Remember to clean up /var/log/bootchart from time to time, I installed it 3 months ago and forgot about it, upon looking into the folder today I had 162 bootcharts taking up 14MB :)

Interestingly it now takes my laptop 5 seconds longer to boot compared to 3 months ago.

---

### Post by reacocard on 2007-08-22
32 seconds on a laptop w/ 1.7ghz Pentium M and a 5400rpm HD, beat that!

I still have ideas left for tweaking too...

---

### Post by st33med on 2007-09-02
In bumping this thread, this is how to make it boot faster.
[http://ubuntuforums.org/showthread.p...ht=faster+boot]("http://ubuntuforums.org/showthread.p...ht=faster+boot")

And, if it is stuck on Checking Network Interfaces:
```
sudo gedit /etc/network/interfaces
```

Comment out everything BUT lines with 'lo'.

---

### Post by st33med on 2007-09-02
> **reacocard said:**
> 32 seconds on a laptop w/ 1.7ghz Pentium M and a 5400rpm HD, beat that!

I have better :)
Try '20 seconds'

---

### Post by smartboyathome on 2007-09-02
> **st33med said:**
> In bumping this thread, this is how to make it boot faster.
[http://ubuntuforums.org/showthread.p...ht=faster+boot]("http://ubuntuforums.org/showthread.p...ht=faster+boot")

And, if it is stuck on Checking Network Interfaces:
```
sudo gedit /etc/network/interfaces
```

Comment out everything BUT lines with 'lo'.

two things:
1) that link doesn't work
2) will commenting out checking network interfaces make it so I cannot connect to the internet?

---

### Post by st33med on 2007-09-02
> **smartboyathome said:**
> two things:
1) that link doesn't work
2) will commenting out checking network interfaces make it so I cannot connect to the internet?

1) Sorry, here is the right one.
[http://ubuntuforums.org/showthread.php?t=89491&highlight=Faster+boot]("http://ubuntuforums.org/showthread.php?t=89491&highlight=Faster+boot")
2) It can, but it really depends. Backup your interfaces files if you don't think it will work and you can't remember what command to do.

---

### Post by reacocard on 2007-09-02
> **st33med said:**
> I have better :)
Try '20 seconds'

Nice, but look closely at mine. my 32 seconds includes starting xorg and most of my desktop too, if you look at when xorg starts, you get about 21 seconds, quite comparable.

Oddly, it was 37 before I turned off a feature that was supposed to decrease boot time. Oh well...

---

### Post by stalker145 on 2007-09-03
Hmmm, 44 seconds without too much effort. Is that good for a 1GHz, 6 year-old laptop?

---

### Post by stmiller on 2007-09-03
0:29 with an AMD X2 3600.

0:46 with 867Mhz Powerbook G4.

---

### Post by st33med on 2007-09-03
> **stalker145 said:**
> Hmmm, 44 seconds without too much effort. Is that good for a 1GHz, 6 year-old laptop?

Pretty good.
Another thing you can do is press 'e' at the GRUB menu on your kernel. Go down to the line that begins with 'kernel', hit 'e' again, and add 'profile' at the end. Hit Enter and then 'b' to boot. It will now profile the boot up files for faster reading by making those files closer to the center of disk. It will take longer for that boot, but, on your next reboot, you could see an increase from 1-10 seconds. It improved mine by 3 seconds.

---

### Post by Spr0k3t on 2007-09-03
Here's mine... I haven't done anything to optimize the boot times yet.  Running gnome with kde apps so some elements of both DEs are loading.

I'm going to try a few of those speed tweaks mentioned.

---

### Post by st33med on 2007-09-03
> **Spr0k3t said:**
> Here's mine... I haven't done anything to optimize the boot times yet.  Running gnome with kde apps so some elements of both DEs are loading.

I'm going to try a few of those speed tweaks mentioned.

My prediction: you will smash my record. On lucky days, I can have boot-up times of 19 seconds.

---

### Post by bobbocanfly on 2007-09-03
God my boot time is utterly crap!

---

### Post by st33med on 2007-09-03
> **bobbocanfly said:**
> God my boot time is utterly crap!

Don't worry, just follow the link and my instructions in previous posts.

I think I should write a HOWTO to make Ubuntu faster, because that previous link hasn't updated since a looooonnnnng time and uses Dapper. 

Another thing to disable in sysv-rc-conf is brltty. It is for brail output devices in a shell, and, if you or someone you know uses your computer isn't blind, then turn that off.

---

### Post by st33med on 2007-09-03
Oh, and, if you do profile, don't turn off readahead. It is needed to find those profiled files faster.

Another thing, some people have an option in your BIOS to choose whether you want your hard drive for performance, quiet, or normal speed. Check your BIOS by *rapidly* hitting the button that onscreen says 'Setup' on bootup. Scroll through the menus to try and find Hard-drive performance. 

I don't do overclocking, because a) I don't want to reduce my CPU's lifespan, and b) My vendor, Dell, has locked in the clockspeed, and I can't modify it through the BIOS.

---

### Post by reacocard on 2007-09-03
To those wanting to speed up their boot (and everything else in fact), k.mandla has an awesome guide over on his blog: [http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/](http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/)

---

### Post by eph1973 on 2007-09-03
Here are my bootcharts for before I did anything, to doing the few quick tweaks mentioned in the above file in the section titled "Step by step".  Gained 8 seconds, from :50 to :42.  Not too bad, I really don't want to run a real minimalist setup.

---

### Post by RageOfOrder on 2007-09-03
[Doesn't this just make you horny? :P](http://omploader.org/vMndo/bootchart.png)

Sabayon = Bloated Gentoo :(

---

### Post by foxy123 on 2007-09-03
here is mine

---

### Post by stmiller on 2007-09-03
> **RageOfOrder said:**
> [Doesn't this just make you horny? :P](http://omploader.org/vMndo/bootchart.png)

Sabayon = Bloated Gentoo :(

Hm that is really too bad. Gentoo boots are infamously as fast as lightning.

---

### Post by TheeMahn2003 on 2007-09-04
Before [Tweaking]("http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html") and after.  Have had it down to 17 secs and lost my net ;)  Another tweak not on that page yet,  I would like to mention, great for those with dual core cpus.  Open a terminal:
```
sudo nano /etc/init.d/rc
```

Go down until you see:
```
CONCURRENCY=none
```

and change it to:
```
CONCURRENCY=shell
```

save and exit.  Enjoy ;)

Edit: Last shot best I could do, and still keep the net & gnome ;)  15 secs. pretty crazy, I have usplash disabled so all i see is text fly by on bootup, but it is lightning quick.  Very low system resource usage as well.

---

### Post by mostwanted on 2007-09-04
Tag for later...

---

### Post by aninaiian on 2007-09-04
Here's mine...

Oh, X.org, Compiz-fusion, and Xfce take around another 15 secs to load (10 if I'm really lucky).

Though, I think that's okay considering it's a laptop with a 1.5 GHz Celeron M (earlier Dothan, 400 MHz fsb) and a 4200 rpm hard drive.

---

### Post by JBAlaska on 2007-09-04
Ok here's mine, I also run xorg and compiz fusion. I wasn't to happy with my original 0:44 sec @ 27MB/s on my stock install of feisty, so I got rid of a few services and enabled writeback and prelinked (I know you dont have to prelink on feisty, but I'm a idiot lol), I think prelinking added some time but writeback pushed my disk throughput up.
Now I'm at 0:46 sec @ 29MB/s. Prolly I'll un-prelink and try again..

---

### Post by acowboydave on 2007-09-04
here is mine

---

### Post by RageOfOrder on 2007-09-04
> **stmiller said:**
> Hm that is really too bad. Gentoo boots are infamously as fast as lightning.

Oh yes. And my original Gentoo install was definately lightening quick. 

Thing is... I don't have time to maintain a full Gentoo install while I'm in school. So I went with Sabayon. It gives me Gentoo with a regular binary update release schedule. So in 6 months I can update in a couple hours instead of a couple days and without worry of breaking ****.

On the downside... my kernel is bloated as hell. I have support for things my comp doesn't even have: Bluetooth... a battery monitor... touchpad drivers... It's a ******* desktop... I don't have those things.  Also about 5 million useless apps. Maybe I'll rice out my slackware laptop sometime.

---

### Post by markp1989 on 2007-09-06
here is my bootchart, anyone know how i can speed up my boot? 


can someone please delete this post i forgot to upload my image

---

### Post by markp1989 on 2007-09-06
here is mt boot chart, any one know how i can speed up my boot time?

system spec
intel celeron D 3.2ghz
2gb ram
nvidia geforce 6200  256mb
80gb sata

---

### Post by reacocard on 2007-09-06
> **markp1989 said:**
> here is mt boot chart, any one know how i can speed up my boot time?

system spec
intel celeron D 3.2ghz
2gb ram
nvidia geforce 6200  256mb
80gb sata

40s is already pretty good, but if you really want more speed you can try k.mandla's guide: [http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/](http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/)

---

### Post by foxy123 on 2007-09-07
> **reacocard said:**
> 40s is already pretty good, but if you really want more speed you can try k.mandla's guide: [http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/](http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/)

The guide helped me to knock down 2 sec from my boot time. Now it is 35 sec vs. 37 sec. I wonder if this is minimum I can get.

---

### Post by markp1989 on 2007-09-07
here is my chart, i managed to save a few seconds by installing the kernel from gusty

> 40s is already pretty good, but if you really want more speed you can try k.mandla's guide: [http://kmandla.wordpress.com/2007/04...sty-for-speed/](http://kmandla.wordpress.com/2007/04...sty-for-speed/)
thanks for the link , im just about to have a look at it 


i wonder what the lowest possible boot time is, anyone have any knowledge they can share?

---

### Post by reacocard on 2007-09-08
> **markp1989 said:**
> i wonder what the lowest possible boot time is, anyone have any knowledge they can share?

quite low, but it'd be a minimal text-only system. I have yet to see anything under 20s for booting into a full X environment.

---

### Post by markp1989 on 2007-09-08
> **reacocard said:**
> quite low, but it'd be a minimal text-only system. I have yet to see anything under 20s for booting into a full X environment.

ok, cool, how do i go about getting my boot to be around 20-25 sec?  so far i got to about 30

---

### Post by reacocard on 2007-09-08
> **markp1989 said:**
> ok, cool, how do i go about getting my boot to be around 20-25 sec?  so far i got to about 30

follow that guide I posted a few back, in particular,

- autologin
- start X automatically
- start from a minimal install
- remove useless init scripts
- shut down unwanted services
- set concurrency to shell
- readahead
- reprofile your boot (do this last!)

I'm currently working on tweaking a minimal gutsy install myself, I'll post the results once I'm done.

---

### Post by markp1989 on 2007-09-08
> **reacocard said:**
> follow that guide I posted a few back, in particular,

- autologin
- start X automatically
- start from a minimal install
- remove useless init scripts
- shut down unwanted services
- set concurrency to shell
- readahead
- reprofile your boot (do this last!)

I'm currently working on tweaking a minimal gutsy install myself, I'll post the results once I'm done.

ok hope you get the results you want, im just about to do this on my laptop, with fiesty nt gusty , il post the results from the boot chart on here when its all done

---

### Post by markp1989 on 2007-09-08
> **markp1989 said:**
> ok hope you get the results you want, im just about to do this on my laptop, with fiesty nt gusty , il post the results from the boot chart on here when its all done

i managed to get it down to 28 seconds:D , there is prob a way to cut a second or 2 off, but im tired, its 3:10 AM here lol , 

does any one know were i can shave a few seconds?

---

### Post by TheeMahn2003 on 2007-09-10
> **reacocard said:**
> quite low, but it'd be a minimal text-only system. I have yet to see anything under 20s for booting into a full X environment.

See my shots above yes it is into gnome in 15 secs.  Still have internet however every service unnecessary including logging daemons have been stripped.

---

### Post by markp1989 on 2007-09-10
> **TheeMahn2003 said:**
> See my shots above yes it is into gnome in 15 secs.  Still have internet however every service unnecessary including logging daemons have been stripped.

15seconds!! thats excellent  well done:D

---

### Post by reacocard on 2007-09-10
> **TheeMahn2003 said:**
> See my shots above yes it is into gnome in 15 secs.  Still have internet however every service unnecessary including logging daemons have been stripped.

very nice!

for some reason bootchart isn't working nicely on this machine, it goes on for 4-5 minutes even though it's at the desktop (with compiz) in 35-40 seconds (starts X at only 20!). ah well, time to go trim my initscripts. :D

---

### Post by nowshining on 2007-09-10
for the 404 error there is such a thing as the wayback machine - the internet archives - archive.org for a shortcut web.archive.org/web/

however just checked it's not in there..

---

### Post by aktiwers on 2007-09-10
brb

---

### Post by Spr0k3t on 2007-09-10
I thought I'd post my laptop with gutsy.  Only one optimization done.

---

### Post by Linuturk on 2007-09-10
> **TheeMahn2003 said:**
> Before [Tweaking]("http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html") and after.  Have had it down to 17 secs and lost my net ;)  Another tweak not on that page yet,  I would like to mention, great for those with dual core cpus.  Open a terminal:
```
sudo nano /etc/init.d/rc
```

Go down until you see:
```
CONCURRENCY=none
```

and change it to:
```
CONCURRENCY=shell
```

save and exit.  Enjoy ;)

Edit: Last shot best I could do, and still keep the net & gnome ;)  15 secs. pretty crazy, I have usplash disabled so all i see is text fly by on bootup, but it is lightning quick.  Very low system resource usage as well.

Thank you for this. I've attached my before and after using your fix.

---

### Post by BLTicklemonster on 2007-09-10
> **bobbocanfly said:**
> God my boot time is utterly crap!

lmao got you beat!

---

### Post by lisati on 2007-09-10
Probably could do with some tweaking and optimizing, but I don't mind....it sometimes still amazes me what can be done, even though I've been using computers in one form or another for nearly 30 years!

---

### Post by BLTicklemonster on 2007-09-10
Aha, I used this:

[http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html](http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html)

and got the same boot time. 

Huh.

So I edited /etc/fstab to remove the fsck stuff (changed the last number on each line to zero, all except for my / drive, which I made a one)
Be squeemish if you don't know what I mean. Ask questions galore before you edit fstab.

Now I'm screaming(ish)

---

### Post by markp1989 on 2007-09-11
Here is the boot chart for my laptop running xubuntu 7.04. 24 sec is not bad, compared to the 40sec before i optimized the boot time.

does any one know of any ways i can speed this up a tad more, because i have to turn this laptop off when not in use, so boot time is important

EDIT: My boot time has gone up by over 10 seconds, just by installing the new kernel, and reprofiling boot hasnt done anything :S

---

### Post by TheeMahn2003 on 2007-09-12
> **markp1989 said:**
> 15seconds!! thats excellent  well done:D

Thanks, I however no longer have that luxury running 1.5, here for the people; god I hated to lose that as much as I install was enjoying it, I suppose a small price to pay in the big picture.  I highly doubt I will ever see that again, I even messed with kintd a huge no-no for the common user, I not only striped services I completely remove them from the O/S, once again a big no-no, I have no printer cupsys hplip history.  I have told you how that somewhat happened take the time and learn, I just don't want every user doing the same w/o knowing the consequences of such action.

Once again thanks

---

### Post by TheeMahn2003 on 2007-09-12
> **Linuturk said:**
> Thank you for this. I've attached my before and after using your fix.

Thank you for the Kudos, far from my fix, I do however have it on my site as a "bonus" tweak, I did not write it, I just learn and present the info to my end users.  None the less thanks.  An to be 100% honest I will not present what it was to get me down to 15 secs boot time and with good reason, I will not put users in harms way.

---

### Post by TheeMahn2003 on 2007-09-12
> **BLTicklemonster said:**
> Aha, I used this:

[http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html](http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html)

and got the same boot time. 

Huh.

So I edited /etc/fstab to remove the fsck stuff (changed the last number on each line to zero, all except for my / drive, which I made a one)
Be squeemish if you don't know what I mean. Ask questions galore before you edit fstab.

Now I'm screaming(ish)

First of all you run Gusty (my website explains it was explicitly written with UUE in mind but does cater to those that run feisty **Not Gusty**), from edgy to feisty many changes have occurred in just booting some I have placed here for others to learn from & perhaps help them.  Probably burns me up to no end, You have no clue how many times I have been asked to make a Gusty Version of UUE, I build off "stability" as far as a distro not beta or alpha, personally I have never ran Gusty -- I have a user base to think of and no [slouch]("http://ubuntuforums.org/showpost.php?p=3355692&postcount=996").  I know they are on top of things, but do not think my userbase should suffer just because they introduce the next great thing, I will not get into details as far as changes I have seen.

---

### Post by TheeMahn2003 on 2007-09-13
> **lisati said:**
> Probably could do with some tweaking and optimizing, but I don't mind....it sometimes still amazes me what can be done, even though I've been using computers in one form or another for nearly 30 years!

If you are willing to try I will help you, first thing I see from the screenshot is the aspi in your kernel.  Are you running this on your laptop?  I have been building computers close to the 30 years.  Wrote my first program when 11.  Probably better then 20, I am not that old ;)  But this is a fact, "I have built 100's if not thousands of computers", and have probably over my lifetime "written 100's of programs, and have given them away free, I have only in my lifetime charged for 1 program".  I feel I have to come back to explain reason I charged was it was written specific for him  he had no problem with it.  ;)

---

### Post by runemaste644 on 2007-09-15
My fastest boot since i installed the bootchart package was 0:58. Or does it only keep max 10 bootcharts?

---

### Post by blockcipher on 2007-09-15
Here is mine.  I have a DELL 700m.

---

### Post by hard_i on 2007-09-20
...

---

### Post by felin on 2007-09-20
No idea what it all means, or whether it is good or bad time, but here it is!

---

### Post by Onyros on 2007-09-20
> **felin said:**
> No idea what it all means, or whether it is good or bad time, but here it is!Have you re-profiled your boot, yet? Edit your boot line in Grub next time you start it up, to include "profile" at the end. That boot will take longer than normal, but the next one (don't include "profile" from then on) will shave a few seconds off your boot time.

I'm writing this because it's strange that my Thinkpad X31(Pentium M 705 - 1.4GHz, 1MB L2 cache) beats your (far superior) system by two seconds: mine boots in 29 seconds. BTW, I'm getting this result on a 4200 rpm 2.5" HDD, which is quite the feat for this lil' machine.

---

### Post by energiya on 2007-09-20
I managed to get to 15 seconds, but can't find the bootchart (I took this from my forum post). Preaty nice for my specs (back then I had 128 MB RAM)
[[img]http://img162.imageshack.us/img162/7061/bootchartf4jb7.th.png[/img]](http://img162.imageshack.us/my.php?image=bootchartf4jb7.png)

---

### Post by st33med on 2007-09-20
> **markp1989 said:**
> 

EDIT: My boot time has gone up by overr 10 seconds, just by installing the new kernel, and reprofiling boot hasnt done anything :S

Have you disabled readahead? If you have profiled your boot, that makes the profile moot.

---

### Post by BLTicklemonster on 2007-09-21
Okay, how do I delete them, the folder is not in my realm of permissions. Is it safe to chown var/log/~ to delete them?

---

### Post by reacocard on 2007-09-21
> **BLTicklemonster said:**
> Okay, how do I delete them, the folder is not in my realm of permissions. Is it safe to chown var/log/~ to delete them?

just do
```
sudo rm /var/log/bootchart/*
```

---

### Post by BLTicklemonster on 2007-09-21
Thank you!

---

### Post by Scruffynerf on 2007-09-23
Here's mine, Feisty running on the specs in my sig.

Sub 30 seconds (About 27?), and I'm pretty happy.

Running Gnome

Concurrency to shell, boot profiled, and followed a lot of the suggestions from TheeMan's Ubuntu Ultimate website, [Here]("http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html")

Cheers

---

### Post by markp1989 on 2007-09-23
> **st33med said:**
> Have you disabled readahead? If you have profiled your boot, that makes the profile moot.

how would i check if read ahead has ben disabled?

---

### Post by Scruffynerf on 2007-09-23
> **markp1989 said:**
> how would i check if read ahead has ben disabled?

Check your boot chart - if read-ahead had been disabled, then it shouldn't appear in the bootchart.

---

### Post by AbredPeytr on 2007-09-23
Ok. Here's mine. Is this like modern art, or what? :-)

---

### Post by ahaslam on 2007-09-23
Fast enough?

---

### Post by stevebakerj on 2007-09-23
Here my testing setup

---

### Post by regomodo on 2007-09-23
i wonder if anyone elses is as slow as mine. 74 seconds!! Damn fsck

---

### Post by regomodo on 2007-09-23
> **ahaslam said:**
> Fast enough?

how did you get bootchart to work in Arch. I can't find the bootchart folder

[edit] nevermind. figured it out and it looks horrendous. load-modules.sh everywhere. 87seconds

---

### Post by markp1989 on 2007-09-23
Here is my current boot chart for the laptop mentioned in my sig ;23sec is not bad, any one know where i can shave a few seconds off?

---

### Post by markp1989 on 2007-09-23
> **Scruffynerf said:**
> Check your boot chart - if read-ahead had been disabled, then it shouldn't appear in the bootchart.
 
yes it was disabled,  i set it on again and it works fine thankyou

---

### Post by StreetSmart on 2007-09-24
Heres mine, kinda slow for my lenovo R60. How can I make this process faster?

---

### Post by ahaslam on 2007-09-24
Is that a laptop using wireless?
It looks as though it's waiting for a network response.

---

### Post by Scruffynerf on 2007-09-24
Multiple occurrences of avahi-deamon?

What happens if you disable the service/session? I've not noticed a problem, but then my rig is a wired desktop.

---

### Post by markp1989 on 2007-09-27
i got my desktop down to 22 seconds 

all i did was
- remove useless init scripts
- shut down unwanted services
- set concurrency to shell
- readahead
- Reduce_tty_count
- reprofile your boot

---

### Post by kqueenc on 2007-09-27
You guys have awesome computers.
It takes mine almost 40 seconds.

---

### Post by Frak on 2007-09-29
> **kqueenc said:**
> You guys have awesome computers.
It takes mine almost 40 seconds.
Heh, Mine's not the best either...

---

### Post by TheeMahn2003 on 2007-10-04
> **Linuturk said:**
> Thank you for this. I've attached my before and after using your fix.

Thanks, I have added a few other tweaks to that page, I will not add anything that will bork your system, but please pay attention to the comments.  Building a Gusty Ultimate will test that page against Gusty as well ;)

Thanks again,

---

### Post by TheeMahn2003 on 2007-10-04
> **Scruffynerf said:**
> Here's mine, Feisty running on the specs in my sig.

Sub 30 seconds (About 27?), and I'm pretty happy.

Running Gnome

Concurrency to shell, boot profiled, and followed a lot of the suggestions from TheeMan's Ubuntu Ultimate website, [Here]("http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html")

Cheers

Thanks, that is fast for the chip you have, do you have sata?  The #1 thing slowing your boot is NTFS, I assume you dual boot, you could remove it from start up, and if you need to access that partition you could use your NTFS Configuration tool, probably would shave 3 secs off your boot time.  but if you use that drive / partition all the time I would leave it be.

Thanks again for the kudos.

---

### Post by xat_ on 2007-10-04
[img]http://xat.uguu.us/feisty-20071001-2.png[/img]


Loading 9 partitions; 6 ntfs, 1 ext3, 1 swap, 1 smbfs.

---

### Post by foxy123 on 2007-10-05
I have upgraded to Gutsy and my boot-up time jumped from 37-40 sec up to 56-60 sec.

---

### Post by markp1989 on 2007-10-19
gusty boots so fast, here is mine with no boot optimization done, i wonder what boot optimizations will be discovered for gusty, and if they will be effective

25 sec in to gnome

---

### Post by Frak on 2007-10-19
Here's mine with a powerful boot optimization, no GUI ;)

---

### Post by Paul820 on 2007-10-19
Heres mine with no boot optimisation and GUI. Running gutsy now so i thought i would post again.

---

### Post by Paul820 on 2007-10-19
Ok, so it never appeared :lolflag: Here it is, i don't think i press upload.

---

### Post by bobbocanfly on 2007-10-19
My new gutsy bootchart. My fesity ones were utterly shocking, about 55s to 1minute 20s on a bad day. Disabed GDM on startup ,also a couple of other stuff that i will never need, like bluetooth and wireless.

---

### Post by odnalro on 2007-10-21
22 seconds without optimization

---

### Post by RAV TUX on 2007-10-21
Here's a history of mine:

---

### Post by RAV TUX on 2007-10-21
> **RAV TUX said:**
> Here's a history of mine:...and two more:

---

### Post by Frak on 2007-10-21
> **RAV TUX said:**
> ...and two more:
We don't aperciates showoffs around these joints ;).

---

### Post by RAV TUX on 2007-10-21
> **Frak said:**
> We don't aperciates showoffs around these joints ;).I honestly don't even know if my figures are good or bad?...comparatively speaking.

---

### Post by Frak on 2007-10-21
> **RAV TUX said:**
> I honestly don't even know if my figures are good or bad?...comparatively speaking.
Your speeds are faster than mine while yours has a GUI and mine boots to a very minimal installation ;)

---

### Post by RAV TUX on 2007-10-21
> **Frak said:**
> Your speeds are faster than mine while yours has a GUI and mine boots to a very minimal installation ;)Cool, Thanks for letting me know my $3000 purchase 2 years ago from Dell wasn't a complete waste. ;)

---

### Post by Frak on 2007-10-21
> **RAV TUX said:**
> Cool, Thanks for letting me know my $3000 purchase 2 years ago from Dell wasn't a complete waste. ;)
:lolflag:

---

### Post by stalker145 on 2007-10-21
I think I'm going to cry... I went from about 40 seconds in Feisty to this ](*,)

I ask the pros: what the heck did I do wrong? This is a standard install with a few added programs and no system "tweaks" of any sort.

Thanks.

---

### Post by RAV TUX on 2007-10-21
> **stalker145 said:**
> I think I'm going to cry... I went from about 40 seconds in Feisty to this ](*,)

I ask the pros: what the heck did I do wrong? This is a standard install with a few added programs and no system "tweaks" of any sort.

Thanks.Wow!...that is bad.

---

### Post by reacocard on 2007-10-21
> **stalker145 said:**
> I think I'm going to cry... I went from about 40 seconds in Feisty to this ](*,)

I ask the pros: what the heck did I do wrong? This is a standard install with a few added programs and no system "tweaks" of any sort.

Thanks.

That's really odd, looks like usplash is using all your cpu. Try this: when you start up, press ESC to get the grub menu, then press 'e' to edit, move down to the kernel line, press 'e' again to edit it, and remove the word 'splash' from that line. Press enter, then 'b' to boot. If that gives you a better time, just remove the splash option from defoptions in your menu.lst to keep the change permanently.

---

### Post by Scruffynerf on 2007-10-21
> **reacocard said:**
> That's really odd, looks like usplash is using all your cpu. Try this: when you start up, press ESC to get the grub menu, then press 'e' to edit, move down to the kernel line, press 'e' again to edit it, and remove the word 'splash' from that line. Press enter, then 'b' to boot. If that gives you a better time, just remove the splash option from defoptions in your menu.lst to keep the change permanently.

Alternatively, re-install usplash, or change what the splash image is.

I run a fairly custom rig off IDE drives, and I usually get around 27 seconds to GUI and all done. The only time i've seen a bootchart like that is when fsck decides it's time to do over one of the drives every nth boot.

---

### Post by puccaso on 2007-10-21
> **st33med said:**
> Everybody, attach your boot charts!


how on earth do u get a 20second boot time? what is that about..

check this

---

### Post by rand0m on 2007-10-22
20 seconds on a new optimized Kubuntu 7.10 install. Besides booting faster than Feisty (gnome, xfce, or kde),  it's noticeably snappier, smoother, and doesn't run like KDE ontop of a gnome distro. Only downside is I can't break 20 sec without sacraficing services I need to use :grin:

---

### Post by steveneddy on 2007-10-22
Ok!!

---

### Post by Rhubarb on 2007-10-22
:D wow, gutsy is fast on my PC here.
No optimisations, 17sec boot time including entering my user name and password on gdm srceen.

---

### Post by reacocard on 2007-10-22
now down to 23 seconds on my two-year-old laptop with optimizations, not bad at all.

takes longer to log in than to boot :mrgreen:

---

### Post by Scruffynerf on 2007-10-22
Feisty, heavily customised install: 27 seconds.

---

### Post by andrewabc on 2007-10-22
Here is my bootchart on new gusty with a couple installed programs.
22 seconds.

What is all the k stuff at bottom of bootchart?
I installed amarok the other day, does that mean it has to load lots of kde stuff when booting? I use regular gnome ubuntu. If using amarok means loading a bunch of kde stuff, any recommendations on a good gnome player? (link?).

I notice in running processes there are 5 different kdeinit programs running.

See anything that is slowing it down lots?

---

### Post by stalker145 on 2007-10-22
> **reacocard said:**
> That's really odd, looks like usplash is using all your cpu. Try this: when you start up, press ESC to get the grub menu, then press 'e' to edit, move down to the kernel line, press 'e' again to edit it, and remove the word 'splash' from that line. Press enter, then 'b' to boot. If that gives you a better time, just remove the splash option from defoptions in your menu.lst to keep the change permanently.

I'll definitely try that when I get home to my computer. Thank you for the advice.

Funny thing is that I have yet to see a Gutsy splash. The screen goes black through the whole boot process until GDM.

I'll let you all know how it goes.

---

### Post by Scruffynerf on 2007-10-22
> **andrewabc said:**
> Here is my bootchart on new gusty with a couple installed programs.
22 seconds.

What is all the k stuff at bottom of bootchart?
I installed amarok the other day, does that mean it has to load lots of kde stuff when booting? I use regular gnome ubuntu. If using amarok means loading a bunch of kde stuff, any recommendations on a good gnome player? (link?).

I notice in running processes there are 5 different kdeinit programs running.

See anything that is slowing it down lots?

Yes, if you use amorak, then there's a bunch of KDE stuff needed to make it work.

An alternative in the repo's that people seem to like is Exaile

---

### Post by andrewabc on 2007-10-22
> **Scruffynerf said:**
> Yes, if you use amorak, then there's a bunch of KDE stuff needed to make it work.

An alternative in the repo's that people seem to like is Exaile

Thanks. I noticed a thread about it and the screenshots look nice. Will try. wow only 500kb download as well.

---

### Post by stalker145 on 2007-10-22
> **stalker145 said:**
> [QUOTE=reacocard;3595889]That's really odd, looks like usplash is using all your cpu. Try this: when you start up, press ESC to get the grub menu, then press 'e' to edit, move down to the kernel line, press 'e' again to edit it, and remove the word 'splash' from that line. Press enter, then 'b' to boot. If that gives you a better time, just remove the splash option from defoptions in your menu.lst to keep the change permanently.I'll definitely try that when I get home to my computer. Thank you for the advice.

Funny thing is that I have yet to see a Gutsy splash. The screen goes black through the whole boot process until GDM.

I'll let you all know how it goes.[/QUOTE]

WOOT!! IT WORKS!!

OK, i have to give you the rundown here. A summary of attached images.

#1 Yesterday, Me crying.

#2 YEEE HAW, it friggin' works :D

#3 CRAP!! I forgot to make the changes permanant.

#4 Made the changes permanant :)

#5 Profiled the boot... dropped another second... wheee ;)


Anyway, thanks for the advice. It helped tons.

P.S. Sorry for all the pics, I just wanted to illustrate the madness that is going from almost 3 minutes boot times down to 27 stinking seconds ;)

---

### Post by reacocard on 2007-10-22
> **andrewabc said:**
> Here is my bootchart on new gusty with a couple installed programs.
22 seconds.

What is all the k stuff at bottom of bootchart?
I installed amarok the other day, does that mean it has to load lots of kde stuff when booting? I use regular gnome ubuntu. If using amarok means loading a bunch of kde stuff, any recommendations on a good gnome player? (link?).

I notice in running processes there are 5 different kdeinit programs running.

See anything that is slowing it down lots?

the k junk at the bottom is just kernel stuff, nothing to do there. The chart looks pretty dang good, you're one second faster than I am. :D You could try reprofiling your boot if you haven't already (and maybe moving the readahead to the background, it coincides with udev surprisingly well), but that's the only tweak likely to yield a perceivable difference on that hardware.

---

### Post by Scruffynerf on 2007-10-23
> **reacocard said:**
> the k junk at the bottom is just kernel stuff, nothing to do there. The chart looks pretty dang good, you're one second faster than I am. :D You could try reprofiling your boot if you haven't already (and maybe moving the readahead to the background, it coincides with udev surprisingly well), but that's the only tweak likely to yield a perceivable difference on that hardware.

How do you move readahead to a background? I thought that it was by default ?:confused:

---

### Post by reacocard on 2007-10-23
> **Scruffynerf said:**
> How do you move readahead to a background? I thought that it was by default ?:confused:

no, by default readahead runs w/o anything else allowed to run at the same time because that is more efficient on many systems. However, I have found that on my system, moving it to the background actually increases performance. On my system, it sped up the boot by about 7 seconds. To do this tweak, open /etc/init.d/readahead and change this:
```
	    log_begin_msg "Reading files needed to boot..."
	    if /sbin/start-stop-daemon --start --quiet \
```
to this:
```
	    log_begin_msg "Reading files needed to boot..."
	    if /sbin/start-stop-daemon --start --quiet --background \
```
and then edit /etc/init.d/readahead-desktop so that this:
```
	    log_begin_msg "Reading files needed to boot (second stage)..."
	    if /sbin/start-stop-daemon --start --quiet \
```
becomes this:
```
	    log_begin_msg "Reading files needed to boot (second stage)..."
	    if /sbin/start-stop-daemon --start --quiet --background \
```
save the files and reboot. Note that I have not tried this on any systems except this one, so it may not actually improve the time. If it doesn't, just reverse the edits to go back to the old way.

---

### Post by Scruffynerf on 2007-10-23
Many thanks reacocard - I'll have to try this out.

---

### Post by Scruffynerf on 2007-10-23
Well, here it doesn't seem to have made a difference to the overall time - still 26/27 seconds, however the profile of the bootchart is quite different.

Fig 1 is running readahead normally, Fig 2 is readahead running as background. My hardware specs are in my sig.

---

### Post by reacocard on 2007-10-23
> **Scruffynerf said:**
> Well, here it doesn't seem to have made a difference to the overall time - still 26/27 seconds, however the profile of the bootchart is quite different.

Fig 1 is running readahead normally, Fig 2 is readahead running as background. My hardware specs are in my sig.

Interesting, your readahead is set differently from mine. Mine runs before udev, so it can run in the idle time while udev waits on the hardware (this is where my speedup comes from), which on yours, it runs after udev, which negates the benefit. You can try to figure out how to move readahead before udev (it involves editing /etc/rcS.d, my readahead is S01, udev is S10), or just be happy with what you have and switch it back to foreground as that's better in your current setup.

---

### Post by Yes on 2007-10-23
Meh, it seems a bit slow, but I suppose it's not bad.

---

### Post by Pixel on 2007-10-23
Nothing special :p

---

### Post by Scruffynerf on 2007-10-24
> **reacocard said:**
> Interesting, your readahead is set differently from mine. Mine runs before udev, so it can run in the idle time while udev waits on the hardware (this is where my speedup comes from), which on yours, it runs after udev, which negates the benefit. You can try to figure out how to move readahead before udev (it involves editing /etc/rcS.d, my readahead is S01, udev is S10), or just be happy with what you have and switch it back to foreground as that's better in your current setup.

Interesting... I just got thoroughly lost in my own filesystem.

Eventually found some files that look like it, under the directory you indicated.

There's a S01Readahead, a S10udev and a S39readaheat-desktop. All are links to scripts. Now, I'm not exactly confident about how all this works, so I might just leave well enough alone.

---

### Post by reacocard on 2007-10-24
> **Scruffynerf said:**
> Interesting... I just got thoroughly lost in my own filesystem.

Eventually found some files that look like it, under the directory you indicated.

There's a S01Readahead, a S10udev and a S39readaheat-desktop. All are links to scripts. Now, I'm not exactly confident about how all this works, so I might just leave well enough alone.

Those sound right, so why is it doing them in a different order....? I don't know, probably best not to mess with it.

---

### Post by boast on 2007-10-28
Here's mine on a 1.8ghz AXP.

It shows 32 secs, but it takes forever for my screen to load up to desktop :(

---

### Post by Habo on 2007-10-29
Ok,  and now.. the slowest one: :(
[ATTACH]48334[/ATTACH]

Something is gone wrong, but no solution atm.

---

### Post by reacocard on 2007-10-29
> **Habo said:**
> Ok,  and now.. the slowest one: :(
[ATTACH]48334[/ATTACH]

Something is gone wrong, but no solution atm.

ouch. It looks like there's an insane amount of CPU use going on, and only one processor is being used as well. You could try enabling concurrency (search the thread for tips, there are tons of them), as that would let both CPUs be used which could cut the time almost in half, but with that processor I really don't know why it's taking this long.

---

### Post by rand0m on 2007-10-30
As far I as I know, the concurrency tweak doesn't work in Gutsy. Breaks a couple things for me.

---

### Post by Habo on 2007-11-01
> **reacocard said:**
> ouch. It looks like there's an insane amount of CPU use going on, and only one processor is being used as well. You could try enabling concurrency (search the thread for tips, there are tons of them), as that would let both CPUs be used which could cut the time almost in half, but with that processor I really don't know why it's taking this long.

I didn't have that problem about one week ago. My boot time was about 1,5 min.  It comes suddenly, without any system or hardware changes.

---

### Post by Habo on 2007-11-05
Because there was no solution vor my probelm I decide to reinstall Ubuntu and now:
[ATTACH]49171[/ATTACH]

:)

Habo

---

### Post by markp1989 on 2007-11-05
here is mine 

any one know what the IRQ-X... is at the bottom?

---

### Post by Rinzwind on 2007-11-07
0:27 seconds.
 
Dell Inspiron 9300 1.86Gz with Gutsy 7,10.

I still need to tweak it: I see cups among the bootscripts and have no printer. The boot is including start of mysql so I can't say I'm disappointed,

The only thing: gnome takes to long to boot. Can this program scan gnome for me too?

I am still new to this and also need to read the rest of this topic but if anyone sees anything weird I'd like to know ;)
[[img]http://img3.freeimagehosting.net/uploads/th.dfa857f95b.png[/img]](http://img3.freeimagehosting.net/image.php?dfa857f95b.png)

---

### Post by Humph on 2007-11-07
First one is my desktop machine, as detailed in my sig. Second is my Fujitsu-Siemens Amilo Pro v3505 Laptop.

Edit: Forgot to say what a damn cool utility bootchart is! Never seen anything like it before.

---

### Post by Lostincyberspace on 2007-11-07
this is really neat I never realized how fast it was till now

---

### Post by klange on 2007-11-07
I think I win for longest *regular* boot cycle.
Gutsy on my laptop. Dual 1.73ghz, 1gb of ram.
Total time: one minute, forty five seconds.

---

### Post by reacocard on 2007-11-08
> **WindowsSucks said:**
> I think I win for longest *regular* boot cycle.
Gutsy on my laptop. Dual 1.73ghz, 1gb of ram.
Total time: one minute, forty five seconds.

not really, bootchart appears to not be stopping when it should, if you examine the chart closely, gdm/xorg starts up at about 30s, on par with many other people's untweaked results.

---

### Post by aaargh486 on 2007-12-06
Do I win? Do I get a prize now? :)

30 sec from BIOS to GRUB (that's gotta something wrong)
17 sec from GRUB to login
few seconds to login

---

### Post by ushills on 2007-12-06
Any suggestions to improve this, specs for box 1 in sig.

---

### Post by bobbocanfly on 2007-12-06
Quite proud of this one. Got it down from 20 to 18 by disabling the laptop stuff but dont want to take any more out as this is my desktop and i want all the GUI tricks i can get :D

---

### Post by nat6138 on 2007-12-06
Not too shabby considering the specs of my laptop aren't the greatest.

---

### Post by dimbulb1024 on 2007-12-06
I'm in at 22 seconds

---

### Post by neoraptor on 2007-12-08
Here is mine :

How could I improve it? How could I tweak it? How could I disable some services (eg : I have no printer, so I would like to disable cups)

---

### Post by bobbocanfly on 2007-12-08
> **neoraptor said:**
> Here is mine :

How could I improve it? How could I tweak it? How could I disable some services (eg : I have no printer, so I would like to disable cups)

Use BUM (Boot Up Manager) (sudo apt-get install bum) to remove services from startup. A lot of it is Laptop/Wireless stuff which obviously, if its a wired desktop, is totally useless.

---

### Post by neoraptor on 2007-12-08
Thank you.
Is there no way to improve gnome startup speed?

---

### Post by markp1989 on 2007-12-14
boot up time is fast, i just wish i could speed up login time, 

i tried this [http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651) but didnt make much difference, does anyone know how i can speed up login time, i am currently using compiz fusion effects, and i have noticed every time i login the panels appear, then disappear, resulting in a login time of about 30seconds which is longer then my boot time

---

### Post by ~LoKe on 2007-12-16
I'd like to get 20 seconds or under.  Is there anything on the list that I could afford to remove?

---

### Post by Lostincyberspace on 2007-12-16
> **~LoKe said:**
> I'd like to get 20 seconds or under.  Is there anything on the list that I could afford to remove?
I used this how to and I sped up about 10 seconds
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

I don't know if that is of any help though? You don't have to many extra processes. The best thing you could probably do to speed up your time right now is upgrade your processor.

---

### Post by ~LoKe on 2007-12-16
> **Lostincyberspace said:**
> I used this how to and I sped up about 10 seconds
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

I don't know if that is of any help though? You don't have to many extra processes. The best thing you could probably do to speed up your time right now is upgrade your processor.

I used that guide, actually.  Worked out pretty well. =]

As for upgrading the processor...well...I can't really afford much faster than my 3.6GHz Q6600. =p

---

### Post by reacocard on 2007-12-16
> **~LoKe said:**
> I'd like to get 20 seconds or under.  Is there anything on the list that I could afford to remove?

you're already at 22s, it's difficult to improve on that. the part between 'S20exim4' and 'update-binfmts' might have a few things you could remove (privoxy seems to be taking a few seconds on its own), but everything else is pretty much needed. (except for sysklogd and klogd, but those are so tiny you won't get more than a fractional improvement)


For those looking to speed up their login time, not just boot time, take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=565651"). It sped up my login time immensely.

---

### Post by new2*buntu on 2007-12-16
Here is mine with Linux Mint XFCE 4.0 (I know it says Gutsy Gibbon). I have applied no tweaks and it was done with the laptop in my sig. I am satisfied with my 36 seconds, though.

---

### Post by Lostincyberspace on 2007-12-16
My latest reboot configuration I have since removed a few more processes. Not to bad I hope to shave another second or two off.

---

### Post by coolbrook on 2007-12-17
Without any optimization I get 0:29 on the first PC in my sig.  I noticed my desktop wallpaper didn't load.  I had to run a couple of terminal commands to start up my wireless.  I'll have a look at what I can tweak.  I don't wanna break anything.

---

### Post by fatality_uk on 2007-12-17
Somethings gone wrong with mine? Duel boot error maybe?

---

### Post by coolbrook on 2007-12-17
OK so I did some tweaking and it showed 0:30, now it's at 0:27, but now I'm getting a HAL failure error.  When I try to reboot, I click on the green man and it takes about 15 seconds for the exit options to come up.  I also noticed that I don't see my normal file system icon any more.  Just 'dev'.

---

### Post by coolbrook on 2007-12-17
> **coolbrook said:**
> OK so I did some tweaking and it showed 0:30, now it's at 0:27, but now I'm getting a HAL failure error.  When I try to reboot, I click on the green man and it takes about 15 seconds for the exit options to come up.  I also noticed that I don't see my normal file system icon any more.  Just 'dev'.

I changed concurrency from shell back to none and that removed the error and that terrible (actually almost 30 second) lag after clicking the green man.

---

### Post by Dr Small on 2007-12-17
My system finally rebooted, so here is my bootchart.

---

### Post by reacocard on 2007-12-17
> **fatality_uk said:**
> Somethings gone wrong with mine? Duel boot error maybe?

MS windows in 29 seconds on a PIII?


:lolflag:

---

### Post by -grubby on 2007-12-17
I had not idea that my boot time was so low (36 secs) I thought it was higher

---

### Post by Lostincyberspace on 2007-12-17
You might be including login time for your estimate.

---

### Post by popch on 2007-12-17
Racing computer with 1GHz. Zero to 100 in 31 secs.

---

### Post by new2*buntu on 2007-12-21
Here is mine (untweaked and on the system in my sig):

---

### Post by Adtk on 2007-12-22
Anybody got any advice on why my load is quite so slow?  

(Given that the machine is old, can it run any faster?)


Running Ubuntu 7.10
Pentium4, 1.8 Ghz
2 GB RAM
Boots of an old (40 GB) IDE drive
also has a PCI SATA II card with 2 500 GB drives (Software RAID 1)

---

### Post by mellowd on 2007-12-22
20 seconds. untweaked. This is my server and doesn't load X of course.

---

### Post by reacocard on 2007-12-22
> **Adtk said:**
> Anybody got any advice on why my load is quite so slow?  

(Given that the machine is old, can it run any faster?)


Running Ubuntu 7.10
Pentium4, 1.8 Ghz
2 GB RAM
Boots of an old (40 GB) IDE drive
also has a PCI SATA II card with 2 500 GB drives (Software RAID 1)

looks like you're having that odd usplash issue. next time you boot, try this: at grub (right before the pretty ubuntu progressbar starts up, but after the BIOS), press ESC to get the menu (if necessary), then press 'e' (for 'edit'), then use the arrow keys to select the 'kernel' line, press 'e' again, and use the arrow keys and backspace to remove the word 'splash' from this line. Press enter, and then press 'b' to boot with this modification. If you boot is much faster now, you can make this permanent by editing your /boot/grub/menu.lst file's defoptions line to also not have 'splash' in it, and then run 'sudo update-grub' in a terminal.

---

### Post by Adtk on 2007-12-23
reacocard, many thanks!

Will try that shortly.  I don't actually get any progress bar ....

This is what I see:
Bios boot up
Raid card
Grub count down
then black

eventually kicks in to the desktop (I have auto login enabled)

I'll try your suggestion and let you know.
Many thanks for the suggestion!

---

### Post by Adtk on 2007-12-23
reacocard,

Wow, that seems to have halved my boot time!

And rather than a black screen for a minute I now at least have feedback.

Many thanks for the solution!

---

### Post by m0rphex on 2007-12-23
Here is my Debian. It's minimalistic since this box is pretty old :D But how could I improve the disk throughput speed? Otherwise I'm pretty proud of the time :cool:

---

### Post by reacocard on 2007-12-24
> **m0rphex said:**
> Here is my Debian. It's minimalistic since this box is pretty old :D But how could I improve the disk throughput speed? Otherwise I'm pretty proud of the time :cool:

do you have DMA enabled on the drive? (hdparm -i can tell you) If not, enabling that would probably give you a substantial speed increase.

---

### Post by m0rphex on 2007-12-24
Yeah I have it enabled :/

---

### Post by p_quarles on 2007-12-24
A few minor tweaks, and I'm sure I could get it loading up faster if I tried. Meh. I'm lazy.

---

### Post by mozillar on 2007-12-28
Managed to get down to 22 seconds. If only I could reduce the 12 second time from power on to grub starting. Still, 34 seconds from pressing the power button to a usable desktop is plenty fast for me. :)

---

### Post by -grubby on 2008-01-06
I just can't get it under 35 seconds!

---

### Post by Spanarn on 2008-01-06
Is 23s ok for a lapptop?

Its an HP nx9420 and i have 2GB or RAM, and I changed the hard drive to a Seagate Momentus 7200.2 ST9200420ASG 16MB 200GB

hdparm with unmodified settings gives,
 Timing cached reads:   1984 MB in  2.00 seconds = 992,30 MB/sec
 Timing buffered disk reads:  174 MB in  3.02 seconds =  57.54 MB/sec


/Daniel

---

### Post by Waappu on 2008-01-06
Hi

Here is mine

---

### Post by ~LoKe on 2008-01-06
16 seconds.  Gotta try to hit 15!

---

### Post by revenant_org on 2008-01-06
here is mine;

---

### Post by mcduck on 2008-01-07
Here's one from my laptop with Core Duo 1,6GHz, 1GB of RAM and a horribly slow 5400rpm hard drive..

I haven't really bothered turning any services off, so I could probably easily cut some seconds off the time. But I think 29 seconds is quite OK anyway..

---

### Post by Waappu on 2008-01-07
> **~LoKe said:**
> 16 seconds.  Gotta try to hit 15!

HI

Did you get below 16 ?

Here is mine "normal" boot

You can see there is Oracle and ssh that slow things down =)

---

### Post by ~LoKe on 2008-01-07
> **Waappu said:**
> HI

Did you get below 16 ?

Here is mine "normal" boot

You can see there is Oracle and ssh that slow things down =)

Nope, 16 is still my lowest.  Time for desperate measures!

---

### Post by iPower on 2008-01-07
mine :)

---

### Post by AbredPeytr on 2008-01-13
Ubuntu 7.10 64-bit (Ubuntu Studio)

HP Pavilion dv5053EA, ATI Radeo Xpress 200M
AMD Turion, 1GB RAM, 20 GB Linux/55 GB Windows

---

### Post by -grubby on 2008-01-13
32 seconds! at least it's an improvement

---

### Post by kodak on 2008-01-13
any good?

---

### Post by hhhhhx on 2008-01-13
[IMG]http://stashbox.org/71730/gutsy-20080113-1.png[/IMG]

---

### Post by rahul_bhise on 2008-01-15
hear is mine i have problems while booting up. like scrambled images, blank screen, crashing. though not every time

---

### Post by Waappu on 2008-01-15
> **rahul_bhise said:**
> hear is mine i have problems while booting up. like scrambled images, blank screen, crashing. though not every time

Hi

See if this helps
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)

---

### Post by Lostincyberspace on 2008-01-22
yay 24 seconds not to shabby for not doing any thing to it yet.

---

### Post by aaargh486 on 2008-01-22
I'm going to post a new one. I compiled about every driver I needed hardcoded in the kernel. Next time I booted:lolflag:

It looks like letting udev and readahead work at the same time could save a couple of seconds. I'll be back.

---

### Post by p_quarles on 2008-01-22
> **aaargh486 said:**
> I'm going to post a new one. I compiled about every driver I needed hardcoded in the kernel. Next time I booted:lolflag:

It looks like letting udev and readahead work at the same time could save a couple of seconds. I'll be back.
We have a winner. Good work. :)

---

### Post by Lostincyberspace on 2008-01-22
11 seconds wow that is fast I wonder if it is possible to boot in 1 second.

---

### Post by reacocard on 2008-01-22
> **Lostincyberspace said:**
> 11 seconds wow that is fast I wonder if it is possible to boot in 1 second.

probably not, unless you stripped out almost everything and had a VERY fast disk to boot from. 11 seconds is quite impressive.

---

### Post by Lostincyberspace on 2008-01-22
I was thinking maybe solid state hard drives and reconfigureing the kernel might even have to rewrite the kernel to run multiple things at a time on boot better.

---

### Post by andrewabc on 2008-01-22
25 seconds with a buggy Hardy.

---

### Post by gotthardt on 2008-01-24
Here's mine:

---

### Post by ~LoKe on 2008-01-24
Now I have to beat 12 seconds?  DAMN IT!

---

### Post by ~LoKe on 2008-01-24
14seconds.  Gonna recompile the kernel and hopefully get a few seconds.

---

### Post by markp1989 on 2008-01-24
> **aaargh486 said:**
> I'm going to post a new one. I compiled about every driver I needed hardcoded in the kernel. Next time I booted:lolflag:

It looks like letting udev and readahead work at the same time could save a couple of seconds. I'll be back.

thats excellent, would love it if i could boot that fast, well done!!

here is my chart, 19 seconds

---

### Post by ~LoKe on 2008-01-24
13 seconds.  I tried a few things, guess a re-compile is necessary.

---

### Post by markp1989 on 2008-01-24
how did you people get your boot time down to about 11 seconds?  

let me know your secret

---

### Post by ~LoKe on 2008-01-24
Do I win?

---

### Post by ~LoKe on 2008-01-26
Come on, someone beat me!  I need motivation to cut it down even more.

---

### Post by markp1989 on 2008-01-26
> **~LoKe said:**
> Come on, someone beat me!  I need motivation to cut it down even more.

tell me how you got it that low in the first place, and i mite be able to

---

### Post by Lostincyberspace on 2008-01-26
> **~LoKe said:**
> Do I win?
It is currently a tie 2 people have an 11 second boot time

---

### Post by ~LoKe on 2008-01-26
> **Lostincyberspace said:**
> It is currently a tie 2 people have an 11 second boot time

Who else has 11 seconds?  People are saying 11 seconds for [this](http://ubuntuforums.org/showthread.php?p=4186194#post4186194) guy, but his image clearly says 12.

---

### Post by Gigamo on 2008-01-26
I had expected it to be faster. :(

---

### Post by Lostincyberspace on 2008-01-26
@Loke:I was mistaken You are the current winner.

---

### Post by tuebinger on 2008-01-26
Well, here's mine... I guess there's no competition from me.

---

### Post by Lostincyberspace on 2008-01-26
I just did mine without tweaking 25 seconds isn't to bad

---

### Post by markp1989 on 2008-01-26
here is my current boot chart, does anyone know what i can cut out or change to make boot faster?

---

### Post by Kevbert on 2008-01-26
My 64bit Ubuntu bootchart.

---

### Post by Lostincyberspace on 2008-01-26
recompile the kernel? I also have a few howtos I am going through right not to see how fast it can boot up. Once I am done I will post the linkss.

---

### Post by ~LoKe on 2008-01-26
I got 11 seconds with the unmodified 2.6.24 32bit kernel.  So I didn't get the speed from there.  On that topic: which modules in the kernel take up the most time, that are usually unnecessary?

---

### Post by markp1989 on 2008-01-26
> **Lostincyberspace said:**
> recompile the kernel? I also have a few howtos I am going through right not to see how fast it can boot up. Once I am done I will post the linkss.

thanks :)

never compiled a kernel before, so im kinda nervous doing it, but il give it a go

here is the spec of my machine what would i have to disable/enable to help boot time:
acer aspire sa85 f870
2gb ram
intel celeron D 352 3.2ghz 
nvidia geforce 6200 256mb
motherboard: ECS 661fx-m7 REV1.2a  Details here [http://www.newegg.com/Product/Product.asp?Item=N82E16813135171](http://www.newegg.com/Product/Product.asp?Item=N82E16813135171)

---

### Post by Gigamo on 2008-01-26
How would I go about recompiling my kernel to increase boottime? And how would it increase boottime? I'm kinda new to this. :D

I'm using a T7700 laptop CPU if that is any help, currently booting at 24 seconds. I have followed the guide to turn unnecessary services off.

---

### Post by Lostincyberspace on 2008-01-26
You should also follow this guide
[http://ubuntuforums.org/showthread.php?t=254263&highlight=boot](http://ubuntuforums.org/showthread.php?t=254263&highlight=boot)
Before you recompile the kernel
I am right now working on getting initNG to work It inst loading my network card for some reason? or bootchart but that should be easy to fix.

---

### Post by Gigamo on 2008-01-26
> **Lostincyberspace said:**
> You should also follow this guide
[http://ubuntuforums.org/showthread.php?t=254263&highlight=boot](http://ubuntuforums.org/showthread.php?t=254263&highlight=boot)
Before you recompile the kernel
I am right now working on getting initNG to work It inst loading my network card for some reason? or bootchart but that should be easy to fix.


Hmm, that didn't really help. Instead, it gave me a 6second longer boot. :D

---

### Post by Lostincyberspace on 2008-01-26
did you remove profile after booting through once the profile one will be longer but you need to only boot and then reboot without for it to work right

---

### Post by Gigamo on 2008-01-26
I just added the word profile to my boot line, it hung for a while on "preparing to profile boot sequence". then I logged in (no gdm) and sudo shutdown -r now. And that reboot was 6 secs longer than the one before profiling. :)

---

### Post by ~LoKe on 2008-01-26
> **Gigamo said:**
> I just added the word profile to my boot line, it hung for a while on "preparing to profile boot sequence". then I logged in (no gdm) and sudo shutdown -r now. And that reboot was 6 secs longer than the one before profiling. :)

Check for the cause in your bootchart.  It shouldn't increase boot time.

---

### Post by Lostincyberspace on 2008-01-26
You need to reboot before you log in for it to work right I believe.

---

### Post by Gigamo on 2008-01-26
> **Lostincyberspace said:**
> You need to reboot before you log in for it to work right I believe.

Well, I cant reboot without logging in unless I press the reset button. I'm not using GDM so logging in doesnt start X or anything else, it just brings me to the CLI.

My bootchart shows like 15 seconds of readahead and nothing else. Maybe its a bootchart from the profiling boot? That would be weird since I only have one bootchart from those 2 reboots (1 normal and 1 profiled).

---

### Post by Lostincyberspace on 2008-01-26
have you rebooted since? Because it is the time after that you get the benefits.

---

### Post by Gigamo on 2008-01-26
> **Lostincyberspace said:**
> have you rebooted since? Because it is the time after that you get the benefits.

Yes. I'll explain again.

I rebooted my pc, entered grub boot options, added profile, and did the profile boot. Then I rebooted again (with shutdown -r now from the fullscreen bash), and this boot was also longer than before the profiling. After that I didn't reboot yet, no.

However, I only have one bootchart from one of those two boots (don't know which one, they were both longer). The only thing I know is that the bootchart says 30 sec and before it was 24sec. :D

---

### Post by Gigamo on 2008-01-26
I just rebooted again now, and now its 36 seconds. This is nice.

From 24 seconds to 36 seconds :D

---

### Post by phenest on 2008-01-26
From 24 seconds to 18 seconds.

I do believe we need some ground rules if this is to be a competition. Some here are claiming fast times, but they are not booting to a graphical screen.

Can anyone suggest how to get my times down?

---

### Post by ~LoKe on 2008-01-26
> **phenest said:**
> From 24 seconds to 18 seconds.
Some here are claiming fast times, but they are not booting to a graphical screen.

So we should be required to use GDM to qualify? :confused:

I think the single requirement is that you must have a **fully functional** system after booting.

---

### Post by phenest on 2008-01-26
> **~LoKe said:**
> So we should be required to use GDM to qualify? :confused:

I think the single requirement is that you must have a **fully functional** system after booting.

The reason I say this is because someone has claimed 12 seconds WITH xorg, and the 11 second was without.

Perhaps 2 groups: Those with xorg and those without.

---

### Post by Gigamo on 2008-01-27
So I guess I know whats causing my longer boot time now; its "readahead-list" taking up fifteen seconds, and nothing else happens while it does that. How do I disable this?

---

### Post by Lostincyberspace on 2008-01-27
In this howto you can do it.

[http://ubuntuforums.org/showthread.php?t=89491&highlight=boot](http://ubuntuforums.org/showthread.php?t=89491&highlight=boot)

---

### Post by Gigamo on 2008-01-27
> **Lostincyberspace said:**
> In this howto you can do it.

[http://ubuntuforums.org/showthread.php?t=89491&highlight=boot](http://ubuntuforums.org/showthread.php?t=89491&highlight=boot)

Should have known to look there, I followed that guide earlier and enabled readahead :lolflag:

Thanks! Back at 25 sec now.

---

### Post by Lostincyberspace on 2008-01-27
Your welcome I figured you just forgot to look there. You might try initNG to get down even faster.

[http://ubuntuforums.org/showthread.php?t=144831](http://ubuntuforums.org/showthread.php?t=144831)

Make sure you make a new section for it in grub or else it could be hard to trouble shoot.

---

### Post by markp1989 on 2008-01-27
im using initng, and it cut my boot time from 20 sec to about 13/12, but i dont know how to get bootchart to work with initng, any one has any ideas?


here is my default.runlevel config file:

```
daemon/acpid
daemon/dbus
daemon/syslogd
net/all
system
system/alsasound
system/alsasound/cards
system/alsasound/mixerstate
system/console-screen
daemon/hald
system/usb
system/swap
system/modules/depmod
daemon/gdm
daemon/NetworkManager

```


anything i can cut out or add to increase boot time?

---

### Post by Lostincyberspace on 2008-02-03
Here is my latest 13 seconds not bad for no tweaks though.

---

### Post by gletob on 2008-02-03
any tips on speeding up my boot time?  I disabled the bluetooth stuff since I don't use bluetooth

---

### Post by Milos_SD on 2008-02-15
Here is mine:

Intel Core2Duo E6550 2.33 Ghz
2x1GB dual channel 800Mhz
WD3200AAKS 320GB SATA2

Is this good for this system? I didn't used any optimizations. :)

---

### Post by k2t0f12d on 2008-02-15
> **Milos_SD said:**
> Here is mine:

Intel Core2Duo E6550 2.33 Ghz
2x1GB dual channel 800Mhz
WD3200AAKS 320GB SATA2

Is this good for this system? I didn't used any optimizations. :)

Not too shabby

EDIT: removed attachment, see the image in the next post provided through a third party host.

---

### Post by k2t0f12d on 2008-02-15
Without nfs and samba daemons  :D

[[IMG]http://img81.imageshack.us/img81/5931/bootchartqh2.th.png[/IMG]](http://img81.imageshack.us/my.php?image=bootchartqh2.png)

---

### Post by tehquickness on 2008-02-16
Dell Inspiron 9100
P4 3.2 Ghz 
1Gb Ram
Linux Mint 4.0

What are the depmod and readahead-list processes doing?? Those seem to access the disk the most.

[[IMG]http://ryangathmann.com/gutsy-small.png[/IMG]]("http://ryangathmann.com/gutsy-20080215-4.png")

---

### Post by k2t0f12d on 2008-02-16
If Im not mistaken, depmod is loading kernel modlues that drive your devices.

---

### Post by Superkoop on 2008-02-16
First one to the left is the chart before any optimizations.  The second one is after I disabled some stuff, there may be some other things that I don't use, but under 30 seconds is plenty good enough for me. =)

---

### Post by markp1989 on 2008-03-06
i think i have my boot down to around 11 seconds, using icebuntu and initng, but i dont know how to use bootchart to time initng, any one know how i do this?

---

### Post by ElEdwards on 2008-03-07
Here's mine.  Is it good? :)

---

### Post by andrewabc on 2008-03-22
Ubuntu hardy beta 1.
1.8ghz pentium4, 768 mb ram (just put another 256mb in yesterday).
Takes 48 seconds to start.

---

### Post by spupy on 2008-03-22
Whoa, mine is so short (as in height). Something is fishy, it normally is ~5s shorter.

---

### Post by Frak on 2008-03-22
> **andrewabc said:**
> Ubuntu hardy beta 1.
1.8ghz pentium4, 768 mb ram (just put another 256mb in yesterday).
Takes 48 seconds to start.
Nice specs. Same as mine. This now leads me to install boot-chart again and see how mine boots :)

---

### Post by spupy on 2008-03-22
Here is the real deal. Removed HAL and won 6 seconds!

---

### Post by Mazza558 on 2008-03-22
What the hell is happening for 30 seconds?!

(Hardy Beta)

---

### Post by reacocard on 2008-03-22
> **Mazza558 said:**
> What the hell is happening for 30 seconds?!

(Hardy Beta)

looks like udev is stalling, which is likely caused by some piece of hardware you have. try removing/disabling various pieces of hardware and see if you can figure out which is causing the problem.

---

### Post by wazzup on 2008-03-28
18 seconds (Gutsy)

- Use static network setup instead of DHCP,
- Disable isa pnp probing if unneeded (noisapnp to kernel command line)
- Reprofile readahead, 
- Disable usplash (remove "splash" from kernel cmdline)
- disabled avahi-deamon
- removed some other unused services (like samba, rsync, ntp, portmap)

(dualcore 2.3 Ghz / 4 GB RAM)

and this is with GDM :)

---

### Post by skymera on 2008-05-02
Ok heres mine :)
Anyway to tweak it? seems sluggish

---

### Post by reacocard on 2008-05-02
> **skymera said:**
> Ok heres mine :)
Anyway to tweak it? seems sluggish

84MB/s? That's a ridiculously fast HD you have.

I should bootchart my flash drive ubuntu install sometime, just for fun. Except I think bootchart needs java. :(

---

### Post by skymera on 2008-05-02
Ok tweaked some more.
Shaved it down to 16 seconds.

Update: 15seconds :)
1.86GHz Dual Core
3GB 533MHz RAM

---

### Post by seatex on 2008-05-02
Here's mine.

---

### Post by Amranu on 2008-05-12
Here's mine.

Ubuntu 8.04 64-bit

200gb 7200rpm HD

Anyway to speed this up?

---

### Post by Madman6510 on 2008-05-12
Here's mine

---

### Post by itmanvn on 2008-05-12
here's mine:lolflag:

---

### Post by ghindo on 2008-05-13
Still working on getting the time down.  :/  Regardless, this thread has helped a *lot*.  I'm learning a lot from it! :)

Any suggestions on how I can get my boot time down, from what the boot chart shows?

---

### Post by ghindo on 2008-05-14
> **~LoKe said:**
> 14seconds.  Gonna recompile the kernel and hopefully get a few seconds.What does recompiling the kernel do to speed up boot?  How do you recompile a kernel?

---

### Post by Frak on 2008-05-14
> **ghindo said:**
> What does recompiling the kernel do to speed up boot?  How do you recompile a kernel?
The faster your kernel and driver modules load, the faster your system loads (and performs)

[Kernel Check]("http://kcheck.sourceforge.net/") - Autokernel compiler for Ubuntu and other distributions

More [instructions]("http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html")

---

### Post by JHawk24821 on 2008-05-15
Processor:  Intel Core 2 Quad Q6600 @ 2.40GHz
Memory:  4,046MB
OS:  Ubuntu 8.04

/dev/sda1:  133.0 GiB total, 81.5 GiB free
/dev/md0:  1,848.3 GiB total, 1,753.7 GiB free

CPU ZLib:  23584.341
CPU Fibonacci:  4.162
CPU MD5:  59.783
CPU SHA1:  74.545
CPU Blowfish:  20.864
FPU Raytracing:  13.049

NOTE: nVidia graphics drivers not installed at this point, just got done building the array.  I will be tweaking and reposting.

---

### Post by ghindo on 2008-05-15
> **Frak said:**
> The faster your kernel and driver modules load, the faster your system loads (and performs)

[Kernel Check]("http://kcheck.sourceforge.net/") - Autokernel compiler for Ubuntu and other distributions

More [instructions]("http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html")Thanks for the help, but upgrading to the latest kernel just broke my wireless.  :(  Had to revert back, but I suppose it was worth a shot.

I gotta say, I'm stumped.  I've followed every guide linked in this thread, but can't get my boot time under 40 seconds.  I thought my hardware was pretty good, so I'm not sure what's going on.

Could someone help me out please?

---

### Post by hyper_ch on 2008-05-15
1:00 on an old 1.6 Ghz Sempron with a fully encrypted filesystem

---

### Post by smartboyathome on 2008-05-15
> **Amranu said:**
> Here's mine.

Ubuntu 8.04 64-bit

200gb 7200rpm HD

Anyway to speed this up?

Wow that's fast! :D I don't know about how to do this on Ubuntu, but in arch you can edit rc.conf and make some jobs load in the background. I don't think you need this though.

---

### Post by smartboyathome on 2008-05-15
> **ghindo said:**
> Thanks for the help, but upgrading to the latest kernel just broke my wireless.  :(  Had to revert back, but I suppose it was worth a shot.

I gotta say, I'm stumped.  I've followed every guide linked in this thread, but can't get my boot time under 40 seconds.  I thought my hardware was pretty good, so I'm not sure what's going on.

Could someone help me out please?

Just saw your post. Try BUM - boot up manager. It allows you to disable stuff which would be loaded at boot up. This can save some time off your boot up.

---

### Post by ghindo on 2008-05-16
> **smartboyathome said:**
> Just saw your post. Try BUM - boot up manager. It allows you to disable stuff which would be loaded at boot up. This can save some time off your boot up.Already messed around with it to no avail.  :(  I'm beginning to consider a fresh start anyway, so I may just do that...

---

### Post by Polomint01 on 2008-06-26
Hi

When my pc boots up it starts in the gui then switches to the verbose mode.
I notice I have a [COLOR="Red"]fail[/COLOR],but its to quick for me to notice.
Ubuntu runs fine, but I would like to know what is failing to start.

Paul

---

### Post by fatality_uk on 2008-06-26
1 characters.

---

### Post by master_kernel on 2008-06-27
Shiny new kernel...

---

### Post by markp1989 on 2008-07-05
on my deasktop

Hardy, started with cli install then added packages, uses openbox 

would like to get it faster, any thing i can remove from startup?


Edit: I noticed that during boot up, there is some output saying "activating swap" , i dont have a swap partition, so i should be able to remove that from startup right?

---

### Post by markp1989 on 2008-08-10
here is mine: 

fujitsu siemens amilo pro v2030, just replaced the sata hard drive with a 2gb CF card

ubuntu hardy 32bit

openbox

15 sec, would love to get it faster, but i dont think i can

---

### Post by freonchill on 2008-08-17
dell 1150 laptop
p4m 2.8ghz
1280mb pc3200 ddr
60gb seagate 5400rpm (ST960815A)
dell g-wifi w/ restricted driver

---

### Post by mkarnicki on 2008-08-17
HP tx1320us
AMD Turion(tm) 64 2cores 2Gz
2GB of RAM
250GB of HDD
ndiswrapper for wireless

Can I remove anything that you think I might not use? (I use wi-fi and bluetooth).

---

### Post by markp1989 on 2008-08-17
heres  mine, same laptop/setup, only difference is replaced nm-applet with wicd, lighter, but made  boot times slower.

udev spends about 30% of boot time as a zombie, if i could stop this i could speed up boot time alot!

---

### Post by stinger30au on 2008-08-17
heres mine, a pentium 4 HT 3Ghz prescott with 1 gig ram and mainboot hdd is a 40 gig seagate.... nothing flash

---

### Post by markp1989 on 2008-09-18
here is my desktop, out of everything i have tried i cannot beat 15sec, its driving me mad, i think im abit obsessed lol 

3.2ghz Celeron D
2gb Ram
80gb SATA OS drive
160gb SATA data drive 
Nvidia 6200 256mb 
Hardy 32bit (i usually use 64bit picked up the wrong cd during the install)


wm: openbox
Display manager: none, autologin and startx : see here for details [http://ubuntuforums.org/archive/index.php/t-256120.html](http://ubuntuforums.org/archive/index.php/t-256120.html)

The only thing i can think of that may help is to compile my own kernel, add the nvidia drivers, and get rid of loads that i dont need , but i never successfully done that before

---

### Post by BeachBum on 2008-09-19
Hey all,

I posted in my own thread about a 10s delay in my initial boot which is frustrating me.  I'm not overly knowledgeable with boot up tweaking, but I have followed several guides successfully to shave a few seconds off my boot time.  My original thread is here: [http://ubuntuforums.org/showthread.php?p=5818874#post5818874](http://ubuntuforums.org/showthread.php?p=5818874#post5818874)

I REALLY appreciate any tips!

---

### Post by run1206 on 2008-09-23
here's my bootchart.  hoping to reduce the time, i'm gonna take out boinc-client;i don't really use it much. anything else i could take out, let me know.  I'm on a Toshiba Satellite A55 series.

---

### Post by ghindo on 2008-10-03
> **markp1989 said:**
> The only thing i can think of that may help is to compile my own kernel, add the nvidia drivers, and get rid of loads that i dont need , but i never successfully done that before**Adding** nVidia drivers can reduce boot time?  How's that work?

---

### Post by Frak on 2008-10-03
> **ghindo said:**
> **Adding** nVidia drivers can reduce boot time?  How's that work?
I was going to say "Add it into the kernel", but since the driver is proprietary, and Prop + GPL is a NO NO, I don't know how it would speed up boot time.

---

### Post by Patrick793 on 2008-10-03
I'm happy with the boot time.

---

### Post by VancouverCowboy on 2008-10-03
Greetings from Lotus Land.

Here's my chart.

My box:
HP dv9743CA Notebook PC
Core 2 Due T5450 (1.67 GHz)
250 GB 5400 RPM HDD (Dual boot with Vista BLECH)
2 GB DDR2 SDRAM
GeForce 8600M GS 512 MB DDR

My boot is slow.  After I log in it takes forever again.  Any help is greatly appreciated.

---

### Post by Livid on 2008-10-05
run1206:
Actually, your hard disk is a bit too slow, installing a faster one can give you a significant boost. Not sure it's technically possible in your case though.
---
As for me, after some tweaking, I've got a nice 20-second boost.
Mayhap, it's possible to win two or three seconds more omitting those various sleeps in my boot sequence.

---

### Post by markp1989 on 2008-10-06
3.2ghz Celeron D
2gb Ram
80gb SATA OS drive
160gb SATA data drive 
Nvidia 6200 256mb 
arch 64bit
wm: compiz

---

### Post by run1206 on 2008-10-06
> **Livid said:**
> run1206:
Actually, your hard disk is a bit too slow, installing a faster one can give you a significant boost. Not sure it's technically possible in your case though.

i probably couldn't increase the speed any faster in terms of the hardware, it's from '05 and is a single processor. don't know too many people who swap out HDDs in laptops either :?

i have yet to check my bootchart since i've upgraded to Intrepid, though the networking processes hold the boot for about a minute.

---

### Post by eragon100 on 2008-10-06
Intel core 2 duo e 6300 @ 1.86 GHZ

3 GB ram DDR2-533

512 MB GeForce 8 8600 GT

32 second boottime, no tweaks. Are there any good tips  / tricks / tutorials etc. Around here to get it to boot faster?

---

### Post by ghindo on 2008-10-06
> **eragon100 said:**
> Are there any good tips  / tricks / tutorials etc. Around here to get it to boot faster?There are more in this thread than I can list.  Just take a look around ;)

---

### Post by Frak on 2008-10-06
> **run1206 said:**
> i probably couldn't increase the speed any faster in terms of the hardware, it's from '05 and is a single processor. don't know too many people who swap out HDDs in laptops either :?

i have yet to check my bootchart since i've upgraded to Intrepid, though the networking processes hold the boot for about a minute.
Buy a SCSI drive controller and 2 SCSI drives and run them with RAID 0.

Can't get much faster than that.

---

### Post by klange on 2008-10-06
[[img]http://oasis-games.com/gallery.php?do=img&type=thumb&i=21[/img]](http://oasis-games.com/gallery.php?do=img&i=21)
1:02 is good enough for me.

---

### Post by justsomedude on 2008-10-06
Athlon X2

884 MB RAM

(Laptop)


Arch Linux (Gnome)

16 s

---

### Post by crexor on 2008-10-20
16 seconds is the best I can seem to get too, not sure if there is some of this stuff i can dump either, maybe the ksuspend, and that other junk...it looks like my 6 disk raid array in xfs might be slowing down boot up too, any tips from anyone?

---

### Post by steveydoteu on 2008-10-20
Still tweaking Intrepid at the moment, but was wondering if anyone could point me in the direction of some HOWTOs for setting up Openbox?

---

### Post by speedkreature on 2008-10-20
New install, no optimizations whatsoever.  
This is on an IBM T43, with an SSD replacing the OEM harddisk.
Boot times can be as low as 13 seconds--or, at least that's the fastest I've been able to to get it.
My experience shows however that you can't do much optimizations before you start having issues with some services not starting properly on T43's with non-approved hard drives installed.  For example, at it's fastest; once booted, I had to manually restart bluetooth and NetworkManager (0.7.x)

IBM does warn of potential instability when replacing OEM equipment with non-OEM parts.  C'est la vie.

---

### Post by steveydoteu on 2008-10-21
Voilà.

I am curious if I can get it under twenty seconds.

I've removed all unnecessary services at run level, profiled the boot, removed the splashes and such.

Any suggestions for things to tweak?

Granted its not important as its a fast boot anyhow, just intrigued how quick I can get it.

---

### Post by MyBlueSkies on 2008-10-26
before i made changes it was 36 secs

---

### Post by Sealbhach on 2008-10-26
My bootchart with Intrepid.

---

### Post by Old_Grey_Wolf on 2008-10-26
I'm happy with mine. Now I know why I hate booting Vista.

---

### Post by TheBigT on 2008-10-27
Here you go

---

### Post by andrewabc on 2008-10-27
> **TheBigT said:**
> Here you go

Umm, what is making it take 1:36 with a decent core2duo?
It is loading firefox? is this a custom boot chart that shows until it is at desktop with everything loaded? I thougth boot chart only did until login.

My core2duo g965 x3000 takes around 25 seconds.

---

### Post by klange on 2008-10-27
[[img]http://ogunderground.com/gallery.php?do=img&type=thumb&i=1[/img]](http://ogunderground.com/gallery.php?do=img&i=1)

52 seconds, with lots of extra crap I don't need.

---

### Post by Old_Grey_Wolf on 2008-10-27
Deleted.

---

### Post by markp1989 on 2008-10-28
3.2ghz Celeron D
2gb Ram
80gb SATA OS drive
160gb SATA data drive 
Nvidia 6200 256mb 
Hardy 64bit

wm: openbox
Display manager: none, autologin and startx : see here for details [http://ubuntuforums.org/archive/index.php/t-256120.html](http://ubuntuforums.org/archive/index.php/t-256120.html)

Is there any way i can stop udev from being a zombie?

---

### Post by markp1989 on 2008-11-03
Same setup as above, just using arch

---

### Post by Toe on 2008-11-03
With some opimizations like disabling unnecessary services (bluetooth, printing, samba), using concurrency=shell and switching from dhcp to a static ip address, I've managed to get down to 33 seconds.

This PC has been running development releases since one of the early Hardy alphas, so it could probably be made even faster by a clean install.

---

### Post by benow on 2008-11-03
22s for intrepid on an Mtron 7500/AMD64/Nvidia :)

Not overly optimized, suggestions welcome.

---

### Post by aard on 2008-11-04
So this is my bootchart. And, yes, it's quite messed up. I'm fairly new to linux, so could anyone point out what's causing the huge waste of time during my boot? Any easy way to fix it?
I'm sorry if I'm asking this question in the wrong topic.

---

### Post by reacocard on 2008-11-04
> **aard said:**
> So this is my bootchart. And, yes, it's quite messed up. I'm fairly new to linux, so could anyone point out what's causing the huge waste of time during my boot? Any easy way to fix it?
I'm sorry if I'm asking this question in the wrong topic.

looks like your networking maybe? it's waiting on a dhcp address I think.

---

### Post by steveydoteu on 2008-11-04
Networking and the Usplash seem to be the culprits.

---

### Post by ak47gen on 2008-11-08
If I can get my bootchart down to 13 seconds and have it load all drivers that goes from bootload to GUI.  Is that hard to do?

---

### Post by markp1989 on 2008-11-20
3.2ghz Celeron D
2gb Ram
80gb SATA OS drive
160gb SATA data drive
Nvidia 6200 256mb
Arch 64bit

wm: openbox

Im planing to recompile my kernel soon, but i have never done it before

---

### Post by spamerfrommars900 on 2008-11-20
hi everyone, i have adhd! spank, spank, spank! hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahhahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahaha
hahahahahahahahahahahahahahahahahahahahahahahahahah
hahahahahahahahahahahahahahahahahahahahahahahahahah

---

### Post by seenxu on 2008-12-08
10sec is indeed fast...

---

### Post by seatex on 2008-12-08
Here is mine.  8)

---

### Post by ghindo on 2008-12-09
I'm getting pretty good at stripping down Ubuntu installs. 8)

---

### Post by Opeth on 2008-12-10
[http://i36.tinypic.com/2j1vq79.png](http://i36.tinypic.com/2j1vq79.png)

20 seconds... anything else see anything in there that I can do?

---

### Post by fiona-conn on 2008-12-10
Here be my bootchart.

---

### Post by Swagman on 2008-12-10
Here's mine.  Had to install it first  & reboot though.

---

### Post by Frak on 2008-12-27
35 seconds on an AMD X2 2.4GHz 4600+
The only thing holding back the times is the fact that I have a PATA 100 HD installed instead of a SATA II, which would decrease the times by a lot.

---

### Post by fwojciec on 2008-12-27
Desktop (22s) and laptop (15s).  Vanilla kernel 2.6.28.  Archlinux.

---

### Post by boomersooner on 2008-12-29
Here's mine, any suggestions are welcome - this is my first experience with linux ( for about a month now)

---

### Post by MikeTheC on 2008-12-29
But I don't have any boots!

No, check that. I actually *do*, but they're dress-ish boots which haven't fit me in many, many years. But I'm not making a chart of them, or from them.

Oh, wait a minute. You meant *boot*, as in "to boot-strap a system". Right. Now I got you. All the same, it means installing another program on my computer.

*groans*

Alright, but I'm gonna hafta reboot...

BBIAF...

---

### Post by MikeTheC on 2008-12-29
Here ya go.

Now, tell me the truth, is this like reading palms or tea leaves? I mean, it sure looks interesting but also is a bit above my head.

[[IMG]http://img75.imageshack.us/img75/8479/intrepid200812291xo4.th.png[/IMG]](http://img75.imageshack.us/my.php?image=intrepid200812291xo4.png)

---

### Post by Tares on 2008-12-29
here's my fresh 17s :>

---

### Post by Amranu on 2008-12-29
My arch linux bootchart :) (I don't have ubuntu installed)

---

### Post by ogcub on 2008-12-30
Mine,
Not sure what resume is doing there

---

### Post by markp1989 on 2008-12-30
agetty is where autologin takes place


edit: here is my last bootchart. [http://ubuntuforums.org/showpost.php?p=6219190&postcount=315](http://ubuntuforums.org/showpost.php?p=6219190&postcount=315) i have changed my router since that one, and havnt bothered setting static ip up yet, hence the slower boot.

---

### Post by thefirstM on 2009-01-03
Here is my bootchart.  (From Kubuntu Jaunty 64-bit).

As you can see, modprobe is completely killing my boot time.  Anybody have an idea on how to make it take less time?  I have also attached dmesg, lspci, and lsusb logs inside the zipfile.

---

### Post by sofasurfer on 2009-01-03
I have /var/log/boot which is empty. I do not have a /var/log/bootchart.
Where is it? What is it? What is the reason for comparing bootcharts?

---

### Post by thefirstM on 2009-01-04
You must install bootchart:

```
sudo aptitude install bootchart
```

---

### Post by Malta paul on 2009-01-04
Here is mine, not to bad for an old Computer I suppose.

---

### Post by Hybrid-photog on 2009-01-04
Here's mine.
[ATTACH]98674[/ATTACH]
As far as I can see, my old reiserfs partitions are slowing the startup down. Or it could just be my decrepit 2 80GB IBM IDE HDD's anyway.

---

### Post by sofasurfer on 2009-01-08
I installed 'bootchart'  and the directory /var/log/bootchart was created, but there is nothing in it even after a reboot. What am I missing?

---

### Post by smurfgod on 2009-01-08
[ATTACH]99140[/ATTACH]

heres mine and what does it mean???

---

### Post by sofasurfer on 2009-01-08
As long as this thread is, I can't believe nobody else but me could not figure out how to get bootchart to work.

Anyway, I found the answer and here it is for anyone who is having trouble not getting a chart... 

Taken from... [https://bugs.launchpad.net/ubuntu/+source/bootchart/+bug/185523](https://bugs.launchpad.net/ubuntu/+source/bootchart/+bug/185523)

1. when u install bootchart, you first need sun-java* installed and selected via
sudo update-alternatives --config java
2. After that, you must consider that we are using an initrd system (like Debian) so we need to regenerate initramfs for bootchart to works:
sudo update-initramfs -u -k kernel_name
..where kernel_name is:
uname -r

---

### Post by sertse on 2009-01-11
16 seconds.

when does bootchart stop logging btw; When I get the login? (I use a text login)

---

### Post by x-na on 2009-01-15
This is what I have. Quite slow boot.

---

### Post by WiTcHkInG on 2009-01-15
13 secs :P

---

### Post by seatex on 2009-01-18
Fresh 9.04 Alpha 3 install, and ext4 format on my notebook.  20 sec. boot time with standard installation config (no tweaking yet).  Notebook specs are in my sig below.  :)

---

### Post by Spr0k3t on 2009-01-23
Here's a fresh install of alpha3 on my system.  The only thing I've installed is bootchart.

I should install ext4 and try again.

---

### Post by BatPenguin on 2009-01-24
Wow, great thread. I've been wondering if I can do something to make this guy boot up faster. I'm not looking for these 15 second boot times many of you seem to be able to get, but it seems like the machine stops for up to 10 seconds twice during the boot (this is based on watching it, not the log), so I think this one minute boot could probably be cut down to 40 seconds or so.

This machine runs Mythtv and is quite a busy boy with Mythweb and everything. If I'm intrpreting the picture correctly, the start of Mysql takes about 10 seconds of sleeping. Modprobe seems to be going on for quite a while too. Any tips on how to start optimizing this? Thanks!

---

### Post by hard_i on 2009-01-24
14 sec / arch linux / ext4

[[img]http://www.upload.ee/thumb/7358/bootchart.png[/img]](http://www.upload.ee/image/7358/bootchart.png)

---

### Post by Procuro on 2009-01-24
I was wondering why it was taking 40 seconds for me to boot! It's because I was trying to find aliens on my computer :-|  Oh well, problem solved at least.

---

### Post by oomingmak on 2009-01-24
**12 seconds  **(to full desktop with GDM etc.)

[URL="http://i219.photobucket.com/albums/cc48/0omingmak/BootchartMintFelicia.png"][IMG]http://i219.photobucket.com/albums/cc48/0omingmak/BootchartMintFelicia.png[/IMG]
[/URL]


This is still much slower than my Windows boot time though.

---

### Post by rebegin on 2009-01-24
> **oomingmak said:**
> [B]12 seconds
[/B]

[URL="http://i219.photobucket.com/albums/cc48/0omingmak/BootchartMintFelicia.png"][IMG]http://i219.photobucket.com/albums/cc48/0omingmak/BootchartMintFelicia.png[/IMG]
[/URL]

nice one!
could you please share some tweaking ideas?
thanks in advance.

---

### Post by oomingmak on 2009-01-24
> **~LoKe said:**
> So we should be **required **to use GDM to qualify? :confused:

Yes. :tongue:

> **~LoKe said:**
>  I think the single requirement is that you must have a **fully functional** system after booting.
Well, you would say that wouldn't you? ;)

---

### Post by S0m3th1ngw13rd on 2009-01-24
my boot chart

---

### Post by millerah on 2009-01-30
Fresh default Jaunty install with splash disabled.  Notice I have a slower processor in my Inspiron 8600 laptop.

---

### Post by phrostbyte on 2009-01-30
> **millerah said:**
> Fresh default Jaunty install with splash disabled.  Notice I have a slower processor in my Inspiron 8600 laptop.

That's extremely impressive for the disk throughput rate / CPU you have.

---

### Post by run1206 on 2009-01-31
so i finally installed Intrepid on my Acer laptop
120GB SATA HDD
2GB Ram
Dual CPU @ 1.86GHz
here's my "stock" bootchart...

i'll try to further lower that time with the sysv-rc-conf tweak, hopefully i can hit sub-25 seconds, we'll see :)
i'm wondering if i should disable my splash as well :?

---

### Post by neo_1in on 2009-02-05
36 seconds...
P4 2.5 GHz, 768 MB RAM, nVidia GeForce 6200
Is is possible to bring this further down,...anyone....??

---

### Post by run1206 on 2009-02-05
> **neo_1in said:**
> 36 seconds...
P4 2.5 GHz, 768 MB RAM, nVidia GeForce 6200
Is is possible to bring this further down,...anyone....??

try either sysV-rc-conf...
```
sudo apt-get install sysv-rc-conf
```


```
sudo sysv-rc-conf
```
to run the program.  it will show the processes being run at bootup.

another option in BUM (Boot-Up Manager)
```
sudo apt-get install bum
```
this has a GUI which you can click which processes and services you want to run at startup.

i'm went from 32 to 26 seconds with eliminating processes i don't use.  good luck

---

### Post by Tomatz on 2009-02-05
Here is mine:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=102248&d=1233841572[/IMG]



32 seconds, not bad considering moblock and vmware are installed.



:)

---

### Post by run1206 on 2009-02-05
^ you're dual core... might get it even lower...

> **mb_webguy said:**
> Since you have a multi-core processor, you can set the boot process to use concurrency, which may significantly decrease boot time.

In the terminal, type "sudo gedit /etc/init.d/rc" and look for the line "CONCURRENCY=none".  Change this to "CONCURRENCY=shell", then save and exit.  The very next time you boot may not be much faster, but subsequent boots should be.  I have the same processor as you, and doing this cut my boot time significantly, to the point that booting is faster than login.

unless you already did this tweak before....

---

### Post by Tomatz on 2009-02-05
> **run1206 said:**
> ^ you're dual core... might get it even lower...

Already set to use both cores :(

---

### Post by neo_1in on 2009-02-05
Well its 34 seconds now, 2 sec drop in boot time, though overall time from grub to kde 4.2 dropped from around 98 secs to 85 secs, so *yay*!! thanks *run1206*

---

### Post by andrewabc on 2009-02-05
> **run1206 said:**
> ^ you're dual core... might get it even lower...



unless you already did this tweak before....

Before I did that it was 26 seconds.
Did that, and next boot was 24 seconds, and the boot after that it was 25 seconds. So not sure if it improved it much. Although I guess at 25 second range getting rid of 1 second is a 4% decrease in boot time.

Attached is most recent one.

---

### Post by D_one on 2009-02-08
There seems to be some sort of bottle-neck with s15moduule-init or modprobe at around 25 sec. where the cpu and disks stop, any suggestions?

---

### Post by thefirstM on 2009-02-08
You should post the output of "dmesg".  This might help to determine what is causing the problem.

---

### Post by Xbehave on 2009-02-08
Mines slow because ubuntu doesnt support rieserfs properly (seriously guys use ext3 instead isn't a fix)

also attached is a boot with a fsck, which shows why im on reiser (just an extra seconds including a ~90G and 6G fscks)

---

### Post by Stalker72 on 2009-02-10
Is there any way I can tweak mine?

Western Digital Black (1 TB, 7.2k RPM, 32 MB cache)
15 GB root (/) : JFS
500 GB /home : XFS
6 GB /var : ReiserFS
1 GB swap
Rest is for Windows (I'm a hardcore gamer)

Stalker72

---

### Post by glotz on 2009-02-10
Is this for an art project?

---

### Post by Onyros on 2009-02-10
16 second boot, I swear it was 1 second faster just a couple of days ago :P

It's an EEEPC 701, btw.

---

### Post by Xbehave on 2009-02-12
> **Stalker72 said:**
> Is there any way I can tweak mine?

Western Digital Black (1 TB, 7.2k RPM, 32 MB cache)
15 GB root (/) : JFS
500 GB /home : XFS
6 GB /var : ReiserFS
1 GB swap
Rest is for Windows (I'm a hardcore gamer)

Stalker72
looks like reiserfs is costing you a few seconds

---

### Post by Tomatz on 2009-02-15
> **Tomatz said:**
> Here is mine:

[http://ubuntuforums.org/attachment.php?attachmentid=102248&d=1233841572](http://ubuntuforums.org/attachment.php?attachmentid=102248&d=1233841572) ***[COLOR="Red"]_<-- Hardy bootchart._[/COLOR]***



32 seconds, not bad considering moblock and vmware are installed.



:)
[http://georgia.ubuntuforums.org/showthread.php?p=6681378](http://georgia.ubuntuforums.org/showthread.php?p=6681378)


I posted a while back with my bootchart results under Hardy. I am now running Kubuntu Jaunty x86/64 alpha with the ext4 filesystem and have shaved 12 seconds off my boot :guitar:

[IMG]http://georgia.ubuntuforums.org/attachment.php?attachmentid=103490&stc=1&d=1234737573[/IMG]

---

### Post by kiisu on 2009-02-17
Suggestions on what can be done for a faster boot? Is 39 sec. the fastest I can expect?
thanks all

---

### Post by SKLP on 2009-02-17
Latest Jaunty, ext4 root, on my laptop :)
15 second boot

---

### Post by gecko3940 on 2009-02-24
mine takes 60 seconds to orange/brown screen then another 20-25 seconds til all icons are on desktop. Too slow. Any ideas? Pentium 4 2.8ghz 533 FSB 1gig ram.

---

### Post by a0peter on 2009-02-25
Ext4 + Arch + Gnome = 12s

---

### Post by a0peter on 2009-03-07
> **a0peter said:**
> Ext4 + Arch + Gnome = 12s

I just broke my own, and possibly this threads record?! 9s!

[My bootchart]("http://farm4.static.flickr.com/3403/3335559297_2e53043737_o_d.png")
This is Ext4+Arch+MSI Wind+Startx

---

### Post by markp1989 on 2009-03-09
Arch: ext2 openbox
[img]http://i246.photobucket.com/albums/gg102/markp1989/bootchart-8.png[/img]

---

### Post by oomingmak on 2009-03-10
> **a0peter said:**
> I just broke my own, and possibly this threads record?! 9s!

This is Ext4+Arch+MSI Wind+Startx
Well if it was anything like your last post, I'd be interested to know how.

You got 12s (the same as me) but the chart that you attached shows a disk throughput of only [SIZE=3]**7MB/s**. My SSD was doing 146MB/s throughput to get 12 seconds, but that's to a full desktop (and on Ext3, not the newer Ext4).

[/SIZE]

---

### Post by a0peter on 2009-03-10
> **oomingmak said:**
> Well if it was anything like your last post, I'd be interested to know how.

You got 12s (the same as me) but the chart that you attached shows a disk throughput of only **7MB/s**. My SSD was doing 146MB/s throughput to get 12 seconds, but that's to a full desktop (and on Ext3, not the newer Ext4).


Linux Mint or Ubuntu for that sake, has put so many modules and daemons to run at startup, that it is no wonder they are slow. I have handpicked everything on my Arch installation (which isn't as hard as it sounds). The ArchWiki is filled with howtos for everything imaginable. For my optimization i used:
[Tweaking for a faster boot time]("http://wiki.archlinux.org/index.php/Tweaking_for_a_faster_boot_time") and [Start X at boot]("http://wiki.archlinux.org/index.php/Start_X_at_boot")

---

### Post by jiveaxe on 2009-03-12
Here mine:

Kubuntu Jaunty 64bit + Kernel 2.6.29-rc7 + ext4 = **19 sec**.

[[IMG]http://img17.imageshack.us/img17/5913/kubuntujaunty200903122.th.png[/IMG]](http://img17.imageshack.us/my.php?image=kubuntujaunty200903122.png)

Maybe someone as asked for this, yet:

Why 4 seconds at the beginning with no disk or cpu activity? Can be reduced or elimaned?

Bye

---

### Post by markp1989 on 2009-03-13
> **jiveaxe said:**
> Here mine:

Kubuntu Jaunty 64bit + Kernel 2.6.29-rc7 + ext4 = **19 sec**.

[[IMG]http://img17.imageshack.us/img17/5913/kubuntujaunty200903122.th.png[/IMG]](http://img17.imageshack.us/my.php?image=kubuntujaunty200903122.png)

Maybe someone as asked for this, yet:

Why 4 seconds at the beginning with no disk or cpu activity? Can be reduced or elimaned?

Bye


i think that is the inital ramdisk, or the kernel loading, but im not sure.

it can probably be reduced by recompiling the kernel, or making a smaller initial ram disk. 

any one else be able to confirm if that is true or not?

---

### Post by jiveaxe on 2009-03-14
I've discovered a script in linux kernel that turns a dmesg output into a SVG graphic that shows which functions take how much time. Its name is bootgraph.pl and can be found in /usr/src/linux-headers-$(uname -r)/scripts.

You must change kernel line in /boot/grub/menu.lst adding **printk.time=1** and **initcall_debug**. Then reboot and create svg file with this command:

dmesg | perl /usr/src/linux-headers-$(uname -r)/scripts/bootgraph.pl > output.svg

It shows what happens in the first few seconds (in my case 4 seconds) of the boot process. What can I see is that approximately 60% of the time is occupied by ahci_init function.

Can somebody else post own graph for comparison? What ahci_init function do?

Bye

---

### Post by markp1989 on 2009-03-14
> **jiveaxe said:**
> I've discovered a script in linux kernel that turns a dmesg output into a SVG graphic that shows which functions take how much time. Its name is bootgraph.pl and can be found in /usr/src/linux-headers-$(uname -r)/scripts.

You must change kernel line in /boot/grub/menu.lst adding **printk.time=1** and **initcall_debug**. Then reboot and create svg file with this command:

dmesg | perl /usr/src/linux-headers-$(uname -r)/scripts/bootgraph.pl > output.svg

It shows what happens in the first few seconds (in my case 4 seconds) of the boot process. What can I see is that approximately 60% of the time is occupied by ahci_init function.

Can somebody else post own graph for comparison? What ahci_init function do?

Bye

have no such dir on my arch system, any one know how to do this with arch?

---

### Post by Mehall on 2009-03-14
Not bad.

Not got the dual-core optimisation on yet, and not profiled.

Minor issue: the whole boot stalls a few seconds in, no clue why, my friend told me I'd need to fix my own kernel to fix this, but I wouldn't know how to start.

I'll do the possible changes next boot, but I'll let it stall for a decent bit of time the boot after so I can work out whats wrong, and you lot can maybe help me fix it, lol

---

### Post by Mehall on 2009-03-14
So here's a chart with concurrency=shell but I went away and did something for a bit while it loaded, and it got stuck, as usual.

It turns out it had been about 20secs I guess till I forced it to boot. Any clues whats causing this mofo here? Didn't have to do it in 8.04, but in 8.10 (Kubuntu and Crunchbang) and in OpenSuse 11.something (I think) x86_64 it did it.

---

### Post by ivaarsen on 2009-03-14
LOL, this poor old machine.  I'm surprised it's still running!

---

### Post by reacocard on 2009-03-15
> **markp1989 said:**
> have no such dir on my arch system, any one know how to do this with arch?

use /usr/src/linux-$(uname -r)/scripts/bootgraph.pl instead

---

### Post by Sealbhach on 2009-03-16
This is 64-bit Jaunty Alpha 6 on ext4.

18.59 seconds.:D

---

### Post by markp1989 on 2009-03-16
> **reacocard said:**
> use /usr/src/linux-$(uname -r)/scripts/bootgraph.pl instead

thanks:D

---

### Post by Scubdup on 2009-03-16
Anything I can do to speed this boottime up? Struggling to read the bootchart info to be honest.

---

### Post by run1206 on 2009-03-16
> **Scubdup said:**
> Anything I can do to speed this boottime up? Struggling to read the bootchart info to be honest.

that's about where i'm at currently. if you don't use a printer, you can remove the cups process. 

to check which process you have running, try this code
```

sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf

```

BUM could also be used to view currently running processes.

---

### Post by Scubdup on 2009-03-17
> **run1206 said:**
> that's about where i'm at currently. if you don't use a printer, you can remove the cups process. 

to check which process you have running, try this code
```

sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf

```

BUM could also be used to view currently running processes.Thanks a lot. I'll have a look.

---

### Post by pah99 on 2009-03-20
Hehe. I got mine down to 12.2 seconds.

---

### Post by js.opdebeeck on 2009-03-20
My participation ...

9.04 (from today), Dell Latitude 630, SSD, 4GB Ram ... and ext4

Not really hard to be fast .

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=107119&stc=1&d=1237591615[/IMG]

Can do better ... but without Laptop modules and runlevel3 ... 


Can someone tell me what the "ONDEMAND" program, and if it's safe to remove ?

Kind regards


Js

---

### Post by markp1989 on 2009-03-24
heres mine, arch.

been experementing with readahead. 

3 charts, 1 with no readahead, 1 with readahead at boot, and 1 with readahead on login.

if anything readahead makes it worse.

---

### Post by mamamia88 on 2009-03-24
wow how do you get 12 second boot?  mines like 38 seconds

---

### Post by klange on 2009-03-28
Totally unoptimized, just a fresh Jaunty with some minor tweaks:
[[img]http://blog.phpwnage.com/gallery.php?do=img&type=thumb&i=8[/img]](http://blog.phpwnage.com/gallery.php?do=img&i=8)
Acer Aspire 5610, HDD, 1GB, 2x1.7GHz.

---

### Post by other guy on 2009-03-28
Just a simple install of Jaunty. No tweaks or optimization. For giggles, later on I am going to try and see if I can break 10 seconds.

---

### Post by an.erni on 2009-04-03
Hey guys

Wow, I must admit that most of you reach amazing boot times!
Sadly, I'm stuck to more than three minutes... How can I find out why it takes so long and what can I improve? It's especially confusing since the CPU is idle most of the time. 
I assume that it has something to do with my wireless, which doesn't work properly even after login.

Can anybody help me, please?

Cheers, Andy

Edit: After Upgrading to Jaunty Beta (out-of-box!), the boot time is below 30sec. This is still higher than most other systems with Jaunty, but for the moment, this is sufficient.

---

### Post by markp1989 on 2009-04-04
> **an.erni said:**
> Hey guys

Wow, I must admit that most of you reach amazing boot times!
Sadly, I'm stuck to more than three minutes... How can I find out why it takes so long and what can I improve? It's especially confusing since the CPU is idle most of the time. 
I assume that it has something to do with my wireless, which doesn't work properly even after login.

Can anybody help me, please?

Cheers, Andy

its dhcp trying to get an ip address, to speed it up you would have to switch to a static ip, or disable networking from startup.

---

### Post by an.erni on 2009-04-04
Is it possible to reduce the time dhcp is trying to get an ip adress?
How can I switch off networking from startup?

---

### Post by kuja on 2009-04-05
> **an.erni said:**
> Is it possible to reduce the time dhcp is trying to get an ip adress?
How can I switch off networking from startup?

What I do is this:
- install + run sysv-rc-conf
- in it, disable network-manager
- create a new script in /etc/init.d, you can call it whatever you want, but dhclient will make most sense here :) ```
sudo editor /etc/init.d/dhclient
```
- in it: (brutally simple, but it works well enough)
```
#!/bin/sh
dhclient eth0
```
- make it executable ```
sudo chmomd +x /etc/init.d/dhclient
```
- add it to the startup ```
sudo update-rc.d dhclient defaults 75
```



----------------------------------


in other news, My bootchart is attached now. 17s ... not too bad considering I require quite a few things to run at startup, and I haven't really done much at all to speed things up. Biggest contributor keeping it from being slow though, is my GSKill 128GB Solid State Drive.

---

### Post by G@B0 on 2009-04-05
Fresh Install of Jaunty with Ext4.

16:04 seconds. Better that I thought.

---

### Post by klange on 2009-04-05
Jaunty's boot times really are quite amazing. My laptop (which I posted earlier) used to take over a minute to boot. It still did after upgrading, but a reinstall (my first ever) made a massive cut in the times. "25 to desktop" seems to be a fairly consistent figure with Jaunty.

---

### Post by markp1989 on 2009-04-05
> **klange said:**
> Jaunty's boot times really are quite amazing. My laptop (which I posted earlier) used to take over a minute to boot. It still did after upgrading, but a reinstall (my first ever) made a massive cut in the times. "25 to desktop" seems to be a fairly consistent figure with Jaunty.

i may have to give Jaunty ago, hopefully it will be better then intrepid was.

---

### Post by wingnux on 2009-04-05
Here's mine. I don't know how to read it but there you go...

---

### Post by sideaway on 2009-04-07
Here's my laptop. I coud do my desktop, but it's still being configured. Any tips on speeding it up?

---

### Post by run1206 on 2009-04-07
> **sideaway said:**
> Here's my laptop. I coud do my desktop, but it's still being configured. Any tips on speeding it up?

you could turn off cups if you don't use a printer in Linux...

i turned mine off and decreased time by about a second or two.
(i have a lexmark x2500 and doesn't work in Linux :( , so i turned off the process )

---

### Post by wingnux on 2009-04-07
Here's the one from my laptop running xubuntu jaunty on ext4. BLAZING FAST!

---

### Post by sideaway on 2009-04-07
I don't have a printer :P So how do you turn of CUPS?

---

### Post by pah99 on 2009-04-07
> **sideaway said:**
> I don't have a printer :P So how do you turn of CUPS?

A really good place to learn more about start up processes is here. [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by Mehall on 2009-04-08
Latest boot-chart.

acpi=off fixed earlier issue, how can I optimise from here?

cups stays for now on mine, fyi

---

### Post by Stupendoussteve on 2009-04-08
Jaunty... not an extremely powerful system, but runs well...

---

### Post by Mehall on 2009-04-08
> **Stupendoussteve said:**
> Jaunty... not an extremely powerful system, but runs well...

No offence, and I know Jaunty did a lot for boot speed, but it almost makes me sick that I have a PC essentially twice as powerful as yours and it takes longer to boot ;_;

Jaunty here I come I guess :D I'll wait for stable though.

---

### Post by mrm48 on 2009-04-09
New laptop w/ intrepid

---

### Post by wingnux on 2009-04-09
I've just installed Kubuntu Jaunty 64bit on my desktop but bootchart only creats .tgz files on /var/log/bootchart, I can't find the png files anywhere. Any help?

---

### Post by jayanramesh on 2009-04-09
Dear pal,
could you tell me how to install bootchart on jaunty 64 bit.Trying at terminal "sudo apt-get install bootchart"I've got
> "jayanr@jayanr-com:~$ sudo apt-get install bootchart
[sudo] password for jayanr: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bootchart is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  bootchart-java
E: Package bootchart has no installation candidate"

Thanks

---

### Post by wingnux on 2009-04-09
Have you enabled all repositories on your "Software Sources"? That's all I've done regarding repositories, I didn't add any extra ones, just enabled the ones that were disabled.

---

### Post by pah99 on 2009-04-09
Fresh install was about 18 seconds. After some tweaks, got it down to 12.X. Seems to me that's as low as it will get without starting to kill a lot of necessary things.

---

### Post by pah99 on 2009-04-09
> **wingnux said:**
> I've just installed Kubuntu Jaunty 64bit on my desktop but bootchart only creats .tgz files on /var/log/bootchart, I can't find the png files anywhere. Any help?

You need to install pybootchartgui. Then run the following.

pybootchartgui /var/log/bootchart

This will open it up in a window viewer. After running this command, there will be a .png file in the bootchart folder.

If you dont see pybootchartgui in synaptic, go here. [http://ubuntuforums.org/showthread.php?t=1092337](http://ubuntuforums.org/showthread.php?t=1092337).

---

### Post by wingnux on 2009-04-09
> **pah99 said:**
> You need to install pybootchartgui. Then run the following.

pybootchartgui /var/log/bootchart

This will open it up in a window viewer. After running this command, there will be a .png file in the bootchart folder.

If you dont see pybootchartgui in synaptic, go here. [http://ubuntuforums.org/showthread.php?t=1092337](http://ubuntuforums.org/showthread.php?t=1092337).

Whenever I try to run this command I get this error:

> wingnux@wingnux-desktop:~$ pybootchartgui /var/log/bootchart
Traceback (most recent call last):                          
  File "/usr/bin/pybootchartgui", line 7, in <module>       
    sys.exit(main())                                        
  File "/var/lib/python-support/python2.6/pybootchartgui/main.py", line 56, in main                                                                       
    res = parsing.parse(args, options.prune)                                 
  File "/var/lib/python-support/python2.6/pybootchartgui/parsing.py", line 195, in parse                                                                  
    state = parse_paths(ParserState(), paths)                                
  File "/var/lib/python-support/python2.6/pybootchartgui/parsing.py", line 178, in parse_paths                                                            
    state = parse_paths(state, files)                                        
  File "/var/lib/python-support/python2.6/pybootchartgui/parsing.py", line 184, in parse_paths                                                            
    state = _do_parse(state, name, tf.extractfile(name))                     
  File "/var/lib/python-support/python2.6/pybootchartgui/parsing.py", line 157, in _do_parse                                                              
    state.ps_stats = _parse_proc_ps_log(file)                                
  File "/var/lib/python-support/python2.6/pybootchartgui/parsing.py", line 34, in _parse_proc_ps_log                                                      
    pid, cmd, state, ppid = int(tokens[0]), tokens[1], tokens[2], int(tokens[3])                                                                          
ValueError: invalid literal for int() with base 10: 'S'          

---

### Post by bigbrovar on 2009-04-09
> **pah99 said:**
> Fresh install was about 18 seconds. After some tweaks, got it down to 12.X. Seems to me that's as low as it will get without starting to kill a lot of necessary things.

what tweaks please share :lolflag:

---

### Post by pah99 on 2009-04-09
wingnux: I'm wondering, if you go into /var/log/bootchart and you look into the folder itself, what is in there? Just the .tgz's or are there any .pngs now?

> **bigbrovar said:**
> what tweaks please share
Um, a lot of the stuff I did pertained to shutting off a lot of unneeded startup programs (for example, I shut off anacron, apmd, atd, brltty, etc). For more info go to [http://ubuntuforums.org/showpost.php?p=6926578&postcount=8](http://ubuntuforums.org/showpost.php?p=6926578&postcount=8). Start reading after the line. Those are basically the things I did.

---

### Post by Korcia on 2009-04-13
Ubuntu Jaunty 64bit, ext4 and LVM which I think add a little overhead in the boot process.

---

### Post by wingnux on 2009-04-13
My bootchart is still f'ed up =/

---

### Post by pah99 on 2009-04-13
> **wingnux said:**
> My bootchart is still f'ed up =/

But when you go into /var/log/bootchart are you still seeing the .tgz's or are there any png's now?

---

### Post by wingnux on 2009-04-14
Finally! After installing the last bugfix I get a valid png file!

16", nice boot! Is there any way to make it faster?

---

### Post by pah99 on 2009-04-14
> **wingnux said:**
> Finally! After installing the last bugfix I get a valid png file!

16", nice boot! Is there any way to make it faster?

Try out this: [http://ubuntuforums.org/showpost.php?p=6926578&postcount=8](http://ubuntuforums.org/showpost.php?p=6926578&postcount=8)

---

### Post by markp1989 on 2009-04-20
here is mine, just got a OCZ vertex SSD today

Info: 
OS : Arch
PC : Specs in sig

WM : Openbox

---

### Post by CraigPaleo on 2009-04-20
Here you go. How much should Jaunty shave off this?

---

### Post by pah99 on 2009-04-20
> **CraigPaleo said:**
> Here you go. How much should Jaunty shave off this?

At least 5 seconds. That processor is pretty wimpy. I'm thinking more like ten though, seeing as how you don't really have too many startup processes.

---

### Post by CraigPaleo on 2009-04-21
> **pah99 said:**
> At least 5 seconds. That processor is pretty wimpy. I'm thinking more like ten though, seeing as how you don't really have too many startup processes. 
Yeah, it's wimpy. I was hoping to cut it to 15 seconds. I see Jaunty has cut others' by 50%

---

### Post by Saint Angeles on 2009-04-21
Here's mine... my boot time has gotten longer since I installed Apache server and mySQL for PHP testing purposes.

Its still pretty impressive for being both a desktop and a server!

---

### Post by Saint Angeles on 2009-04-21
i followed these instructions here:
[http://its-about-amoena.blogspot.com/2007/12/how-to-make-ubuntu-to-start-faster.html](http://its-about-amoena.blogspot.com/2007/12/how-to-make-ubuntu-to-start-faster.html)

and it shaved about one second off my boot time.

but i'm thinking having the pretty usplash is worth that extra second!

---

### Post by MaxIBoy on 2009-04-21
Okay, this is what I got. 

First screenshot is my boot chart. Second screenshot is sysv-rc-conf (two terminals, since the configuration wouldn't fit in one window.) As you can see, I've also compiled a kernel-- pretty much just disabling hardware support I don't need, enabling better parallelization, various latency settings, and setting the tick to 300 instead of 250. I've also enabled the experimental repos, giving me the latest xorg and drivers.

I've changed fstab to mount my filesystems as ext4, set the b-tree thingy with tune2fs, and optimized them with e2fsck -D. I set vm.swappiness to 1 (since I have 3 gigs of RAM and have never even used 2 gigs,) rearranged the boot order using insserv, installed preload, and set the bootup concurrency to "shell."


Any suggestions for further improvements? I know Debian isn't supposed to be supported here, but most of these speed hacks void Ubuntu's "warranty" anyway.

**EDIT: DUE TO A MISTAKE ON MY PART, THIS BOOTCHART IS DISHONEST! **See my more-recent posts.

---

### Post by LinuxGuy1234 on 2009-04-23
This is my laptop's bootchart (sry for Gentoo on it):

---

### Post by pah99 on 2009-04-23
> **LinuxGuy1234 said:**
> This is my laptop's bootchart (sry for Gentoo on it):

Isn't Gentoo supposed to be blazing fast? Well, okay, the specs on the computer are pretty crappy.

---

### Post by MaxIBoy on 2009-04-23
> **pah99 said:**
> Isn't Gentoo supposed to be blazing fast? Well, okay, the specs on the computer are pretty crappy.It's not fast if you don't customize it at all. I've done a lot of tuning on my Debian installation, so it's going to be faster than a typical stock system. This is because a distro has to support a reasonable amount of hardware "out of the box," at least enough to install the operating system, but my setup only has to run on one system, so there's more I can do. Also, I can do things like disable cron, exim, and atd, since I don't use them. If a distro shipped without these out of the box, a lot of users would complain.

---

### Post by pah99 on 2009-04-24
Yeah, I understand. So I have one question: after a couple years of using Ubuntu, do you think its time I move onto Debian? Will it be better?
Sorry for going off topic.

---

### Post by MaxIBoy on 2009-04-24
Depends on what you want from your distro. 

The Debian stable releases tend to be rock solid, but months or even years out-of-date. They suffer from performance issues, and they're missing a lot of important functionality. 

The unstable repos tend to be at most six months out-of-date (which is pretty good, actually,) and they're fairly stable too.

The experimental repos tend to be a couple months out of date (better than almost all distros,) but things break all the time unless you constantly monitor your packages and make sure not to upgrade anything that will break anything else. (Example: Package A depends on package B, package B gets updated in the repos, package A does not, so package A is automatically removed when you update package B.) Leaving the automatic updates on with the experimental repos enabled is a big no-no.

---

### Post by frup on 2009-04-24
15 seconds on an average computer with no modifications.  9.04 with ext4

---

### Post by master5o1 on 2009-04-24
15.42 seconds was the fastest boot so far.

---

### Post by MaxIBoy on 2009-04-24
How do you get less-than-second increments?

My record is 15 seconds, straight up. Don't have that one anymore, but this one is close:

**EDIT: DUE TO A MISTAKE ON MY PART, THIS BOOTCHART IS DISHONEST! **See my more-recent posts.

---

### Post by Mehall on 2009-04-24
Jaunty.

Alternate install disc --> CLI Install --> Add xorg, openbox, lxpanel, slim, etc.

---

### Post by oomingmak on 2009-04-24
After my first boot chart [**[COLOR=DarkOrange]here[/COLOR]**]("http://ubuntuforums.org/showpost.php?p=6609853&postcount=347"), I thought I'd try again but this time using Ubuntu 9.04 (standard Live CD install).

My boot time is now **[SIZE=3]7 seconds [/SIZE]**to full desktop (with GDM etc.)

[COLOR=White].[/COLOR]

---

### Post by CraigPaleo on 2009-04-24
Intrepid (ext3) then Jaunty (ext4): 29 seconds to 16 seconds.

---

### Post by cdwillis on 2009-04-24
Under 30 seconds doesn't seem bad for a netbook, but I'd like to tweak it a bit and see if I can get even quicker boot time.

---

### Post by bobbocanfly on 2009-04-25
Bootchart from my new Jaunty desktop. Ext4 / and /home partitions.

---

### Post by calrogman on 2009-04-25
Here you go!

---

### Post by LinuxGuy1234 on 2009-04-25
New bootchart. Still close to 30 seconds. I provide my full rig info...
Acer Aspire 5315-2153, 2GHz processor (rounded), 2G RAM, 160GB HDD, 9G space used, Gentoo Linux 2008.0 from an autobuild stage.

The difference is that I use a 2.6.28.9 kernel.

---

### Post by Mehall on 2009-04-26
Right, got my booting issues sorted, so I have no issues with a broken ACPI anymore (yay!!!)

any tips on how to bring down this boot time?

(last two boots attached)

---

### Post by MaxIBoy on 2009-04-26
I compiled a kernel, which helped (does anyone really use the Voodoo 3DFX cards anymore? Does anyone really use AmigaOS-formatted disks anymore? I certainly don't.) Installing the package "preload" cut my boot time by 10 seconds. I also installed "sysv-rc-conf" and used it to eliminate a bunch of things I didn't need (Does anyone really use exim4 anymore? Evolution and Mutt both run fine without it.) Enabling boot concurrency can help if you've got a multi-core or multi-processor system, but it causes bugs for some people.

---

### Post by jayanramesh on 2009-04-27
Dear maxIboy,
I've done what you asked to do but to my surprise nothing has changed my boot time .It shows 30:33-anything I 've done wrong?. Could you guide me through?

---

### Post by MaxIBoy on 2009-04-27
Go into sysv-rc-conf and see if "preload" is there.

Also, look at your bootchart picture, and look at what each process is, then Google what it does.

It's fun! It's like a puzzle!

---

### Post by jayanramesh on 2009-04-27
Dear MaxIboy,
I installed sysv-rv-conf but I am not able to find it from either applications or places or system.Could you tell me first of all where I have to dig in to?
Thank you

---

### Post by MaxIBoy on 2009-04-27
Pull up a terminal and run it with sudo.

---

### Post by CraigPaleo on 2009-04-27
> **MaxIBoy said:**
> Go into sysv-rc-conf and see if "preload" is there.



I have preload installed but it's not showing up there. ???

Never mind. It's there.

---

### Post by MaxIBoy on 2009-04-27
You're sure? It should be there.

---

### Post by CraigPaleo on 2009-04-27
> **MaxIBoy said:**
> You're sure? It should be there.

Sorry, it is there. It said I could use the mouse or the arrow keys. The mouse didn't do anything but the arrow keys did. I guess I'm CLilliterate.

---

### Post by jayanramesh on 2009-04-27
Dear MaxIboy,
Thank you so much for your step by step advice.If I were a software eng.or a  programmer I should have taught someone like you in explicit way unfortunately being a physician I can only treat you.By the way could you give me command line- instructions.
Thanks

---

### Post by CraigPaleo on 2009-04-27
Maxiboy,

I notice you don't have readahead. Doesn't that help speed up the boot process?

---

### Post by MaxIBoy on 2009-04-27
Readahead tends to slow down boot time a bit, but it makes your system a bit faster the rest of the time by loading commonly-used programs into RAM at boot time.



> **jayanramesh said:**
> Dear MaxIboy,
Thank you so much for your step by step advice.If I were a software eng.or a programmer I should have taught someone like you in explicit way unfortunately being a physician I can only treat you.By the way could you give me command line- instructions.
ThanksI'm not really qualified to teach the command line. This is a good website for that:
[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)
Very handy skill to have.


Anyway, eventually you'll run out of things to optimize and it'll be as fast as it can get.

---

### Post by CraigPaleo on 2009-04-27
> **MaxIBoy said:**
> Readahead tends to slow down boot time a bit, but it makes your system a bit faster the rest of the time by loading commonly-used programs into RAM at boot time.


Drat! :-( I uninstalled readahead and my boot time went from 16 - 20 seconds. :confused:

Edit: Reinstalled and it's back to 16. It might have worked under intrepid (where I had a boot time of :29) but Ubuntu must have optimized readahead for Jaunty.

---

### Post by MaxIBoy on 2009-04-27
Actually, if it's early on in the boot process, may be it will speed things up. The guide I read on readahead was pretty old, before they started optimizing the order in which the processes spawn. I just noticed that when I disabled it, things seemed slower in general on my system, so I re-enabled it without even checking the boot time.

---

### Post by skymera on 2009-04-27
Readahead added 6-8 seconds to my boot time. Which is more than what it seemed to take off at login
Wihtout it im sailing in at 11 seconds.
Q6600 @ 2.70GHz
WD Raptor 10,000RPM 16MB cache

---

### Post by jayanramesh on 2009-04-29
Dear MaxIBoy,
Thank you so much

---

### Post by jayanramesh on 2009-04-29
> **jayanramesh said:**
> Dear MaxIBoy,
Thank you so much.Indeed you've given me wonderful and very delicious food -it is up to me to have.Once again thanks a lot and I love it.

---

### Post by folgado on 2009-04-29
This is my bootchart. Too slow.

BR

---

### Post by MaxIBoy on 2009-04-29
> **folgado said:**
> This is my bootchart. Too slow.

BR
Do you have boot concurrency enabled?
[http://www.debian-administration.org/article/Concurrent_boot_sequence](http://www.debian-administration.org/article/Concurrent_boot_sequence)

---

### Post by Ubuntu Terrier on 2009-04-29
Any suggestion to improve my boot time?

---

### Post by xir_ on 2009-04-29
ugh my jaunty is really slow 40 seconds and this is after i already to 10 seconds of using profiling.


funny thing is that with a stripped down kernel it is even slower...

any tips? i use nvidia and intel wireless.

---

### Post by freakofwar on 2009-04-30
Hi everyone i have been having a very slow boot time. i do not know what the long pause is about at the beginning? Can anyone give me any insight in to what it may be?

---

### Post by folgado on 2009-05-01
> **MaxIBoy said:**
> Do you have boot concurrency enabled?
[http://www.debian-administration.org/article/Concurrent_boot_sequence](http://www.debian-administration.org/article/Concurrent_boot_sequence)

I have do that and still the same time. Probably the problem is hardware. I have a Toshiba A300.

BR

---

### Post by markp1989 on 2009-05-03
my desktop

OS: Arch 
kernel: Factory

wm: openbox
panel: fbpanel 
autologin : added to the top of my rc.multi 
```
##Login and start X
(/bin/su mark -l -c "/bin/bash --login -c startx >/dev/null 2>&1") &
```
heavily modified rc.sysinit 


Root drive is an OCZ Vertex 30gb 


[img]http://i246.photobucket.com/albums/gg102/markp1989/bootchart-17.png[/img]

---

### Post by reacocard on 2009-05-03
> **markp1989 said:**
> my desktop

OS: Arch 
kernel: Factory

wm: openbox
panel: fbpanel 
autologin : added to the top of my rc.multi 
```
##Login and start X
(/bin/su mark -l -c "/bin/bash --login -c startx >/dev/null 2>&1") &
```b
heavily modified rc.sysinit 


Root drive is an OCZ Vertex 30gb 

<snip>
Nice! Mind posting more details on exactly what you did? In particular, I'm curious what that fastboot parameter in your kernel options is doing.

---

### Post by markp1989 on 2009-05-03
> **reacocard said:**
> Nice! Mind posting more details on exactly what you did? In particular, I'm curious what that fastboot parameter in your kernel options is doing.

[http://bbs.archlinux.org/viewtopic.php?id=69258](http://bbs.archlinux.org/viewtopic.php?id=69258) acording to this post, it initializes scsi and ata devices asynchronous, which helps to speed up boot . 

but i just relized (slow moment) that on my kernel its doing nothing , because im 1 version behind, updating now .

---

### Post by Ubuntu Terrier on 2009-05-03
> **xir_ said:**
> ugh my jaunty is really slow 40 seconds and this is after i already to 10 seconds of using profiling.


funny thing is that with a stripped down kernel it is even slower...

any tips? i use nvidia and intel wireless.

I see that for some reason your hard disk is working a lot and inefficiently. I don't know what could be the cause, though.
Putting read-ahead on background could lower the boot time, but not solve the problem.

---

### Post by MaxIBoy on 2009-05-03
> **markp1989 said:**
> my desktop

OS: Arch 
kernel: Factory

wm: openbox
panel: fbpanel 
autologin : added to the top of my rc.multi 
```
##Login and start X
(/bin/su mark -l -c "/bin/bash --login -c startx >/dev/null 2>&1") &
```heavily modified rc.sysinit 


Root drive is an OCZ Vertex 30gb 
I did not know about the fastboot option! It didn't beat any records, but now my boot time is a consistent 15-16 seconds, as apposed to 15-21 seconds.

I tried the "elevator=noop" option, and it really slowed things down for me. But I found redhat's guide to scheduler types ([http://www.redhat.com/docs/wp/performancetuning/iotuning/iosubsystem-scheduler-types.html](http://www.redhat.com/docs/wp/performancetuning/iotuning/iosubsystem-scheduler-types.html),) and based on that I chose "elevator=deadline." Added about a second to my boot time, but WOW! My computer feels really "snappy" now! They didn't joke around when they said the latancy was low!


The next thing I'm going to check out will be using XDM instead of GDM.




**EDIT: DUE TO A MISTAKE ON MY PART, THIS BOOTCHART IS DISHONEST! **See my more-recent posts.

---

### Post by BenderRodriguez on 2009-05-04
Hi everyone,  I'm using Ubuntu 8.10 on a system equiped with a Patriot SSD drive and my boot times are not satisfying. It takes about 37 sec to boot up the OS. I'm whondering about the large delays induced by modprobe and udev. Those two sections make up almost half of the boot time !

Any suggestions how to improve my boot performance ?

---

### Post by CraigPaleo on 2009-05-04
Hmmph!  I upgraded my kernel to 2.6.29.2, enabled fastboot and still 16 second boot time.  

My boot times have never varied. Always 16 sec. (always 20 without readahead) 
I think I'll give up on this before I end up seriously bonking my system. I'm getting too curious and courageous. I need a test machine!

Edit: I see that fastboot reduced a lot of the stuff at the bottom but this must not be my bottle neck.

---

### Post by MaxIBoy on 2009-05-04
XDM actually seems slower than GDM, but I have yet to run empirical tests.

Attached is my best time yet (14 seconds.) Also attached is a bootchart I made before I made any major changes, for comparison.


**EDIT: DUE TO A MISTAKE ON MY PART, THIS BOOTCHART IS DISHONEST! **See my more-recent posts.

---

### Post by swoll1980 on 2009-05-04
right[ here]("redwingworx.com/size_chart.htm")

---

### Post by unoodles on 2009-05-04
> **swoll1980 said:**
> right[ here]("redwingworx.com/size_chart.htm")

:lolflag::lolflag::lolflag:
Took me a minute, but that was brilliant.

---

### Post by MaxIBoy on 2009-05-04
> **unoodles said:**
> :lolflag::lolflag::lolflag:
Took me a minute, but that was brilliant.I had it at about five seconds on my first try, but my brain's integrated caching should reduce that time in the future.

---

### Post by surfed on 2009-05-04
I was hoping for under 20secs but 22 ain't bad.... any tips?

---

### Post by CraigPaleo on 2009-05-04
> **MaxIBoy said:**
> XDM actually seems slower than GDM, but I have yet to run empirical tests.

Attached is my best time yet (14 seconds.) Also attached is a bootchart I made before I made any major changes, for comparison.

Do you have a comparison of before and after you enabled fast boot? It added some async/* to mine and shortened the processes at the bottom of my chart but no change in boot time. 

I don't see those same changes that I got in your bootchart.

---

### Post by CraigPaleo on 2009-05-04
> **surfed said:**
> I was hoping for under 20secs but 22 ain't bad.... any tips?

It looks like nothing's happening between the 5 & 10 sec mark. Go back and look at some of the recent pages. You have two cores so there should be more you can do. 

I think the reason nothing helps me much is because I have one core. I just cut some processes and now have it down to 15 sec. Anything else I've done either adds to my boot time or has no effect.

---

### Post by CraigPaleo on 2009-05-04
> **swoll1980 said:**
> right[ here]("redwingworx.com/size_chart.htm")

Ha! Is shorter better here also?

---

### Post by swoll1980 on 2009-05-04
> **CraigPaleo said:**
> Ha! Is shorter better here also?

Well, you know what they say about guys with short boots...

---

### Post by MaxIBoy on 2009-05-04
> **CraigPaleo said:**
> Do you have a comparison of before and after you enabled fast boot? It added some async/* to mine and shortened the processes at the bottom of my chart but no change in boot time. 

I don't see those same changes that I got in your bootchart.I did not, but there were no glaring dissimilarities I noticed from memory.

---

### Post by CraigPaleo on 2009-05-04
> **swoll1980 said:**
> Well, you know what they say about guys with short boots...

Laughing my fanny off! Maybe I don't want the shortest boot after all. :)

---

### Post by swoll1980 on 2009-05-04
> **CraigPaleo said:**
> Maybe I don't want the shortest boot after all. :)

lol

---

### Post by CraigPaleo on 2009-05-04
> **MaxIBoy said:**
> I did not, but there were no glaring dissimilarities I noticed from memory.

So, you did a bunch of things without rebooting? 

What is the reason for the non-activity until about 7 sec on your machine. Mine's about 2.5 seconds. If we could combine my first half with your second half, it'd be pretty quick. 

Oh, and did you disable Xorg just to get a better boot time or do you like booting into CLI?

---

### Post by Screwdriver0815 on 2009-05-04
normal Jaunty setup:

17 seconds. Its a bit slow isn't it?

how do I avoid that the hdd will be flooded with bootcharts? As it always creates a new chart with a new date?

---

### Post by CraigPaleo on 2009-05-04
> **Screwdriver0815 said:**
> normal Jaunty setup:

17 seconds. Its a bit slow isn't it?

how do I avod that the hdd will be flooded with bootcharts? As it always creates a new chart with a new date?

You can just go through and cull the bootcharts you don't want to keep. I have a lot since I've been rebooting quite a bit trying to get my time down. Otherwise, I don't boot very often. 

The thing that brought my time down the most was upgrading to Jaunty, which you have. I'd go through and read this thread starting at [page 44]("http://ubuntuforums.org/showthread.php?t=531453&page=44") and see what's worked for others.

---

### Post by CraigPaleo on 2009-05-04
> **BenderRodriguez said:**
> Hi everyone,  I'm using Ubuntu 8.10 on a system equiped with a Patriot SSD drive and my boot times are not satisfying. It takes about 37 sec to boot up the OS. I'm whondering about the large delays induced by modprobe and udev. Those two sections make up almost half of the boot time !

Any suggestions how to improve my boot performance ?

Is there a reason that you haven't upgraded to Jaunty? It's the single biggest thing that helped me: [My Intrepid Jaunty Comparison]("http://ubuntuforums.org/showpost.php?p=7137337&postcount=443").

I have a slow hard drive, 5900 rmp. I've been reading that readahead can benefit slower hard drives and sreadahead (super readahead) can benefit faster hard drives regarding boot times. Since you have a SSD, you might want to give [sreadahead]("apt:sreadahead") a try.

---

### Post by Screwdriver0815 on 2009-05-04
thanks 

I have switched off some services but it didn't shave off any time. Anyway, I think this modprobe-thing is disturbing a little bit. I also get 2 failure messages (all the time) during startup:

1.) ata1 (a cryptic number) softreset failed (device not ready)

2.) fatal error... can not find... something... its too fast to read.
I think its because of the soundcards and is connected with modprobe.
The issue is: I have 2 soundcards in the computer but I only use one (the other one is on the mainboard and can not be switched off). 
So I have set up the one I want to use as default with the padevchooser and pavucontrol (the pulseaudio tools) but since then I get this message although the sound is okay. :confused:

can I do something about the modprobe maybe to speed this beast up? Or does the modprobe nothing to the boot time?

Edit: 
from the system logfiles:

> Ziva kernel: [    1.812017] ata1: softreset failed (device not ready)

---

### Post by Nick Rhodes on 2009-05-04
I have modest hardware, its a Toshiba laptop with a 1.7 ghz P4m cpu and 768mhz ram.
I have a fresh install of Jaunty, only difference from default is using XFS (tweak formatting and mount options) and my machine boots in 14s, really impressed, that's approx twice as quick as intrepid (as I expected).
Oh and I reprofiled my boot (by adding profile to the kernel boot flags in grub), which shaved 1s off.

Chart: [http://img205.imageshack.us/img205/6830/riverjaunty200905042.png](http://img205.imageshack.us/img205/6830/riverjaunty200905042.png)

Cheers, Nick.

---

### Post by CraigPaleo on 2009-05-04
> **Screwdriver0815 said:**
> thanks 

I have switched off some services but it didn't shave off any time. Anyway, I think this modprobe-thing is disturbing a little bit. I also get 2 failure messages (all the time) during startup:

1.) ata1 (a cryptic number) softreset failed (device not ready)

2.) fatal error... can not find... something... its too fast to read.
I think its because of the soundcards and is connected with modprobe.
The issue is: I have 2 soundcards in the computer but I only use one (the other one is on the mainboard and can not be switched off). 
So I have set up the one I want to use as default with the padevchooser and pavucontrol (the pulseaudio tools) but since then I get this message although the sound is okay. :confused:

can I do something about the modprobe maybe to speed this beast up? Or does the modprobe nothing to the boot time?

Edit: 
from the system logfiles:

Just to be clear, this was happening all along, even before you switched any services off, correct? 

If so, it wouldn't hurt to post this in the general support forum. It would take me too long to figure out what's going wrong if I could at all.

---

### Post by Screwdriver0815 on 2009-05-04
> **CraigPaleo said:**
> Just to be clear, this was happening all along, even before you switched any services off, correct? 

If so, it wouldn't hurt to post this in the general support forum. It would take me too long to figure out what's going wrong if I could at all.

yes it was happening also before I switched off the services. 

Maybe I'll post it in the support forum but since I can not see the message and nothing is saved in the logfiles... I think I can live with the 17 seconds (which is 5 seconds faster than my old machine)

thank you anyway!

---

### Post by MaxIBoy on 2009-05-04
> **CraigPaleo said:**
> So, you did a bunch of things without rebooting? 

What is the reason for the non-activity until about 7 sec on your machine. Mine's about 2.5 seconds. If we could combine my first half with your second half, it'd be pretty quick. 

Oh, and did you disable Xorg just to get a better boot time or do you like booting into CLI?I didn't disable xorg. 

Having looked at my rc[1-5].d folders, it seems that the "stop bootchart" script is called fairly early on (see attachment.) Didn't notice this before.

I'll try moving it up to the last.

---

### Post by CraigPaleo on 2009-05-04
> **MaxIBoy said:**
> I didn't disable xorg. 

Having looked at my rc[1-5].d folders, it seems that the "stop bootchart" script is called fairly early on (see attachment.) Didn't notice this before.

I'll try moving it up to the last.

Please do. I don't see the "stop bootchart" but I do see the "stop readahead." 

How fast is your hard drive and what effect does readahead have on it? Your bootchart starts (say that five times fast) early on. Are you sure you weren't manipulating bootchart purposely or am I just paranoid?

---

### Post by CraigPaleo on 2009-05-04
Bump? It's not 17 minutes.

---

### Post by MaxIBoy on 2009-05-04
This should clarify things a little for you.



Paradoxically, the initscript named "bootchart" is actually the script to *stop* the bootchartd daemon. Look for yourself in "/etc/init.d/bootchart," the file starts out with this comment:
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          bootchart
# Required-Start:    $remote_fs rmnologin
# Required-Stop:
# Default-Start:     1 2 3 4 5
# Default-Stop:
# Short-Description: Stop bootchartd
# Description:       This script stops the bootchartd daemon after
#                    the system came up.
### END INIT INFO

# Author: Jörg Sommer <joerg@alea.gnuu.de>

# Do NOT "set -e"
```


My hard drive is an el cheapo 5400 RPM 250 GB laptop hard drive. Running preload and readahead at the same time is redundant, and actually I thought I'd disabled the darn thing. Disabled it again, and it took a few seconds off my early boot process.


Yes, my previous boot charts weren't totally honest, no it wasn't on purpose (your question about why xorg wasn't there was the reason why I looked in /etc/rc2.d and saw that the bootchart script was too early.)








Today, my most recent round of optimizations has been:

[LIST]
[*]Cut off bootchart logging *after* XDM, giving a more-honest boot time. This was the first thing I did, and it gave me a time of 33 seconds to XDM.
[*]Moved a few other things after XDM. I doubt I'll need to connect to the Internet or connect to a printer *before* XDM starts. Bootchart recording is killed first thing after XDM, so these things won't show up. I also moved preload to be the final thing to execute, which improved the boot time dramatically.
[*]Moved a few things (notably rsyslogd and x11-common) to /etc/rcS.d instead of rc2.d.
[*]Looked at the dependencies of the initscripts and "collapsed" them, making the excecution order far more parallel.
[/LIST]

New initscript excecution order:
```
~$ ls /etc/rcS.d #early boot initscripts
K05preload            S07hwclockfirst.sh        S14urandom
K20nfs-common         S07hwclock.sh             S14x11-common
K60pcmciautils        S07keyboard-setup         S16networking
K61readahead-desktop  S07procps                 S17portmap
K98readahead          S08checkroot.sh           S18mountnfs.sh
README                S09ifupdown-clean         S19mountnfs-bootclean.sh
S01glibc.sh           S09module-init-tools      S20alsa-utils
S02hostname.sh        S09mtab.sh                S20bootmisc.sh
S03mountkernfs.sh     S09udev-mtab              S20console-screen.sh
S04udev               S10checkfs.sh             S20sudo
S05mountdevsubfs.sh   S11mountall.sh            S21console-setup
S06keymap.sh          S12mountall-bootclean.sh  S22stop-bootlogd-single
S07bootlogd           S13mountoverflowtmp       S30rsyslog
S07hdparm             S14ifupdown               S47lm-sensors
S07hibernate          S14resolvconf
~$ ls /etc/rc2.d #runlevel 2 initscripts
K01apmd            K11cron           S02cpufrequtils
K01atd             K20acct           S02dbus
K01bluetooth       K20openbsd-inetd  S02fancontrol
K01exim4           K30x11-common     S03dhcdbd
K01kerneloops      K78gdm            S03hal
K01nfs-common      K86avahi-daemon   S22xdm
K01openvpn         K90rsyslog        S23bootchart
K01rc.local        K93hdparm         S23cups
K01saned           K99vbesave        S23network-manager
K01stop-bootlogd   README            S23rmnologin
K01stop-readahead  S01acpi-support   S26network-manager-dispatcher
K09apache2         S01loadcpufreq    S95preload
K11anacron         S02acpid
~$ 

```




New boot time is attached.

---

### Post by CraigPaleo on 2009-05-04
> **MaxIBoy said:**
> This should clarify things a little for you.



Paradoxically, the initscript named "bootchart" is actually the script to *stop* the bootchartd daemon. Look for yourself in "/etc/init.d/bootchart," the file starts out with this comment:
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          bootchart
# Required-Start:    $remote_fs rmnologin
# Required-Stop:
# Default-Start:     1 2 3 4 5
# Default-Stop:
# Short-Description: Stop bootchartd
# Description:       This script stops the bootchartd daemon after
#                    the system came up.
### END INIT INFO

# Author: Jörg Sommer <joerg@alea.gnuu.de>

# Do NOT "set -e"
```


My hard drive is an el cheapo 5400 RPM 250 GB laptop hard drive. Running preload and readahead at the same time is redundant, and actually I thought I'd disabled the darn thing. Disabled it again, and it took a few seconds off my early boot process.


Yes, my previous boot charts weren't totally honest, no it wasn't on purpose (your question about why xorg wasn't there was the reason why I looked in /etc/rc2.d and saw that the bootchart script was too early.)








Today, my most recent round of optimizations has been:

[LIST]
[*]Cut off bootchart logging *after* XDM, giving a more-honest boot time. This was the first thing I did, and it gave me a time of 33 seconds to XDM.
[*]Moved a few other things after XDM. I doubt I'll need to connect to the Internet or connect to a printer *before* XDM starts. Bootchart recording is killed first thing after XDM, so these things won't show up. I also moved preload to be the final thing to execute, which improved the boot time dramatically.
[*]Moved a few things (notably rsyslogd and x11-common) to /etc/rcS.d instead of rc2.d.
[*]Looked at the dependencies of the initscripts and "collapsed" them, making the excecution order far more parallel.
[/LIST]

New initscript excecution order:
```
~$ ls /etc/rcS.d #early boot initscripts
K05preload            S07hwclockfirst.sh        S14urandom
K20nfs-common         S07hwclock.sh             S14x11-common
K60pcmciautils        S07keyboard-setup         S16networking
K61readahead-desktop  S07procps                 S17portmap
K98readahead          S08checkroot.sh           S18mountnfs.sh
README                S09ifupdown-clean         S19mountnfs-bootclean.sh
S01glibc.sh           S09module-init-tools      S20alsa-utils
S02hostname.sh        S09mtab.sh                S20bootmisc.sh
S03mountkernfs.sh     S09udev-mtab              S20console-screen.sh
S04udev               S10checkfs.sh             S20sudo
S05mountdevsubfs.sh   S11mountall.sh            S21console-setup
S06keymap.sh          S12mountall-bootclean.sh  S22stop-bootlogd-single
S07bootlogd           S13mountoverflowtmp       S30rsyslog
S07hdparm             S14ifupdown               S47lm-sensors
S07hibernate          S14resolvconf
~$ ls /etc/rc2.d #runlevel 2 initscripts
K01apmd            K11cron           S02cpufrequtils
K01atd             K20acct           S02dbus
K01bluetooth       K20openbsd-inetd  S02fancontrol
K01exim4           K30x11-common     S03dhcdbd
K01kerneloops      K78gdm            S03hal
K01nfs-common      K86avahi-daemon   S22xdm
K01openvpn         K90rsyslog        S23bootchart
K01rc.local        K93hdparm         S23cups
K01saned           K99vbesave        S23network-manager
K01stop-bootlogd   README            S23rmnologin
K01stop-readahead  S01acpi-support   S26network-manager-dispatcher
K09apache2         S01loadcpufreq    S95preload
K11anacron         S02acpid
~$ 

```




New boot time is attached.

Thank you! It clears up a lot!

---

### Post by MaxIBoy on 2009-05-04
More things I plan to try: 

[LIST=1]
[*]Setting up runlevel 3 specifically to run fsck and then restart, then removing fsck from my main boot process.
[*]Backing up and reformatting my partitions as true ext4 (I merely migrated them from ext3 to ext4, which will improve performance somewhat but not totally.) Unfortunately, I won't be able to set my root partition as true ext4 unless I install grub2. However, my /home and /opt partitions are fair game.
[*]Installing grub2 (I'm a little bit wary of doing that just yet, I plan to wait until at least a release candidate.) This should be a big improvement.
[*]Compile a fully monolithic kernel and get rid of initrd.
[/LIST]
However, at this point, I don't think there are many more "easy" tweaks I can make.

---

### Post by b@sh_n3rd on 2009-05-04
Hi...here's my bootchart... I'm running Jaunty on an 11yr old system BTW. What puzzles me is I was expecting a 57MB/s throughput with 3 XFS partitions...strangely enough the chart show's 23...what's up with that?

---

### Post by MaxIBoy on 2009-05-04
> **b@sh_n3rd said:**
> Hi...here's my bootchart... I'm running Jaunty on an 11yr old system BTW. What puzzles me is I was expecting a 57MB/s throughput with 3 XFS partitions...strangely enough the chart show's 23...what's up with that?57 MB/s is a little bit much for a hard drive of that age-- my recent hard drive can just about manage 56 and that's without filesystem overhead. I know XFS has less FS overhead than EXT3, but it's still there. Now granted my hard drive is only 5400 RPM, but it's still probably faster than yours.

My throughput is only 8 or 9 MB/s because my boot process is more CPU-bound than it is hard drive bound. Since you have a pentium II, this is probably even more true in your case.

---

### Post by CraigPaleo on 2009-05-04
Maxiboy,

I've uninstalled preload and still have a :16 boot? The only difference is that all my programs take longer to load: Evolution, Firefox, Rhythmbox... 

Preload and readahead are NOT redundant, at least not on my Jaunty.

---

### Post by rudenko_ruslan on 2009-05-05
That's mine:

---

### Post by b@sh_n3rd on 2009-05-05
> **MaxIBoy said:**
> 57 MB/s is a little bit much for a hard drive of that age-- my recent hard drive can just about manage 56 and that's without filesystem overhead. I know XFS has less FS overhead than EXT3, but it's still there. Now granted my hard drive is only 5400 RPM, but it's still probably faster than yours.

My throughput is only 8 or 9 MB/s because my boot process is more CPU-bound than it is hard drive bound. Since you have a pentium II, this is probably even more true in your case.

Yeah...It's probably to do with the HDD I suppose but this HDD has gotta be newer than the system. See, I got it second-hand but it's quite a good comp. When we bought it, it had a 3.00GB HDD which again couldn't have been the one that came with it coz it sorta gets mixed up and recently I grabbed this 15GB HDD from another sys. which, i'm currently using on this. I THINK it's a Matrox, not sure I've got about 3 similar HDD's..muddling :D.

---

### Post by MaxIBoy on 2009-05-05
> **CraigPaleo said:**
> Maxiboy,

I've uninstalled preload and still have a :16 boot? The only difference is that all my programs take longer to load: Evolution, Firefox, Rhythmbox... 

Preload and readahead are NOT redundant, at least not on my Jaunty.Preload does seem to work better than readahead for me, which is why I chose it.

On the other hand, keep in mind that I'm not running Ubuntu.

---

### Post by CraigPaleo on 2009-05-05
> **MaxIBoy said:**
> Preload does seem to work better than readahead for me, which is why I chose it.

On the other hand, keep in mind that I'm not running Ubuntu.

How rude! How about YOU keep in mind that WE are running Ubuntu? 
Good grief! How will I trust you again?

---

### Post by MaxIBoy on 2009-05-05
> **CraigPaleo said:**
> How rude! How about YOU keep in mind that WE are running Ubuntu? 
Good grief! How will I trust you again?Not everyone is. That guy with the 3-second boot is running Arch. Anyway, it says Debian right in the boot chart itself, you'd have seen that had you been paying attention.

Good grief, way to flip out. You're such a distro bigot!

I... I just don't think I could ever talk to you again! Discrimination is just too painful for me to deal with... *sob* You realize I'm gonna have to go eat a quart of ice cream and then cry in the shower, right?

---

### Post by CraigPaleo on 2009-05-05
> **MaxIBoy said:**
> Not everyone is. That guy with the 3-second boot is running Arch. Anyway, it says Debian right in the boot chart itself, you'd have seen that had you been paying attention.

Good grief, way to flip out. You're such a distro bigot!

I... I just don't think I could ever talk to you again! Discrimination is just too painful for me to deal with... *sob* You realize I'm gonna have to go eat a quart of ice cream and then cry in the shower, right?

Are you okay?

I didn't mean to take it out on you. It's just that my mind gets too occupied sometimes.

---

### Post by lisati on 2009-05-05
Here's today's efforts

---

### Post by CraigPaleo on 2009-05-05
> **lisati said:**
> Here's today's efforts

Awesome!

---

### Post by lisati on 2009-05-05
> **CraigPaleo said:**
> Awesome!

Thanks. I'd forgotten about this thread, and decided to while away a small amount of time getting boot charts for my current crop of machines.

---

### Post by CraigPaleo on 2009-05-05
> **lisati said:**
> Thanks. I'd forgotten about this thread, and decided to while away a small amount of time getting boot charts for my current crop of machines.

I'm glad you did and that they're working alright! Is the Windows (gasp) working okay as well?

---

### Post by lisati on 2009-05-05
> **CraigPaleo said:**
> I'm glad you did and that they're working alright! Is the Windows (gasp) working okay as well?

The Vista on my laptop seems OK, but the XP on the desktop was misbehaving yesterday - was booting to the recovery console. A bit of tinkering with things like fixmbr, fixboot and bootcfg (?), and subsequent reinstall of grub got things back working. 

I tried to put a minimal CLI installation of Jaunty on the old machine, but got bored looking at a blank screen, so I put FreeDOS on it, and then Windows 98 over the top of FreeDOS - apart from a disk I/O error (fixed with the help of "sys C:" from an emergency boot floppy - odd, perhaps FreeDOS handles its MSDOS.SYS and IO.SYS files differently, or possibly because it's a non-MS OS) the installation went well. Next step get the beast networking properly with Ubuntu and some kind of malware protection.

---

### Post by CraigPaleo on 2009-05-05
> **lisati said:**
> The Vista on my laptop seems OK, but the XP on the desktop was misbehaving yesterday - was booting to the recovery console. A bit of tinkering with things like fixmbr, fixboot and bootcfg (?), and subsequent reinstall of grub got things back working. 

I tried to put a minimal CLI installation of Jaunty on the old machine, but got bored looking at a blank screen, so I put FreeDOS on it, and then Windows 98 over the top of FreeDOS - apart from a disk I/O error (fixed with the help of "sys C:" from an emergency boot floppy - odd, perhaps FreeDOS handles its MSDOS.SYS and IO.SYS files differently, or possibly because it's a non-MS OS) the installation went well. Next step get the beast networking properly with Ubuntu and some kind of malware protection.

Do you confuse me on purpose or does it just happen that way?:)

---

### Post by lisati on 2009-05-05
> **CraigPaleo said:**
> Do you confuse me on purpose or does it just happen that way?:)

If it happened, it wasn't on purpose......I suppose I was having a little rant.

---

### Post by Nforcr on 2009-05-05
Here's mine:

---

### Post by MaxIBoy on 2009-05-05
> **CraigPaleo said:**
> Are you okay?

I didn't mean to take it out on you. It's just that my mind gets too occupied sometimes.Eh? I thought you were joking, I was playing along.


I'm currently compiling kernel 2.6.29.2 to replace 2.6.29.1, I'll post here if there are any benefits.

---

### Post by surfed on 2009-05-05
So if you look at my bootchart, I have this 5 second pause from 5-10 secs with udevd taking that time and sleep and resume. I dont see resume in any other boot charts on here, how do i get rid of it? I get a 21 sec boot right now and if i could fix this i am sure i would achieve ~17secs....

---

### Post by MaxIBoy on 2009-05-07
New personal best: 13 seconds, straight up, from grub to XDM. The normal range of variation is now between 13.0 and 13.3, not from 17 to 19.

I looked carefully at my bootchart and saw that somethings were running twice. This was because of some dependencies that hadn't run yet. Reordered the initscripts again with that in mind, took four seconds off the boot process. I fixed the annoyance of hwclock running twice for some reason.

After many tries and many profanities, I successfully compiled a kernel which needed no initrd. This took 2.5 seconds off my early boot process but added 2.5 seconds to the late boot process, so it came out the same. I then compiled one which needs no modprobe whatsoever, which took off the 2.5 seconds once and for all. 


I'm still convinced that there's room for improvement, but I think probably 8 to 10 seconds is as good as it'll get for me.


Initscript order:
```

~$ ls /etc/rcS.d #early boot
K05preload           S06hibernate              S14urandom
K20nfs-common        S06keymap.sh              S14x11-common
K60pcmciautils       S07keyboard-setup         S15portmap
K80alsa-utils        S08checkroot.sh           S16resolvconf
K92hwclockfirst.sh   S09ifupdown-clean         S18mountnfs.sh
K95bootlogd          S09module-init-tools      S19mountnfs-bootclean.sh
README               S09mtab.sh                S20bootmisc.sh
S01glibc.sh          S09udev-mtab              S20console-screen.sh
S02hostname.sh       S10checkfs.sh             S20lm-sensors
S02readahead         S10ifupdown               S20rsyslog
S03mountkernfs.sh    S11hwclock.sh             S20stop-bootlogd-single
S04procps            S11mountall.sh            S20sudo
S04udev              S12mountall-bootclean.sh  S21console-setup
S05mountdevsubfs.sh  S13mountoverflowtmp       S39readahead-desktop
S06hdparm            S14networking
~$ ls /etc/rc2.d/ #runlevel 2
K01apmd            K11cron           S02dbus
K01atd             K20acct           S04fancontrol
K01bluetooth       K20openbsd-inetd  S04hal
K01exim4           K30x11-common     S05dhcdbd
K01kerneloops      K50alsa-utils     S06xdm
K01nfs-common      K78gdm            S23bootchart
K01openvpn         K86avahi-daemon   S23cups
K01rc.local        K90rsyslog        S23network-manager
K01saned           K93hdparm         S23rmnologin
K01stop-bootlogd   K99vbesave        S26network-manager-dispatcher
K01stop-readahead  README            S94loadcpufreq
K09apache2         S01acpid          S95cpufrequtils
K11anacron         S01acpi-support   S95preload
~$ 
```Bootchart is attached. I've also attached my .config for building the kernel source (renamed from .config to config.txt because of the attachment system.)

NOTE: This .config is for 2.6.30-rc4. 

NOTE: This .config is tailor-made for MY computer, using the perl script I found in [this]("http://www.debian-administration.org/articles/620") article, and with a lot more functionality disabled by me. It will most likely not work on your computer.

---

### Post by CraigPaleo on 2009-05-07
> **MaxIBoy said:**
> Eh? I thought you were joking, I was playing along.


I'm currently compiling kernel 2.6.29.2 to replace 2.6.29.1, I'll post here if there are any benefits.

Sorry. That happens to me a lot. I thought I'd caused, yet another person, a psychotic break. 

I don't have the nerve yet to compile a custom colonel. I know I could choose a different one at start-up if need be. I really need a test machine. I've tried using my old mac mini but the hard drive is shot. Only Mandriva will install on it but with many media errors - about a 10 minute boot!

---

### Post by MaxIBoy on 2009-05-07
Compiling a kernel isn't so hard. Either it works, or it doesn't work. If it doesn't work, you can always go to the bootloader menu and pick your old one instead.

---

### Post by CraigPaleo on 2009-05-07
> **MaxIBoy said:**
> Compiling a kernel isn't so hard. Either it works, or it doesn't work. If it doesn't work, you can always go to the bootloader menu and pick your old one instead.

Might compilation work on my mac mini with the borked HDD? Or would it take endlessly longer?

---

### Post by RATM_Owns on 2009-05-07
[img]http://i44.tinypic.com/2aivbs.png[/img]

---

### Post by lariosa42 on 2009-05-12
Hello,

I'm looking for some help in improving my startup time.  Despite upgrading to Jaunty, my boot time is still around 50 sec.  After searching around in the forums for an hour, I can't seem to find a good way to speed things up.  Any help would be appreciated.

I'm running Jaunty on a Dell laptop with 1GB RAM, and a dual-core 1.7ish GHZ processor.  My bootchart is attached.  It seems like the biggest bottlenecks are:

twistd (~10sec), readahead-list (~10sec) and find (~6 sec).

I don't really know what twistd does, and I'm a bit foggy on the other two.  Any help would be sincerely appreciated! =)

---

### Post by Seishuku on 2009-05-12
Yay!:KS

---

### Post by js.opdebeeck on 2009-05-12
> **lariosa42 said:**
> Hello,


twistd (~10sec), readahead-list (~10sec) and find (~6 sec).

I don't really know what twistd does, and I'm a bit foggy on the other two.  Any help would be sincerely appreciated! =)


I think you have a bit too much services

Install rcconf 

```
sudo apt-get install rcconf
```

Launch it ... and remove the non needed services (just uncheck)... 

More info about the services and their usage (maybe better info on this forum).

[http://ubuntu-tweak.com/2007/09/30/how-to-control-ubuntus-services-easily.html](http://ubuntu-tweak.com/2007/09/30/how-to-control-ubuntus-services-easily.html)

[http://allhuda.blogspot.com/2008/01/comprehensive-linux-system-services.html](http://allhuda.blogspot.com/2008/01/comprehensive-linux-system-services.html)


If you really need some of them ... call them when needed.

Create a script on your desk to launch them when needed (like iscsi, nfs, winbind, avahi, vmware, ...).

```

#!/bin/sh

# Sample to start your services on demand.
sudo /etc/init.d/yourapp0 start
sudo /etc/init.d/yourapp1 start
sudo /etc/init.d/yourapp2 start


```

---

### Post by phaed on 2009-05-12
Jaunty, ext4.

13 seconds.  It was 15 seconds, but I removed some unnecessary stuff with BUM and got it down to 13.

---

### Post by lariosa42 on 2009-05-12
Thanks for your help!  Unfortunately, things are running even slower now. =(

I used [FONT="Courier New"]rcconf[/FONT] and turned off [FONT="Courier New"]readahead[/FONT] as well as some of the services mentioned in 

[http://allhuda.blogspot.com/2008/01/comprehensive-linux-system-services.html](http://allhuda.blogspot.com/2008/01/comprehensive-linux-system-services.html)

However, now the boot time is even worse, 54 sec!  I still can't figure out how to turn off the [FONT="Courier New"]twistd[/FONT] daemon, but I found out that it apparently has something to do with Python (which I never use, at least not explicitly). Not sure about [FONT="Courier New"]find[/FONT] yet either.

Any help/suggestions would be welcome!

---

### Post by pah99 on 2009-05-13
> **lariosa42 said:**
> Thanks for your help!  Unfortunately, things are running even slower now. =(

I used [FONT="Courier New"]rcconf[/FONT] and turned off [FONT="Courier New"]readahead[/FONT] as well as some of the services mentioned in 

[http://allhuda.blogspot.com/2008/01/comprehensive-linux-system-services.html](http://allhuda.blogspot.com/2008/01/comprehensive-linux-system-services.html)

However, now the boot time is even worse, 54 sec!  I still can't figure out how to turn off the [FONT="Courier New"]twistd[/FONT] daemon, but I found out that it apparently has something to do with Python (which I never use, at least not explicitly). Not sure about [FONT="Courier New"]find[/FONT] yet either.

Any help/suggestions would be welcome!

I recommend you leave readahead on.

---

### Post by pah99 on 2009-05-13
Hey can someone explain to me why there's a bunch of duplicates in my boot?

This is a fresh install, with a new kernel, but it also does this in the regular ubuntu kernel.

---

### Post by MaxIBoy on 2009-05-13
Well, I can at least explain the duplicate modprobes.

Modprobe is called to load a kernel module. Some modules require other modules to also be loaded, and in that case, Modprobe will run itself recursively, spawning more modprobes to add the dependencies and the dependencies of the dependencies, etc. Modprobe is called once for every module you load.

---

### Post by pah99 on 2009-05-13
> **MaxIBoy said:**
> Well, I can at least explain the duplicate modprobes.

Modprobe is called to load a kernel module. Some modules require other modules to also be loaded, and in that case, Modprobe will run itself recursively, spawning more modprobes to add the dependencies and the dependencies of the dependencies, etc. Modprobe is called once for every module you load.

So could it have something to do with the fact that I have been playing around with building various kernels lately? And also, this is a fresh install.

---

### Post by lariosa42 on 2009-05-13
OK, thanks.  Still no luck though...

---

### Post by pah99 on 2009-05-13
> **lariosa42 said:**
> OK, thanks.  Still no luck though...

When you first installed jaunty, did it boot fast? Because if so, I had sort of a similar problem. I had started to mess around with various boot processes and options and I screwed it up pretty badly. It got to the point that it was taking like a minute to load. The only way to solve this is to just reinstall Ubuntu.

---

### Post by coldReactive on 2009-05-14
Here's mine.

---

### Post by lariosa42 on 2009-05-14
Nope.  When I installed Jaunty (via Update Manager, from 8.10) I did not notice a significant change in the startup time.

---

### Post by coldReactive on 2009-05-14
Here's mine now without usplash and evolution client.

Down to 27 seconds.

---

### Post by pah99 on 2009-05-14
> **lariosa42 said:**
> Nope.  When I installed Jaunty (via Update Manager, from 8.10) I did not notice a significant change in the startup time.

Well, if you're up for it, I recommend a fresh install. That was the only thing that ever worked for me. And you will probably be able to get rid of the twistd thing too.

---

### Post by 5carby on 2009-05-14
Here's mine. :)

---

### Post by tomcheng76 on 2009-05-15
Is it too slow?

---

### Post by lariosa42 on 2009-05-17
OK, thanks.  I was hoping it wouldn't come to doing a fresh install.   I guess I'll have to wait until I can get an external hard drive.  Thanks again for your help.

---

### Post by Hador on 2009-05-19
stripped down setup on my sony vaio =)

---

### Post by smorar on 2009-05-22
How come I have a lot of IO waiting going on? Anyone know how to sort this out?

```

root@spider:/var/log/bootchart# hdparm -i /dev/sda

/dev/sda:

 Model=TOSHIBA MK8032GSX                       , FwRev=AS111G  , SerialNo=           Y59L1963S
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6


```
```

smorar@spider:/var/log/bootchart$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   426 MB in  2.00 seconds = 212.83 MB/sec
 Timing buffered disk reads:   92 MB in  3.03 seconds =  30.39 MB/sec

```

---

### Post by Greenwidth on 2009-05-26
At the risk of sounding like the joke with the bear, why the big pause at the start of my boot chart?

---

### Post by Artemis3 on 2009-06-02
Here is my current bootchart. As you might guess, i don't like rebooting too much... Any ideas?

---

### Post by Tibuda on 2009-06-02
Huge thread. Does someone knows how to keep only the last boot chart on /var/log/bootchart?

---

### Post by sim-value on 2009-06-02
Interesting

I installed bootchart while my install was pretty new now after some monts i remembered it again ...

Between my first log and now there is 2 seconds diference ... and 10 mb/s less Hardisk throughoutput ?!

---

### Post by kuja on 2009-06-03
> **Artemis3 said:**
> Here is my current bootchart. As you might guess, i don't like rebooting too much... Any ideas?

Well, there are lots of things that might help. 
- Reprofile readahead (reboot, on the grub screen use 'e' to edit, 'b' to boot. Append " profile" to the end of the line that starts with kernel").
- Change concurrency to shell in /etc/init.d/rc 
- Play with insserv to re-order the init scripts start order
- Use sysv-rc-conf to disable any services you don't need.
- Perhaps add all modules that you use to /etc/modules ... you could get a list of that with a command like this "lsmod | tail -n +2 | cut -d ' ' -f 1 | tr '\n' ' '" - That way hopefully they'll all be loaded at once, instead of scattered about your startup. 
- If you have time and such, you could even recompile the kernel to include the modules you need, to eliminate the need for an initramfs in most cases. 
- Disabling any and all splash screens may help (including usplash, gdm/kdm/xdm, and others)
- autologin helps if you can afford to use it
- Not using a display manager to login is definitely faster, if you need the speed 
- Shorten scripts in /etc/init.d if possible ... some of them are rather lengthy when _you_ don't need them to be.

Surely there are plenty of other things you can do too.

---

### Post by TFrog on 2009-06-07
I'm running an old Compaq Presario R4125US laptop.  It has a lowly old AMD64 Athlon 2500+ running at 2.2Ghz.  When running Hardy my boot times were over 45 seconds.  Now with Jaunty, my bootchart times show at or just above 23 seconds:D

---

### Post by Artemis3 on 2009-06-09
> **kuja said:**
> Well, there are lots of things that might help. 
- Reprofile readahead (reboot, on the grub screen use 'e' to edit, 'b' to boot. Append " profile" to the end of the line that starts with kernel").
- Change concurrency to shell in /etc/init.d/rc 
- Play with insserv to re-order the init scripts start order
- Use sysv-rc-conf to disable any services you don't need.
- Perhaps add all modules that you use to /etc/modules ... you could get a list of that with a command like this "lsmod | tail -n +2 | cut -d ' ' -f 1 | tr '\n' ' '" - That way hopefully they'll all be loaded at once, instead of scattered about your startup. 
- If you have time and such, you could even recompile the kernel to include the modules you need, to eliminate the need for an initramfs in most cases. 
- Disabling any and all splash screens may help (including usplash, gdm/kdm/xdm, and others)
- autologin helps if you can afford to use it
- Not using a display manager to login is definitely faster, if you need the speed 
- Shorten scripts in /etc/init.d if possible ... some of them are rather lengthy when _you_ don't need them to be.

Surely there are plenty of other things you can do too.

Great! After concurrency=shell and profile, im down to 123s from 128s... I'll play with the rest now :)

---

### Post by PatrickVogeli on 2009-06-09
Here goes mine, 20 secs.

---

### Post by WiTcHkInG on 2009-06-29
Tweaked Karmic on low end ssd

8.48 secs

---

### Post by JDShu on 2009-06-29
Wow, nice!

So from what I understand Karmic is aiming to have a 10 second boot time on *any* system? Do you guys think this will be possible? Think that upgrading to Karmic when its released will speed up boot time from Jaunty?

Heres mine:

[ATTACH]119381[/ATTACH]

---

### Post by andrewabc on 2009-06-29
> **WiTcHkInG said:**
> Tweaked Karmic on low end ssd

8.48 secs

I'm sure the core i7 helps.
Your disk throughput peaked at more than twice my hard drive (55MB/s). I'm waiting to get a nice SSD on sale. What SSD do you have?

> **JDShu said:**
> Wow, nice!

So from what I understand Karmic is aiming to have a 10 second boot time on *any* system? Do you guys think this will be possible? Think that upgrading to Karmic when its released will speed up boot time from Jaunty?
I sincerely doubt 10 second in karmic will happen on "any" system.
And the 10 second boot goal is for 10.04 not 9.10, so don't expect it (unless you have decent CPU and SSD).

---

### Post by JDShu on 2009-06-29
Ahh right, my mistake. So sounds like there won't be a point to upgrading to Jaunty for now if I have no use for cloud computing.

---

### Post by andrewabc on 2009-06-29
> **JDShu said:**
> Ahh right, my mistake. So sounds like there won't be a point to upgrading to Jaunty for now if I have no use for cloud computing.
What version are you on? Jaunty does have some improvements over previous versions, mostly newer software. And I don't know anything about cloud computing for jaunty. I'm guessing you read a press release for 10.04?

But if what you have works fine, then I'd wait for Karmic (9.10). Start testing the alphas (for you I'd wait until alpha 3 at end of july) to make sure everything works, if not file bugs. Although looking at your join date and # of posts, maybe stay away from testing alphas if you are not sure what to do.

---

### Post by JDShu on 2009-06-29
Ack sorry, I meant upgrading to Karmic, using Jaunty right now.

---

### Post by ajgreeny on 2009-06-29
here's mine.  I'm pretty pleased with the boot time here.  The hardware is not particularly new, as you can see from the chart header paragraph, and it's an old single core sempron 2400+ with 2GB ram, so 19 secs seems fast to me.

I do stop a number of unwanted services eg bluetooth and the various laptop services such as dns-clean, acpi-support, apmd, and saned (no scanner) as this is a desktop, and I suspect this must make some difference, but not a huge amount.

Will karmic be even faster as some are suggesting?

---

### Post by WiTcHkInG on 2009-06-30
> **andrewabc said:**
> I'm sure the core i7 helps.
Your disk throughput peaked at more than twice my hard drive (55MB/s). I'm waiting to get a nice SSD on sale. What SSD do you have?

[30gb OCZ core v2]("http://www.ocztechnology.com/products/flash_drives/ocz_core_series_v2_sata_ii_2_5-ssd") (Read: up to 170 MB/sec
Write: up to 98 MB/sec).
Got 2 but ones playing up, else they would be in raid0.

Just got [this OCZ 30gb Agility]("http://www.ocztechnology.com/products/flash_drives/ocz_agility_series_sata_ii_2_5-ssd") which is my main drive with Jaunty on. Boots around 8 secs too.
Both using ext4.

---

### Post by andrewabc on 2009-06-30
> **WiTcHkInG said:**
> [30gb OCZ core v2]("http://www.ocztechnology.com/products/flash_drives/ocz_core_series_v2_sata_ii_2_5-ssd") (Read: up to 170 MB/sec
Write: up to 98 MB/sec).
Got 2 but ones playing up, else they would be in raid0.

Just got [this OCZ 30gb Agility]("http://www.ocztechnology.com/products/flash_drives/ocz_agility_series_sata_ii_2_5-ssd") which is my main drive with Jaunty on. Boots around 8 secs too.
Both using ext4.

I've been reading lots about SSD, and specifically OCZ as they were best with their vertex series (competition is catching up soon). I hope to get one in October for ubuntu 9.10.

---

### Post by Gizenshya on 2009-06-30
Do I have to take off my password to get it to nt count that dead time space while typing password?

Also.. thats a lot of pages...

so did someone update that tutorial yet?

---

### Post by centered effect on 2009-07-01
My boot times.  Any reason why the system seems to "sit" for the first 5 seconds?

---

### Post by jumjum11 on 2009-07-11
> **centered effect said:**
> My boot times.  Any reason why the system seems to "sit" for the first 5 seconds?

It's the time it takes for your kernel to initialize your hardware. You can bring it down to under 2 seconds with a custom kernel containing only the drivers you need.

My notebook boot Jaunty 9.04 to the login screen in under 6 seconds.

Tweaks:
kernel 2.6.30.1 + trace(open) patch, built without any modules
sreadahead instead of readahead
"fastboot rootfstype=ext4" in /boot/grub/menu.lst
"CONCURRENCY=shell" in /etc/init.d/rc

---

### Post by orengolan on 2009-07-14
it takes around 60 seconds to reach the login screen
and 27 seconds from there to until I see the keyring password string.

is it normal?
take a look at my bootchart and let me know if there is something I can improve.

also here is the list of apps in my /etc/init.d,
what can I disable ?

```
acpid
acpi-support
alsa-utils
anacron
apmd
apparmor
apport
atd
aumix
avahi-daemon
bluetooth
bootlogd
bootlogs.sh
bootmisc.sh
checkfs.sh
checkroot.sh
clamav-freshclam
console-screen.sh
console-setup
cron
cups
dansguardian
dbus
dhcdbd
dns-clean
firehol
gdm
glibc.sh
hal
halt
hostname.sh
hotkey-setup
hwclock.sh
keyboard-setup
killprocs
klogd
laptop-mode
libpam-foreground
linux-restricted-modules-common
module-init-tools
mountall-bootclean.sh
mountall.sh
mountdevsubfs.sh
mountkernfs.sh
mountnfs-bootclean.sh
mountnfs.sh
mountoverflowtmp
mtab.sh
networking
NetworkManager
NetworkManager.dpkg-backup
nfs-common
nvidia-kernel
ondemand
pcmciautils
policykit
portmap
powernowd
powernowd.early
pppd-dns
procps
pulseaudio
rc
rc.local
rcS
readahead
readahead-desktop
README
reboot
rmnologin
rsync
saned
screen-cleanup
sendsigs
single
skeleton
stop-bootlogd
stop-bootlogd-single
stop-readahead
sysklogd
system-tools-backends
tinyproxy
udev
udev-finish
ufw
umountfs
umountnfs.sh
umountroot
urandom
usplash
vboxdrv
vboxnet
wpa-ifupdown
x11-common
```

---

### Post by andrewabc on 2009-07-14
> **orengolan said:**
> it takes around 60 seconds to reach the login screen
and 27 seconds from there to until I see the keyring password string.

is it normal?
take a look at my bootchart and let me know if there is something I can improve.

also here is the list of apps in my /etc/init.d,
what can I disable ?



Looks like something definitely wrong in bootchart. Between 16 seconds and 23 seconds it is not doing anything.

Not sure how to fix it. Looks like nm-modem-probe or s10udev or udevadm causing the wait. If that gets fixed you could save 5 seconds.

what's your computer specs? The disk throughput is low 30mb/s (laptop hard drive?). Based upon your processor, I'm guessing it is older computer. How much RAM?

---

### Post by orengolan on 2009-07-14
It's a sony vaio laptop - vgn-txn27n.  1.33GHz Intel Core Solo CPU, 2GB RAM.

It will be great if you can link to a site that teach how to read this chart, this is very interesting.

Thanks for the help!

---

### Post by andrewabc on 2009-07-14
> **orengolan said:**
> It's a sony vaio laptop - vgn-txn27n.  1.33GHz Intel Core Solo CPU, 2GB RAM.

It will be great if you can link to a site that teach how to read this chart, this is very interesting.

Thanks for the help!

I don't know of any sites to teach that. Google might know.
It's pretty obvious looking at the chart that something is happening at a certain point and waiting for something since there is no CPU or disk usage.

With 2gb of ram, assuming your hard drive is a slow 5400 RPM, there are ways to speed up firefox and other programs by having them in RAM.
[Howto; Firefox profile in RAM for increased speed and stability](http://ubuntuforums.org/showthread.php?t=1120475)

---

### Post by wynneth on 2009-07-15
Typical bootup, HP laptop AMD64x2 running 32bit, 2.5Gi DDR2, non graphical bootup - no GDM, no splash, no quiet option.

---

### Post by The Real Dave on 2009-07-15
A respectable 26 seconds on a 3Ghz Pentium IV, with 1.4Gb RAM and SATA drives :D I reckon its mainly down to Ext4 and my newer Samsung Spinpoint drive. 

However, though usplash is listed, and is in GRUB, I dont get any graphical boot :( I've tried re-installing splash, but it didn't help. Any advice would be greatly appreciated.

---

### Post by wynneth on 2009-07-15
> **The Real Dave said:**
> A respectable 26 seconds on a 3Ghz Pentium IV, with 1.4Gb RAM and SATA drives :D I reckon its mainly down to Ext4 and my newer Samsung Spinpoint drive. 

However, though usplash is listed, and is in GRUB, I dont get any graphical boot :( I've tried re-installing splash, but it didn't help. Any advice would be greatly appreciated.

Hmm. Well, when you say no graphical boot, are you still getting the graphical login screen after the boot process itself? 

I assume when you say 'usplash is listed, and is in GRUB' you mean 'splash' is in fact listed in the boot options for the chosen kernel. Also, do you have the 'quiet' option on as well? I believe the typical Ubuntu installation has both quiet and splash enabled. If by chance you're also not getting the graphical login, you might have problems with GDM(if you're using gnome).

---

### Post by The Real Dave on 2009-07-16
> **wynneth said:**
> Hmm. Well, when you say no graphical boot, are you still getting the graphical login screen after the boot process itself? 

I assume when you say 'usplash is listed, and is in GRUB' you mean 'splash' is in fact listed in the boot options for the chosen kernel. Also, do you have the 'quiet' option on as well? I believe the typical Ubuntu installation has both quiet and splash enabled. If by chance you're also not getting the graphical login, you might have problems with GDM(if you're using gnome).

After a non-graphical boot, I do get a graphical login screen. Both quiet and splash options are listed as options in GRUB. And yes, I am using Gnome. 

Thanks for your help :D

---

### Post by Dessicus on 2009-07-18
17 sec. not bad
3.2 GHz Athalon X2, 2 GB of ram, 350 GB IDE HDD Ext 3

---

### Post by colorprint on 2009-07-20
17sec on Samsung SATA2 64Gb SSD

---

### Post by PhoHammer on 2009-07-23
So I just installed a minimal ubuntu ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD))
 and only installed the stuff I need (I went with xfce, so I guess you could call
it xubuntu). It seemed to boot faster than usual, and when I checked it with bootchart I
was surprised to say the least. The best I´ve ever done with a full ubuntu install was
23 seconds. This beast booted in 14 seconds, including the pause to spit out gtk errors
on the end of it!! I need to find out how to fix those.... and no telling what this would do
if I had the karmic alpha installed!

edit: Oh and it is ext4 (on a laptop HDD, 5400 rpm i think...)

---

### Post by PhoHammer on 2009-07-23
Fiddled around and got the python/gtk to be quiet and prevented dns-clean and the 
pppwhatever dial-up stuff from starting with BUM and tadaa...**.13.28 seconds**!!

---

### Post by Dullstar on 2009-07-23
I did not know boot charts were even possible...

---

### Post by Dessicus on 2009-07-23
After some tweaking I got my boot time down to 12 seconds

---

### Post by PhoHammer on 2009-07-23
> **markp1989 said:**
> my desktop

OS: Arch 
kernel: Factory

wm: openbox
panel: fbpanel 
autologin : added to the top of my rc.multi 
```
##Login and start X
(/bin/su mark -l -c "/bin/bash --login -c startx >/dev/null 2>&1") &
```heavily modified rc.sysinit 


Root drive is an OCZ Vertex 30gb 




How in the world did you do this?! Haha!! So what are init=/ and elevator and would they
work in ubuntu? 

I tried to install arch and it said something about my hdd being bad
and when it gave me the option to select which drive to partition it said the 
size was ´´0GiB´´and would not let me select it...:( Ubuntu/debian/pclinuxos/opensuse
never said this...

I guess that throughput on the SSD might have something to do with your boot as well ;)

---

### Post by proxygeek on 2009-07-24
_**Ubuntu Taking Too Long to Load!**_

Hi All...greetings!
Was happy with my Ubuntu boot time till my roomie got a laptop and suddenly my laptop seemed to be taking forever to load Ubuntu, compared to the other laptop in the room.

The Grub loading is taking about 20-22 seconds, and from Grub to Login Prompt in Ubuntu takes another 47 seconds! Infact, it takes 20-22 seconds from Grub Option selection to first Loading Splash screen. 

Meanwhile, its just stuck at "Starting Up..." message after Grub and before splash screen for 20 odd seconds.

Attached is my bootchart. I am using HP Pavilion DV4 TX 1241 with Core2Duo 2.0 GHz, 3GB RAM, 320 GB HDD @ 5400 RPM

Somebody please help me speeding up the loading process!

Thanks in advance
Proxygeek

---

### Post by moster on 2009-07-24
CPU: Intel E5200 OC to 3,4 GHz
RAM 2GB DDR2
Disk: Seagate 250 GB, 7200 RPM, 8 MB cache
Ubuntu 9.4 x86, everything default

---

### Post by Nburnes on 2009-07-24
15 Sec isn't bad I think

---

### Post by Tomatz on 2009-07-25
> **proxygeek said:**
> _**Ubuntu Taking Too Long to Load!**_

Hi All...greetings!
Was happy with my Ubuntu boot time till my roomie got a laptop and suddenly my laptop seemed to be taking forever to load Ubuntu, compared to the other laptop in the room.

The Grub loading is taking about 20-22 seconds, and from Grub to Login Prompt in Ubuntu takes another 47 seconds! Infact, it takes 20-22 seconds from Grub Option selection to first Loading Splash screen. 

Meanwhile, its just stuck at "Starting Up..." message after Grub and before splash screen for 20 odd seconds.

Attached is my bootchart. I am using HP Pavilion DV4 TX 1241 with Core2Duo 2.0 GHz, 3GB RAM, 320 GB HDD @ 5400 RPM

Somebody please help me speeding up the loading process!

Thanks in advance
Proxygeek

I had this problem. 

Disabling the floppy drive in the bios (even though i dont have a FDD) fixed the problem for me.

---

### Post by proxygeek on 2009-07-28
> **Tomatz said:**
> I had this problem. 

Disabling the floppy drive in the bios (even though i dont have a FDD) fixed the problem for me.

Thanks for the suggestion Tomatz. I had pushed the FDD boot to last in order in the sequence of drive in the BIOS. But that definitely didn't help. Let me try disabling it altogether and check.

Somehow, I feel it may ve something to do with the [restricted] drivers I am using for my nVidia Card. Hope I am wrong though :-P

Will post the result by EOD.

Regards,
Proxygeek

---

### Post by prime85 on 2009-07-29
i am curious how fast everyones ubuntu boots... 


either tell us your boot time or post a boot chart.
:P

and if anyone has any suggestions to speed it up

---

### Post by overdrank on 2009-07-29
> **prime85 said:**
> i am curious how fast everyones ubuntu boots... 


either tell us your boot time or post a boot chart.
:P

and if anyone has any suggestions to speed it up

Threads merged :)

---

### Post by proxygeek on 2009-07-30
> **proxygeek said:**
> Thanks for the suggestion Tomatz. I had pushed the FDD boot to last in order in the sequence of drive in the BIOS. But that definitely didn't help. Let me try disabling it altogether and check.

Somehow, I feel it may ve something to do with the [restricted] drivers I am using for my nVidia Card. Hope I am wrong though :-P



Disabled the FDD option.  No joy yet :(

Tried checking the UUID for the resume file and the UUID of swap partition:
   [FONT=&quot]cat /etc/initramfs-tools/conf.d/resume[/FONT]
AND
  blkid


Both are the same. Attached is the new bootchart.

 It's still hanging for 20 seconds before doing anything :(
[FONT=&quot][/FONT]
  
Any help guys? 

Regards,
Proxygeek

---

### Post by coldReactive on 2009-08-02
My new computer.

---

### Post by RATM_Owns on 2009-08-02
Jeez, Ubuntu has a ******** of daemons. O_O

I'm glad I use Arch. :P

---

### Post by proxygeek on 2009-08-03
> **proxygeek said:**
> Disabled the FDD option.  No joy yet :(

 It's still hanging for 20 seconds before doing anything :(



Yoohoo! Slashed about 14 seconds from my prev boot-time!
The prob turned out to be a bios bug [EHCI Handoff failed]. Recompiled the kernel with the probe time in pci-quirks.c reduced to 50ms from 5000 ms.

Still needs to go down by about 8 seconds to qualify as "fast". 

For more info: 
[https://lists.linux-foundation.org/pipermail/bugme-new/2008-December/020541.html](https://lists.linux-foundation.org/pipermail/bugme-new/2008-December/020541.html)  OR [http://www.proxygeek.org/moments/technical/linux/speedupyourbootingprocess](http://www.proxygeek.org/moments/technical/linux/speedupyourbootingprocess)

 The new bootchart attached.

---

### Post by rossmoore on 2009-08-03
I'm using a laptop: Dell XPS 1530M. Boot time seems respectable, but I noticed that disk utilization seems to be pegged at no more than 50% whereas everyone else's boot charts show full utilization.

Is this just a random effect caused by that 67Mb/s spike, or is this not right?..

---

### Post by blah1898 on 2009-08-03
No idea what this means, but here's mine.

---

### Post by xir_ on 2009-08-04
> **rossmoore said:**
> I'm using a laptop: Dell XPS 1530M. Boot time seems respectable, but I noticed that disk utilization seems to be pegged at no more than 50% whereas everyone else's boot charts show full utilization.

Is this just a random effect caused by that 67Mb/s spike, or is this not right?..


just a thought if your system has dual cores then you might not have enabled concurrent boot. This enables both the cpu's to be used on boot.

---

### Post by madscientist032 on 2009-08-04
Has anyone booted faster than 18 seconds?

---

### Post by x33a on 2009-08-05
here's mine:

[ATTACH]123675[/ATTACH]

---

### Post by gorade on 2009-08-07
The chart says 17 s but when I clock it takes above 60 s. What does it measure?

---

### Post by cariboo on 2009-08-07
Bootcharts reports the time from grub start to the login screen.

---

### Post by gorade on 2009-08-07
That took 48 s by clock. Nearer, yes, but far more than was charted.

---

### Post by gorade on 2009-08-08
There are quite a lot of postings to this thread so I am not sure someone has said this before. 
It seems to med that the most important factor is capacity of hardware. An old CPU in an elderly laptop makes boot-chart report a long booting time and contrary. 

However it also is something more going on than is recorded by boot-chart.
As you can see, my relatively powerful Intel quad 2.6 GHz makes it in less than 20 s. 

When I clock it it takes 46 s from GRUB to Log in. What is it doing during the 26+ seconds? Looking for a proper network? I moved from /etc/rcS.d/S40networking to /etc/rc2.d/14networking, which I believed would give it lower priority than GDM. However I couldn't discern any difference what so ever.

Anyone with better understanding that could give me a hint?

---

### Post by madscientist032 on 2009-08-09
Just performed a fresh install of Ubuntu 9.04 (switched from xubuntu 9.04). I know there's code to disable the bootsplash but I can't remember it! 

Here's my boot-chart!

---

### Post by rossmoore on 2009-08-10
Are you timing it all the way to the gnome/KDE desktop? I _think_ that bootchart stops at GDM - i.e. the login screen. If, like a lot of people, you autologin to your main account you'll never see the GDM screen.

On my machine, the bootchart time corresponds pretty well to the amount of time it takes for GDM to present itself. If you don't have readahead set to also pull in the gnome stuff, the remaining 20s or so then corresponds to the amount of time it takes gnome, and compiz, and everything else to load.

---

### Post by antoniosanct on 2009-08-18
I have a problem at boot. One 'sh' process hangs about 50 secs when it didn't before :(.
This is my attach. Thanks a lot! Regards!

---

### Post by gorade on 2009-08-20
> **rossmoore said:**
> Are you timing it all the way to the gnome/KDE desktop? I _think_ that bootchart stops at GDM - i.e. the login screen. If, like a lot of people, you autologin to your main account you'll never see the GDM screen.

On my machine, the bootchart time corresponds pretty well to the amount of time it takes for GDM to present itself. If you don't have readahead set to also pull in the gnome stuff, the remaining 20s or so then corresponds to the amount of time it takes gnome, and compiz, and everything else to load.

As I wrote I am timing from GRUB to login. I use Gnome. So by my timer it takes 46 seconds from starting in GRUB until my login screen appears. Latest Bootchart record was 16,5 seconds so it is obviously timing something else. 

Windows XP 64 bit boots some seconds faster on the same machine.
Thats humilating, eh?
Gorade

---

### Post by bjorkiii on 2009-08-24
how do i put an image up of my bootchart

---

### Post by gorade on 2009-09-05
bjorkii

Start Replay. 

Look below the text.
Below Post Icons.

Look at Additional Options.
Second section: "Attach Files"

Click at Manage Attachments

You get a pop up window for uploading files. 

Now, let us see it! [http://ubuntuforums.org/images/icons/icon7.gif](http://ubuntuforums.org/images/icons/icon7.gif)

---

### Post by Dessicus on 2009-09-09
I've been getting in the low 30s on my Asus Eee PC 1005HA. Anyone have any suggestions on speeding it up a bit? I've already turned off usplash and turned off the unnecessary processes in bootup manager. Also how do I profile my boot in Karmic?

---

### Post by apocalypse80 on 2009-09-10
Intel x25m 160GB @ HP Elitebook 8530p
No optimizations whatsoever.

Actual time between grub selection and a fully working desktop (using autologin) is 20 seconds - and that includes loading a ton of applets, openoffice quickstarter, conky, gnome do etc.

I LOVE :KS this thing.

---

### Post by Atze_B on 2009-09-10
Here's my. I am very happy with my 10seconds boot. Got a SSD drive inside my PC (OCZ Agility 120MB). 2nd figure is from last boot, after upgrading to final 2.6.31 kernel and sreadhead running on last boot. Disk utilization looks very different but no further improvement in boot time.

---

### Post by PhoHammer on 2009-09-11
> **Atze_B said:**
> Here's my. I am very happy with my 10seconds boot. Got a SSD drive inside my PC (OCZ Agility 120MB). 2nd figure is from last boot, after upgrading to final 2.6.31 kernel and sreadhead running on last boot. Disk utilization looks very different but no further improvement in boot time.

Ohh yummy, I want a SSD. Maybe it is time to get one, as Karmic is telling me that my main HDD is failing...:p

---

### Post by apocalypse80 on 2009-09-12
Just a thought here, but isn't the default configuration of bootchart pretty much irrelevant?
It seems to me that the login->desktop time is usually much longer than grub->login.

Anyway I made me some charts quantifying the difference between my laptop's original hdd (fujitsu 250GB, 5400rpm) and the shiny new intel ssd.
Cloned installation, only optimization is removing usplash.

grub -> login (default bootchart): 19 vs 8 seconds
grub -> desktop (autologin, bootchart=nostop): 57 vs 16.5 seconds

The ssd is barely even working from grub->login, it only stretches it's legs a bit after login.

And for kicks, one with the ssd and a new user (= just the default applets) : grub->desktop in 13 seconds :D
I think I'll try a fresh install and shoot for 10 secs :twisted:

---

### Post by Lekensteyn on 2009-09-13
Special notes:
Installed on an external HDD, USB 2.0.
Other OS is Win XP (although I don't use it)
This file says it took 22 sec to boot, but I counted 3:35 minutes (from grub loading to login screen)

---

### Post by apocalypse80 on 2009-09-14
> **Lekensteyn said:**
> Special notes:
Installed on an external HDD, USB 2.0.
Other OS is Win XP (although I don't use it)
This file says it took 22 sec to boot, but I counted 3:35 minutes (from grub loading to login screen)

Edit /boot/grub/menu.lst and add the parameter bootchart=nostop (after ro quiet splash).
That way bootchart will not stop on it's own.

Boot, login, wait until everything is finished - for more accurate results you may want to enable autologin.
Then run "sudo /etc/init.d/stop-bootchart start" to stop bootchart.
That should show any major delays that don't fall within the default bootchart time-frame.

Oh and remember to go back to menu.lst and remove bootchart after you're done.

---

### Post by KonradKathan on 2009-10-17
I've been fiddling with this machine for a while. Its running faster with a P4 1500MHZ, 512MB RAM and a 7200RPM drive than My other Dell with 3GB RAM, X64 AMD 3800 processor and a 5400RPM drive. I am surprised a the speed this box can output! I'm also not sure if I can bring it any lower without getting more RAM.

Konrad

---

### Post by madscientist032 on 2009-10-17
> **KonradKathan said:**
> I'm also not sure if I can bring it any lower without getting more RAM.

Konrad

Your hard drive speed is the bottleneck. 5400 RPM hard drives are notorious for this issue, especially when they are paired with large amounts of RAM and a dual or quad-core processor. So the faster Ubuntu can get from the hard drive to the RAM depends on the hard disk's RPM. The faster, the better.

---

### Post by andrewabc on 2009-10-30
6 second bootchart on ubuntu 9.10 32bit
OCZ Vertex 60gb aligned to 512kb. Firmware 1.3. ext4. No tweaks to speed up ubuntu.

Ubuntu 9.04 on same SSD had 10 second bootchart. 9.04 on my hard drive had 19 second bootchart.

If you install bootchart you will get +45 seconds added to what would have normally occured in other ubuntu versions.

After rebooting once or twice to get the new bootcharts
[do this to removed the 45 second delay](http://ubuntuforums.org/showthread.php?p=8015068#post8015068)

---

### Post by gsch on 2009-10-31
I have a more pressing question: How do you boot Karmic? Basic, huh? I just get "starting up ..." after upgrading to karmic. When I escape and select an older kernel i can boot, but my touchpad isn't working. It was a mission just to write this message. Even the live cd does not boot. How do I fix the touchpad? How do I fix the boot issue?
Acer Travelmate 2450 ATI 200M if that is of any consequence.

---

### Post by omarly on 2009-10-31
I am comfy with my new install, but pls tell me how 2 speed it up :)

Lust love my new 64 install - do i have 2 get out?

---

### Post by Valygard84 on 2009-10-31
Seems like my boot time is pretty okay. Bootchart reports about 40s on a fresh karmic install w/ apache and mysql.
Any pointers on how I could improve that?

Edit: Due to the size of the pic, I had to upload it elsewhere. Now without the +45s delay from bootchart. I'ld still say ~40secs isn't all that great. Help! :D

link: 
[http://www.planethodor.de/philipp-laptop-karmic-20091031-2.png](http://www.planethodor.de/philipp-laptop-karmic-20091031-2.png)

---

### Post by apocalypse80 on 2009-10-31
> **Valygard84 said:**
> I'ld still say ~40secs isn't all that great. Help! :D

Hate to break it to you but your boot time isn't 40 seconds, it's longer.
Your chart doesn't show the cpu/hdd going idle, so it doesn't include the end of the boot process.

Look at mine.
[http://img265.imageshack.us/img265/8148/paez.png]("http://img265.imageshack.us/img265/8148/paez.png")

At 16 seconds the thing goes completely idle, then I start running my apps.
If you look low, you'll also see xsplash ending at 16 seconds.
Therefore my boot time is 16 seconds.

You might want to increase bootchart's delay (find "sleep xx" in /etc/init/bootchart.conf) until you can see the end.

---

### Post by Dirtpile on 2009-10-31
Mine.   Sorry about the size.

[[IMG]http://www.imageput.com/hosted/95134computron-jaunty-20091031-1.png[/IMG]]("http://www.imageput.com/")

---

### Post by andrewabc on 2009-10-31
@gsch
Ask in support forum. This thread is specifically for posting bootcharts.

@apocalypse80
His bootchart is correct. He does not have the extra 45 seconds added that yours does. This is the way bootchart was before karmic. Now in karmic by default it adds 45 seconds extra to whatever the old bootchart showed. That is why you see firefox and your programs running. See my previous post about how to remove the 45 seconds to get the old style of bootchart back. I think you meant to say his bootchart is "shorter" (because of 45 second delay), but looking at his bootchart it doesn't appear to get to desktop and do other stuff by that time. Boot stuff is still near end of 40 seconds. Although I could be misreading his bootchart.

I think there could be something wrong with Valygard84 bootchart as it takes way to long to boot. 40 seconds for a dualcore? The diskthroughput is very minimal, flatlined most of the time. My 3 year old core2duo on my hard drive booted in 19 seconds in Jaunty. Not sure why it would be twice as long for a similar looking system.

Old bootchart is GRUB->GDM
New bootchart is GRUB->GDM + 45seconds

For simplicity sake I've uploaded both old bootchart method and new bootchart method on my SSD. My boot time is not 55 seconds, as I have audacious (music player) running by the 15 second mark. My computer is not still booting at that time. It is idle at 12 second mark or so on new bootchart. Old bootchart method is 6 seconds.

Comparing old bootchart method is much better and easier to look at as we are not looking over extra 45 seconds that can be doing anything (browsing web etc).

---

### Post by apocalypse80 on 2009-10-31
> **andrewabc said:**
> @apocalypse80
His bootchart is correct. He does not have the extra 45 seconds added that yours does. This is the way bootchart was before karmic.

Oh I know, you'll notice me quoting my boot as 16 secs, but I've always thought the old bootchart method was pretty useless - boot doesn't end until I can work.

It's very easy to see when the thing has fully booted, you just let the pc be (not start any apps for a few seconds) when benchmarking and then look for idle cpu+hdd on the graph.
The only downside is that the number up top means nothing.

PS. is it just me or are png bootcharts being automatically converted to unreadable jpgs?

---

### Post by andrewabc on 2009-10-31
> **apocalypse80 said:**
> Oh I know, you'll notice me quoting my boot as 16 secs, but I've always thought the old bootchart method was pretty useless - boot doesn't end until I can work.

It's very easy to see when the thing has fully booted, you just let the pc be (not start any apps for a few seconds) when benchmarking and then look for idle cpu+hdd on the graph.
The only downside is that the number up top means nothing.

PS. is it just me or are png bootcharts being automatically converted to unreadable jpgs?

Ok, maybe they could change the 45 seconds to 10 seconds. Most newer (mine is 3 years old), wouldn't take more than 10 (heck even 20) seconds to get to idle desktop after GDM. 45 is a bit of overkill, unless that was their intention. But peopel could manually change it to 60 seconds if they want. Majority of users don't have reason to see that firefox has been open and running for 30 seconds in a 'bootchart'

You are correct about png. Must be forum problem. Someone contact a moderator.

---

### Post by Valygard84 on 2009-11-01
> **andrewabc said:**
> 
*snip*
I think there could be something wrong with Valygard84 bootchart as it takes way to long to boot. 40 seconds for a dualcore? The diskthroughput is very minimal, flatlined most of the time. My 3 year old core2duo on my hard drive booted in 19 seconds in Jaunty. Not sure why it would be twice as long for a similar looking system.
*snip*


I'ld be very interested in knowing what makes my laptop take so long to boot. 
Would you be so nice to elaborate on what you meant?
I'ld be happy to fiddle around a bit to reduce my boot time. 20secs sounds really nice. :)

---

### Post by andrewabc on 2009-11-01
> **Valygard84 said:**
> I'ld be very interested in knowing what makes my laptop take so long to boot. 
Would you be so nice to elaborate on what you meant?
I'ld be happy to fiddle around a bit to reduce my boot time. 20secs sounds really nice. :)

Well first off, did you edit bootchart to remove the extra 45 seconds (to make it like bootchart was in previous ubuntu versions)? If so then maybe a problem. post your computer specs.

Or is that just a default installed bootchart you posted? If so then it is normal (although not possible since it is 40 seconds and it should be x+45 seconds.)

---

### Post by topdownjimmy on 2009-11-01
Hi everyone -- I'm looking to get some help on interpreting my bootchart.  I get the feeling it's lamentably overblown, after having looked at some of the other ones on here.

[my bootchart](http://www.kilobitspersecond.com/scraps/jay-desktop-karmic-20091101-2.png)

I'd very much appreciate any opinions.  Thanks.

---

### Post by Valygard84 on 2009-11-01
> Well first off, did you edit bootchart to remove the extra 45 seconds (to make it like bootchart was in previous ubuntu versions)? If so then maybe a problem. post your computer specs.

Or is that just a default installed bootchart you posted? If so then it is normal (although not possible since it is 40 seconds and it should be x+45 seconds.)

That one was without the 45 seconds.

I made 2 new bootcharts, one with +45 secs and one with +70 secs.
I started firefox manually immidiatly when possible.
Judging from when firefox starts, my system needs about 78 seconds to boot. Help. :(

+45 secs: (no firefox process visible yet)
[http://planethodor.de/bootchart/philipp-laptop-karmic-20091101-1.png](http://planethodor.de/bootchart/philipp-laptop-karmic-20091101-1.png)

+70secs: (firefox starting at about 78 seconds)
[http://planethodor.de/bootchart/philipp-laptop-karmic-20091101-3.png](http://planethodor.de/bootchart/philipp-laptop-karmic-20091101-3.png)

The only changes I made that could impact boot time are removing apache2, mysql and sane startup from boot with sysv-rc-conf. 
That should lower boot time though.

For basic specs see my sig.

Some diagnostic files:
lspci: [http://planethodor.de/bootchart/lspci.txt](http://planethodor.de/bootchart/lspci.txt)
lsmod: [http://planethodor.de/bootchart/lsmod.txt](http://planethodor.de/bootchart/lsmod.txt)
dmesg: [http://planethodor.de/bootchart/dmesg.txt](http://planethodor.de/bootchart/dmesg.txt)

If further infos are needed I'll be happy to oblige. And maybe open a new thread to stop messing up this one here if needed.

Also, thanks a lot for looking at my case. :)

---

### Post by andrewabc on 2009-11-01
> **topdownjimmy said:**
> Hi everyone -- I'm looking to get some help on interpreting my bootchart.  I get the feeling it's lamentably overblown, after having looked at some of the other ones on here.

[my bootchart](http://www.kilobitspersecond.com/scraps/jay-desktop-karmic-20091101-2.png)

I'd very much appreciate any opinions.  Thanks.

Bootchart on 9.10 is 45 seconds longer than on jaunty and previous.
So subtract 45 seconds from your time if comparing to previous bootcharts, and if someone has disabled the 45 second delay.

In your bootchart it shows dropbox, gnome-do, beagle, and other apps starting. So your 'boottime' is definitely less than the time shown.

as other have pointed out look for idle cpu for bootime, but in case of your bootchart there is none so this makes that method difficult, and another reason why 45 second delay is silly, as it makes boottime comparisons impossible without a bunch of math and looking at chart to see when it possibly stopped 'booting' and is at desktop.

EDIT:
Attached is pentium 4 1.7ghz, 768mb SDRAM, 80gb hard drive (ubuntu installed near end of hard drive on small partition).
So **topdownjimmy** not sure what is making your bootchart longer than my old computer when your CPU is twice as fast as mine. I'm sure your RAM/hard drive is better than mine too :(
I'm not sure why your I/O (wait) and disk utilization is always being used. Maybe there is something wrong with hard drive or it is just extremely slow?

I thought someone says bootchart doesn't stop until idle CPU, but I don't think that is true. It is simply old bootchart+45 second delay. I think that person meant it is new way to manually time it by looking at bootchart. If you see idle cpu it must be done booting...

---

### Post by apocalypse80 on 2009-11-01
Looking for idle time works assuming there is idle time.
Or you can find the end of the second xsplash instance = appearance of desktop.

@topdownjimmy

You chart says you first see a desktop at 56 seconds.
It looks like you're using both beagle and tracker for indexing which is suicidal (hdds don't do multitasking) and is the reason your system doesn't go idle anywhere on that chart.
Try disabling at least one of those.

@Valygard84

In a similar fashion, your desktop appears at 60 seconds, but during that time dropbox is raping your hdd - again no idle time.
You are on a laptop (5400 rpm hdd?) so 60 seconds doesn't sound like so much - I was getting 57 seconds with a 5400rpm hdd.

---

### Post by scout4536 on 2009-11-01
Dell Mini 10 1.60ghz 1Gb RAM Ubuntu 9.04 ext3  24secs any good?[ATTACH]134245[/ATTACH]

---

### Post by rp3 on 2009-11-01
> **st33med said:**
> To attach a file: click on the paper-clip in the advance Reply to topic. A window pops-up. Click the browse button, and browse to the file, namely /var/log/bootchart/*. Then click 'Upload' and close the window. It is now attached to your reply.

Or, if you mean you don't have bootchart:
```
sudo apt-get install bootchart
```
Then reboot and look in /var/log/bootchart

Not sure what it all means but decided to give it a go on my Toshiba A305 laptop with the new 7200 Seagate 320gigHD...

:)

---

### Post by proxygeek on 2009-11-01
_***Karmic Koala Upgrade from Jaunty***_

Boottime used to be a breezy 23-25 seconds on Jaunty for me, minus the splash.
But after the upgrade, Karmic bootcharts are showing boot time as way [U][I]over 1min 30 seconds!!
[/I][/U]
I am sure it's not measuring the correct boot time on Karmic as seems to be the case from some other posts here, but it still seems to be a lil slower than Jaunty.Attaching below the Karmic bootchart...any suggestions to pare it down a bit?
Regards,
[proxygeek]("http://www.proxygeek.org")

---

### Post by dash2 on 2009-11-02
I've got a similar long startup... here's my bootchart:
[ATTACH]134339[/ATTACH]

I don't really know how to read this... can anyone suggest how to shorten things a bit?

---

### Post by 133794m3r on 2009-11-02
> **dash2 said:**
> I've got a similar long startup... here's my bootchart:
[ATTACH]134339[/ATTACH]

I don't really know how to read this... can anyone suggest how to shorten things a bit?

how can you even read that? That image is so small that i can't make out anything at it's native resolution. I don't know how to read it.. and there was a post earlier in this thread about how to reduce boot up time.

---

### Post by proxygeek on 2009-11-02
> **proxygeek said:**
> _***Karmic Koala Upgrade from Jaunty***_

Boottime used to be a breezy 23-25 seconds on Jaunty for me, minus the splash.
But after the upgrade, Karmic bootcharts are showing boot time as way [U][I]over 1min 30 seconds!!
[/I][/U]
I am sure it's not measuring the correct boot time on Karmic as seems to be the case from some other posts here, but it still seems to be a lil slower than Jaunty.Attaching below the Karmic bootchart...any suggestions to pare it down a bit?
Regards,
[proxygeek]("http://www.proxygeek.org")


Here's the bootchart minus the 45 seconds. Looks much leaner now at 55 seconds. But still a big fat sloth compared to Jaunty.

> **dash2 said:**
> I've got a similar long startup... here's my bootchart:
[ATTACH]134339[/ATTACH]

I don't really know how to read this... can anyone suggest how to shorten things a bit?

Dash, you may try commenting out the below section in /etc/init/bootchart.conf as suggested in earlier posts:

```
#pre-stop script
    # Sleep for an extra 45s to allow enough time to chart the desktop
    # login
#    [ "$UPSTART_STOP_EVENTS" = "stopped" ] && sleep 45
#end script
```

Helps shave 45 seconds from the chart but not the actual boot process.

Regards,
[proxygeek]("http://www.proxygeek.org")

---

### Post by proxygeek on 2009-11-02
I think the boot up time for Karmic, even though seemingly quite higher than Jaunty, can still be accounted for to some extent:

1) Weired behavior from Bootchart, deciding to wait for an extra 45 seconds. Comment out as suggested, and 45 seconds off. 

2) EHCI Handoff time limit reduced (to 2 seconds ?), but can still be reduced further to 50 ms, if need be.

3) Karmic decides to wear some extra bling before presenting itself to you after logon. For example, the WiFi and ethernet are totally up and running when you are presented with the desktop, while in Jaunty, these started a few seconds after you you saw the desktop.

That said, it would still leave at least 20-30 seconds of extra delay un-explained.

Regards,
[proxygeek]("http://www.proxygeek.org")

---

### Post by gjoellee on 2009-11-02
I will post mine when I get my laptop (probably today). It has the Intel Core i7 processor which is said to be the fastest processor on the planet. Now I don't get the fastest i7 processor but I am sure it will be fast. 

Can't wait to see the boot chart :D

---

### Post by m00ds on 2009-11-02
Boot time 31.18 secs. Dell Vostro 1200 laptop

---

### Post by dash2 on 2009-11-04
ProxyGeek: Thanks very much... is there a way to shorten the actual boot process, though?

---

### Post by scout4536 on 2009-11-06
Dell Mini 10, 1.6ghz, 1gb RAM

In 9.04 I had a boot time of 24 seconds, now with 9.10 it is 1:11???  Any words of wisdom to make this lower.

---

### Post by apocalypse80 on 2009-11-06
Folks you might want to upload your bootcharts somewhere else and link to them.
It seems the forum automatically converts/resizes the attached huge png bootcharts to completely unreadable jpgs.

Back on topic : I didn't have time to fool around with optimizations on a clean karmic install, but I did create a new (empty) user and did some tests.

[http://img690.imageshack.us/img690/6407/cleanuseroptimized.png](http://img690.imageshack.us/img690/6407/cleanuseroptimized.png)

11s to desktop on an install with fglrx,virtualbox etc is about 2s faster than jaunty.
I'm guessing low 9s - high 8s might be possible with a clean karmic setup.

---

### Post by dash2 on 2009-11-06
Thanks apocalypse80, fair point. Here's a link.

[http://img405.imageshack.us/img405/9965/davelaptopkarmic2009110.png]("http://img405.imageshack.us/img405/9965/davelaptopkarmic2009110.png")

---

### Post by apocalypse80 on 2009-11-06
> **dash2 said:**
> Thanks apocalypse80, fair point. Here's a link.

[http://img405.imageshack.us/img405/9965/davelaptopkarmic2009110.png]("http://img405.imageshack.us/img405/9965/davelaptopkarmic2009110.png")

Wow, if I'm reading this right you don't have a fully loaded desktop even after 90s, gnome-panel starts loading at 84s.

- Your hdd looks way way too slow even for a notebook drive, is it a 4200rpm one?
- mount.ntfs takes 9 seconds? wtf?
- you spawn 3 xsplash instances, I'm pretty sure the normal count is 2. Are you using autologin?
- resume? is stalling the process between 4s-9s, maybe you have a wrong swap uuid in /etc/fstab?

I'd look at the hdd and it's controller first, make sure it's all working as it should (dma etc).
You may also want to disable xsplash and usplash, so you'll be able to see any errors/warnings as they happen.

Oh even before that, is this an upgrade or clean install?
If it's an upgrade - just spare yourself the headaches and do a clean install.

---

### Post by gjoellee on 2009-11-06
Due to compatibility issues with Ubuntu on my new laptop, I am not able to use Ubuntu too do my work. However...I get to the login screen in about 15 sec.

---

### Post by cjbackhouse on 2009-11-06
[http://www-pnp.physics.ox.ac.uk/~bckhouse/chimera-karmic-20091107-1.png]("http://www-pnp.physics.ox.ac.uk/%7Ebckhouse/chimera-karmic-20091107-1.png")

Seriously 1:52? It was about 2:30 before I disabled a couple of things and installed stuff out of the ubuntu-boot ppa (looks like most ureadahead).
The machine has been through several dist-upgrades, did something get totally screwed up?

---

### Post by andrewabc on 2009-11-06
> **scout4536 said:**
> Dell Mini 10, 1.6ghz, 1gb RAM

In 9.04 I had a boot time of 24 seconds, now with 9.10 it is 1:11???  Any words of wisdom to make this lower.

Subtract 45 seconds to compare to bootcharts before 9.10.
So Karmic is 2 seconds longer than before for you.

> **cjbackhouse said:**
> [http://www-pnp.physics.ox.ac.uk/~bckhouse/chimera-karmic-20091107-1.png](http://www-pnp.physics.ox.ac.uk/~bckhouse/chimera-karmic-20091107-1.png)

Seriously 1:52? It was about 2:30 before I disabled a couple of things and installed stuff out of the ubuntu-read ppa (looks like most ureadahead).
The machine has been through several dist-upgrades, did something get totally screwed up?

something definitely wrong with your bootchart. Between 8 and 25 seconds it is doing nothing with hard drive (disk throughput). Then 25 seconds to 50 seconds disk throughput is good, but there is no CPU.

It could be because of lots of dist upgrades.
If you have spare >=1gbUSB stick, put 9.10 on it via system->administration->usb startup disk creator. I'm not sure if you can install bootchart to it if you allow for 'store in extra reserved space'.
Boot and stopwatch time if there is large difference than stopwatch difference of your installed version. You'll have to correct for the 45 seconds extra bootchart automatically adds. I think your on fully loaded desktop at 80 seconds. So GRUB->desktop for installed looks to be 80 seconds. Boot liveusb from selecting first option to bootable desktop (also have to remember it has to detect all your devices which would add several seconds).

My 7 year old pentium 4 boots in 68 seconds. Your pentium dualcore boots in 112 seconds. Definitely something wrong. Probably fastest and best solution is to backup anything important and do format/fresh install.

---

### Post by dash2 on 2009-11-07
apocalypse80: thank you very much for these thoughts. My laptop is a Lenovo X60 so the disk shouldn't be that bad, and the Ubuntu disk diagnostics report nothing wrong. This is an upgrade, so I guess I could just do a clean install... if I can avoid formatting my drive.

---

### Post by bizexpert on 2009-11-07
The log tarball is later passed to the Java application for parsing and rendering the data.  The CPU and disk statistics are used to render stacked area and line charts.  The process information is used to create a Gantt chart showing process dependency, states and CPU usage.
  A typical boot sequence consists of several hundred processes. Since it is difficult to visualize such amount of data in a comprehensible way, tree pruning is utilized.  Idle background processes and short-lived processes are removed.  Similar processes running in parallel are also merged together.

---

### Post by medivh on 2009-11-07
I have a clean karmic install on my ACER 6935g laptop(T6400,4gb Memory,500GB 5400rpm HDD, Nvidia m9600gt)

My boot time is 1:05 even after disabling fsck on all drives and disabling some unused start-up apps.(without touching anythign it was 1:09 so not so much improvement)

[[IMG]http://img689.imageshack.us/img689/7890/medivhlaptopkarmic20091.th.png[/IMG]](http://img689.imageshack.us/i/medivhlaptopkarmic20091.png/)

Any suggestions for improvement? I had like 15 seconds boot on 9.04 with autologin, openbox, xfce4-panel, conky, feh, xcompizmgr(i cant remember exact name))

---

### Post by 5BallJuggler on 2009-11-07
I thought it was slow, but I don't really know what I'm looking at, any help would be greatly apreciated.

[http://s929.photobucket.com/albums/ad133/5BallJuggler/?action=view&current=phil-netbook-karmic-20091107-1.png]("http://s929.photobucket.com/albums/ad133/5BallJuggler/?action=view&current=phil-netbook-karmic-20091107-1.png")

---

### Post by markp1989 on 2009-11-07
here is mine:

specs:

e8400 oc to 4ghz
4gb ram
OCZ vertex ssd 

os arch, with very edited boot scripts

edit: when did UF start compresing the **** out of any uploaded pics so i cannot read them?

here is a readable version 
[IMG]http://i246.photobucket.com/albums/gg102/markp1989/bootchart-18.png[/IMG]

---

### Post by admelfo on 2009-11-07
Here you go -- would LOVE feedback on getting this to run better.

Compaq Armada M300 laptop, Hardy LTS
pIII, about 300 MG RAM, 60Gb HD

Thanks!

---

### Post by andrewabc on 2009-11-08
@medivh
Subtract 45 seconds to compare to 9.04. So your bootchart is 20 seconds compared to 9.04.
You do upgrade or fresh install?

@5BallJuggler
You're chart is unreadable.

---

### Post by old_salt on 2009-11-08
Here you go, now you know why I say GRUB 2 STINKS!!!

Yes, Your reading correctly..... 70 second bootup on a dual core 3.0 GHz box with 4Gb RAM using EXT4 partition.

---

### Post by medivh on 2009-11-08
> **andrewabc said:**
> @medivh
Subtract 45 seconds to compare to 9.04. So your bootchart is 20 seconds compared to 9.04.
You do upgrade or fresh install?

@5BallJuggler
You're chart is unreadable.

I did a fresh install. I have heard of this 45 second thing but it feels like difference is a lot more than 4-5 seconds when I compare. I will try to get the same system (openbox etc. and then repost)

By the way after enabling concurrency I have 59seconds.:p

---

### Post by andrewabc on 2009-11-08
> **old_salt said:**
> Here you go, now you know why I say GRUB 2 STINKS!!!

Yes, Your reading correctly..... 70 second bootup on a dual core 3.0 GHz box with 4Gb RAM using EXT4 partition.

Did you customize bootchart (to removed 45 second delay)? If not subtract 45 seconds to compare to previous versions.

How many times do I have to say this :(

Also, Uploading bootcharts to ubuntuforums does not work currently. So try at imageshack.us

---

### Post by gorade on 2009-11-09
Well, I think this is my last posting to this thread. 1'11'' - 45'' is 26''. In reality (by stopwatch) time from GRUB to Login is 42', an improvement from Jaunty with 5''. 
Honestly, what is the point of doing this? Boot-chart doesn't measure what it is meant to measure. Who has got a useful hint of how to really improve boot up time?
There ought to be some other way.
Bye for now ):P

---

### Post by hard_i on 2009-11-10
14 Sec

[http://www.upload.ee/image/257299/k-2-karmic-20091111-3.png](http://www.upload.ee/image/257299/k-2-karmic-20091111-3.png)

---

### Post by neutronj on 2009-11-11
4 sec

It takes longer for my BIOS to get through POST than it does for Koala to boot.

Specs:
AMD Phenom II X4 955 Black (3.2 Ghz)
4 GB DDR3 1333
Kingston SSD - SNM125 (80GB, using Intel controller)


[img]http://www.upload.ee/image/257758/achesong-lanbox-karmic-20091111-2.png[/img]

---

### Post by keypox on 2009-11-12
wow much slower than i thought ...

Install on WD Black... 

i had some issues on reboot, i think it normally boots faster will try again later

---

### Post by KayakJim on 2009-11-19
I am about to work on improving my boot time for 9.04 but thought I would post my current bootchart before improvements were made.

[IMG]http://www.bluefiredev.com/jim-p505-jaunty-20091119-1.png[/IMG]

---

### Post by zarf on 2009-11-21
well, at 3:21 i believe i win :)

I'll check out the link referred to earlier in the thread, but any ideas?

thx

---

### Post by The Real Dave on 2009-11-21
Mate, upload your bootchart somewhere else, its compressed here so we can't read it. Something is using **alot** of CPU for some reason, but no HDD....very strange

---

### Post by zarf on 2009-11-21
Yes, should have zipped it up.

give this a shot & thanks

---

### Post by hugmenot on 2009-11-29
Anyone know how I can find out why it is sleeping for 5 seconds doing nothing in the beginning?

[IMG]http://imgur.com/aULF6.png[/IMG]

---

### Post by hugmenot on 2009-11-29
I figured it out. 

It was stalling for 5 seconds on the resume partition (viz., swap) because there was an old UUID in /etc/initramfs-tools/conf.d/resume since I formatted my disk recently.

---

### Post by qalimas on 2009-11-29
Wow, my machines take a lot longer to boot than I had thought.

---

### Post by The Real Dave on 2009-11-29
> **zarf said:**
> Yes, should have zipped it up.

give this a shot & thanks

Hmmm usplash seems to be hogging your CPU. Edit your grub with 

> gksudo gedit /boot/grub/menu.lst

and remove the word splash. That will get rid of your graphical boot, but might help with the time

---

### Post by renkinjutsu on 2009-11-29
> **st33med said:**
> Pretty good.
Another thing you can do is press 'e' at the GRUB menu on your kernel. Go down to the line that begins with 'kernel', hit 'e' again, and add 'profile' at the end. Hit Enter and then 'b' to boot. It will now profile the boot up files for faster reading by making those files closer to the center of disk. It will take longer for that boot, but, on your next reboot, you could see an increase from 1-10 seconds. It improved mine by 3 seconds.

my boot charts are in my signature.

Wouldn't moving the files closer to the center of the disk make them  read slower? .. 

I'll see if appending profile will affect my boot time in the future

---

### Post by FunkeyMonk on 2009-11-29
Well, you can see my Toshiba Laptop takes nearly FOUR MINUTES to boot.  Anybody got any brilliant ideas to fix this?

[Toshiba BootChart Karmic]("http://charleslatshaw.com/testing/wp-content/uploads/2009/12/BSO-Laptop-karmic-20091201-11.png")

---

### Post by andrewabc on 2009-11-29
DO NOT UPLOAD BOOCHARTS TO FORUM.

The forum software renders them unreadable as it tries to shrink them.

---

### Post by zarf on 2009-11-30
> **The Real Dave said:**
> Hmmm usplash seems to be hogging your CPU. Edit your grub with 



and remove the word splash. That will get rid of your graphical boot, but might help with the time
yes, got rid of splash and am down to 1:08 from 3:21.
getting better!

---

### Post by cartisdm on 2009-12-30
Just out of curiosity, how long does it take your systems to boot up to the desktop? I just installed 9.10 and the boot time that everyone was raving about isn't really blowing anything of out of water for me, it's about 40 seconds from the GRUB. That's right about average for my Windows 7 partition and my past ubuntu experiences.

Are any of you getting blazing fast speeds (be sure to mention if your using a SSD or a HDD and if your counting the BIOS load time)

---

### Post by aktiwers on 2009-12-30
Did you do an upgrade?
When I upgraded my boot time actually got slower. After doing a clean install, it boots a lot faster.
About 10-12 sec.

I have a VelociRaptor WD1500HLFS which might help though :)
But I hardly ever reboot..

---

### Post by cartisdm on 2009-12-30
> **aktiwers said:**
> Did you do an upgrade?
When I upgraded my boot time actually got slower. After doing a clean install, it boots a lot faster.
About 10-12 sec.

I have a VelociRaptor WD1500HLFS which might help though :)
But I hardly ever reboot..

Fresh install.  For me, that's the only way to install an OS.  I hate doing upgrades because it never works quite right.

10-12 sec?! Must be nice....:):)

---

### Post by falconindy on 2009-12-30
20 seconds from GRUB to login. 3 year old 7200RPM 80gb Barracuda for a boot drive. Also, not Ubuntu.

---

### Post by cartisdm on 2009-12-30
Well I just downloaded/installed BUM and I got my boot time to 30 seconds flat from GRUB.  Not too shabby for an old HDD that is in desperate need of repair...

---

### Post by jbrown96 on 2009-12-30
~60 seconds, but I have a Thinkpad with a tiny 1.8" hard drive. I've found that the time to login is less than half the actual boot time. 

I have to say that I'm very disappointed with the boot times. I don't reboot a lot, but there's so many flipping kernel updates...

---

### Post by blueshiftoverwatch on 2009-12-30
46 seconds: from pressing the power button to login
23 seconds: from GRUB to login

My stats are in my signature (in case you have signatures turned off)

---

### Post by djsroknrol on 2009-12-31
Mine is less that 30 seconds from GRUB to login....I'm running 8.04 on an Intel 2.80MHz Duo Core and a 250GB Western Digital SATA HD.

---

### Post by witeshark17 on 2009-12-31
About 40 seconds on my laptop.

---

### Post by Hwæt on 2009-12-31
13 seconds from GRUB.

**HDD:** 1TB Seagate Barracuda
**SATA Cable:** 3GB/s
**Processor:** AMD Athlon X2
**OS Architecture:** 32 bit
**RAM:** 2 1GB sticks
**Graphics Card:** Nvidia GeForce 9500 GT
**PSU:** 650W Corsair

---

### Post by FunkeyMonk on 2009-12-31
> **cartisdm said:**
> Just out of curiosity, how long does it take your systems to boot up to the desktop?

Mine takes about 3-4 minutes to boot, WHEN/IF it boots successfully.  Anybody want to take a look and see if you can tell me why?

[Toshiba laptop bootchart with 9.10]("http://charleslatshaw.com/testing/wp-content/uploads/2009/12/BSO-Laptop-karmic-20091201-11.png")

---

### Post by markp1989 on 2010-01-01
here is mine 5 sec from grub to desktop :D

for specs see desktop in sig, 

os arch, with heavily modified boot scripts

one day i will give static /dev ago and see if i can save any more

just wana get rid of the 2 sec where it seems to do nothing at the start then i can be happy :D 

edt: made bootchart wait longer before stoping logging, so you can see when xmonad starts

---

### Post by andrewabc on 2010-01-02
> **FunkeyMonk said:**
> Mine takes about 3-4 minutes to boot, WHEN/IF it boots successfully.  Anybody want to take a look and see if you can tell me why?

[Toshiba laptop bootchart with 9.10]("http://charleslatshaw.com/testing/wp-content/uploads/2009/12/BSO-Laptop-karmic-20091201-11.png")

There is something seriously wrong with your bootchart at beginning. It most likely is searching or waiting for something to initialize.

What is it doing for first 1.5 minutes? What's on screen?

---

### Post by FunkeyMonk on 2010-01-02
> **andrewabc said:**
> There is something seriously wrong with your bootchart at beginning. It most likely is searching or waiting for something to initialize.

What is it doing for first 1.5 minutes? What's on screen?

Generally, it's just sitting.   I think the problem has something to do with Karmic accessing my USB ports.   I can't get the machine to boot at all unless there's something in one of the USB ports.   If I put a Flash drive in a port, it boots right up but the trackpad/keyboard stop working about 30 seconds after getting to the desktop.  If I plug in a keyboard and mouse too, then they'll work for about five minutes.   If I unplug/replug them, the whole system crashes. 

[I've posted a thread about this issue.]("http://ubuntuforums.org/showthread.php?t=1348714")

For what it's worth, 9.04 still boots and runs fine and dandy, with no such USB problems.  (Boot time is about 35 seconds on 9.04)

---

### Post by andrewabc on 2010-01-03
> **FunkeyMonk said:**
> Generally, it's just sitting.   I think the problem has something to do with Karmic accessing my USB ports.   I can't get the machine to boot at all unless there's something in one of the USB ports.   If I put a Flash drive in a port, it boots right up but the trackpad/keyboard stop working about 30 seconds after getting to the desktop.  If I plug in a keyboard and mouse too, then they'll work for about five minutes.   If I unplug/replug them, the whole system crashes. 

[I've posted a thread about this issue.]("http://ubuntuforums.org/showthread.php?t=1348714")

For what it's worth, 9.04 still boots and runs fine and dandy, with no such USB problems.  (Boot time is about 35 seconds on 9.04)

35 seconds is normal, add 45 seconds to it and you get your 9.10 boot since bootchart adds 45 seconds to bootchart starting with 9.10. I replied to your thread.

---

### Post by Paqman on 2010-01-23
Here's mine. I feel like it could be a lot faster. Indeed, the whole second half of the boot seems to be pretty low CPU and flatline on disk activity. Hmm.

---

### Post by Xbehave on 2010-01-23
> **Paqman said:**
> Here's mine. I feel like it could be a lot faster. Indeed, the whole second half of the boot seems to be pretty low CPU and flatline on disk activity. Hmm.
Attach an SVG the image is too low res to make out any details. readahead should help sort out disk activity, check that you have that installed.

---

### Post by Paqman on 2010-01-24
> **Xbehave said:**
> Attach an SVG the image is too low res to make out any details. readahead should help sort out disk activity, check that you have that installed.

Sorry about that, fixed now. Looks like it changed the png into a jpg when I attached it for some reason?!?

Definitely got readahead. It's installed by default anyway isn't it? Certainly not the kind of thing i'd unistall anyway.

---

### Post by Xbehave on 2010-01-24
> **Paqman said:**
> Sorry about that, fixed now. Looks like it changed the png into a jpg when I attached it for some reason?!?

Definitely got readahead. It's installed by default anyway isn't it? Certainly not the kind of thing i'd unistall anyway.
erm now you've attached a broken svg (well broken to me), basically attach the default output of bootchart (for some reason i thought it was .svg, it might be png or some other lossless format)

---

### Post by Psumi on 2010-01-24
Wheeeeeeeee..... 1 minute or so boot time :3

Sorry, can't upload to tinypic, too big! It'll still resize it to the point you can't see it >:3

I have no DE even, and no gvfs.

---

### Post by YeOK on 2010-01-24
Here's mine.

[ATTACH]144802[/ATTACH]

Edit, I'll add a link to the full size view.

[[img]http://xs.to/thumb-86AC_4B5C70E0.jpg[/img]](http://xs.to/image-86AC_4B5C70E0.jpg)

---

### Post by Paqman on 2010-01-24
> **Xbehave said:**
> erm now you've attached a broken svg (well broken to me), basically attach the default output of bootchart (for some reason i thought it was .svg, it might be png or some other lossless format)

Looks like the image is waaay too large for vBulletin to swallow, so here it is off Photobucket:

[http://i3.photobucket.com/albums/y69/seret/desktop-karmic-20100123-3-1.png]("http://i3.photobucket.com/albums/y69/seret/desktop-karmic-20100123-3-1.png")

---

### Post by Psumi on 2010-01-24
> **Paqman said:**
> Looks like the image is waaay too large for vBulletin to swallow, so here it is off Photobucket:

[IMG]http://i3.photobucket.com/albums/y69/seret/desktop-karmic-20100123-3.png[/IMG]

lol, can't see anything, it's just a thumbnail.

---

### Post by Paqman on 2010-01-24
> **Psumi said:**
> lol, can't see anything, it's just a thumbnail.

Yeah, didn't realise they resized on upload by default.

---

### Post by Xbehave on 2010-01-24
> **Psumi said:**
> Wheeeeeeeee..... 1 minute or so boot time :3

Sorry, can't upload to tinypic, too big! It'll still resize it to the point you can't see it >:3

I have no DE even, and no gvfs.
It clocks till xorg starts + then some, 1 minute is about the minimum it will log and gvfs doesn't slow down your boot.


**Paqman**: Try attaching a png in a zip, i can't see much info on there but you seam to have 11 seconds to gdm-session then a pause (do you have autologin?)
After login there is a slight pause for pulseaudio jamming things up for 1 second (you could look into fixing that but it will be faster to take my other advice)
After gnome is done setting itself up AWN sleeps for an extra 10seconds (something calls sleep ~15 then awn, you could drop the sleep to 5 seconds and then it would look like you were booting faster)

[LIST]
[*]Biggest speedup will be got from enabling autologin (or if you don't want that setup readahead (for the user account) & preload to do some useful work before you boot.
[*]After that there is the AWN problem
[*]You can gain a couple of seconds by adding noresume (or something like that) to your grub line (if you never hibernate, otherwise it's worth a ~2s pause is probably worth it)
[*]You might be able to get better disk usage, by reprofiling readahead (not sure how to do that google it?)
[*]Xorg seams to take a couple of seconds doing it's autoconfiguration, perhaps this can be won back by using a static xorg.conf
[*]Finally there is the pa bug/bad config.
[/LIST]

---

### Post by Paqman on 2010-01-25
> **Xbehave said:**
> 
**Paqman**: Try attaching a png in a zip, i can't see much info on there but you seam to have 11 seconds to gdm-session then a pause (do you have autologin?)
After login there is a slight pause for pulseaudio jamming things up for 1 second (you could look into fixing that but it will be faster to take my other advice)
After gnome is done setting itself up AWN sleeps for an extra 10seconds (something calls sleep ~15 then awn, you could drop the sleep to 5 seconds and then it would look like you were booting faster)

[LIST]
[*]Biggest speedup will be got from enabling autologin (or if you don't want that setup readahead (for the user account) & preload to do some useful work before you boot.
[*]After that there is the AWN problem
[*]You can gain a couple of seconds by adding noresume (or something like that) to your grub line (if you never hibernate, otherwise it's worth a ~2s pause is probably worth it)
[*]You might be able to get better disk usage, by reprofiling readahead (not sure how to do that google it?)
[*]Xorg seams to take a couple of seconds doing it's autoconfiguration, perhaps this can be won back by using a static xorg.conf
[*]Finally there is the pa bug/bad config.
[/LIST]

Cool, thanks for the advice, i'll sit down and work through it when i've got some time. I already use preload, but I haven't messed about with readahead. Looks like it might be worth reprofiling it, but I do wonder if it'll make such a big difference since i'm using an SSD. I thought the main point of readahead was to organise disk head seeking?

Looks like the sleep before AWN is due to [an old bug]("https://bugs.launchpad.net/ubuntu/+source/avant-window-navigator/+bug/451741"). Fixed in a new version, so it should just be a case of either upgrading or dropping the delay from the start script.

---

### Post by k64 on 2010-01-25
[http://ubuntuforums.org/showthread.php?p=8720777](http://ubuntuforums.org/showthread.php?p=8720777)

---

### Post by skymera on 2010-01-27
Restarted a few times and here's my bootchart:

16.48 seconds
[[IMG]http://img682.imageshack.us/img682/1007/scottdesktoplucid201001.th.jpg[/IMG]](http://img682.imageshack.us/i/scottdesktoplucid201001.jpg/)

Still a bit slow.

---

### Post by skymera on 2010-01-27
New chart:

14.70 seconds

[[IMG]http://img196.imageshack.us/img196/6747/scottdesktoplucid201001.th.png[/IMG]](http://img196.imageshack.us/i/scottdesktoplucid201001.png/)

---

### Post by Xbehave on 2010-01-27
> **skymera said:**
> New chart:
14.70 seconds

There seams to be a 1/2 second of not doing much when alsactl launches, but now your down to such a short boot up time, you might want to give it a try with noresume to see if that will cut of 3 seconds at the start (it may not, it may be a kernel thing holding up or it may just due to the way bootchart logs the data.

---

### Post by skymera on 2010-01-27
> **Xbehave said:**
> There seams to be a 1/2 second of not doing much when alsactl launches, but now your down to such a short boot up time, you might want to give it a try with noresume to see if that will cut of 3 seconds at the start (it may not, it may be a kernel thing holding up or it may just due to the way bootchart logs the data.

I'll have to try.
I believe noresume gets added into GRUB? How is this done on GRUB2? 

I need to read up on GRUB2 :(

---

### Post by sudoer541 on 2010-01-27
here is mine c/p


> BIOS= updated May 20th 2003
hard drive(s) name(s) and space:
Samsung 215F 60GB, Western Digital 546K 80GB
Samsung= main
Western Digital = slave
configuring USB devices.... FAILED!!! 
re-reconfiguring USB devices....pass
checking for extra hardware....
checking for extra hard drives.... found 3 
checking for OS....... found 3
checking for boot loader... found: 3
Boot loader(s) name and priority: 
GRUB 1.9 = main
GRUB 2.0 = unused
Windows boot loader (October 2004) = unused
booting:  ubuntu 9.04 
Linux kernel 2.6.12.32
auto login enabled= no
number of users = 5
number of startup programs = 36


is this what you are looking for?

 o-0
  v
 >=<

---

### Post by dlumpp on 2010-05-13
Can someone help me, please? 3 min boot is not cool. By the looks of this, it doesn't even do anything for 2 mins, what's wrong?

[http://img146.imageshack.us/img146/4969/dandesktoplucid20100513.png](http://img146.imageshack.us/img146/4969/dandesktoplucid20100513.png)

---

### Post by Phrea on 2010-05-13
I don't really know how to read it, but it seems to be a bit, well, long...

[http://i.imgur.com/YIQAy.png](http://i.imgur.com/YIQAy.png)

Attaching the file to this post didn't work all that well.

---

### Post by andrewabc on 2010-05-13
DO NOT ATTACH BOOT CHARTS TO FORUM. THEY DON'T SHOW UP.
UPLOAD ELSEWHERE.

/sorry for shouting but this happens all the time.

---

### Post by ubunterooster on 2010-05-13
Edit: Oops did not see previous post. How do I upload elsewhere? I have 6.48sec

---

### Post by cariboo on 2010-05-13
> **ubunterooster said:**
> Edit: Oops did not see previous post. How do I upload elsewhere? I have 6.48sec

Try [http://imgur.com/](http://imgur.com/). it works well for me.

---

### Post by ubunterooster on 2010-05-13
[http://imgur.com/TBadc.png](http://imgur.com/TBadc.png) this way?

Edit: it works. Thanks, Cariboo.

---

### Post by GarmaZed on 2010-05-14
Hot sauce on salami... I may be a noob but I'm pretty shocked at how fast my time is.  Windows 7 took roughly around twice as long to boot.

[http://img408.imageshack.us/img408/3756/lappytoppygzlucid201005.png](http://img408.imageshack.us/img408/3756/lappytoppygzlucid201005.png)

Soooooo gonna keep Ubuntu on this thing, frickin' awesome.

26.88 seconds, ~$350 lappy-toppy from over 3 years ago.
Making a note here: HUGE SUCCESS

---

### Post by andrewabc on 2010-05-14
> **GarmaZed said:**
> Hot sauce on salami... I may be a noob but I'm pretty shocked at how fast my time is.  Windows 7 took roughly around twice as long to boot.

[http://img408.imageshack.us/img408/3756/lappytoppygzlucid201005.png](http://img408.imageshack.us/img408/3756/lappytoppygzlucid201005.png)

Soooooo gonna keep Ubuntu on this thing, frickin' awesome.

26.88 seconds, ~$350 lappy-toppy from over 3 years ago.
Making a note here: HUGE SUCCESS

And that's probably with a slow 5400rpm hard drive.

Go to [System->Admin->Disk Utility->Benchmark results](http://ubuntuforums.org/showthread.php?t=1468995) and post your results. And then compare to SSD that some people have posted. If your HDD gets around 80mb/s, if you put SSD in your laptop in future it's possible you could cut boot time almost in 1/2. :)

EDIT:
Your boot chart shows a max of 22mb/s disk throughput with an average of probably 11mb/s.
With my SSD I get a max of around 115mb/s. On a 3.5 year old desktop.

---

### Post by Ellipsis on 2010-05-22
I'll get a bootchart up ASAP but for now all I have is:

[http://www.youtube.com/watch?v=S1FDDaTTxDQ](http://www.youtube.com/watch?v=S1FDDaTTxDQ)

---

### Post by k@e on 2010-05-22
[http://imgur.com/f7mUk.png](http://imgur.com/f7mUk.png)

This is pretty amazing considering on average karmic took **a whole minute** to boot. Yay for lucid!

---

### Post by andrewabc on 2010-05-22
> **k@e said:**
> [http://imgur.com/f7mUk.png](http://imgur.com/f7mUk.png)

This is pretty amazing considering on average karmic took **a whole minute** to boot. Yay for lucid!

If comparing bootcharts between karmic and Lucid, Karmic had +45 seconds added to it.

Unless you're saying that pressing power button to usable desktop in karmic was over 1 min and in lucid it is much less.

---

### Post by cetoka on 2010-05-23
This is my bootchart image.I am a Linux newbie,and Ubuntu is the only operating system on my desktop.Is there anything that I could do to achieve a better startup time? Thanks in advance.
[http://imgur.com/IIDI2.png](http://imgur.com/IIDI2.png)

---

### Post by MissouriNewb on 2010-05-27
This is insane. Never had these kind of boot times with Win7.

Don't misunderstand me 7 was a big improvement over Vista. But, I am an Ubuntu man now.

[http://imgur.com/FgAkm.png](http://imgur.com/FgAkm.png)

Respectfully Submitted,

MN

---

### Post by firesyde424 on 2010-06-09
Here's mine before optimizations:

[ATTACH]159899[/ATTACH]

Dell XPS M1530, 80 GB Intel G2 SSD, Ubunto 10.04 32 bit.

---

### Post by Jordanwb on 2010-06-13
8.6 seconds. Aww yeah. For some reason this was the only bootchart I was able to get. Bootchart kepts crashing when parsing the .tgz files manually.

[Unmodified bootchart]("http://img529.imageshack.us/img529/4959/jordancd3cda3blucid2010.png")

---

### Post by pinguy on 2010-07-27
Bootchart will not only provide you an exact time (in seconds) of how long it takes you to boot up but also provide you with a graphical representation of the processes that run during the boot process including CPU & HDD usage.

```
sudo apt-get install bootchart
```

Using bootchart requires no effort on your part at all -  just reboot! Boothart will do its&#8217; thing during boot and will place a .png file with all the accumulated stats in **/var/log/bootchart**.  

[URL="http://img252.imageshack.us/img252/1203/pinguydesktoplucid20100.png"]
My Boot time 00:17.15[/URL]

[[IMG]http://img252.imageshack.us/img252/1203/pinguydesktoplucid20100.th.png[/IMG]](http://img252.imageshack.us/img252/1203/pinguydesktoplucid20100.png)

**To Disable Bootchart**

Unless disabled Bootchart will run on every boot. For most of you out there this is likely excessive and unwarranted.  
```
sudo apt-get purge bootchart
```

---

### Post by SunnyRabbiera on 2010-07-27
About 20 seconds or so, not too shabby.

On linux mint isadora

---

### Post by mendhak on 2010-07-27
This can't be good... 1:01 :(

Edit: Thumbnails not working too well, here's a link instead:

[http://img148.imageshack.us/img148/9269/ashenvalelucid201007271.png](http://img148.imageshack.us/img148/9269/ashenvalelucid201007271.png)





[URL="http://img148.imageshack.us/i/ashenvalelucid201007271.png/"]


[/URL]

---

### Post by cariboo on 2010-07-27
Merged with bootchart thread.

---

### Post by pinguy on 2010-07-27
> **mendhak said:**
> This can't be good... 1:01 :(

Edit: Thumbnails not working too well, here's a link instead:

[http://img148.imageshack.us/img148/9269/ashenvalelucid201007271.png](http://img148.imageshack.us/img148/9269/ashenvalelucid201007271.png)





[URL="http://img148.imageshack.us/i/ashenvalelucid201007271.png/"]


[/URL]

Run this:
```
sudo rm /var/lib/ureadahead/pack
```

Reboot twice. First time to generate a new ureadahead. Then the second time you boot it, it should be a lot faster.

---

### Post by mendhak on 2010-07-27
:neutral: Are you a wizard?

That brought it down to about 30 seconds.  ([link]("http://img36.imageshack.us/img36/9269/ashenvalelucid201007271.png")).

I'm going to have to read up on [ureadahead]("http://ubuntuforums.org/showthread.php?t=1434502") a bit more to actually understand why the regeneration worked.  Thank you for that.

---

### Post by ~Aquatic on 2010-07-27
Time: 27.39 seconds

[[linky]]("http://dl.dropbox.com/u/6029947/FREAX-lucid-20100727-1.png")

By the way, why does it say 'release: Ubuntu 10.04.[COLOR=Red]1[/COLOR] LTS'?

---

### Post by CharlesA on 2010-08-09
Mine is absurdly slow. Slightly over a minute and a half to boot.

Running a Pentium Dual-Core E6500 @ 2.93GHz, 6GB of RAM and a 320GB HDD.

EDIT: After messing with ureadahead I got it down to under a minute.

[Link.]("http://img443.imageshack.us/img443/8242/thorlucid201008092.png")

---

### Post by quequotion on 2010-08-10
My boot is taking over a minute--pproximately 75 seconds. Activity is really sparse in the last fourty seconds or so.

I'd really like to shorten this if at all possible. In total, in takes my machine about a minute and a half to boot at the moment. It's own CMOS/BIOS/POST takes quite a while and there's nothing that can be done about it so if Ubuntu can boot faster, then I'd like to see it do so!

---

### Post by quequotion on 2010-08-10
> **quequotion said:**
> My boot is taking over a minute--pproximately 75 seconds. Activity is really sparse in the last fourty seconds or so.

I'd really like to shorten this if at all possible. In total, in takes my machine about a minute and a half to boot at the moment. It's own CMOS/BIOS/POST takes quite a while and there's nothing that can be done about it so if Ubuntu can boot faster, then I'd like to see it do so!

Solved some of my own problems.

1. removed packages **hal** and **hal-info**. No longer running hald each boot... maybe saved three or four seconds.

2. finally resolved a huge issue with gdm failing to start and ubuntu running in low graphics mode at nearly every boot. Including waiting for gdm to fail, clicking two buttons to get to terminal, terminal login, and typing a command to start gdm manually saved approximately forty seconds.

3. reprofiled for ureadahead

Now Ubuntu is booting in about 30 seconds, but I still think it's way too long.

My system is booting ubuntu from a set of 4 500GB, 3GB/s SATA drives in one 2TB fakeRAID:0 (dmraid). Theoretically the I/O speed of this drive should be excellent (~12GB/s), but in reality it benchmarks below 200MB/s. I know the theoretical limit is more or less impossible, but is there any way to speed this up?

---

### Post by andrewabc on 2010-08-10
uploading bootcharts to forum does not work. Upload elsewhere.

---

### Post by CharlesA on 2010-08-10
> **andrewabc said:**
> uploading bootcharts to forum does not work. Upload elsewhere.

It doesn't?

Each file is around 30KB.

---

### Post by andrewabc on 2010-08-10
> **CharlesA said:**
> It doesn't?

Each file is around 30KB.

Nope doesn't, it resizes the files and impossible to read them. They are too long height wise.

---

### Post by Thryn on 2010-08-11
[My bootchart, 26.58 seconds on Lubuntu 64-bit.]("http://img838.imageshack.us/img838/1861/hypatialucid201008101.png")

So how's it look? I know it's about twice as fast as on Windows 7, and I think it's around the same about of time as with GNOME, but I'll check in a minute.

Second bootchart, booted into Lubuntu again by mistake. For some reason this one has a thumbnail. And it was faster.
[[IMG]http://img37.imageshack.us/img37/7929/hypatialucid201008102.th.png[/IMG]](http://img37.imageshack.us/i/hypatialucid201008102.png/)

Ubuntu 64-bit, 19.2 seconds:
[[IMG]http://img534.imageshack.us/img534/3038/hypatialucid201008103.th.png[/IMG]](http://img534.imageshack.us/i/hypatialucid201008103.png/)

I've been restarting, if that makes a difference.

---

### Post by CharlesA on 2010-08-11
> **andrewabc said:**
> Nope doesn't, it resizes the files and impossible to read them. They are too long height wise.

Ah ok. Didn't notice that. Thanks.

I've editing my post to have a link. :)

---

### Post by andrewabc on 2010-08-12
> **~Aquatic said:**
> Time: 27.39 seconds

[[linky]]("http://dl.dropbox.com/u/6029947/FREAX-lucid-20100727-1.png")

By the way, why does it say 'release: Ubuntu 10.04.[COLOR=Red]1[/COLOR] LTS'?

[https://wiki.ubuntu.com/MaverickReleaseSchedule](https://wiki.ubuntu.com/MaverickReleaseSchedule)

10.04.1 is a snapshot release that includes all fixes (updates) that were released since 10.04 release back in April. Saves people from downloading/installing 10.04 and then having to download install 200+mb of updates.

They do this with LTS versions. There will be a 10.04.2 and probably 10.04.3
People who have 10.04 installed do not need to download 10.04.x releases, just do regular update manager updates and you have it.

Your bootchart has max disk throughput of 25mb/s (probably average of 8mb/s). That is extremely low. Your CPU isn't maxing out, so it is waiting for disk input/output.

I'm guessing old laptop/desktop? If capable of SATA, in near future SSD prices will drop a lot and you can increase the 25mb/s to 120mb/s (SATAI, mostly in laptops/netbooks) or 250mb/s (SATAII, desktops). Currently price points are $120 for 60gb SSD. Newest generation SSD (Sandforce) are ~$180 for 60gb. But if on laptop limited to SATAI, then previous generation (Indilinx and, jmicron from 2010) would be more than enough due to 120mb/s SATA limitation.

Some computer specs would be nice. :)

@CharlesA
Looks like your bootchart is done loading OS around 12 second mark. If you time from GRUB to time you see desktop, it should be a lot less than the 57 seconds bootchart is reporting. Did you upgrade from previous release? If you did it might have kept the bootchart+45second timeout calculation from 9.10 release.

For all you laptop owners attached is SSD limited to SATAI. If using 10.04, you can test your own by going to system->admin->disk utility->benchmark->read only test.

---

### Post by odinfromvalhalla on 2010-08-12
here is my bootchart, before putting up the SSD. hopefully this weekend i have time to reinstall on SSD and we'll see then.

---

### Post by andrewabc on 2010-08-12
> **odinfromvalhalla said:**
> here is my bootchart, before putting up the SSD. hopefully this weekend i have time to reinstall on SSD and we'll see then.

Upload image elsewhere. Forum cant handle large images properly.

Also when you post update with SSD, also put up system->admin->disk utility->benchmark->read only test, and SSD brand/model.
Also upload it to [this](http://ubuntuforums.org/showthread.php?t=1468995) thread.

---

### Post by CharlesA on 2010-08-12
> **andrewabc said:**
> 
@CharlesA
Looks like your bootchart is done loading OS around 12 second mark. If you time from GRUB to time you see desktop, it should be a lot less than the 57 seconds bootchart is reporting. Did you upgrade from previous release? If you did it might have kept the bootchart+45second timeout calculation from 9.10 release.

Well it's actually on my server with no GUI installed, so that might be throwing it off. 

It's a clean install of Lucid x64, but I've got a bunch of services installed and running off it: samba, ssh, exim, etc. I'm guessing those load up after the main OS starts.

Also: Thanks for the info about 10.04.x, that'll mean I won't have to do a reinstall as long as I keep everything up to date.

Learn something new everyday. :)

---

### Post by ~Aquatic on 2010-08-12
> **andrewabc said:**
> [https://wiki.ubuntu.com/MaverickReleaseSchedule](https://wiki.ubuntu.com/MaverickReleaseSchedule)

10.04.1 is a snapshot release that includes all fixes (updates) that were released since 10.04 release back in April. Saves people from downloading/installing 10.04 and then having to download install 200+mb of updates.

They do this with LTS versions. There will be a 10.04.2 and probably 10.04.3
People who have 10.04 installed do not need to download 10.04.x releases, just do regular update manager updates and you have it. 
[SIZE=1]*[COLOR=Red]Nice to know, thanks! :D Noticed that here you can see the exact date of lucid's all snaphot releases. :)[/COLOR]*[/SIZE]

Your bootchart has max disk throughput of 25mb/s (probably average of 8mb/s). That is extremely low. Your CPU isn't maxing out, so it is waiting for disk input/output.

I'm guessing old laptop/desktop? If capable of SATA, in near future SSD prices will drop a lot and you can increase the 25mb/s to 120mb/s (SATAI, mostly in laptops/netbooks) or 250mb/s (SATAII, desktops). Currently price points are $120 for 60gb SSD. Newest generation SSD (Sandforce) are ~$180 for 60gb. But if on laptop limited to SATAI, then previous generation (Indilinx and, jmicron from 2010) would be more than enough due to 120mb/s SATA limitation.

Some computer specs would be nice. :)
[I][SIZE=1][COLOR=Red]It's a HP 550 laptop

Specs:
Processor: Intel® Celeron® M Processor 530
Chipset: Mobile Intel® GME965 (or GME960) Express
Memory: 1 GB 667 MHz DDR2 SDRAM
Harddrive: 160-GB 5400 rpm SMART SATA
Display: 15.4-inch diagonal WXGA Brightview
Graphics: Mobile Intel® GMA X3100[/COLOR][/SIZE][SIZE=1]
[COLOR=Red]
Have I missed something?
EDIT: More detailed: [[Linky]]("http://dl.dropbox.com/u/6029947/mySpecs.html")
[/COLOR][/SIZE][/I] 
For all you laptop owners attached is SSD limited to SATAI. If using 10.04, you can test your own by going to system->admin->disk utility->benchmark->read only test.
*[SIZE=1][COLOR=Red]I tried but it failed unfortunately. :confused: _[[Pic]]("http://dl.dropbox.com/u/6029947/benchmark_error.png")_[/COLOR][/SIZE]*

Everything marked in red :)

---

### Post by andrewabc on 2010-08-12
> **~Aquatic said:**
> Everything marked in red :)

Decent laptop specs. Similar vid card as my desktop. I have g965, GMA X3000.

I'm pretty sure you have SATAI.

I had nettop (SATAI) with 160gb 5400 RPM, which I replaced with SSD.
Attached is pic of the 160gb, vs 60gb SSD.
This is the performance difference you should see with old HDD vs SSD.

Not sure why it is not working for you. [Possibly failing disk?](http://www.webhostingtalk.com/showthread.php?t=968761) Or could be bug in software. Actually, in your screenshot I see that it says there are a few bad sectors. That could be the reason. Now it's an older laptop, with old disk, so these things could be normal. Backup any important info/data before doing anything, and keep regular backups in case of failure. :)
If mostly OS+APP laptop, then SSD in future would be ok idea if HDD fails (make sure you can replace HDD before buying anything!). By end of year $100 for decent 60gb.

---

### Post by ~Aquatic on 2010-08-13
> **andrewabc said:**
> Decent laptop specs. Similar vid card as my desktop. I have g965, GMA X3000.

I'm pretty sure you have SATAI.

I had nettop (SATAI) with 160gb 5400 RPM, which I replaced with SSD.
Attached is pic of the 160gb, vs 60gb SSD.
This is the performance difference you should see with old HDD vs SSD.

Not sure why it is not working for you. [Possibly failing disk?]("http://www.webhostingtalk.com/showthread.php?t=968761") Or could be bug in software. Actually, in your screenshot I see that it says there are a few bad sectors. That could be the reason. Now it's an older laptop, with old disk, so these things could be normal. Backup any important info/data before doing anything, and keep regular backups in case of failure. :)
If mostly OS+APP laptop, then SSD in future would be ok idea if HDD fails (make sure you can replace HDD before buying anything!). By end of year $100 for decent 60gb.

Right now, I am not sure if I'll buy anything. I don't really think it's worth it to upgrade this laptop. And the prices for SSD hard drives seems really high at the moment. Hopefully they will drop soon, as you say. 

But thanks for all the tips and info. ;) Really appreciate it.

---

### Post by Primus1 on 2010-08-13
Here is my bootchart, sorry if this is in the wrong place.

---

### Post by Noz3001 on 2010-08-13
22 seconds, not bad. I'll try to make it even faster.

[http://img835.imageshack.us/img835/1064/gladoslucid201008133.png](http://img835.imageshack.us/img835/1064/gladoslucid201008133.png)

---

### Post by kamaaina on 2010-09-04
Something is getting causing a delay but I can't tell what.  Any ideas?

---

### Post by Austin25 on 2010-09-04
Here's mine.

---

### Post by cariboo on 2010-09-04
All of you posting your bootcharts as attachments, please use an image hosting service, as the forum resizes the image to the point that they are unreadable.

---

### Post by Primus1 on 2010-09-05
put mine on photobucket, hope this is ok.

[http://i576.photobucket.com/albums/ss201/cugel_2009/Yorkshire%20museum/ub/dave-desktop-lucid-20100905-1.png]("http://i576.photobucket.com/albums/ss201/cugel_2009/Yorkshire%20museum/ub/dave-desktop-lucid-20100905-1.png")

sorry I don't think this is working, don't know why it's so small.

---

### Post by toupeiro on 2010-09-05
12 seconds after 60+ updates from update manager including a new kernel patch.  On a fresh system with this processor and SSD, it was a little over 4, but once I have all my software loaded (databases, both MySQL and postgresql, pcscd and others) it adds a bit.

don't have a place to post the png at the moment.

---

### Post by Jesus_Valdez on 2010-09-12
So, any tips?

[http://i.imgur.com/b8TvK.png](http://i.imgur.com/b8TvK.png)

My bootchart.

---

### Post by Primus1 on 2010-09-13
Here is my bootchart, any help appreciated. Please tell me if this is in the right form I've been having trouble uploading the chart with it being too small but this looks like the right size now.
Thanks.

[http://imgur.com/Basfa.png](http://imgur.com/Basfa.png)

any advice, the above png is legible ..

---

### Post by andrewabc on 2010-09-14
> **Jesus_Valdez said:**
> So, any tips?

[http://i.imgur.com/b8TvK.png](http://i.imgur.com/b8TvK.png)

My bootchart.
That is a really long bootime. Your disk utilization is always maxed out, and your max speed is 66mb/s, but usually running around 10mb/s or less.

Are you running an old 5400 RPM hard drive?

I'm just confused as to why a core i5 has such a slow HDD paired with it. Laptop?

Run:
System->Admin->Disk Utility->Benchmark results->read benchmark to see speed of HDD.

Feel free to also put benchmark in
[System->Admin->Disk Utility->Benchmark results](http://ubuntuforums.org/showthread.php?t=1468995) thread and you can see results of others to see what speeds you should be getting or can get with different hardware.

---

### Post by steve77 on 2010-10-10
Here's mine.
34 secs...any idea?

[http://imgur.com/NUNtC.png](http://imgur.com/NUNtC.png)

Thanks

---

### Post by M4570D0N on 2010-10-10
I'm hoping someone might be able to provide some insight here. 1st, is  there a thread here or some good resources elsewhere on how to decrease  boot times? My boot time seems to be getting worse lately. I did a fresh  install to the 10.10 RC  and the boot time was a little bit slower than  it was Mint 9 gnome, but it was ok I suppose. I started out arond 24-25  sec, but now I am consistently averaging over 30 seconds, and the time  from when I type in my login password, to when it shows my desktop is  also noticeably longer as well. When I was on Mint 9, I was averaging  15-18 sec. boot times. 

Oct. 8th (32.77 sec.):
[http://i596.photobucket.com/albums/t...20101008-2.png]("http://i596.photobucket.com/albums/tt45/SH00TTH3H0STAG3/aaron-HP-Pavilion-dv5-Notebook-PC-maverick-20101008-2.png")

Sept. 30th (25.45 sec.):
[http://i596.photobucket.com/albums/t...20100930-2.png]("http://i596.photobucket.com/albums/tt45/SH00TTH3H0STAG3/aaron-HP-Pavilion-dv5-Notebook-PC-maverick-20100930-2.png")

Sept 5th on Mint 9 gnome (15.45 sec.):
[http://i596.photobucket.com/albums/t...20100905-1.png]("http://i596.photobucket.com/albums/tt45/SH00TTH3H0STAG3/aaron-laptop-isadora-20100905-1.png")

I upgraded today to the final 10.10 release from the rc, but I'm still getting boot times of around 32sec. Obviously, it is possible for my boot time on this laptop to be faster, but I'm not sure what the issue(s) is(are). Any help figuring out what's causing the  extended boot time would be much appreciated.

---

### Post by markp1989 on 2010-10-12
Boot chart from 10.10, boots fast, but could be alot faster as for the first 7 sec of the boot chart, its not doing anything. 


[img]http://i246.photobucket.com/albums/gg102/markp1989/mark-desktop-maverick-20101012-1.png[/img]

---

### Post by andy22286 on 2010-10-13
[http://img88.imageshack.us/img88/4152/thedoombringermaverick2.png](http://img88.imageshack.us/img88/4152/thedoombringermaverick2.png)

It looks like ureadahead operates for some time without anything else happenning.  Is this normal?  This is a laptop, but the Disk Utility Benchmark gave min 46 MB/s, max 113 MS/s, avg 84 MB/s.  Any ideas?

Andy

---

### Post by alan2796 on 2010-10-17
Heres Mine, Can anything be done to speed it up ?

[http://i246.photobucket.com/albums/gg102/markp1989/mark-desktop-maverick-20101012-1.png](http://i246.photobucket.com/albums/gg102/markp1989/mark-desktop-maverick-20101012-1.png)

---

### Post by NightwishFan on 2010-10-18
I had a strange boot experience just now. Booting into maverick after testing with bootchart the first boot took around 1:04. I thought that was a bit long however quite easily bearable. I did a reboot to confirm and my boot was at 24 seconds (quite good for a 5400rpm disk). So hey I guess ureadahead is doing it's job well.

Here is the boot chart:
[http://ubuntuone.com/p/KxQ/](http://ubuntuone.com/p/KxQ/)


> **alan2796 said:**
> Heres Mine, Can anything be done to speed it up ?

[http://i246.photobucket.com/albums/gg102/markp1989/mark-desktop-maverick-20101012-1.png](http://i246.photobucket.com/albums/gg102/markp1989/mark-desktop-maverick-20101012-1.png)

Nice!

---

### Post by Viciou§ on 2010-11-26
This is mine:
[http://imgur.com/2PzfV.png]("http://imgur.com/2PzfV.png")

Running on C2D E6300 1.86GHz, 7200rpm SATA drive, 1GB RAM, nVidia GT210

Any idea on what to debug why it takes so long between 12-22s?
Something to do with some hardware is my guess but don't really know where to start and what to look for =/

Any pointers appreciated.

---

### Post by lithopsian on 2011-01-07
A little late, but maybe you'll get this :)

What is modprobe flailing at?  Take that six seconds out and I'm sure you'd be happy, so work at that first.  I notice alsa-utils kicks on right when it stops flailing.  Coincidence?  One non-trivial thing that will help is to compile a kernel with all the modules that you would load on every boot built in.  Not for everyone!

Also ureadahead doesn't seem to be doing anything useful.  Perhaps you could try reprofiling and see if it picks up any files that do you some good.  Tricky to know when it should stop.  You obviously want to read ahead enough to get you to a working desktop, but not too far or you'll actually be slowing the boot down by caching stuff that starts in the background later.

---

### Post by Spr0k3t on 2011-01-07
Thought someone might like this one...  I haven't even trimmed the fat yet.

---

### Post by psusi on 2011-01-07
> **Spr0k3t said:**
> Thought someone might like this one...  I haven't even trimmed the fat yet.

The forum shrinks attached thumbnails into unreadability; you need to post them elsewhere.

---

### Post by psusi on 2011-01-07
> **Viciou§ said:**
> This is mine:
[http://imgur.com/2PzfV.png]("http://imgur.com/2PzfV.png")

Running on C2D E6300 1.86GHz, 7200rpm SATA drive, 1GB RAM, nVidia GT210

Any idea on what to debug why it takes so long between 12-22s?
Something to do with some hardware is my guess but don't really know where to start and what to look for =/

Any pointers appreciated.

You seem to have removed ureadahead.

---

### Post by Spr0k3t on 2011-01-07
> **psusi said:**
> The forum shrinks attached thumbnails into unreadability; you need to post them elsewhere.

Just noticed that... so I've updated the post with a zoom of the critical information on top.  Enjoy.

---

### Post by Viciou§ on 2011-01-08
> **lithopsian said:**
> A little late, but maybe you'll get this :)

What is modprobe flailing at?  Take that six seconds out and I'm sure you'd be happy, so work at that first.  I notice alsa-utils kicks on right when it stops flailing.  Coincidence?  One non-trivial thing that will help is to compile a kernel with all the modules that you would load on every boot built in.  Not for everyone!

Also ureadahead doesn't seem to be doing anything useful.  Perhaps you could try reprofiling and see if it picks up any files that do you some good.  Tricky to know when it should stop.  You obviously want to read ahead enough to get you to a working desktop, but not too far or you'll actually be slowing the boot down by caching stuff that starts in the background later.

I have tried reprofiling but didn't really help. And now bootchart has stopped working.
Will try a maverick install and see how that works out. I believe that a part of the problem is alsa and hdmi sound (have compiled alsa 1.0.23 since  I need it for hdmi passthrough)

---

### Post by zer010 on 2011-01-08
I never knew about bootchart. Quite interesting. Anyways, here's mine. 
[http://i1178.photobucket.com/albums/x370/dividebyezer0/20110108-1.png](http://i1178.photobucket.com/albums/x370/dividebyezer0/20110108-1.png)
Somehow, I don't think I have the most efficient boot up, but it works I guess.

---

### Post by idovecer on 2011-08-21
Huh, beat that.
Anyway, thank you for any suggestions on how speed up my Ubuntu?

78 seconds it is too much, 3GB DDR2 RAM, 500GB Hitachi HD, Athlon XP 3GHz.

Its kinda too much know.


Thank you for any tip.

Link to Bootchart photo:
[http://open-dir.com/idovecer-desktop-natty-20110821-1.png](http://open-dir.com/idovecer-desktop-natty-20110821-1.png)

---

### Post by Lucradia on 2011-08-22
Mine's too big to attach. ;)

[http://i.imgur.com/NQhCj.jpg](http://i.imgur.com/NQhCj.jpg)

Can't get any lower, this is after applying a ton of windows hacks and tweaks (Removing Windows search, stopping a ton of services, and disabling a ton.)

---

### Post by markp1989 on 2011-08-22
Here is mine:

[http://dl.dropbox.com/u/4137122/marks-desktop-natty-20110822-2.png](http://dl.dropbox.com/u/4137122/marks-desktop-natty-20110822-2.png)

Specs are in sig, root drive is an OCZ revo drive, very past pcie ssd, but modprobe is slowing down my boot :(

on this boot chart i am using the server kernel as I was hoping it may fix the modprobe hang, but it made no difference.

---

### Post by pqwoerituytrueiwoq on 2011-08-24
[[IMG]http://i.imgur.com/QQhU3s.jpg[/IMG]]("http://i.imgur.com/QQhU3.png")
this is my rig
current hardware:
[AMD Phenom II x4 965]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103727")
[Nvidia GeForce GT 430 1GB]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814162067")
[ASUS M4A79XTD EVO]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131402")
[WD  WD5000AAKX]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136769")
[KINGSTON SS100S216G]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136769")
[G.Skill Ripjaw DDR3 1600  12GB]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231358") (purchased in a pack of 2 and a pack of 1)
[LITE-ON DVD Burner]("http://www.newegg.com/Product/Product.aspx?Item=N82E16827106289")
[74 in 1 Rosewill Card Reader]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820223109")
[Sata 3.5" Hot Swap Rack]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817993031")
MadDog 500W Modular (MD-500SCPS) was given to me free
Case was given to me free

---

### Post by andrewabc on 2011-08-24
> **pqwoerituytrueiwoq said:**
> [[IMG]http://i.imgur.com/QQhU3s.jpg[/IMG]]("http://i.imgur.com/QQhU3.png")
this is my rig
current hardware:

[WD  WD5000AAKX]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136769")


Impressive that the HDD was able to reach high of 204mb/s and looks like sustained speed of ~150mb/s

---

### Post by pqwoerituytrueiwoq on 2011-08-24
> **andrewabc said:**
> Impressive that the HDD was able to reach high of 204mb/s and looks like sustained speed of ~150mb/s
you missed the low end SSD ([KINGSTON SS100S216G]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136769"))
/var, /home, swap are on the WD drive
and /tmp is on the ram
edit:
just pulled a 248MB/s during boot

---

