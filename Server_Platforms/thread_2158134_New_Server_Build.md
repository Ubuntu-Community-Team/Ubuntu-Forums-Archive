---
title: "New Server Build"
date: 2013-06-28
forum: Server Platforms
---

### Post by samkarpluk on 2013-06-28
I'm building my own server (well, a local chop-shop is assembling it for me). Here's what I'm getting:

Case: [Fractal Design 340]("http://www.fractal-design.com/?view=product&prod=94")
CPU: Intel Core i3 3220
Motherboard: Asus P8H77
Memory: 8 GB DDR3
PSU: Corsair CX Series CX430
Hard-drives:
[LIST]
[*]OS - Intel 520 120 GB SSD
[*]Storage - 3 2TB WD Red
[/LIST]

I'll be putting 12.04 on it. Servers: openssh, samba, lamp, plex, squeezecenter (Logitech LMS), probably missing something but those are the highlights.

Use case: backups, media streaming, test box for web projects.

I have a mixed network, windows, mac, android. This will be a stretch for me. I'll probably be a frequent poster on this (and other forums). We'll see. 

Wish me luck!

---

### Post by ally_uk on 2013-06-28
Good Luck you should document everything you do I would be interested in learning more :) and it would be very beneficial for all noobz out there :)

---

### Post by rubylaser on 2013-06-28
Good Luck! Luckily, none of these things are super difficult to setup.  Just google "Ubuntu 12.04 plexmediaserver", "Ubuntu 12.04 afp", etc. :)

---

### Post by samkarpluk on 2013-07-07
> **rubylaser said:**
> Good Luck! Luckily, none of these things are super difficult to setup.  Just google "Ubuntu 12.04 plexmediaserver", "Ubuntu 12.04 afp", etc. :)

Things went pretty well. I have accomplished most of what I set out to do over the past couple of days. 

Friday night I booted the new machine from a USB stick and installed the OS on the SSD. I also set the raid up and let it build the array. That process took about 4 hours. I went to bed.

Saturday morning I installed Samba, set up four shares, and moved my music into the Music folder. I then installed the Logitech Media Server and configured it with the location of my media. It's great to get my music back!

Then I moved over my movies and tv shows and photos onto the shares for these and set up the Plex Media Server.

Today I installed afp and set up a Time Machine share. I'm running my first time machine backup to the server share as I write this. That was the last thing I wanted to get done this weekend. Here's what it looks like, in situ. It is remarkably quiet, which is awesome.

[ATTACH=CONFIG]244492[/ATTACH]

---

### Post by rubylaser on 2013-07-07
Congratulations! That looks very nice, and it sounds like you have a lot of things working already :) 

Did you use mdadm/LVM/SnapRAID/ZFS on Linux/Hardware for your RAID?  Also, what have you implemented as backup mechanism for this box?  Here are a bunch of other things to consider...

[LIST=1]
[*]Have you setup smartmontools to monitor your disks?
[*]Have you considered a UPS to safely shutdown your box in the event of a power outage?
[*]Have you setup email so that you will receive alerts if things go wrong?
[*]Have you setup your disks to spindown when they are idle to conserve power?
[*]Do you have any questions, now that you have ventured down the Linux server road?
[/LIST]

---

### Post by grunge09 on 2013-07-07
Is there a real reason to use something like Plex Server, when you can setup Samba to share music and movie folders and use the players on the client boxes to play the material.  (i.e. Windo Media Player on XP or totem on Ubuntu).

---

### Post by rubylaser on 2013-07-07
> **grunge09 said:**
> Is there a real reason to use something like Plex Server, when you can setup Samba to share music and movie folders and use the players on the client boxes to play the material.  (i.e. Windo Media Player on XP or totem on Ubuntu).

Sure, one example is that Plex allows you to stream remotely to any Android or IOS device with the Plex App installed.  It automatically transcodes and provides it in the correct format for the device.  Plus, it provides a much nicer interface to view and select your movies, tv shows, music, or photos than Totem or Windows Media Player does.

