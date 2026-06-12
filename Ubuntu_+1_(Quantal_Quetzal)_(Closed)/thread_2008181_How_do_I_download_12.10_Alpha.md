---
title: "How do I download 12.10 Alpha?"
date: 2012-06-22
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by sam-c on 2012-06-22
How do I download 12.10 Alpha?

---

### Post by nothingspecial on 2012-06-22
You acn get it from here [http://cdimage.ubuntu.com/releases/quantal/alpha-1/](http://cdimage.ubuntu.com/releases/quantal/alpha-1/)

---

### Post by codemaniac on 2012-06-22
> **sam-c said:**
> How do I download 12.10 Alpha?

Please refer the below link .

[https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Alpha1](https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Alpha1)

---

### Post by jppr on 2012-06-22
> **sam-c said:**
> How do I download 12.10 Alpha?

You can download daily-live... [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)
that is fresh and latest verion

---

### Post by VinDSL on 2012-06-22
Not to mention: Um... But, wait.  The question was, HOW do I download UbuQQ?

Maybe, the OP needs download instructions...

Personally, I download the .iso image using the DTA (DownThemAll) extension in Firefox.

Alternately, if I'm doing a lot of .iso testing, I update my local image daily using ZSync, from CLI.

Then, I burn the .iso image to a bootable USB thumb drive using "Startup Disk Creator".

Alternately, you can burn the image to a CD/DVD, but the results are often flaky, in my experience.

HOW you get a USB thumb drive to boot is left as an exercise in the second-order coefficient. LoL!  :D

All depends on the motherboard vendor and BIOS you're running...

---

### Post by jbicha on 2012-06-22
Zsync instructions are at [https://help.ubuntu.com/community/ZsyncCdImage](https://help.ubuntu.com/community/ZsyncCdImage)

---

### Post by kevpan815 on 2012-06-22
> **VinDSL said:**
> Not to mention: Um... But, wait.  The question was, HOW do I download UbuQQ?

Maybe, the OP needs download instructions...

Personally, I download the .iso image using the DTA (DownThemAll) extension in Firefox.

Alternately, if I'm doing a lot of .iso testing, I update my local image daily using ZSync, from CLI.

Then, I burn the .iso image to a bootable USB thumb drive using "Startup Disk Creator".

Alternately, you can burn the image to a CD/DVD, but the results are often flaky, in my experience.

HOW you get a USB thumb drive to boot is left as an exercise in the second-order coefficient. LoL!  :D

All depends on the motherboard vendor and BIOS you're running...

I have found that I have very good luck Burning Disks with my Mid Year 2010 Mac Mini's Super Drive, Just FYI. I also have very good luck changing them back to a .iso file (Using Copy a DVD in Brasero) as well. Just FYI.

---

### Post by VinDSL on 2012-06-23
> **kevpan815 said:**
> I have found that I have very good luck Burning Disks with my Mid Year 2010 Mac Mini's Super Drive, Just FYI. I also have very good luck changing them back to a .iso file (Using Copy a DVD in Brasero) as well. Just FYI.
You are most certainly blessed!

In my experience:  

[LIST]
[*]CD/DVD burners are obnoxiously quirky.
[*]All media (regardless of price/quality) have defects.
[*]Often, discs written on burner-a cannot be read by burner-b.
[/LIST]
I've had MUCH better luck using USB thumb drives.

Just saying...  ;)

---

### Post by ventrical on 2012-06-23
I have an old Phillips DVD RAM disk burner which has been super reliable ,but, as VinDsl pointed out , USB s are much more reliable and faster . No muss, no fuss.

---

### Post by jerrylamos on 2012-06-23
Actually I prefer booting the .iso file direct.  I zsync it into the first folder of a partition I call Archive where I have lots of stuff, name doesn't matter, then do as follows.  

The first 5 lines should be there already, just add the rest.  In my case the .iso file is on /dev/sda5
```

sudo gedit /etc/grub.d/40_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
menuentry "Quantal sda5" {
set isofile="/quantal-desktop-amd64.iso"
loopback loop (hd0,5)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
save
exit
sudo update-grub
sudo grub-install /dev/sda       < may not be necessary 

Reboot, select the entry above
select "Try Ubuntu"
open a terminal window Ctrl-Alt-t
df           < to see where the /isodevice is, /dev/sda5 in this case
sudo umount -r -l /dev/sda5

```

Then check out the live ubuntu.  Before doing an install, make sure there aren't any other disks mounted by doing a df and a sudo umount /dev/sda1 or whatever.

This is booting the .iso off the hard drive direct, faster than USB and CD/DVD.  

Now this is also faster since it omits the startup disk creation.  I recently ran into a complication installing onto a USB hard drive from a USB flash memory with a remote USB keyboard and USB mouse.  Install just slowed down and never got anywhere.  I presume there were so many USB devices install got confused.

Anyway, booting the .iso direct, I can check out bugs on the daily live every day I have time, and install when it seems worthwhile.  Do note an install changes the grub menu so after booting the 40_custom needs copied in and sudo update-grub. 

Have fun,

Jerry

p.s. over the years I've acquired a mediocre working knowledge of Ubuntu linux from testing, and this is one of the time savers I use.

---

### Post by jerrylamos on 2012-06-25
> **bkerensa said:**
> If you grab the torrent file you can download it much faster and save Canonical money which they can then invest into other things :)
Here, torrent is slower.  Much.  However, once downloaded, zsync which only downloads changes not the whole file is a whole lot faster and less load on the servers for updates.  

