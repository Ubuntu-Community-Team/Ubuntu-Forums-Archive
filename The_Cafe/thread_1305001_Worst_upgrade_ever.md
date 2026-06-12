---
title: "Worst upgrade ever?"
date: 2009-10-29
forum: The Cafe
---

### Post by ticktricktrack on 2009-10-29
How well did this upgrade work for you?

I thought mine wasn't fixable, but I could repair my software sources and restart the upgrade after about 10 attempts. Hope this one runs through.

---

### Post by gvor54 on 2009-10-29
It went OK. Only trouble is I cannot shutdown my computer!

---

### Post by Shibblet on 2009-10-29
So far, I can't install the NBR on my MSI-Wind.  Haven't tried my desktop yet.

---

### Post by grayrainbow on 2009-10-29
Total disaster! Starting from dbus to xorg everything already present in the system wont install, then of course system was unbootable. Now I'm with fresh install(which looks pretty cool btw).

---

### Post by ticktricktrack on 2009-10-29
Finally it went through. Upstart is more a Slowstart, it lazes about for a minute until it can be bothered to do some work. But otherwise it seems to work fine.

---

### Post by stalet on 2009-10-29
Disastrous - allmost since the installer actually stopped before doing real damage. 
I can still use the machine with 9.04.

Cant say i'm looking forward to do a full reinstall tho...

---

### Post by dochood on 2009-10-29
I tried to install the Release Candidate the other day.  Here are my problems that I had:

[LIST]
[*]Grub2 failed to detect my partitions, and it did not install correctly.
[*]I found some instructions that were supposed to fix this, but I still could not get Grub2 fixed (Error 15).
[*]After reinstalling 9.10, I could no longer boot into Windows 7.
[*]I restored the Windows 7 boot loader, but for some reason, it decided to swap my boot drive so Windows 7 came first.... it took me awhile to figure that out!
[/LIST]

I'm back at 9.04, 64 bit.

---

### Post by overdrank on 2009-10-29
Moved to The Community Cafe

---

### Post by Chronon on 2009-10-29
My netbook upgraded fine.  My desktop has an intel q6600 processor and I wanted to try a fresh install of the 64-bit version of Kubuntu.  Unfortunately, the LiveCD won't let me proceed past choosing my language.  (I made a thread in the installation forum, so not seeking any advice or help here.)

---

### Post by hoppipolla on 2009-10-29
Flawless man. But then I did it back on Beta 1. And it was still relatively flawless xD

---

### Post by Johnsie on 2009-10-29
The process of upgrading returned no errors... But many of the apps seem to be crashing for different reasons. I've had 3 different apps crash in the last hour.

Boot time seemed longer too. I hope that's only because it was the first boot.

---

### Post by paulisdead on 2009-10-29
I did it about a week ago, though I had to uninstall update manager and use the server upgrade method.  For some reason it wanted to remove it during the upgrade, which of course won't work when you're using update manager to upgrade.

Nautilus is still hosed up for me, and won't remember icon locations or folder views.  Firefox won't open a torrent into transmission, so I have to save it, then open it in transmission.  My boot and shutdown time's a touch longer under 9.10 than 9.04, as well.  In order to get temp sensors working on my Asus P5Q-E, I had to get a more updated lm_sensors that can work with the newer asus driver.  Figures this version of lm_sensors won't work with the version of gkrellm included.  At least it works with Gnome's monitors.

I swear, I should stick to only the LTS releases, it's just that I wind up needing more up to date versions of packages, and adding too many PPAs can be a hassle.  I'm probably going to need a clean install.  It seems to defeat the purpose of running linux at all if you need to reinstall it just because a new version came out.  Maybe it is time to go back to Gentoo for my desktop, I feel like 3 years of Ubuntu has made me rusty.

---

### Post by Johnsie on 2009-10-29
In terms of performance, Karmic feels like a beta or an alpha. It seems like a work in progress that needs a little polish and bug fixing.

---

### Post by starcannon on 2009-10-29
I keep /home on its own partition, all upgrades are flawless for me. Just a clean install without formatting the /home partition.

---

### Post by days_of_ruin on 2009-10-29
> **starcannon said:**
> I keep /home on its own partition, all upgrades are flawless for me. Just a clean install without formatting the /home partition.

Same here. The best way to upgrade IMO.

---

### Post by aamcse04 on 2009-10-29
I have tried a clean install multiple times now.  I can not figure out what is going on.  Every previous version has worked fine but when I install this, the GRUB loader comes up but when I try any selection it says error: no such device:2102a76f-d260-455d-8dca-971fa9f4010e press any key to continue...