---

### Post by samkarpluk on 2013-07-08
> **grunge09 said:**
> Is there a real reason to use something like Plex Server, when you can setup Samba to share music and movie folders and use the players on the client boxes to play the material.  (i.e. Windo Media Player on XP or totem on Ubuntu).

My purpose was to make this content available on my tv. I have a samsung and there is a plex client app available for it. Probably the most difficult thing about this process was navigating the abominable interface of the Samsung "Smart" TV to actually get the client installed. What a disaster that UI is.

---

### Post by CharlesA on 2013-07-08
> **rubylaser said:**
> Congratulations! That looks very nice, and it sounds like you have a lot of things working already :) 

Did you use mdadm/LVM/SnapRAID/ZFS on Linux/Hardware for your RAID?  Also, what have you implemented as backup mechanism for this box?  Here are a bunch of other things to consider...

[LIST=1]
[*]Have you setup smartmontools to monitor your disks?
[*]Have you considered a UPS to safely shutdown your box in the event of a power outage?
[*]Have you setup email so that you will receive alerts if things go wrong?
[*]Have you setup your disks to spindown when they are idle to conserve power?
[*]Do you have any questions, now that you have ventured down the Linux server road?
[/LIST]

Huge +1 to all 5 of those points.

> **samkarpluk said:**
> My purpose was to make this content available on my tv. I have a samsung and there is a plex client app available for it. Probably the most difficult thing about this process was navigating the abominable interface of the Samsung "Smart" TV to actually get the client installed. What a disaster that UI is.

The build looks awesome and makes me a bit jealous cuz my server is in a tower. :p

---

### Post by samkarpluk on 2013-07-08
> **rubylaser said:**
> Congratulations! That looks very nice, and it sounds like you have a lot of things working already :) 

Did you use mdadm/LVM/SnapRAID/ZFS on Linux/Hardware for your RAID?  Also, what have you implemented as backup mechanism for this box?  Here are a bunch of other things to consider...

[LIST=1]
[*]Have you setup smartmontools to monitor your disks?
[*]Have you considered a UPS to safely shutdown your box in the event of a power outage?
[*]Have you setup email so that you will receive alerts if things go wrong?
[*]Have you setup your disks to spindown when they are idle to conserve power?
[*]Do you have any questions, now that you have ventured down the Linux server road?
[/LIST]


Hi rubylaser. To answer some of your questions here:

I used mdadm for the raid 5 implementation.

Backup mechanism? We don't need no stinkin' backups do we?...

Just kidding. I have some old internal drives sitting around (500 GB and 1 TB) as well as a 1 TB WD My Book. I was thinking of getting an enclosure for my spares and rotate a backup (i.e. leave one at work). I have under 500 GB of user data (music and photos are the most important items here). I do need to get an offsite backup solution in place for this data. I hooked the WD My Book up yesterday and it wasn't recognized at all. Didn't even power up. Not sure what the deal is there. 

Smartmon tools, not yet. It's on the list.

UPS: haven't thought about this but it would be a good idea. Recommendations?

Email Notifications: I have set this up but I have to look into a schedule for this, i.e. cron.

Disk spin down? No. How is this accomplished?

Questions? I have many. There are a few above.

---

### Post by CharlesA on 2013-07-08
> **samkarpluk said:**
> Hi rubylaser. To answer some of your questions here:

I used mdadm for the raid 5 implementation.

RAID5 should be fine for only 3 disks. If you add more, I would say go with RAID6, even though you lose two disks for parity vs one disk with RAID5.

> Backup mechanism? We don't need no stinkin' backups do we?...

Just kidding. I have some old internal drives sitting around (500 GB and 1 TB) as well as a 1 TB WD My Book. I was thinking of getting an enclosure for my spares and rotate a backup (i.e. leave one at work). I have under 500 GB of user data (music and photos are the most important items here). I do need to get an offsite backup solution in place for this data. I hooked the WD My Book up yesterday and it wasn't recognized at all. Didn't even power up. Not sure what the deal is there. 