Only have to do one download per development cycle then zsync for the next few months.

Jerry

---

### Post by VinDSL on 2012-06-25
> **bkerensa said:**
> If you grab the torrent file you can download it much faster and save Canonical money [...]

> **jerrylamos said:**
> [...] zsync which only downloads changes not the whole file is a whole lot faster and less load on the servers [...]
You crystallized my thoughts exactly, Jerry!

Plus, I'm too paranoid to use torrents.  :)

I *know* downloading Ubu is perfectly legal, but why shine a light on yourself?!?!?

Extra credit reading:  [https://en.wikipedia.org/wiki/Legal_issues_with_BitTorrent](https://en.wikipedia.org/wiki/Legal_issues_with_BitTorrent)

---

### Post by pressureman on 2012-06-25
> **jerrylamos said:**
> Only have to do one download per development cycle then zsync for the next few months.

You don't even have to download the whole file at the start of a new development cycle. You can simply tell zsync to use a specific input file as the seed, eg.

```

zsync -i ubuntu-12.04-alternate-amd64.iso http://cdimage.ubuntu.com/daily/current/quantal-alternate-amd64.iso.zsync

```

At the very beginning of the development cycle, the first daily images are probably a good 80-90% identical to the final release of the previous cycle.

> **VinDSL said:**
> Plus, I'm too paranoid to use torrents.  :)

I *know* downloading Ubu is perfectly legal, but why shine a light on yourself?!?!?

If that's your attitude, then you've already let Big Brother win, and it's a slippery downhill slope to complete censorship of your online activities.

---

### Post by philinux on 2012-06-25
> **VinDSL said:**
> You crystallized my thoughts exactly, Jerry!

Plus, I'm too paranoid to use torrents.  :)

I *know* downloading Ubu is perfectly legal, but why shine a light on yourself?!?!?

Extra credit reading:  [https://en.wikipedia.org/wiki/Legal_issues_with_BitTorrent](https://en.wikipedia.org/wiki/Legal_issues_with_BitTorrent)

/me uses Deluge and encryption for what it's worth these days.

---

### Post by VinDSL on 2012-06-25
> **pressureman said:**
> If that's your attitude, then you've already let Big Brother win, and it's a slippery downhill slope to complete censorship of your online activities.
Yet, we all use nicks, and don't think a thing about it, yes?!?!?

LoL! I always felt funny replying to "Little Red Riding Hood", but...

You've got ppl that are sitting on routers, on the "backbone of the web", waiting for suspicious activity to flow across their network, so they can report you, and collect a reward.  And, that's a fact, not paranoia.

One conspicuous act can cause you a world of hurt...

---

### Post by pressureman on 2012-06-25
> **VinDSL said:**
> Yet, we all use nicks, and don't think a thing about it, yes?!?!?

I use my real name in plenty of places on the web - on Google+, on Facebook, on LinkedIn, and you can find it in all of the code that I've contributed to various open source projects. If people want to be credited for work that they've contributed to some community, I find it best to use real names - especially if it could potentially lead to future employment. That said, I don't consider Ubuntu Forums especially important to the advancement of my career, and frankly it's just not a priority for me to advertise my real name here.

> **VinDSL said:**
> You've got ppl that are sitting on routers, on the "backbone of the web", waiting for suspicious activity to flow across their network, so they can report you, and collect a reward.  And, that's a fact, not paranoia.

One conspicuous act can cause you a world of hurt...

I'm afraid that does sound like paranoia to me. I've worked for carriers and service providers in the past, and if by "backbone of the web" you mean tier 1 networks, I can tell you that they handle such ridonculous amounts of traffic, that deep packet inspection is impossible. As for "reporting you", or collecting rewards (from whom?), that would be financially insignificant compared to their core business of moving packets from A to B. Tier 1 networks are all about bulk IP transit from one network to another. They have nothing to do with end users.

Some tier 3 networks (eg. ISPs) may do a certain amount of packet inspection, but usually only if they are leaned on by government or law enforcement agencies. Again, their core business is simply moving packets, and anything that impedes the flow of traffic obviously reduces the efficiency of their network, and ultimately customer satisfaction. Packet inspection and logging of user activities actually requires considerable investment from ISPs, which is why many of them avoid it where possible.

Anyway.... we digress.

---

### Post by kansasnoob on 2012-06-25
> **jbicha said:**
> Zsync instructions are at [https://help.ubuntu.com/community/ZsyncCdImage](https://help.ubuntu.com/community/ZsyncCdImage)

+1 from me ;)

I have a couple of dumb questions though, for anyone.

#1: Looking at the posted link:

[https://help.ubuntu.com/community/ZsyncCdImage#Acquiring_the_ISO](https://help.ubuntu.com/community/ZsyncCdImage#Acquiring_the_ISO)

Why in the world would it say:

> **To download a stable iso image is best to use the torrent file if you can. **

#2: I'd think the torrents listed on Ubuntu's own site, eg;

[http://cdimage.ubuntu.com/releases/precise/release/](http://cdimage.ubuntu.com/releases/precise/release/)

Are just as safe as the zsync or jigdo images, eh :confused:

So, if those two assumptions are true wouldn't it be best to amend that wiki page to say:

**To download a stable iso image is best to use the [COLOR="Red"]official[/COLOR] torrent file if you can. **

Just my mind running out of control again :D

I don't trust the accuracy of my own judgment well enough to edit or create a wiki page.

---

### Post by VinDSL on 2012-06-25
American Idiom:

> If you fly with the crows, you get shot with the crows

What does If you fly with the crows, you get shot with the crows mean?> If you wish to be associated with a particular high risk and/or high profile situation and benefit from the rewards of that association, you have to accept the consequences if things go wrong - you cannot dissociate yourself.
SOURCE: [http://www.americanidioms.net/If-you-fly-with-the-crows%2C-you-get-shot-with-the-crows](http://www.americanidioms.net/If-you-fly-with-the-crows%2C-you-get-shot-with-the-crows)

> **pressureman said:**
> Anyway.... we digress.
True... 

Let's stop now, before we get an infraction (more paranoia)  ;)

---

### Post by jerrylamos on 2012-06-25
> **pressureman said:**
> You don't even have to download the whole file at the start of a new development cycle. You can simply tell zsync to use a specific input file as the seedThanks for the hint!  Let me give it a whirl on a different quantal version.

Thanks, Jerry

---

### Post by cariboo on 2012-06-25
> **kansasnoob said:**
> +1 from me ;)

I have a couple of dumb questions though, for anyone.

#1: Looking at the posted link:

[https://help.ubuntu.com/community/ZsyncCdImage#Acquiring_the_ISO](https://help.ubuntu.com/community/ZsyncCdImage#Acquiring_the_ISO)

Why in the world would it say:



#2: I'd think the torrents listed on Ubuntu's own site, eg;

[http://cdimage.ubuntu.com/releases/precise/release/](http://cdimage.ubuntu.com/releases/precise/release/)

Are just as safe as the zsync or jigdo images, eh :confused:

So, if those two assumptions are true wouldn't it be best to amend that wiki page to say:

**To download a stable iso image is best to use the [COLOR="Red"]official[/COLOR] torrent file if you can. **

Just my mind running out of control again :D

I don't trust the accuracy of my own judgment well enough to edit or create a wiki page.

I agree with you, about the torrent comment, and have removed it. It looks more like it is someone's personal opinion, rather than an accurate statement.

---

### Post by cpatrick08 on 2012-06-26
> **jerrylamos said:**
> Thanks for the hint!  Let me give it a whirl on a different quantal version.

Thanks, Jerry
just remember to change the ubuntu code name each release cycle this time it is precise to quantal

---

### Post by ventrical on 2012-06-26
> **VinDSL said:**
> You crystallized my thoughts exactly, Jerry!

Plus, I'm too paranoid to use torrents.  :)

I *know* downloading Ubu is perfectly legal, but why shine a light on yourself?!?!?

Extra credit reading:  [https://en.wikipedia.org/wiki/Legal_issues_with_BitTorrent](https://en.wikipedia.org/wiki/Legal_issues_with_BitTorrent)


Same here Vin.   Only used torrents a few times with Windows XP. However, some will swear by torrents. Me ? I swear at them :) lol

---

