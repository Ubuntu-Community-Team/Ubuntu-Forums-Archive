---
title: "What is the max uptime for ur ubuntu box?"
date: 2007-01-12
forum: The Cafe
---

### Post by neoflight on 2007-01-12
I was wondering what people noticed as their ubuntu box's max(uptime)...
the command uptime will give you a brief info...

the reason i am asking is that i never had more than 2 days uptime with my edgy. its a relatively stable system with not much graphic customization.

i am several times forced to restart the system or X to get back to get to the normal working speed. after a couple of days my system goes to really slow mode and things such as FF and all start to respond really slow... worst part is 
clicking (the still clickable) log off button in the panel produces no response...

i dont know where to look for either...](*,)
Edit: Please mention if it s desktop or server installation. (additional details such as the version (dapper, edgy etc..), gnome/kde/xfce, graphics would be helptul)

**For an average user, this could be one of the ways to check the stability of the installation **

---

### Post by blackened on 2007-01-12
On Dapper here, but the only time I'm required to turn my machines off is when an update requires a reboot. Other than that they run 24/7 without fail.

---

### Post by Mateo on 2007-01-12
never been one to keep my computer on all the time.

by the way, if you're logg off button is failing i think you can just type "halt" in terminal to turn the compu off.

---

### Post by neoflight on 2007-01-12
> **Mateo said:**
> never been one to keep my computer on all the time.

by the way, if you're logg off button is failing i think you can just type "halt" in terminal to turn the compu off.

yes thats true.. but there should some reason for the mishap....i am wondering what that is...still waiting to get the behavior consistent so that i can file a bug report...

---

### Post by Pobega on 2007-01-12
I only go for days at a time when I'm downloading, but I'm using a laptop and I'm very anal when it comes to running it for long periods of time. I do notice slowdown though, you're right. Usually causes me to restart X after two days or so.

---

### Post by zerhacke on 2007-01-12
My Edgy/E17 box has been running since Edgy came out except for one reboot where I put a new kernel in.

---

### Post by parker13 on 2007-01-12
About 6 months... between dist upgrades!

---

### Post by ixus_123 on 2007-01-12
Got a an ibook running ubuntu dapper PPC with an uptime of 10 days  - id dont remember restarting - that thing never has a problem

my work horse sounds like a hoover. (2.1 gig overclocked Sempron, 512mb ram) I usually transcode video on it. That;s usually on for 24 - 60 hours max (transcoding to h264 takes ages!!)  That's Ubunty Efty Edge. Seems pretty stable to me on 2nd install although I do get mouse freezes for a few seconds every now & then & firefox loves to crash every few hours so I restart it now evvery couple of hours rather than leaving it run

---

### Post by beercz on 2007-01-12
Had a debian server with an uptime of 412 days - only got turned off to move it!

---

### Post by Kateikyoushi on 2007-01-12
Usually months I do not turn off my notebook unless updates require or I am not using it for a day or so in plane etc.
Ubuntu is really stable on my machine.

---

### Post by neoflight on 2007-01-13
> **parker13 said:**
> About 6 months... between dist upgrades!

woo wow!!...thats amazing.....what displaymanager are using?any bells and whistles?

---

### Post by Horizon on 2007-01-13
For all my Ubuntu boxes they run as long as I want them to. I don't like kernel updates etc. Once it works and it's setup the way I want I just lock the kernel packages. They all run xgl + beryl and they're stable as a rock. Even my notebook will run for pretty much however long I want. I used to get slowdowns after a while in dapper but that's all gone in edgy.

Longest I ever left one running was a couple (3?) of months though. But they'd easily run for longer.

---

### Post by sloggerkhan on 2007-01-13
I mess with my system without knowing what I'm doing all that well and sometimes that causes bad behaviour and I must restart X or maybe the comp. But if I leave the thing alone I can easily run it for at least a couple of weeks, possibly more. But I have such an urge to mess around that I usually have to restart X at least every few days. (Even if I don't reboot the comp.)