I have been using Seagate external drives for backups via USB3 and they have worked fine so far. My backup scheme (?) is:

Daily incremental via hard links + rsync.
Monthly incremental via hard links + rsync
Monthly full backups via rsync
Monthly "offsite" backups via rsync (They don't really go offsite any more. I've thought about storing them at work, but I don't trust people not to go "Oh look a hard drive!" and use it when Windows says it is unformatted...).
CrashPlan which backs up files every 15 minutes to "the cloud" - The plan I have isn't free, but the backups are encrypted with a strong key, so I don't think think security is a problem. That solution depends on your internet connection and how much you trust the party who is storing your backups.

As far as the WD MyBook not powering up, it could be a bad power block, or the drive could be dead. Do you have a spare power brick that has the same volts/amps around that you could try?

> Smartmon tools, not yet. It's on the list.

Good. :) You might want to read this [thread]("http://ubuntuforums.org/showthread.php?t=2157352"). It's one of mine, and kinda shows some of the issues SMART has, but don't dismiss SMART completely.

> UPS: haven't thought about this but it would be a good idea. Recommendations?

I use APC UPSes mostly cuz I trust them (and they are dead simple to configure apcupsd for). I know some people who use Cyberpower and say they work fine, and if I remember right they do have management software for *nix.

I just prefer APC but I think that is mostly due to brand recognition.

> Email Notifications: I have set this up but I have to look into a schedule for this, i.e. cron.

Cron works wonders. :) I use it to run the scripts I have written up. Makes getting notifications very easy.

> Disk spin down? No. How is this accomplished?

Check our rubylaser's blog: [http://zackreed.me/](http://zackreed.me/) There are a ton of howtos there. ;)

---

### Post by rubylaser on 2013-07-08
> **samkarpluk said:**
> Hi rubylaser. To answer some of your questions here:

I used mdadm for the raid 5 implementation.

Backup mechanism? We don't need no stinkin' backups do we?...

Just kidding. I have some old internal drives sitting around (500 GB and 1 TB) as well as a 1 TB WD My Book. I was thinking of getting an enclosure for my spares and rotate a backup (i.e. leave one at work). I have under 500 GB of user data (music and photos are the most important items here). I do need to get an offsite backup solution in place for this data. I hooked the WD My Book up yesterday and it wasn't recognized at all. Didn't even power up. Not sure what the deal is there. 

Smartmon tools, not yet. It's on the list.

UPS: haven't thought about this but it would be a good idea. Recommendations?

Email Notifications: I have set this up but I have to look into a schedule for this, i.e. cron.

Disk spin down? No. How is this accomplished?

Questions? I have many. There are a few above.
**Edit:** Charles got in ahead of me, but I'll leave this for my thoughts.

mdadm will work great, and you do want backups :)  I backup my really important stuff in a few places
[LIST=1]
[*]I have (2) encrypted hard drives that I backup two and rotate to work and my parent's house monthly.
[*]I do a nightly rsync to my colocated fileserver at the datacenter.
[*]I also do a incremental tar backup to Amazon Glacier (this costs less than $2/month)
[/LIST]

I cover all of the rest of things things in tutorials that I have on my site, for example, [smartmontools]("http://zackreed.me/articles/45-how-do-i-know-if-my-hard-drive-is-failing").

In regards to a UPS, there are lots of good brands.  Personally, I use APC at home.  They are very well supported by both apcupsd and NUT.  Here are a few [UPS tutorials]("http://zackreed.me/articles?tag_id=25") I have on my site.

For email, I typically just setup [ssmtp and use my Gmail account]("http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp") to send system emails from home. This will also allow mdadm to send you emails if your array is degraded. This is the most common point of failure for most new mdadm users.  They don't set up email alerts, and never know that a disk has failed until the second disk fails and their data is lost.

Finally, here's how I [spindown hard drives]("http://zackreed.me/articles/60-spin-down-idle-hard-disks") (the disks do have to support the Advanced Power Management for this to work).

