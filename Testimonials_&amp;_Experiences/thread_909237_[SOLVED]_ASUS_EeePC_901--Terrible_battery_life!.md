---
title: "[SOLVED] ASUS EeePC 901--Terrible battery life!"
date: 2008-09-03
forum: Testimonials &amp; Experiences
---

### Post by bornagainpenguin on 2008-09-03
I have an ASUS EeePC 901, and like the thread header says, the battery life is terrible!

I have full hardware support using Adamm's kernel and am running Hardy Heron 8.04.1 with all updates and everything 'just works' for me on it.  I love Ubuntu but I got the EeePC for for its mobility and battery life.  I'm not getting that under Ubuntu....

How in the world is it possible that Windows XP manages to hit 8-9hrs consistently on this thing but Ubuntu is able to do only half of that?

--bornagainpenguin

---

### Post by ukripper on 2008-09-03
> **bornagainpenguin said:**
> 
How in the world is it possible that Windows XP manages to hit 8-9hrs consistently on this thing but Ubuntu is able to do only half of that?

--bornagainpenguin

how much battery life you get on ubuntu?

---

### Post by tuxxy on 2008-09-03
It is still known that microsoft OS's outperform linux at power management regarding laptops.

---

### Post by bornagainpenguin on 2008-09-03
> **ukripper said:**
> how much battery life you get on ubuntu?

4hrs and 25 mins


> **tuxxy said:**
> It is still known that microsoft OS's outperform linux at power management regarding laptops.

Well then what are they doing that Ubuntu (Linux) is not?  Given the state of their latest OS, it shouldn't be too hard to overtake them on it...

Or are you saying I should just up and go to WinXP for a year or two until things evolve some more on the Linux side of things?

--bornagainpenguin

---

### Post by linuxgeocacher on 2008-09-04
Here are my measured data with an EEEPC 901 with a fully charged battery running **Ubuntu 8.04 with the Array.org Custom Linux Kernel** and with **medium display brightness**:

**WLAN activated**

Battery Charge Monitor 2.22.2
5:03
Power Manager 2.22.1
4:05
watch -n 1 acpi -V
5:00

**WLAN deactivated**

Battery Charge Monitor 2.22.2
6:09
Power Manager 2.22.1
4:05
watch -n 1 acpi -V
6:05

There are **huge differencies** between the "Battery Charge Monitor" and the "Power Manager", which uses the following "discharge time accuracy profile" (see attachment)

---

### Post by ukripper on 2008-09-04
> **bornagainpenguin said:**
> I have an ASUS EeePC 901, and like the thread header says, the battery life is terrible!

I have full hardware support using Adamm's kernel and am running Hardy Heron 8.04.1 with all updates and everything 'just works' for me on it.  I love Ubuntu but I got the EeePC for for its mobility and battery life.  I'm not getting that under Ubuntu....

How in the world is it possible that Windows XP manages to hit 8-9hrs consistently on this thing but Ubuntu is able to do only half of that?

--bornagainpenguin

try sidux with kde-lite.

---

### Post by bornagainpenguin on 2008-09-04
> **linuxgeocacher said:**
> There are **huge differencies** between the "Battery Charge Monitor" and the "Power Manager", which uses the following "discharge time accuracy profile" (see attachment)

This is interesting....  I did think it was discharging a little slower than the monitor was claiming, but I just figured it was wishful thinking on my part.  So...six hours actuality instead of four and a half?  Not great but not necessarily as horrible as I'd feared.

> **ukripper said:**
> try sidux with kde-lite.

Well doing a search for sidux brings me to a wiki with this huge warning splashed over the top of nearly every page...

[quote=sidux]WARNING: Today [2008-08-28] new kernel version 2.6.26 has hit Lenny what causes some problems on the Eee PC. See DebianEeePC/Bugs/2.6.26. The developer team is working on the issue. You are better off holding off your installation and software updates until the issue is solved.[/quote]

Also, why KDE?  I'm much more of a Gnome fan than I am fior KDE--part of the reason I left the original Xandros in fact! Gnome just seems to work within my work flow better.

Are you saying there are documented reasons why KDE gives better power management?  If so, link please!

--bornagainpenguin

---

### Post by Martje_001 on 2008-09-04
You sould look into [wattOS]("http://www.planetwatt.com/") :).

---

### Post by bornagainpenguin on 2008-09-04
> **Martje_001 said:**
> You sould look into [wattOS]("http://www.planetwatt.com/") :).

Looks like it might be good eventually but despite the site's proclamations wattOS does not appear to be running Gnome!  At least if I go by what the developer says in [this thread](http://forum.eeeuser.com/viewtopic.php?id=35181).  (Scroll down to post three where he posts as "biffster" and says that the current betas are running OPENBOX!!)