When I do, it just says the same thing continuously.

---

### Post by koleoptero on 2009-10-29
> **starcannon said:**
> I keep /home on its own partition, all upgrades are flawless for me. Just a clean install without formatting the /home partition.

I used to do that too, but this time various apps started hiccuping. Oh well, I just had more fun reconfiguring my system (although I reused some config files like conky, rtorrent, etc).

---

### Post by jrrader on 2009-10-29
Alternate CD for 64 will not let me install without downloading from the internet even after selecting the option to stay off the internet.  I used the alternate CD to avoid the servers on such a busy day.  32 bit for my wife's computer worked perfectly, but my desktop is getting a slow-drip ubuntu update...  2 hours left.

edit: and I tried CD, mounting the image, unetbootin usb, redownloading the torrent, and unplugging the cat5.

---

### Post by Frak on 2009-10-29
"No Such Device:Random Gobledy Gook"

Failure, absolutely hard.

---

### Post by dj-toonz on 2009-10-29
went perfect for me, 10 minutes to download the torrent, opened up usb-creator to make A a USB image of the .ISO file & rebooted the laptop & 20 minutes after I had dual boot system of Jaunty x64/Karmic x64 then did the same on the Desktop so thats jaunty x64 / Karmic x64 aswell, all together, tock just short of an hour & no problems

---

### Post by lovinglinux on 2009-10-29
> **Johnsie said:**
> In terms of performance, Karmic feels like a beta or an alpha. It seems like a work in progress that needs a little polish and bug fixing.

It's the opposite for me. It is running better than Jaunty, although I did a clean install back when the Beta was released and I'm running kde-minimal instead of gnome.

---

### Post by HappyFeet on 2009-10-29
When will people learn that clean install is the way to go. A lot of people have problems after upgrading, then wind up fresh installing anyway. In the time it takes to upgrade, you could have fresh installed, and had a nice clean file system.

Fresh install is recommended for all OS's, including windows, mac, and linux. Wake up. And yes, I realize some people have no issues upgrading. But why take a chance?

---

### Post by HappyFeet on 2009-10-29
> **johnsie said:**
> the process of upgrading returned no errors... But many of the apps seem to be crashing for different reasons. I've had 3 different apps crash in the last hour.

Boot time seemed longer too. I hope that's only because it was the first boot.

**[size="6"]Clean install![/size]** Some people never learn.

My install screams.

---

### Post by JillSwift on 2009-10-29
> **HappyFeet said:**
> **[SIZE=6]Clean install![/SIZE]** Some people never learn. +1

> **HappyFeet said:**
> My install screams.
Mine did, too, but I turned the volume down. The screaming scared my neighbors.

---

### Post by absinthe on 2009-10-29
We need some kind of automated script for when a new release drops.

1. Auto log users onto #****-release-party

2. Auto-refresh main page to see if "OMG IT'S UP!!1"

3. Make 1 thread about "Greatest release yet"

4. and "Worst release yet"

Having said that my upgrade was as smooth as fresh cream.

---

### Post by ericab on 2009-10-29
vsftpd doesn't work now,

VMware Server wont compile necessary modules,

something is wrong with my PAM,

few other things...

overall not as smooth as i had planned *and* prepped for.

luckily i did a clonezilla before upgrading to 9.10 (from 9.04)


too much time invested in upgrade. pretty disappointed. major headache. numbing the pain now with a bottle of wine.

---

### Post by pwnst*r on 2009-10-29
lol, and people bitch about windows.

---

### Post by Excedio on 2009-10-29
> **HappyFeet said:**
> When will people learn that clean install is the way to go. A lot of people have problems after upgrading, then wind up fresh installing anyway. In the time it takes to upgrade, you could have fresh installed, and had a nice clean file system.
 
Fresh install is recommended for all OS's, including windows, mac, and linux. Wake up. And yes, I realize some people have no issues upgrading. But why take a chance?
 
Not to forget...clean install gives you EXT4 by default.

---

### Post by lovinglinux on 2009-10-29
> **absinthe said:**
> We need some kind of automated script for when a new release drops.

1. Auto log users onto #****-release-party

2. Auto-refresh main page to see if "OMG IT'S UP!!1"

3. Make 1 thread about "Greatest release yet"

4. and "Worst release yet"

Having said that my upgrade was as smooth as fresh cream.

:lolflag:

Also a script to reply all new threads asking how to upgrade from the Beta and Release Candidate would be nice.

---

### Post by Jimleko211 on 2009-10-29
Karmic is...a disapointment from Jaunty.  I would have been perfectly happy if they just upgraded the repos and left it there.  The "fast start" is a joke, it's slower than with Jaunty!

