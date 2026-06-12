---
title: "Who here runs ubuntu on a laptop?"
date: 2009-08-09
forum: The Cafe
---

### Post by Sashin on 2009-08-09
And if you do what's the maximum battery life you can get, I'm getting the feeling that Ubuntu can't tell if there's more than 4 hours and 20 minutes of battery.

---

### Post by tom66 on 2009-08-09
I get 2.5 hours battery life.

---

### Post by SKLP on 2009-08-09
I've seen estimates as high as 8+ hours on this netbook) ( in Ubuntu)

---

### Post by JillSwift on 2009-08-09
2.0 hours. Battery's old, about a year ago it got 3.0.

---

### Post by koleoptero on 2009-08-09
An hour and something. 5 year old battery, I'm surprised it can go for that long.

---

### Post by chriskin on 2009-08-09
2 hours and a half with compiz turned off , 1 hour with compiz on

---

### Post by Sashin on 2009-08-09
@SKLP how'd you get it 8+?

My laptop is supposed to have that but it doesn't work in ubuntu.

---

### Post by toejamfootball on 2009-08-09
About 20 minutes, the battery is broken though.

---

### Post by aninaiian on 2009-08-09
Hmm, with my laptop I can get almost 4 hours with wifi off and a little less than 3 and a half with it on.

My netbook gets about 2 hours and 45 min with the 3 cell and around 7 hours and 45 min with the 9 cell battery.  In both cases, wifi is off.  It's quite a bit lower with it on.

---

### Post by dragos240 on 2009-08-09
4 Year old battery 20 mins.

---

### Post by slakkie on 2009-08-09
Depends on what I'm running. Super agressive power safe options are enabled when running on battery.

---

### Post by OldGnome on 2009-08-09
Nearly new Acer Aspire laptop. I got it from my mother when she trashed the hard drive - she slammed her hands down on the unit.

---

### Post by Nevon on 2009-08-09
Slightly less than 2 hours. I'm dual booting though, and in Windows, I can get 2½-3 hours. :(

---

### Post by mamamia88 on 2009-08-09
> **chriskin said:**
> 2 hours and a half with compiz turned off , 1 hour with compiz on

good to know next time i take my laptop off ac power i'll turn off compiz.  right now i get an estimate of 1 hr 55 minutes

---

### Post by lswb on 2009-08-09
2 laptops with ubuntu installed.

Old P3 650Mhz system with a good battery goes about 2 hours. No compiz.

Less old Pentium M 1.4Ghz system but has a bad battery only lasts an hour, compiz enabled. I'll have to try it sometime with metacity instead.

---

### Post by gn2 on 2009-08-09
My Asus F9E lasts about 2hr 45min on battery.

---

### Post by MasterNetra on 2009-08-09
I'd probably be lucky to get more then 30min on my labtop here...not ubuntu's fault though, the battery is over a year old and is dying.

---

### Post by raronson on 2009-08-09
Yes, on a macbook4,1.  I've completely removed OS X if it's any indication as to how good I think Ubuntu is.

---

### Post by thunk77 on 2009-08-09
3 hours on a Sony Vaio..

---

### Post by chriskin on 2009-08-09
> **mamamia88 said:**
> good to know next time i take my laptop off ac power i'll turn off compiz.  right now i get an estimate of 1 hr 55 minutes

it might be just my problem , cause i have TOO many effects on

---

### Post by cmay on 2009-08-09
i get 2 or two an a half hour on mine.

---

### Post by JohnFH on 2009-08-09
I get just less than 4 hours with wifi on and compiz on.  Haven't tested with them off, but I don't think it would make a big difference.

For all you laptop lovers, do this.  In a terminal window, type 
```

watch cat /proc/acpi/battery/BAT0/state

```