Thanks for the suggestion though, and I'll keep wattOS in mind in case it does eventually start running Gnome.

--bornagainpenguin

---

### Post by Martje_001 on 2008-09-04
**wattOS - The core desktop system using a fully featured Gnome desktop**

Openbox is just an window manager, not an desktop environment!

---

### Post by bornagainpenguin on 2008-09-04
> **Martje_001 said:**
> Openbox is just an window manager, not an desktop environment!

Ahh.. my mistake.  Well if you read the thread the other EeePC owners who used it commented it felt like Kubuntu to them not Gnome.  Since I was unable to load any of the screenshots heralded on their website I'll have to take the word of those who've used it...

--bornagainpenguin

---

### Post by Comhra on 2008-09-04
> **bornagainpenguin said:**
> 4hrs and 25 mins

--bornagainpenguin

Hey, that's not bad, I'm running the default OS (Xandros) on my ASUS and I get about an hour less than you.

---

### Post by Comhra on 2008-09-04
And, no, I'm not going back to MS ...ever.

---

### Post by bornagainpenguin on 2008-09-05
> **Comhra said:**
> Hey, that's not bad, I'm running the default OS (Xandros) on my ASUS and I get about an hour less than you.

Well no kidding!  The Xandros that ASUS bundled with the EeePC is broken not to mention has never really been updated for the hardware...  Look at the DVD that comes with your EeePC 901--the image is still named 701!!!  Obviously they've never bothered to update the OS to ensure it functions as well as it could.  More or less Xandros tossed together something that looked pretty and ASUS decided that was good enough...

At least Canonical has been working with Dell on their Mini Inspiron, so hopefully we'll see some real Linux support for the Atom processor and from that hopefully we will be able to expect some serious power management improvements.  Honestly I wonder if perhaps I made a mistake by not waiting for the mini Inspiron...

> **Comhra said:**
> And, no, I'm not going back to MS ...ever.

Heh...I understand that POV completely, but pragmatism compells me to do what will give me the 'best bang for my buck' so to speak and the addition of four more hours of battery life is a compelling argument in favor of Windows XP.

Of course, then I'll miss all my favorite apps, like Straw feed reader, Rhythmbox music player, Frozen Bubbles, Plus the usual assortment of cross platform stuff that IMHO just works better in Linux...  And of course the Gnome Desktop itself!  I've tried theming Windows and using shell replacements like LiteStep to try to get that experience on Windows and it just isn't possible!

...Still, the battery life is a *really* ***really*** compelling argument in favor of Windows XP right now...

--bornagainpenguin

---

### Post by undy on 2008-09-10
Remember that the Linux 901s have a much bigger SSD than the Windows 901s, so you'd anticipate some kind of power hit for that.

I've seen some claims that SSDs use more power than equivalent notebook HDDs, contrary to most people's expectations, so you might be able to replace the big SSD with a 1.8" HDD and get extra legs... but then it wouldn't be quite as drop-proof.

Andy

---

### Post by michaelkahl on 2008-09-10
I have an old compaq that I tried Four Operating systems on, here's what I got.
XP - 4 hours
Opensuse 11 - 4.5 hours
Linux Mint 5.0 - 4.5 hours 
Ubuntu - 3 at best
I'm not sure how this applies to the 901, but isn't there software you can run that helps reduce poweruseage?  My guess is that Mint and Suse come with this pre-configured while Ubuntu doesn't.

---

### Post by stalkingwolf on 2008-09-11
what version are you running?  Have you tried the Ubuntueee version?

When I got my 701 I put the regular 8.01 on it while I was down loading
the EEE version.  I like the EEE version so much more I put it on my desktop.

---

### Post by 3rdalbum on 2008-09-11
I'd suggest installing Powertop and having a look at how Ubuntu can become more energy efficient on your computer.

XP has lower system requirements than Ubuntu, of course, so XP doesn't use as much power. If you want a proper comparison, you should try Vista SP 1 versus Ubuntu Hardy, as they are of the same vintage.

---

### Post by undy on 2008-09-11
> **3rdalbum said:**
> I'd suggest installing Powertop and having a look at how Ubuntu can become more energy efficient on your computer.

XP has lower system requirements than Ubuntu, of course, so XP doesn't use as much power. If you want a proper comparison, you should try Vista SP 1 versus Ubuntu Hardy, as they are of the same vintage.

Once I came off AC, PowerTop suggested that I stop running Gnome Power Manager as old versions of it wake up the CPU too frequently...

Anyway Powertop reckons well over 5 hours, that's with wireless connected and Gnome Power Manager off. (Power Manager was reporting 4 hrs 25).

Without wireless it will be better.

Andy

---