---

### Post by CharlesA on 2013-07-08
> **rubylaser said:**
> For email, I typically just setup [ssmtp and use my Gmail account]("http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp") to send system emails from home. This will also allow mdadm to send you emails if your array is degraded. This is the most common point of failure for most new mdadm users.  They don't set up email alerts, and never know that a disk has failed until the second disk fails and their data is lost.

I use a similar setup for my emails at home. The only difference is I use postfix to send to gmail via smarthost relay.

I really should write up a howto on it for Ubuntu/Debian, but I haven't bothered (yet) >.>

I do have a howto for it on CentOS/Fedora though, so that might help even if the commands are different (and the location of smtp_tls_CAfile is different):
[http://charlesa.net/tutorials/centos/postfix-as-gmail-relay-centos.php](http://charlesa.net/tutorials/centos/postfix-as-gmail-relay-centos.php)

---

### Post by ally_uk on 2013-07-10
Fantastic Thread congrats on getting your server up and running looks like you have done a good job :) what were some of the tutorials / guides you used I am interested in learning more not really sure where to start.

---

### Post by samkarpluk on 2013-07-10
> **ally_uk said:**
> Fantastic Thread congrats on getting your server up and running looks like you have done a good job :) what were some of the tutorials / guides you used I am interested in learning more not really sure where to start.

I did a lot of reading prior to doing my initial install. Plus I did a couple of test installs, first on a virtual box and then on an old laptop I had kicking around (a really old laptop).

However, here are some of the tutorials I followed:

Raid (mdadm):
[LIST]
[*][http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm](http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm)
[*][http://www.tcpdump.com/kb/os/linux/linux-raid-how-to/intro.html](http://www.tcpdump.com/kb/os/linux/linux-raid-how-to/intro.html)
[/LIST]

Samba:

[LIST]
[*][https://help.ubuntu.com/lts/serverguide/samba-fileserver.html](https://help.ubuntu.com/lts/serverguide/samba-fileserver.html)
[/LIST]

AFP:
[LIST]
[*][http://missingreadme.wordpress.com/2010/05/08/how-to-set-up-afp-filesharing-on-ubuntu/](http://missingreadme.wordpress.com/2010/05/08/how-to-set-up-afp-filesharing-on-ubuntu/)
[/LIST]

Plex:

[LIST]
[*][http://forums.plexapp.com/index.php/topic/26727-how-to-plex-media-server-on-ubuntu/](http://forums.plexapp.com/index.php/topic/26727-how-to-plex-media-server-on-ubuntu/)
[/LIST]

Logitech Media Server:
[LIST]
[*][http://www.havetheknowhow.com/Install-the-software/Install-Squeezebox-server.html](http://www.havetheknowhow.com/Install-the-software/Install-Squeezebox-server.html)
[/LIST]

---

### Post by 2Stoned on 2013-07-10
That Fractal Design case looks nice and sleek.

---

### Post by samkarpluk on 2013-07-10
> **2Stoned said:**
> That Fractal Design case looks nice and sleek.

I'm very pleased with it. It's quiet, has 2 USB 3 ports on the front for easy access, and a small footprint. Not sure about the power draw of my setup. I will have to test that at some point. I do plan on looking at spinning down the raid drives as per some of the comments at the top of this thread.

---

### Post by 2Stoned on 2013-07-10
> **samkarpluk said:**
> I'm very pleased with it.

I would be too :cool:  How much did it cost if i may ask?

---

### Post by samkarpluk on 2013-07-10
> **2Stoned said:**
> I would be too :cool:  How much did it cost if i may ask?

The case itself was $90.00 Canadian.

My build was 1000.00. That was all in (see original post for specs) and included assembly and 1 year warranty.

---

### Post by 2Stoned on 2013-07-10
> **samkarpluk said:**
> The case itself was $90.00 Canadian.

My build was 1000.00. That was all in (see original post for specs) and included assembly and 1 year warranty.

$90 canadian dollars is around €67 ;) I might order one as well..

---