Watch how the battery discharge rate changes as you do various things like turn off compiz, remove a memory card, turn off wifi, turn screen brightness down, etc.  As a rough guide I found that wifi makes about a 10-15% difference, no SD memory card inserted makes about 5% difference, but compiz doesn't make any difference although I don't use desktop cube or anything like that, just transparency, etc.

---

### Post by chriskin on 2009-08-09
> **JohnFH said:**
> I get just less than 4 hours with wifi on and compiz on.  Haven't tested with them off, but I don't think it would make a big difference.

For all you laptop lovers, do this.  In a terminal window, type 
```

watch cat /proc/acpi/battery/BAT0/state

```

Watch how the battery discharge rate changes as you do various things like turn off compiz, remove a memory card, turn off wifi, turn screen brightness down, etc.  As a rough guide I found that wifi makes about a 10-15% difference, no SD memory card inserted makes about 5% difference, but compiz doesn't make any difference although I don't use desktop cube or anything like that, just transparency, etc.


that's why i said that it might be my problem, try using all effects at the same time and your battery will go skydiving :)

---

### Post by drooze on 2009-08-09
my battery is pretty much dead. charged 100% it runs out in about 5minutes. Windows recognises this, and correctly tells me my pc is about to switch off.

Ubuntu doesn't, however. it tells me I still have half an hour left, and then without warning it'll just go blank.

---

### Post by J A Smith on 2009-08-09
Yes, on an Acer 5720z.

Fully charged it tells me I have 70 mins. Which if I remember correctly is marginally better then on Vista.

---

### Post by Firestem4 on 2009-08-09
I have a Dell XPS m1210 with the extended cell battery. I get about  4 1/2 in KDE on non-power saving mode (but not doing anything resource intesnsive. The screen backlight does that enoughf or me.)

---

### Post by kevdog on 2009-08-09
Im not sure how old the battery is, however if the unit isnt plugged in -- it wont boot!  Kind of sucks when someone trips over the power cord and pulls it out of the wall.

---

### Post by mr.propre on 2009-08-09
I only use it on my laptop :lolflag:
Battery keeps it up for 30min - 1h but thats because the battery is almost totally dead.

---

### Post by DeadSuperHero on 2009-08-09
I get about 3 1/2 hours on a full charge. If I'm running something lightweight, maybe more.

---

### Post by gjoellee on 2009-08-09
My 6year old laptop was always in the charger when my parents used it, so because of that my battery life is about 5min. In Arch I managed to make it 10min, and in both XP and 7 it lasted for 1min.

---

### Post by tgalati4 on 2009-08-09
For you thinkpad owners:

acpitool -B

tgalati4@tpad-Gloria7 ~ $ acpitool -B
  Battery #1     : present
    Remaining capacity : 16910 mWh, 35.34%, 00:51:03
    Design capacity    : 51830 mWh
    Last full capacity : 47850 mWh, 92.32% of design capacity
    Capacity loss      : 7.679%
    Present rate       : 19869 mW
    Charging state     : discharging
    Battery type       : rechargeable, LION
    Model number       : IBM-92P1091
    Serial number      :    89

I get about 2 hours with an older battery on a thinkpad t43p

---

### Post by ibutho on 2009-08-09
I am using Linux Mint 7 (based on Jaunty) and I get about 2.5 hours battery life on an HP G7000.

---

### Post by MaxIBoy on 2009-08-09
Up until recently my answer would have been no. (I normally use Debian on my laptop.) However I recently used debootstrap to create an Ubuntu installation on a 4-gig disk image in my home directory, intended as a failsafe bootable environment, so I wouldn't need a liveCD if I messed something up.

---

### Post by Revolutionary101 on 2009-08-09
I get about 1 hour and 30 minutes on battery life (thats only because I compiled the linux kernel to favor performance instead of battery life.)

---

### Post by steveneddy on 2009-08-09
> **tom66 said:**
> I get 2.5 hours battery life.


Same here with Hardy - just installed Intrepid. Will post any increased time with 8.10 over Hardy when available.