### Post by bornagainpenguin on 2008-09-15
> **undy said:**
> Remember that the Linux 901s have a much bigger SSD than the Windows 901s, so you'd anticipate some kind of power hit for that.

That's irrelevant. /me twirls imaginary Grouncho Marx cigar

It's the same model Eee.  In Windows XP I get over eight hours; in Ubuntu I'm barely cracking 4hrs40mins and that's after turning all kinds of stuff off and ddoing various power tweaks here and elsewhere.  But it's the same 20g Linux version EeePC 901.

> **undy said:**
> I've seen some claims that SSDs use more power than equivalent notebook HDDs, contrary to most people's expectations, so you might be able to replace the big SSD with a 1.8" HDD and get extra legs... but then it wouldn't be quite as drop-proof.

Andy

Now this, might have some merit--only as stated above I **do** get over eight hours in Windows, on the same hardware.  So at this point regardless of whether the SSD is helping or hurting, I'm getting that battery life in Windows XP and not in Ubuntu.

> **stalkingwolf said:**
> what version are you running?  Have you tried the Ubuntueee version

I'm using stock Ubuntu with Adamm's kernel (the latest and greatest in his Hardy proposed branch which has been working quite well for me and seems to have added at leeast ten minutes to my battery life) and the scripts to add back the OSD notifications.

I don't want to use Ubuntueee until they've managed to fix all their bugs and they've made it pretty clear they intend to release their next version regardless of whether the 901 is completely fixed and supported.  Uggh..no thanks...

> **3rdalbum said:**
> I'd suggest installing Powertop and having a look at how Ubuntu can become more energy efficient on your computer.

I have, its one of the tweaks I'm following trying to eek out better power support from.

> **3rdalbum said:**
> XP has lower system requirements than Ubuntu, of course, so XP doesn't use as much power. If you want a proper comparison, you should try Vista SP 1 versus Ubuntu Hardy, as they are of the same vintage.

Surely you MUST be joking!  I wouldn't try to run Vista on a dead badger!  If Vista were a dog I'd sell the computer for a gun and shoot it.  Vista does not get anywhere near any of my hardware.

Still...taking your post at face value, should I hunt down a early version of Ubuntu--Warty say and expect better power management from it?  Even assuming I could get the hardware to work with a kernel specifically compiled for Warty I don't think I'd be seeing the kind of power savings you seem to be envisioning.

> **undy said:**
> Once I came off AC, PowerTop suggested that I stop running Gnome Power Manager as old versions of it wake up the CPU too frequently...

Hmmm.. how would I go about doing THAT??  I expect I'd swiftly discover myself in dependency hell if I tried...

Oh and before anyone mentions it *again* KDE is **not** an option.  If I have to suffer through KDE then I'd might as well run Windows XP.  Not trying to be a zealot here, but until GNOME started doing things the way the are now I generally lasted two weeks in Linux on average, these days I can use GNOME full time only occasionally venturing back to Windows for specific software programs that don't exist in Linux, work well in Wine, or I dislike the Linux alternatives for.

That's begun to happen more and more infrequently though, as I've either found alternatives for all my apps these days or adapted otherwise.

--bornagainpenguin

PS: Thanks to everyone who replied with advice!

---

