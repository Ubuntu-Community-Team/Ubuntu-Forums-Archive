---
title: "Ubuntu 9.10 constructive criticism"
date: 2009-12-01
forum: Testimonials &amp; Experiences
---

### Post by namekuseijin on 2009-12-01
I hope to be brief.

I've been a happy Ubuntu user for the last 4 years or so.  Before that, I learned Linux in and out the hard way:  learning and fighting over a command-line to get things done, seasoned on Debian and RedHat before.  Getting automatic USB mounts and hardware recognized with no fuss was a joy to behold.

Last 3 iterations of Ubuntu were from automatic upgrades.  No issues at all.

Then, with a new machine, I decided on the AMD64 Ubuntu version and installed over, reusing only my previous ext3 home partition.

Now, here's a few quirks which I feel can detract from the experience:

1) ADSL connection.

Network Manager simply doesn't work for it at all.  I add username and password, turn on the ADSL modem and nothing happens besides eth0 automatically reconnecting everytime I select the adsl connection.

Plus:  there's a parameter there called "Service", between username and password.  What is that supposed to mean?  "ADSL" (lowercase)?  My ISP name?  Whatever I put there, no good.  It's not a combo box with predefined options, just a cryptic parameter with no clue about it's goal.  Then I search for some Help button in the dialogue.  No, nothing.  Then I go to Ubuntu Help and I get this amazing wisdom pearl:

"DSL

   1. Right click on NetworkManager icon and click Edit conections...
   2. Click DSL.
   3. Click Add."

and that's it, ladies and gentleman.  It was profound, really.

Worse!  Much worse for some n00b, I guess.  Back when I started with Ubuntu, there was real information there in the Help:  it taught you how to connect using pppoeconf.  It was thanks to this *prior knowledge* that I was able to connect to the internet.  pppoeconf, sadly, is not mentioned at all to new users this time around.  I can feel the ADSL guys pain and going back to Windows.

2) How in hell can I get back the sound volume applet?!  I removed it by accident from the system tray and I can't get it back! 

There's no sound volume control applet in the "Add to Panel" menu.  I also can't get gnome-volume-control-applet to start from the command-line even if I manually kill the damn process.

And, yes, I know sound volume is in System -> Preferences -> Session Apps, but I couldn't get it back by quitting the current session and logging in again.  oh well, hope a reboot will do the trick like in the good ol' Windows days...


So, I'm obviously not deriding Ubuntu at all, which has been my system of choice for a few years now.  Just offering some insight on subtle points that could be improved for the general public, Linux for human beings.

Is ADSL not that used out there?  here in Brazil, it's very common...

---

### Post by julianb on 2009-12-01
DSL/ADSL are common here in the United States, as far as I know. Though many here are on cable internet connections instead.

---

### Post by lisati on 2009-12-01
I'm not sure if anyone else has experienced this, but for me, I haven't needed to fill in Network Manager's settings for ADSL connection. Mine seems to work quite happily using the user name/password stored in the router.

---

### Post by ticopelp on 2009-12-01
If you really want to be constructive I recommend filing bug reports, if you haven't already. The developers don't really read this forum. Hope you get your issues worked out.

---

### Post by namekuseijin on 2009-12-01
> **lisati said:**
> I'm not sure if anyone else has experienced this, but for me, I haven't needed to fill in Network Manager's settings for ADSL connection. Mine seems to work quite happily using the user name/password stored in the router.

I don't have a router, but that's beside the point.  The point is that the DSL tab has those exact parameters plus a cryptic one, and yet it doesn't work.  How about just dropping it rather than confusing the user?

---

### Post by namekuseijin on 2009-12-01
> **ticopelp said:**
> If you really want to be constructive I recommend filing bug reports, if you haven't already. The developers don't really read this forum. Hope you get your issues worked out.

I don't think those are bugs, just sloppy design.  And yeah, I have them worked out as an experienced user.  Not so sure about new users...

Perhaps I should also mention that I've been experiencing some annoying random page-scrolling stuttering with Firefox I've not had before with 32-bit 9.04?  That's more like a bug...

---

### Post by cariboo on 2009-12-01
It is a bug, you can file it by pressing Alt-F2 and typing:

```
ubuntu-bug network-manager-gnome
```

and add comments when your are taken to the launchpad bug report page. If the developers don't know there is a problem, they can't fix it.

---

### Post by lisati on 2009-12-01
> **namekuseijin said:**
> I don't have a router, but that's beside the point.  The point is that the DSL tab has those exact parameters plus a cryptic one, and yet it doesn't work.  How about just dropping it rather than confusing the user?

My bad, I meant "modem".

---

### Post by lisati on 2009-12-01
> **namekuseijin said:**
> I don't have a router, but that's beside the point.  The point is that the DSL tab has those exact parameters plus a cryptic one, and yet it doesn't work.  How about just dropping it rather than confusing the user?