---

### Post by BrokenKingpin on 2009-08-09
My laptop battery sucks so I only get about two hours, but it reports accurately.

---

### Post by Jesus_Valdez on 2009-08-09
So, am I the only person who gets less battery life on Ubuntu compare to windows?

On windows I got like 2+ hours, on Ubuntu 1.5, more or less.

Is this a problem? I mean, Can I have more battery life turning down compiz or something?

---

### Post by Compucore on 2009-08-09
ABout 20 minutes but I have to get a new battery over here to get better life. The old one is no good anymore.

---

### Post by epidemiks on 2009-08-09
about 1.5hrs with all bells and whistles

---

### Post by Katalog on 2009-08-09
I have Ubuntu running on two netbooks at the moment (an Asus Eee PC 1000HA and a 901). I haven't run Ubuntu on a desktop in over a year and get along just fine, even using resource intensive apps on my little Atom processors, like GIMP and Inkscape.

---

### Post by rifak on 2009-08-09
when playing music, videos, and surfing the web, i get about 1.5-2 hrs...maybe a bit less. it's going on a 2 year old battery, so it has a little bit health loss

---

### Post by Katalog on 2009-08-10
Since we're talking about battery life as well, my wife has been able to squeeze close to 6 hours out of her 901 on occassion, on my 1000HA I typically get around 4 1/2, sometimes 5 if I have the camera, wifi and cardreader turned off. Battery life - if nothing else, it's the one thing you gotta love about netbooks. :P

---

### Post by King_Critter on 2009-08-10
5 1/2 on an eeepc 1000HE. I love netbooks. ^_^

---

### Post by markbuntu on 2009-08-11
I supposedly get 7-8 hours on my Aspire One with a 9 cell battery according to the battery monitor but I have not really pushed it so can't say absolutely but it seems a lot more than that, more like 10-12. I can take it with me for a weekend without the power cord and not worry too much about how much I use it. 

The best thing is it will suspend forever. I just left it in my pack for 10 days on suspend and the battery is still at 47%. That is after taking it on a weekend trip where I used it for 5 or 6 hours. Boot time has become completely irrelevant.

I had a lot of laptops and battery life always made my life miserable. I hated them but this little machine.....netbooks forever...

I use kuki linux on this machine. It is a jaunty remix specifically for aspire ones. It is very very good for me.

---

### Post by Katalog on 2009-08-11
> **markbuntu said:**
> I had a lot of laptops and battery life always made my life miserable. I hated them but this little machine.....netbooks forever...

That's what made me ditch the HP Mini. The battery life was pathetic, and the solution they came out with for a 6 cell was a hideous joke. Real pity, too because the form factor was very nice and the keyboard was the best I've had on a netbook so far. I'm still struggling with the keyboard on my Eee PC 1000HA and I've had it for nearly a month now. I wonder if they make a 9 cell for the 900/1000 series Eee PC? That would be close to nivana! Gonna have to take a look around Newegg.......

---

### Post by djheadley on 2009-08-12
I have a Dell Lattitude C860 and the battery needs to be replaced so I only get about 2 1/2 hours without wifi and a little more than 1 hour with wifi.

---

### Post by stumbleUpon on 2009-08-12
Mine is an age old machine -- DELL Latitude C600. I get a maximum battery life of an hour and a half which is great considering the machine was bought in 2001 :)

---

### Post by Tclarkie on 2009-08-12
umm. i have this old thinkpad with like no battery and it says i have like an hour left lol

---

### Post by madhavhmk on 2009-08-12
2 hours here...with dell inspiron 1525 abt a year old

---

### Post by geekygirl on 2009-08-12
short answer....yes

---

### Post by Nburnes on 2009-08-12
I get about 2 hours out of my year old notebook.

---

### Post by lisati on 2009-08-12
I normally run my laptop on the mains.

---