---

### Post by 3rdalbum on 2007-01-13
I turn mine off at the end of the day usually, so my uptime could be greater than it is.

My maximum uptime has been about 30 hours - I used my computer as a desktop one day, then left it running overnight as a server, kept it running while I was at work and then came home and used it as a desktop again.

I doubt my uptime would ever reach more than a couple of weeks - I run the ATI proprietry driver, and that crashes quite a bit.

You can find out your current uptime through the "uptime" command.

---

### Post by jpkotta on 2007-01-13
Longest I ever had was 130+ days.  It went down because I accidentally typed CTRL-ALT-DELETE into a console.  That key binding is no longer active.  It was due for a kernel update anyway.

---

### Post by hoagie on 2007-01-13
I always turn of my computer at the end of the day because I can't sleep if I hear it:o . I only leave it running if I'm downloading a huge file or if I'm encoding video. So the uptime usually never goes further than 10 hours.

---

### Post by HoMe_CaNiBaL on 2007-01-13
only for days...if i have beryl working...without beryl, i think the computer can work for weeks or even months i think..

---

### Post by Randomskk on 2007-01-13
My desktop gets turned off every night so I can sleep, but my two Ubuntu servers only ever reboot when there was a power failure, and since getting a UPS they've had constant uptime. The most was a few hundred days, right now it's been 84 days since I installed the UPS, and still counting.

---

### Post by KaroSHiv0n on 2007-01-13
100 days for me, only went down due to power cut :(

---

### Post by MetalMusicAddict on 2007-01-13
I have a Xubuntu-Dapper based home server that I only turned off after a drive started to go. I had it up fo 2 months. Im still kinda learning how I like my server setup so I had it on and off every once in awhile before that. 8)

---

### Post by heathen on 2007-01-13
heh, 11h 42m...  but, I just upgraded to edgy so it doesnt have much uptime to base off of...
also, I run a laptop so it get's turned off frequently...

---

### Post by Christmas on 2007-01-13
8 days only with Kubuntu 6.06 if I recall correctly, but I had to restart for some upgrade.

---

### Post by tagra123 on 2007-01-13
3 1/2 months on my breezy (mythtv) machine

When your computer gets real slow  open a terminal and type in 

top

Chances are your xscreensaver may be the culprit.

I had problems on my myth backend box which went long times unattended.  I removed/disabled the screensaver and the problem went away.

Changing swappiness can help big time.  I have swappiness set to 100 on the laptop which could use a memory upgrade and 20 on my desktop.  

Google for 

swappiness ubuntu

or here's a forum thread