My bad, I meant "modem", not "router" (the one of the boxes I use is a combination of the two functions)

---

### Post by meho_r on 2009-12-01
1. As already said, Network Manager that ships with Ubuntu 9.10 has a bug regarding DSL connection. You have two options a) to use **pppoeconf** command (with sudo, of course) instead or b) to install Network Manager from [this PPA](https://launchpad.net/~network-manager/+archive/trunk).

As for "Service" part in NM, just ignore it.

2. Try adding **gnome-volume-control-applet** to System > Preferences > Startup Applications.

---

### Post by namekuseijin on 2009-12-01
> **meho_r said:**
> 1. As already said, Network Manager that ships with Ubuntu 9.10 has a bug regarding DSL connection. You have two options a) to use **pppoeconf** command (with sudo, of course) instead or b) to install Network Manager from [this PPA]("https://launchpad.net/%7Enetwork-manager/+archive/trunk").


I know that.  My concern is that pppoeconf is not mentioned anywhere and a new Ubuntu user will not know about it at all.

> 2. Try adding **gnome-volume-control-applet** to System > Preferences > Startup Applications.

I'm on portuguese locale, but I guess Startup Apps is exactly what I meant by translating "Session apps".

Guys, thanks for the tips, but this was not a plea for help, really.  Any questions are just rhetoric.

Well, I actually have no clue how to add login/password info *into* the modem like some user mentioned.  Now that would be some help...

---

### Post by meho_r on 2009-12-01
I guess he meant that you have two ways of connecting using ADSL (at least in my country): 

1. Doing manual connection (on/off), a.k.a bridged mode. This is the way you described: you put your username and password in Network Manager and start and stop connection by mouse click.

2. Permanent connection, a.k.a routed mode. This way you enter your router/modem settings (through the browser, enter something like 192.168.1.1. and an admin window will appear) and enter your username and password in there, and not Network Manager. You may need to check infos regarding these settings at your ISP. When in routed mode, you are constantly connected to Internet. Actually, the minute you plug in the cable, your connected, since connection is active at modem/router, no matter of OS. Just start browser and start surfing :)

BTW, I agree that Ubuntu should provide at least "Errata" or "Notes" document (like Mandriva, e.g.) in which users can see what are known bugs/issues in the currents release and how to solve them.

---

### Post by Martje_001 on 2009-12-01
I don't get it: why does the computer need to know your ADSL login? Don't ISPs include one of [these]("http://en.wikipedia.org/wiki/DSL_modem") in the USA?

---

### Post by Onesimus on 2009-12-01
> **namekuseijin said:**
> 

2) How in hell can I get back the sound volume applet?!  I removed it by accident from the system tray and I can't get it back! 



You can get your sound volume applet back by.

1. Right Click on Top Panel
2. Select 'Add to Panel'
3. Select 'Notification Area'

Done

---

### Post by namekuseijin on 2009-12-01
> **meho_r said:**
> I guess he meant that you have two ways of connecting using ADSL (at least in my country): 

1. Doing manual connection (on/off), a.k.a brigded mode. This is the way you described: you put your username and password in Network Manager and start and stop connection by mouse click.

What about the cryptic "Service" parameter in-between those 2?  What goes in there?  It's just there to confuse the user?  It's not in the Help.

Network Manager doesn't work, but I'm ok doing the pon/poff jig I've been doing in Ubuntu for the past years.

> **meho_r said:**
> 2. Permanent connection, a.k.a routed mode. This way you enter your router/modem settings (through the browser, enter something like 192.168.1.1. and an admin window will appear) and enter your username and password in there, and not Network Manager.

Where is that info in Ubuntu Help?

Thanks anyway.

> **meho_r said:**
> When in routed mode, you are constantly connected to Internet. Actually, the minute you plug in the cable, your connected, since connection is active at modem/router, no matter of OS. Just start browser and start surfing :)

Does that mean my ADSL modem has to be permanently turned on?  I'm an old-school guy and I turn on/off everything after a day (or night) worth of work.

> **meho_r said:**
> BTW, I agree that Ubuntu should provide at least "Errata" or "Notes" document (like Mandriva, e.g.) in which users can see what are known bugs/issues in the currents release and how to solve them.

Just having an informative Help is enough.  It seems it's even slimmer than Gnome itself.

---

### Post by namekuseijin on 2009-12-01
> **Martje_001 said:**
> I don't get it: why does the computer need to know your ADSL login? Don't ISPs include one of [these]("http://en.wikipedia.org/wiki/DSL_modem") in the USA?

Beats me.  Whenever I turn on my ADSL modem, nothing works until manual pon/poff.

---

### Post by namekuseijin on 2009-12-01
> **Onesimus said:**
> You can get your sound volume applet back by.

1. Right Click on Top Panel
2. Select 'Add to Panel'
3. Select 'Notification Area'

Done