### Post by sideaway on 2009-08-13
3 y/o battery, about 50 minutes watching a movie. Just over 90min with wifi off and bightness down and compiz disabled.

---

### Post by mikcarroll on 2009-08-13
I've got a dual boot hp and an Alienware,the battery lasts 3hrs for hp  Ubuntu 3.5 Vista, Compiz enabled. Alienware 1hour Compiz off.

---

### Post by Swagman on 2009-08-13
Asus A4 book 17" lappie

Battery... about 3 seconds

Click

1

2

3

click .. Dead battery.

Daughter says she gets about 3 hours out of her Eeepc 702 with UNR

---

### Post by khelben1979 on 2009-08-17
No, I never use Ubuntu.

---

### Post by pookiebear on 2009-08-17
9 year old dell laptop. Running xubuntu
1 hour on battery with cisco wireless card running. Have not run it without wifi so can't answer that part. No 3d stuff. just internet mostly use it as a netbook.

---

### Post by matthewbpt on 2009-08-17
I get 6.5 to 7 hours with wifi off, bluetooth off, card reader and webcm disabled, and lots of services disabled. With wifi on i can get 5ish hours. I have an ASUS EeePC 901 netbook, love it! =D

---

### Post by JillSwift on 2009-08-17
> **khelben1979 said:**
> No, I never use Ubuntu.
AKA the "Nobuntu Distro". ;)

---

### Post by jerrrys on 2009-08-17
hp6000; ubuntu 804; <1 hour on battery and no power management

---

### Post by MikeTheC on 2009-08-17
Well *I* don't...

---

### Post by TheNessus on 2009-08-17
2:30 hours, 6 Cell battery... that's because Ubuntu doesn't allow me to minimize brightness or CPU speed. I tried to fix this but to no avail. So on Vista I can get 3:30 hours, and note that Vista eats more resources...

---

### Post by Tamalin on 2009-08-17
2 hr battery life, but longer battery life can be attained when bluetooth and WiFi are turned OFF.

---

### Post by D-RAY on 2009-08-17
I get about 3 hrs

---

### Post by Jackelope on 2009-08-17
About 2 hours with normal use, but i blame the gpu for the poor numbers. 

by the way, this poll is pretty slanted because the majority of people who click on this thread do so because they're running Ubuntu on a laptop....that's why I clicked.

---

### Post by Technoviking on 2009-08-17
I have on my and my wife's laptop, and my son netbook. We all love it.

T-V

---

### Post by #11u-max on 2009-08-17
about an hour, ten minutes running full blast, wifi, bluetooth, GPU running hard, folding @ home running, and all of teh other stuff.

---

### Post by Mistrblank on 2009-08-17
Just from reading some of the replies here, I can't understand the people that complain they only get 2-3 hours on their netbooks.  I have an HP Mini with Ubuntu, gives me about 2 and a half to three depending on what I'm doing and that's with the crummy 3-cell battery.

---

### Post by RiceMonster on 2009-08-17
I have Fedora on my laptop. With monitor brightness turned down I get 4 hours. With it up to a comfortable level I get 2 hours.

---

### Post by Katalog on 2009-08-19
> **Mistrblank said:**
> Just from reading some of the replies here, I can't understand the people that complain they only get 2-3 hours on their netbooks.  I have an HP Mini with Ubuntu, gives me about 2 and a half to three depending on what I'm doing and that's with the crummy 3-cell battery.

Perhaps it's because that is pretty poor battery life for a netbook, considering you can get netbooks in a similar price range as the Mini (as well as some other models) that will easily get 5-7 hours battery life these days. Companies still selling netbooks with an sad little 0.3MP webcam and 3 cell battery as standard at this point in time is almost inexcusable, IMO, considering that it seems to me the whole point of a netbook is extreme portability and therefore not having to be close enough to a power source to recharge it every 2-3 hours. But, again, that's just my opinion.

---