---

### Post by sdlynx on 2009-10-29
update went great more me, since I already had a separate home partition and everything.

---

### Post by JDShu on 2009-10-29
When a new ubuntu distribution comes out, I expect it to be buggy as hell. My Karmic installation has fulfilled my expectations. It generally works fine, but Empathy and the msn protocol don't like each other. More importantly, games like Hedgewars and Open Sonic are choppy and can't really be played. Not sure if this is a problem with the nvidia drivers not working well with Karmic.

---

### Post by misfitpierce on 2009-10-29
I put flawless but I fresh installed!

This release is not good to upgrade to but to fresh install it to take advantage of the new EXT4 filesystem unless you did custom and chose EXT4 on 9.04.

---

### Post by lisati on 2009-10-29
Haven't done an upgrade yet. Based on a couple of brief tests with a USB drive, I've got some homework to do - wouldn't start properly on my laptop & the software store "stopped unexpectedly" (as did the error reporting) on my desktop.

---

### Post by johnboy1313 on 2009-10-29
9.10, i am pleased

---

### Post by danastasio on 2009-10-29
all this awesomeness and i still can't get sound to work :(

---

### Post by dearingj on 2009-10-29
Flawless. Everything I've tried works at least as well as it did in 9.04, and the system as a whole runs faster due to ext4 (and that's not just the placebo effect; I tested ext3 and 4 a few months ago on Jaunty and ext4 was definitely faster)

---

### Post by jpmelos on 2009-10-29
I'll wait a week before installing it even from scratch, so most of the obvious and most dangerous bugs are already solved.

---

### Post by mamamia88 on 2009-10-29
i like it 64 bit flash works great and compiz is much smoother with nvidia 185

---

### Post by D-Sider on 2009-10-29
*sigh* the system is fantastic, minus the Black Screen / Mod Not Supported that happens at login when I activate ATI Prop Drivers.

If I delete Xorg.conf, restart and let it generate a new one (with the drivers), then delete the new one, restart and replace the old one (with the drivers) it works... until I restart again.  Sometimes it's a few restarts and other times its every restart.

Also, the xorg.conf file is amazingly empty. Only had 5 lines in it to start with.

I'll keep playing till I work it out.  I think it's because my Samsung LCD TV has dud EDID info.

---

### Post by toupeiro on 2009-10-29
> **HappyFeet said:**
> When will people learn that clean install is the way to go. A lot of people have problems after upgrading, then wind up fresh installing anyway. In the time it takes to upgrade, you could have fresh installed, and had a nice clean file system.

Fresh install is recommended for all OS's, including windows, mac, and linux. Wake up. And yes, I realize some people have no issues upgrading. But why take a chance?

*citation needed* for ubuntu.

I have a system where I've done upgrades since 6.10 and its 100% rock solid.

---

### Post by qwerty1105 on 2009-10-29
I did a clean install for 8.10.  Upgraded to 9.04 with no problems.  This one (9.10) I upgraded and now keyboard and mouse do not work...  Gonna burn the .iso and see if that works.

---

### Post by MasterNetra on 2009-10-30
lol Upgraded from RC. Just a handful of files needed updating :p

---

### Post by Excedio on 2009-10-30
HOLY CRAP!...

Just did a clean install on my wife's 5 year old laptop. 8.04 & 8.10 couldn't find the wireless out of the box. I'm very excited about this...

---

### Post by Megrimn on 2009-10-30
Sad, 'cause my custom GDM doesn't work anymore.  Everything else is fine, plus some cool new stuff to get used to.

---