I'll try that.  I've tried to lookup "sound volume", "mixer" etc when going through the "Add to Panel" menu, but there was nothing like that there.  I believe the notification area is already there, so I'm not sure that'll work.

In any case, I'm at work now and perhaps a reboot is all that was needed?  I'll check it out once at home...

---

### Post by namekuseijin on 2009-12-01
BTW, I've noticed some troubles with the latest Ubuntu 9.10 that sound like scheduling issues:

1) some Firefox page-scrolling stuttering/hangups
2) rendering with the Luxrender renderer on all 4 cores makes the GUI very stuttering.  Not any such problem up to 9.04.  Happens either with 32 or 64-bits.

full scoop:
[http://www.luxrender.net/forum/viewtopic.php?f=16&t=3160](http://www.luxrender.net/forum/viewtopic.php?f=16&t=3160)

---

### Post by meho_r on 2009-12-01
> **namekuseijin said:**
> ...
Does that mean my ADSL modem has to be permanently turned on?  I'm an old-school guy and I turn on/off everything after a day (or night) worth of work.

No, it means the moment you turn it on (actually, couple of seconds after that, it needs them to boot) you are connected, no need to do anything like "pon/poff", mouse click on NM etc. You turn the modem off you get disconnected. Simple as that. Actually, this way you don't need Network Manager at all for normal connections.

And as for volume control, I told you earlier, it is:
```
gnome-volume-control-applet
```
Press Alt+F2 then input that code and you'll get your applet :)

---

### Post by namekuseijin on 2009-12-01
> **meho_r said:**
> No, it means the moment you turn it on (actually, couple of seconds after that, it needs them to boot) you are connected, no need to do anything like "pon/poff", mouse click on NM etc. You turn the modem off you get disconnected. Simple as that. Actually, this way you don't need Network Manager at all for normal connections.

This is great!  Would be much greater if it was in Ubuntu Help.

> **meho_r said:**
> And as for volume control, I told you earlier, it is:
```
gnome-volume-control-applet
```Press Alt+F2 then input that code and you'll get your applet :)

Like I said, I tried this before and it told me gnome-volume-control-applet was already running.  I killed the process on the CLI and it didn't complain, but didn't show up in the notification area either.  It was marked on in the System -> Preferences -> Startup Apps...

---

### Post by jdrodrig on 2009-12-01
why have we let a clearly Technical question post, survive in experiences and testimonials?

---

### Post by namekuseijin on 2009-12-01
> **jdrodrig said:**
> why have we let a clearly Technical question post, survive in experiences and testimonials?

There's no questioning besides why such basic user-level issues are not documented in Ubuntu Help.  And it's certainly a (bad) experience.

---

### Post by meho_r on 2009-12-01
> **namekuseijin said:**
> This is great!  Would be much greater if it was in Ubuntu Help.
Sorry, but this is not a "basic" info and because of that it isn't in Help files. They provided basic infos already and it does work (it would work if not that NM bug in Karmic. That's where errata should be useful). For all advanced settings you'll have to rely on your ISP, forums or other's help. You won't get this info on any other OS neither.

> Like I said, I tried this before and it told me gnome-volume-control-applet was already running.  I killed the process on the CLI and it didn't complain, but didn't show up in the notification area either.  It was marked on in the System -> Preferences -> Startup Apps...

Well, probably two instances were running if it told you that. Try this:
```
killall gnome-volume-control-applet
```
Run this code in Terminal twice. If bash complains that there's "no process found", try now:
```
gnome-volume-control-applet
```

---

### Post by namekuseijin on 2009-12-01
> **meho_r said:**
> Sorry, but this is not a "basic" info and because of that it isn't in Help files. They provided basic infos already and it does work (it would work if not that NM bug in Karmic. That's where errata should be useful). For all advanced settings you'll have to rely on your ISP, forums or other's help. You won't get this info on any other OS neither.


I learned from pppoeconf (I was not on broadband until then) thanks to info on Ubuntu Help some few iterations ago.  Now that is what I call a helpful Help!  Does it really sound right to drop helpful information from Help because it's not "basic"??!

I vehemently disagree with this "simplicity" -- or better worded "simplism" -- mentality that permeates Gnome and Ubuntu.

Slim, non-informative help and lack of options only means when a user has a problem, he's got to look elsewhere for help.  And that if he can't connect to the internet, it means he'd better have some Windows nearby for dual-booting in a system that actually works in order to lookup for help for his poor Linux system which can't even connect!

I demand that new users be given the light about pppoeconf again!  Not that anyone will listen anyway...

> **meho_r said:**
> ```
gnome-volume-control-applet
```

That is fine, but I've tried killall before.  Doesn't matter, while rebooting didn't bring it back, the tip to Panel -> Add -> Notification Area worked.  I didn't even know it was possible for "system tray" to be turned off, I thought I had accidentally dropped just sound volume...

---