### Post by ukripper on 2008-09-15
Not sure if this may be helpful for you - [http://www.lesswatts.org/tips/wireless.php](http://www.lesswatts.org/tips/wireless.php)

---

### Post by ba5e on 2008-09-17
> Originally Posted by 3rdalbum
XP has lower system requirements than Ubuntu, of course, so XP doesn't use as much power. If you want a proper comparison, you should try Vista SP 1 versus Ubuntu Hardy, as they are of the same vintage.


> Originally Posted by bornagainpenguin
Surely you MUST be joking! I wouldn't try to run Vista on a dead badger! If Vista were a dog I'd sell the computer for a gun and shoot it. Vista does not get anywhere near any of my hardware.

Brilliant that sentence by bornagain made my day!

---

### Post by ulukapata on 2008-09-17
try this...

[http://sikh.myminicity.com/tra/](http://sikh.myminicity.com/tra/)

---

### Post by bornagainpenguin on 2008-10-02
I just switched back to Ubuntu (what's the point in having all the battery life in the world if you don't use it because you hate the OS and the programs?)  I did a standard install using UNetbootin and updating to adamm's kernel.  The two major things I did differently this time after that is I immediately compressed my /usr directory into a squashfs and I installed marx's eeecontrol instead of using elmurato's scripts.  The difference though is amazing...

[[img]http://img90.imageshack.us/img90/8457/screenshotfk6.png[/img]](http://imageshack.us)
[[img]http://img90.imageshack.us/img90/screenshotfk6.png/1/w1024.png[/img]](http://g.imageshack.us/img90/screenshotfk6.png/1/)

As you can see this is on a full battery, so I still need to test things to make sure that this isnt some kind of error or something, but look at that battery life....

[[img]http://img144.imageshack.us/img144/420/screenshot1vk2.png[/img]](http://imageshack.us)
[[img]http://img144.imageshack.us/img144/screenshot1vk2.png/1/w1024.png[/img]](http://g.imageshack.us/img144/screenshot1vk2.png/1/)

Granted it isn't as much as I was getting in Windows XP (and I seem to be getting less on this model than I did on the one I had to return) but at this point the difference is so negligible I just don't see any point in suffering through Windows for the sake of a little more battery life....

[[img]http://img144.imageshack.us/img144/5854/proofhy6.jpg[/img]](http://imageshack.us)
[[img]http://img144.imageshack.us/img144/proofhy6.jpg/1/w1024.png[/img]](http://g.imageshack.us/img144/proofhy6.jpg/1/)

--bornagainpenguin

**UPDATE:** I discovered I get comparable battery life to Windows XP (if not better) when I use the Eee Control applet to turn off the WiFi AND the card reader!  Then I saw nine hours in the battery life.  I just got done using it for over five hours this morning and using it for about three hours last night so I'm saying this is a good sign...

PS: Text copied from my Eeeuser.com post [here](http://forum.eeeuser.com/viewtopic.php?pid=396198).

---

### Post by azanutta on 2008-10-03
sorry, can you post the link of that eee-control package bu marx.... i can't find it... =(

---

### Post by olho on 2008-10-03
I could do with the download link for eeecontrol too. I can only uncover very dubious torrent links to pay-sites. Plus each torrent is differently sized and enormous  - between 300Mb and 1 gig. That can't be right.

---

### Post by TheMono on 2008-10-04
> **bornagainpenguin said:**
> Oh and before anyone mentions it *again* KDE is **not** an option.  If I have to suffer through KDE then I'd might as well run Windows XP.  Not trying to be a zealot here, but until GNOME started doing things the way the are now I generally lasted two weeks in Linux on average, these days I can use GNOME full time only occasionally venturing back to Windows for specific software programs that don't exist in Linux, work well in Wine, or I dislike the Linux alternatives for.


I'm gonna mention it.... Have you tried KDE4, or just KDE3?

---

### Post by bornagainpenguin on 2008-10-07
> **azanutta said:**
> sorry, can you post the link of that eee-control package bu marx.... i can't find it... =(

> **olho said:**
> I could do with the download link for eeecontrol too. I can only uncover very dubious torrent links to pay-sites. Plus each torrent is differently sized and enormous  - between 300Mb and 1 gig. That can't be right.

Marx's eee-control can be found in his thread in the  Eeeuser.com forums [here](http://forum.eeeuser.com/viewtopic.php?id=43975).  His real name is Grigori Goronzy and he has a [site](http://greg.geekmind.org/eee-control/) with a deb file to install.

The deb is much much easier to use than the old 'source' package (the gzip file) which required a lot of manual work and the deb does most of that stuff for you.  I'd recommend grabbing it any way for the documentation...the files are small so I don't see it a hardship to grab both.  Really this utility makes a huge difference!

Another thing you might want to look into is Ubuntu-Tweak, a package found [here](http://ubuntu-tweak.com/).  In the System section, under powermanagement there is are a bunch of options to add some better powermanagement options.

> **TheMono said:**
> I'm gonna mention it.... Have you tried KDE4, or just KDE3?

I've tried all three versions of KDE--including KDE 1.xx and all I can say is "YECH!"  I have yet to try KDE 4.xx but based on previous versions and reports I've heard it still isn't quite ready yet...

To be honest, I also hated GNOME 1.x back in the day as well, it looked nice but would constantly bite me on the rear whenever I wasn't looking.  I'd fix one issue and another would crop up.  These days things are looking much much better.  I love Gnome 2.xx and based on what I saw when I tried the most recent beta of Intrepid its only getting better! :)

--bornagainpenguin

---

### Post by spectrevk on 2008-10-09
So, how did those power tests go? Do you really get 7.5 hours of battery life out of it?

---

### Post by th00ht on 2010-08-12
> **bornagainpenguin said:**
> 

How in the world is it possible that Windows XP manages to hit 8-9hrs consistently on this thing but Ubuntu is able to do only half of that?

--bornagainpenguin

No problems with 8-9 hrs under Ubuntu. With eeebuntu it is quite easy to switch off the services you don't need and has additional power saving options. Please read the forums for excellent battery saving tips.

---

### Post by Iowan on 2010-08-13
Thread is approaching 2 years old - AND marked [SOLVED].

---