[http://ubuntuforums.org/showpost.php?p=1254289&postcount=13](http://ubuntuforums.org/showpost.php?p=1254289&postcount=13)

---

### Post by FredSambo on 2007-01-13
This is the record for my home server, and I only rebooted to add another stick of RAM.  I have one in the field that has been running for 85 days and counting!  Needless to say, Ubuntu server is awesome!

[IMG]http://fredsambo.com/fred/uptime.jpg[/IMG]

---

### Post by insane_alien on 2007-01-13
23 days and counting.

---

### Post by K.Mandla on 2007-01-13
I have a laptop that acts as a music server for the rest of the house; I've left it on for weeks at a time. Family members actually complain if I shut it down overnight. :mrgreen:

---

### Post by SonicSteve on 2007-01-13
I have Ubuntu/edgy running on a server/secondary system and It will run for weeks if I can stand not tinkering for that long.

---

### Post by tagra123 on 2007-01-13
SonicSteve -- Nice Melmet!

---

### Post by punkinside on 2007-01-13
My laptop running edgy gets shut down all the time since I often work from the university or friend's houses. Though I do leave it on for a few days if its a slow week and I'm not on the move.

My cvs / database / testing server running dapper has been up for two months now with no DE.

---

### Post by qpieus on 2007-01-13
About 90 days for my file/print server. Decided to reboot after a kernel upgrade, otherwise it would have stayed running.

---

### Post by neoflight on 2007-01-13
> **tagra123 said:**
> 3 1/2 months on my breezy (mythtv) machine

When your computer gets real slow  open a terminal and type in 

top

Chances are your xscreensaver may be the culprit.

I had problems on my myth backend box which went long times unattended.  I removed/disabled the screensaver and the problem went away.

Changing swappiness can help big time.  I have swappiness set to 100 on the laptop which could use a memory upgrade and 20 on my desktop.  

Google for 

swappiness ubuntu

or here's a forum thread

[http://ubuntuforums.org/showpost.php?p=1254289&postcount=13](http://ubuntuforums.org/showpost.php?p=1254289&postcount=13)


Thank you for the info. I didnt know about the swappiness... and disabled the screensaver ....lets see....i will try from tomorrow for an uptime test...

---

### Post by AndyCooll on 2007-01-13
My server runs for months without rebooting, just reboot it with kernel upgrades. My boxes and laptops I tend to switch off when I've finished using them.

:cool:

---

### Post by Jussi Kukkonen on 2007-01-13
> **K.Mandla said:**
> I have a laptop that acts as a music server for the rest of the house; I've left it on for weeks at a time. Family members actually complain if I shut it down overnight. :mrgreen:

Same here. The previous incarnation of that system got >370 days uptime** -- not bad for an ancient Thinkpad (the battery seemed to have just enough juice to get it through power cuts). I think it was running Warty.

I've had Ubuntu on four different machines now, and frankly, they just don't crash. Having no fancy video cards and otherwise well supported hardware probably helps...

**) The machine was only used for music -- it was not accessible from anywhere else, so I didn't bother with booting into new kernels.

---

### Post by neoflight on 2007-01-14
i use wireless to connect my laptop.....i am trying to avoid shutdowns to check my uptime...

why is that i have to restart my network every time after a login. ...else its really slow and after i restart my network it come back to normal speed....initially it  was the reason i always restarted the computer.....

i have no problem with connecting using ip specified school lan and wireless at home...
but ...this is driving me nuts...even at home....!

---

### Post by compwiz18 on 2007-01-14
120 days on an Edgy server - I'm sure it could of gone for more, but I had to turn it off
as for my laptop, only a couple of days, but I have to turn it off to take it places - it never freezes

---

### Post by neoflight on 2007-01-16
i got 2 days and 10 hrs.... the login after that screwed up the wireless ad it was not finding the wireless driver. !!!

then i had to restart and things went fine...i guess this is the problem with the network-manager....not sure....

---

### Post by Tipo on 2007-01-16
My desktop at home rarely gets restarted or turned off. Probably only when software update requires it, or when there is a power outage (power around my neck of the woods tends to cut out a lot).

Longest I've gone without a reboot/power outage/shut down was around 55 days or so (and that was back with breezy).

---

### Post by mips on 2007-01-16
[http://uptime.netcraft.com/up/today/top.avg.html](http://uptime.netcraft.com/up/today/top.avg.html)

Sorry it's servers...

---

### Post by dca on 2007-01-16
Hmmmm, I have two P4,3GHz systems.  My wifes which is simple (512MB RAM, 80GB SATA HDD) was left on over the weekend and ran for over 72+ hours.  She came back jiggled the mouse and right back on the internet.  She can do that w/o missing a beat sometimes....
 
The second has 512MB RAM and two 400GB SATA drives.  Call it a wanna-be server and that runs Ubuntu 6.06 Server Ed, w/ GNOME added (because let's face it, even sometimes I get tired of the CLI) and it has been up for over three months straight.

---

### Post by Omnios on 2007-01-16
WIth CRTL-ALT-B-space there is no need other than a update to reboot.

---

### Post by neoflight on 2007-01-23
i am getting more than acouple of weeks for my pc at office... i think the laptop is the problem...changing between networks and constant shutdowns...etc...

---

### Post by Grey on 2007-01-23
Months.  I have an Ubuntu file server, running Dapper.  It has a bad stick of memory, and I am too lazy to compile the badram patch for the kernel.  So it needs a reboot every so often when it has a kernel panic.

My laptop regularly lasts over a month, until I get a kernel update.  My desktop usually goes a week or so until I want to play a Windows game.

My girlfriend's mythtv box runs Dapper.  It goes for weeks, but MythTV sometimes brings the system to a crashing halt.  Her desktop has been known to go for months as well (Edgy presently).

---

### Post by rabid9797 on 2007-01-23
i haven't ever tried to see how long i can run it, but looking at the experiences here, i could prolly run mine for a month or so before i needed to do something in windows nad restarted.

---

### Post by timpino on 2007-01-23
I had a Slackware install that went for 1.5 Years before I took it offline, Ubuntu I have maxed at 2 weeks before a faulty PSU took it offline

---

### Post by drummer on 2007-01-23
Just over 18 days for my Ubuntu machine, I usually turn it off at night and only leave it running if I have something downloading.

---

### Post by parker13 on 2007-01-25
190 days and counting (on Dapper)...


ivbadm@frost:~$ cat /etc/issue
Ubuntu 6.06 LTS \n \l

ivbadm@frost:~$ who -b
         system boot  2006-07-18 10:14

ivbadm@frost:~$ uptime
 08:08:32 up 190 days, 22:50,  6 users,  load average: 0.01, 0.02, 0.00

---

### Post by toaste on 2007-01-25
My Dapper box was up for just over 70 days last semester.  It served as a simple samba and headless Azureus machine, but was taken offline by an undiagnosed hardware snafu shortly before exams (found it off, could turn it on and it would post it okay, then randomly reboot.  I checked the ram in memtes86 on another machine, and tried using another PSU with no luck.).  Very impressive given that the motherboard, CPU, and ram were aquired by dumpster diving!

Honestly, however, I'd prefer to sacrifice ridiculous uptimes for more frequent kernel updates.

---

### Post by lyceum on 2007-01-25
I'm on edgy and I only shut down to take it with me (laptop). If I don't more it, it can be on for weeks.

---

### Post by meheheh on 2007-01-25
75 days (see [Netcraft]("http://uptime.netcraft.com/up/graph?site=myserver.mooo.com&probe=1")'s uptime counter.) Died during a long blackout when the UPS ran out of juice. Now the hardware's been upgraded (slightly, it's a PIII now, it was a PII, same install, just moved the hard drive) and it's in the garage.

---

### Post by gewone on 2011-03-19
I have an old laptop under my bed. It's no i5/i7 monster machine, but a rather old P3-isch. However, it operates [eggdrop]("http://www.eggheads.org/"), [nginx]("http://nginx.org/"), [squid]("http://www.squid-cache.org/"), etc pretty well and -- as you can see -- has some uptime as well.

[I]<@gewone> !sysinfo
<@Eggdropper> Hostname: LAPTOP - OS: Linux 2.6.32-25-generic/i686 - Distro: Ubuntu 10.04.2 LTS LTS - CPU: Mobile Intel Pentium III - M 1200MHz (798.000 MHz) - Processes: 140 - Uptime: **97d 10h 21m** - Users: 1 - Load Average: 0.02 - Memory Usage: 150.68MB/488.93MB (30.82%) - Disk Usage: 22.91GB/36.0
[/I]

Some people say that laptops easily take damage of having an excessive uptime. I think this is (at least halfway) rubbish.

:guitar:

---

### Post by HermanAB on 2011-03-19
# uptime
 03:08:18 up 508 days, 14:14

---

### Post by sydbat on 2011-03-19
WOW! A 4 year old thread threadcromanced. + 1 Internets to gewone for finding this and reviving it.

Also, on (a very old) topic...if you do not count the reboots for kernel upgrades, 3 years.

---

### Post by uRock on 2011-03-19
> **sydbat said:**
> WOW! A 4 year old thread threadcromanced.+1 Thread Closed

---