### Post by sonay on 2009-11-05
I upgraded with update-manager when karmic-beta was released, it was OK until the final release, then ubuntu slowed down, even changing a theme took quiet time(a minute or so), then I made a clean install and everything is fine, except my internal mic doesn't work and my touchpad doesn't have a middle click anymore (may be it just needs to be configured somewhere, actually I don't care).

I don't think I'll use the update-manager way again, at least not for the next release.

---

### Post by pwnst*r on 2009-11-05
upgrade borked mine (completely lost the dekstop among other things) but normally i install clean anyway, so that's what i did.  first few boots i had slowness getting to the desktop and my mouse and k/b not being recognized until well after the login prompt appeared, but it's been fine ever since.

---

### Post by SunnyRabbiera on 2009-11-05
> **pwnst*r said:**
> lol, and people bitch about windows.

Yes but the difference between windows and linux is that windows is supposed to be "professional" and iron clad proof that closed source software is superior.
And yet Windows has TONS of issues, despite costing a lot of money and allegedly being "superior" to linux.
For me I can give a lot of pardon to Linux when something goes wrong as its INDIPENDANTLY DEVELOPED, no money no power just time.
I can forgive any errors in the linux world as I know that these are people who work for nothing.
Windows has no excuse if it screws up in my mind as it seems you pay for crap, at least in linux I know what I pay for.

---

### Post by alphaniner on 2009-11-05
My worst upgrade ever was elementary school to middle school.

---

### Post by Frak on 2009-11-05
> **SunnyRabbiera said:**
> Yes but the difference between windows and linux is that windows is supposed to be "professional" and iron clad proof that closed source software is superior.
And yet Windows has TONS of issues, despite costing a lot of money and allegedly being "superior" to linux.
For me I can give a lot of pardon to Linux when something goes wrong as its INDIPENDANTLY DEVELOPED, no money no power just time.
I can forgive any errors in the linux world as I know that these are people who work for nothing.
Windows has no excuse if it screws up in my mind as it seems you pay for crap, at least in linux I know what I pay for.
Pardon common human error Mr. Robinson. Take a look at [CHESS]("http://msdn.microsoft.com/en-us/devlabs/cc950526.aspx") and show me that Microsoft isn't trying to lessen errors in coding. Also, I don't pardon Linux developers because many of them are paid.

---

### Post by pwnst*r on 2009-11-05
> **SunnyRabbiera said:**
> Yes but the difference between windows and linux is that windows is supposed to be "professional" and iron clad proof that closed source software is superior.
And yet Windows has TONS of issues, despite costing a lot of money and allegedly being "superior" to linux.
For me I can give a lot of pardon to Linux when something goes wrong as its INDIPENDANTLY DEVELOPED, no money no power just time.
I can forgive any errors in the linux world as I know that these are people who work for nothing.
Windows has no excuse if it screws up in my mind as it seems you pay for crap, at least in linux I know what I pay for.

okay, but i've never had an installation issue with windows.

---

### Post by sledge73 on 2009-11-05
> **pwnst*r said:**
> okay, but i've never had an installation issue with windows.

man I have! like spending hours chasing down drivers on another computer cause I couldn't connect to the internet on a fresh windoze install! just to point one out.

---

### Post by stars on 2009-11-06
whether installing windows or a linux distro one should research their hardware before a fresh install. it will allow you to acquire drivers as needed & make you aware of common problems. lack of preparation cannot be blamed upon an operating system regardless of the frustration of having poorly supported hardware.

---

### Post by SunnyRabbiera on 2009-11-06
> **sledge73 said:**
> man I have! like spending hours chasing down drivers on another computer cause I couldn't connect to the internet on a fresh windoze install! just to point one out.

I have too

---

### Post by mehaga on 2009-11-06
I don't think any upgraded system is as good as clean installed one. At best, everything works but runs a bit slower. And that is how upgrades usually worked for me. In this case, OS works much slower and error screens pop up all the time (mostly KDE error screens). If I had a tiny spaceship at the bottom of my screen and ability to shoot the damn error screens, it might be fun (remind me to patent this idea). Without it, however, this is my worst upgrade experience ever. 
That said, clean install is fantastic, and I believe this is one of the best Ubuntus so far.

---

### Post by Frak on 2009-11-06
> **stars said:**
> whether installing windows or a linux distro one should research their hardware before a fresh install. it will allow you to acquire drivers as needed & make you aware of common problems. lack of preparation cannot be blamed upon an operating system regardless of the frustration of having poorly supported hardware.
Ubuntu lacks a very special "thing" that makes BSD and Windows AMAZING:


An HCL - Hardware Compatibility List

---

### Post by stars on 2009-11-07
i agree, while it's more time consuming to google "hardware vendor/model" than to view an hcl, it's better than doing a fresh install of a new operating system blindly without some research.

---

### Post by blueshiftoverwatch on 2009-11-07
I think this is the best release yet.

---

### Post by scouser73 on 2009-11-10
I didn't manage to vote on the poll, but Karmic is working brilliantly for me.

---

### Post by diablo75 on 2009-11-10
Flawless, because I chose to NOT UPGRADE for the time being.  I have no rush to get the latest and will wait for 9.10.1 to be released.

---

### Post by RiceMonster on 2009-11-10
> **Frak said:**
> Ubuntu lacks a very special "thing" that makes BSD and Windows AMAZING:


An HCL - Hardware Compatibility List

Yes agreed. Perhaps they should maintain a list on kernel.org or something of available open and proprietary drivers, compatibke hardware, etc.

---

