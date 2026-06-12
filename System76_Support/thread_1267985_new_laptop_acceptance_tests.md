---
title: "new laptop acceptance tests?"
date: 2009-09-16
forum: System76 Support
---

### Post by tlroche on 2009-09-16
I'm planning to buy a [PanP]("https://system76.authsecure.com/product_info.php?cPath=28&products_id=86"). With a view toward the [System 76 30-Day Limited Money Back Guarantee]("https://system76.authsecure.com/article_info.php?articles_id=15") (see end of linked page), after receipt I'm planning to run a fairly quick acceptance checklist (i.e. can be run in under a day), and either keep or return the PanP. I'd like to know, what items do folks think should be on such a checklist? What's on my checklist so far:

[LIST=1]
[*]Photograph the system OOTB, recording all identifications (e.g. laptop and battery serial#s), checking for flaws.
[*]Scan the shipped manuals (since they're pretty short):
[LIST=1]
[*]"welcome manual": one sheet, has pictures of the keys and ports
[*]"quick start guide": one sheet, has a 3-step startup process, "helpful online resources," and system-restore pointers
[*]"concise user's guide": the usual consumer-electronics multilingual booklet. The English portion is only 30 pages--and they're small pages--much of which is for Windows or functionality I don't use (e.g. 3.75G/HSPA).
[/LIST]
[*]Determine the PanP's version# (4 or 5) and model (A-F--see pp 6, 7, 12 of the "concise user's guide").
[*]Initial boot/smoketest:
[LIST=1]
[*]To shipped system:
[LIST=1]
[*]Just turn the box on, let it boot to Ubuntu. Verify no odd sights, sounds, smells
[*]Check for proprietary drivers: System>Administration>Hardware Drivers. If found, record for later restore (if you're doing that).
[*]Check partition table: e.g. in xterm run ```
$ sudo parted -l

``` Results may be like ```
Model: ATA ST9250410AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      512B    15.0GB  15.0GB  primary   ext3         boot 
 2      15.0GB  250GB   235GB   extended                    
 5      15.0GB  18.9GB  3861MB  logical   linux-swap        
 6      18.9GB  250GB   231GB   logical   ext3              
```
[*]Check mount points: e.g. in xterm run ```
$ mount
``` Results may be like ```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda6 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/you/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=you)
```
[/LIST]
[*]To memtest: boot to memtest and run overnight. (This step need not be done in sequence, just make sure it gets done soonest.) Record cycles ran, verify no errors.
[/LIST]
[*]Restore system from restore DVDs (diskmaking in [this post]("http://ubuntuforums.org/showthread.php?t=1278261"), restore process documented [here]("http://knowledge76.com/index.php/Restoring_Your_System")).
[*]Power/session management tests:
[LIST=1]
[*]Runs on AC with battery detached.
[*]Hibernate works with battery detached.
[*]Suspend/standby works with battery detached.
[*]Install battery, verify system works while charging (with AC attached) and after charge (with AC detached).
[*]Hibernate works with battery (without AC).
[*]Suspend/standby works with battery (without AC).
[*]Suspend/standby works from C-A-D and Fn-F4.
[*]Verify runtime after initial battery charge (while doing one or more of following tests).
[/LIST]
[*]Check displays:
[LIST=1]
[*]Record display resolution in use on default monitor.
[*]Check for [dead pixels]("http://www.gdargaud.net/Hack/DeadPixels.html#LCD") [and] [stuck pixels]("http://en.wikipedia.org/wiki/Defective_pixel#Stuck_versus_dead_pixels") (see post# 12)
[*]Check display resolution using external monitor
[*]Check display resolution using projector
[/LIST]
[*]Check networking:
[LIST=1]
[*]Connect to home wired and wireless networks.
[*]Connect to work from home using VPN.
[*]Connect to work wired and wireless networks (both guest and secure).
[/LIST]
[*]Run Update Manager, or ```
sudo aptitude update ; sudo aptitude -s full-upgrade
```
[*]Install some basic software (e.g. curl, emacs, duplicity, firefox, python, rsync, ssh, wget) if required.
[*]Post update, reverify power/session management tests above (step# 7).
[*]Check emacs performance and keyboard feel.
[*]Check bandwidth curl- or wget-ing MP3s from web to MP3 player.
[*]Verify read from or RW to USB devices (MP3 player, camera, thumbdrives)
[*]rsync or duplicity files to/from DVD, USB drive (from backup of one of my other systems).
[*][Install restricted codecs]("http://knowledge76.com/index.php/Installing_Restricted_Formats").
[*]Check audio:
[LIST=1]
[*]Listen to MP3 through headphones, laptop speakers, external speakers.
[*]Listen to audio stream (e.g. last.fm) through headphones, laptop speakers, external speakers.
[/LIST]
[*]Check video:
[LIST=1]
[*]Watch an online video stream (e.g., archive.org, youtube) on default and external monitors
[*]Get/play video on default and external monitors, e.g.
[LIST=1]
[*][a DivX]("http://www.archive.org/download/TheEmpererJones/TheEmpererJones.avi")
[*][a DVD]("http://www.archive.org/download/Sita_Sings_the_Blues/SITA_SINGS_MOVIE_ONLY.iso")
[*][a MOV]("http://storyofstuff.force.com/download")
[*][an MPEG]("http://www.archive.org/download/his_girl_friday/his_girl_friday_512kb.mp4")
[*][an MP4]("http://www.princeton.edu/WebMedia/media/lectures/20101111_publect_wilczek_pt1.mp4")
[/LIST]
[/LIST]
[*]Check chrome, firefox performance.
[*]Print to home and work printers (after driver installs).
[*]Setup sshd, verify connection from other home and work boxes.
[*]Mount AFS via sshfs.
[*]Record from builtin mic to MP3 (installing, e.g., audacity as necessary)
[*]Record from builtin camera to ??? with ???
[*]Check biometric login (e.g., fingerprint reader) if enabled
[*]TODO: add tests for remaining hardware ports.
[*]ONGOING: battery infant mortality: monitor charge capacity, operating time.
[/LIST]

I'm wondering, is there anything else you made sure to check on your new laptop, or wish you had? Feel free to reply to the forum or directly to me, and TIA, Tom Roche <Tom_Roche@pobox.com>

---

### Post by imhavoc on 2009-09-16
Dude, I don't think Linux is the operating system for you. You should buy a machine from Stark Enterprises or Wayne Industries... or one of the other good comic book firms.

---

### Post by macabrem on 2009-09-16
> **imhavoc said:**
> Dude, I don't think Linux is the operating system for you. You should buy a machine from Stark Enterprises or Wayne Industries... or one of the other good comic book firms.

I shouldn't comment on this - but dude, that's too funny!

---

### Post by jml on 2009-09-16
One comment.  Be sure that you isolate problems that are hardware specific such as keyboard feel, vs. software specific such as playing back "restricted codecs".  For a clean test of the hardware I would rely on  officially supported repositories and applications.  In order to play MP3's, Encrypted DVD's, much streaming video you may need to rely on unofficial repositories like Medibuntu for applications not necessarily supported by either Ubuntu or System 76.

The greater question is if the computer does what you need it to do and only you can answer that.  And, no, I can't think of anything to add.  You might want to consider posting your evaluation to this forum when it's done.  It may be of help to others considering a purchase.

Joe

---

### Post by tlroche on 2009-09-16
> **jml said:**
> Be sure that you isolate problems that are hardware specific such as keyboard feel, vs. software specific such as playing back "restricted codecs". For a clean test of the hardware I would rely on officially supported repositories and applications. In order to play MP3's, Encrypted DVD's, much streaming video you may need to rely on unofficial repositories like Medibuntu

Almost certainly.

> **jml said:**
> for applications not necessarily supported by either Ubuntu or System 76.

Quite likely. However, the latter are functionalities that I

[LIST]
[*](IMHO) reasonably expect. I mean, I can do the above on the xubuntu that I personally (with minimal desktop linux experience) setup, so I would expect a System 76 box could do that as well (though perhaps not Out Of The Box).
[*]want--in fact, I'd probably return the box if it couldn't at least play MP3s.
[/LIST]

> **jml said:**
> You might want to consider posting your evaluation to this forum when it's done.

Will do.

---

### Post by jml on 2009-09-16
Quite likely. However, the latter are functionalities that I

[LIST]
[*](IMHO) reasonably expect. I mean, I can do the above on the xubuntu that I personally (with minimal desktop linux experience) setup, so I would expect a System 76 box could do that as well (though perhaps not Out Of The Box).
[*]want--in fact, I'd probably return the box if it couldn't at least play MP3s.
[/LIST]


Sorry if I was not clear.  about your question.  Yes, As delivered by System 76, my experience with the three computers I have purchased from them, offer all of the functionality that Ubuntu/xbuntu would offer out of the box with a clean install on other generic hardware.  In fact, my experience is that the System 76 computers go one better.  Making sure that all of the hardware on the computer is supported.  3D accelerated graphics, wireless networking, card readers special function keys, etc.  And yes it will play MP3's. You may have to download an app to encode in MP3 format but that is not a big problem.

Joe

Sorry about how I handled your quote, tlroche.  I don't use this function that often.

Joe

---

### Post by thomasaaron on 2009-09-16
```
want--in fact, I'd probably return the box if it couldn't at least play MP3s
```

[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

---

### Post by marshmallow1304 on 2009-09-16
I don't really see the point of most of that.  As long as the hardware is both of good quality and properly supported (I can assure that it is in both counts) and you can already do all of these things in Ubuntu, you're not going to have any problems.

I can understand being concerned about battery life and keyboard feel though.

---

### Post by tlroche on 2009-09-16
> **marshmallow1304 said:**
> you're not going to have any problems.

["trust but verify"]("http://en.wikipedia.org/wiki/Trust,_but_Verify")

---

### Post by marshmallow1304 on 2009-09-16
Fair enough.  Might I also suggest testing with an external monitor (if you have one)?

---

### Post by tlroche on 2009-09-16
> **marshmallow1304 said:**
> Might I also suggest testing with an external monitor (if you have one)?

Indeed--good catch. I definitely want to be able to present/project with this thing.

---

### Post by HotShotDJ on 2009-09-16
I would also check for [dead pixels]("http://www.gdargaud.net/Hack/DeadPixels.html#LCD") (don't confuse with [stuck pixels]("http://en.wikipedia.org/wiki/Defective_pixel#Stuck_versus_dead_pixels") which often can be [fixed]("http://www.jscreenfix.com/basic.php"))

Whatever you do, don't freak out over a few dead pixels.  It is just the nature of the technology.  I've seen some manufacturers offer a zero dead pixel warranty option for several hundred dollars -- basically almost having you pay for a new screen up-front. 6 or more does seem to be the industry standard.  Although, I'll tell you, I have 17 laptops in my lab and every computer on our campus is LCD and I've never seen a dead pixel.  Either they are not as common as the industry leads us to believe, or they are just no big deal when they occur.  I tend to think it is the latter more than the former.

If you have 6 or more dead pixels, you can have the screen replaced:[QUOTE="http://system76.com/article_info.php?articles_id=15"]Following the industry standard, System76 warrants a defective LCD display as having 6 or more bad pixels and will accept delivery of such a system within 30 days from the invoice date for a replacement.[/QUOTE]

---

### Post by tlroche on 2009-09-16
> **HotShotDJ said:**
> check for [dead pixels]("http://www.gdargaud.net/Hack/DeadPixels.html#LCD") [and] [stuck pixels]("http://en.wikipedia.org/wiki/Defective_pixel#Stuck_versus_dead_pixels")

Thanks, I hadn't thought of that. And it's good to know the vocabulary: my girlfriend's ancient Dell recently developed a persistent vertical yellow line on its monitor, which I now know (presumably) to call a column of "stuck pixels."

---

### Post by Eldera on 2009-09-16
Off topic
> my girlfriend's ancient Dell recently developed a persistent vertical yellow line on its monitor, which I now know (presumably) to call a column of "stuck pixels."

We have had some discussion in this forum about how to fix stuck pixels if you are interested:

[thread]1185102[/thread]

[post]7891607[/post]

---

### Post by tgalati4 on 2009-09-17
Run memtest for 30 cycles.  This will probably take overnight.

Use your computer for 30 days doing normal tasks.  Make a note to test all of the ports and hardware (such as bluetooth) during that time.

Your list looks like something they would send on the space shuttle.  In fact System76 should pay you to test their machines that can then be sold as "Hammered by the Validator"

I remember shopping for a miniATX computer and the vendor offered a service to test the motherboard for $12.95.  I thought that was dumb until we received 10 of them and 2 were dead-on-arrival.  So there is a need for an extensive validation suite.

---

### Post by drewbenn on 2009-09-17
Do you plan on checking the fingerprint reader (if so, note that the Panp5 wiki page says you need to run the System76 driver first)?

Do you plan on checking audio input (both the mic port and the internal mic)?  How about the internal video camera?

You didn't mention testing the touchpad, or using an external mouse.  Do you have a bluetooth device to test with the laptop?  You also didn't mention testing the function keys (e.g. Fn-F6 to change volume).

If you'll ever be using the laptop on your lap, you might want to see how warm it gets, on battery power vs. AC and at powerup vs. after a couple hours.  And if you can figure out a way to measure it objectively, I'm sure a lot of readers on these forums would love it if you shared your results :)

> **tlroche said:**
> Restore from restore DVD.

I'm not sure it actually comes with one of those (since it would be the same as the Ubuntu ISO you could download yourself).  You might want to burn yourself an Ubuntu CD ahead of time if you still plan on doing this test.

> **tlroche said:**
> Verify read from or RW to USB devices (MP3 player, camera, thumbdrives)

What is your mp3 player?  I ask because some Sansas (like my Sansa e260) aren't detected when connected (due to a gPhoto bug, of all things).  If you have one I can look up a link to the bug info & (easy) fix.

---

### Post by samalex on 2009-09-17
Hi..

Having my PanP5 for about 6 weeks now I can say it's great, and I believe I've done pretty much 100% of what the original poster had on his list thus far.  You will need to install the restricted codecs as several other repliers suggested to play some streams and formats, but that's a given on any install of Ubuntu.

A few things to note is last week at our LUG meeting I showed a few games to the group and used an external projector through the VGA port, and it was awesome.  The nVidia interface was great and intuitive to get things setup as needed, and given this was my first time to use an external monitor/projector it went flawlessly with mirrored desktop.

The only problem I had was with the battery, but that has been resolved with System76 sending me a new battery that is charging at 100% capacity (original battery was at %82 capacity within the second week).  Battery life is blah (60-90 minutes, 120 tops on a good day), but that's to be expected on a system like this I guess.

You also mentioned printing... one thing that REALLY impressed me was we have an HP PSC 750 printer/scanner and since we upgraded our Mac laptops to Leopard the scanner hasn't worked.  HP doesn't offer a driver for it on OS 10.5 but the printer worked with the stock OSX drivers.  When I connected the printer to my PanP5 within seconds the message popped up saying "HP PSC 750 Detected and Installed" and I was printing and scanning outta the box.  It's even able to detect the toner levels which is nice!  The Print interface is nicer here then it is on Windows or OSX.  As for work printers, we use HP networked printers at work, so just feed in the IP address for jetdirect printing or the SMB print server address and you're ready to go.  If you have a funky network printer you may need to fiddle with drives, but this goes the same way on Windows and OSX as well.

All and all I have no complaints thus far with the laptop, and the few I do have are related to Ubuntu and not System76.  I think you'll be pleased with the laptop.

Take care,

Sam

---

### Post by marshmallow1304 on 2009-09-17
> **samalex said:**
> The nVidia interface was great and intuitive to get things setup as needed, and given this was my first time to use an external monitor/projector it went flawlessly with mirrored desktop.

Really?  I had a completely opposite reaction to the nVidia interface.  It's not nearly as nice as its Windows counterpart (as I remember it).


> **samalex said:**
> The Print interface is nicer here then it is on Windows or OSX.

This one I wholeheartedly agree with.  I'm not sure whether you're talking about Ubuntu's print interface or HPLIP Toolbox, but both are very nice.  I was especially pleased with the HPLIP Toolbox, considering the bloated mess that is its Windows counterpart.

---

### Post by tlroche on 2009-09-18
> **drewbenn said:**
> Do you plan on checking the fingerprint reader (if so, note that the Panp5 wiki page says you need to run the System76 driver first)?

Do you plan on checking audio input (both the mic port and the internal mic)? How about the internal video camera?

You didn't mention testing the touchpad, or using an external mouse. Do you have a bluetooth device to test with the laptop? You also didn't mention testing the function keys (e.g. Fn-F6 to change volume).

If you'll ever be using the laptop on your lap, you might want to see how warm it gets, on battery power vs. AC and at powerup vs. after a couple hours.

All good points--gotta add these to the checklist. Followup questions and points:

[LIST=1]
[*]Definitely gotta test the touchpad. Gotta find that wiki page. If you know that, please post the link.
[*]What is a good app for recording the audio input? e.g. to an MP3.
[*]Definitely gotta test the touchpad, don't have an external mouse.
[*]Definitely gotta test the system function keys.
[*]Good idea about the lap temp! I worked @ IBM while lotsa folks had T30s; these were reputed to neuter males :-) FWIW I'm planning to do all the home-based testing like I am now, with the box in my lap wearing boxers. Will definitely record operating temperature.
[/LIST]

> **drewbenn said:**
> I'm not sure [the PanP] actually comes with [a system restore disk].

Correct: I finally pried the card outta my wallet and made the order, and subsequently got this email:

```

info@system76.com Fri, Sep 18, 2009 at 10:23 AM
> We do [not] supply system restore CD's or DVD's as this can be down
> loaded for free. Please contact System76 support for further
> information on this.
```

which I have.

> **drewbenn said:**
>  What is your mp3 player? I ask because some Sansas (like my Sansa e260) aren't detected when connected (due to a gPhoto bug, of all things).

Indeed I have problems with automounting (i.e. plug the Sansa into the USB port -> Thunar opens /media/disk) my Sansa m250 on xubuntu 9.04 on my TP Z61t:

[LIST=1]
[*]it's usually slow
[*]once detected, it often disconnects (fortunately wget handles that well)
[*]however explicit mounting the Sansa (via /etc/fstab) works pretty well
[/LIST]

> **drewbenn said:**
> If you have [a Sansa] I can look up a link to the bug info & (easy) fix.

Please do, and TIA.

---

### Post by tlroche on 2009-09-18
> **tgalati4 said:**
> Run memtest for 30 cycles.  This will probably take overnight.

Good point, added to [checklist]("http://ubuntuforums.org/showpost.php?p=7958828&postcount=1").

> **tgalati4 said:**
> Make a note to test all of the ports

Good point, gotta figure out how to do that.

> **tgalati4 said:**
> System76 should pay you to test their machines that can then be sold as "Hammered by the Validator"

I'll send them a bill :-) but, really, all I'm trying to do is give it a once-over to ensure I catch anything obvious within the 30-day window, because ...

> **tgalati4 said:**
> there is a need for an extensive validation suite.

IMHO, true that!

---

### Post by tlroche on 2009-09-18
> **samalex said:**
> Having my PanP5 for about 6 weeks now [the] only problem I had was with the battery, but that has been resolved with System76 sending me a new battery that is charging at 100% capacity (original battery was at %82 capacity within the second week).

That's good to know. FWIW I had a similar problem with my TP, and IBM/Lenovo (they were in transition then) were good about replacing that too. Added a note to the [checklist]("http://ubuntuforums.org/showpost.php?p=7958828&postcount=1").

---

### Post by jdb on 2009-09-18
> **tlroche said:**
> [*]What is a good app for recording the audio input? e.g. to an MP3.


I kind of like audacity.

jdb

---

### Post by samalex on 2009-09-18
> **marshmallow1304 said:**
> Really?  I had a completely opposite reaction to the nVidia interface.  It's not nearly as nice as its Windows counterpart (as I remember it).

This one I wholeheartedly agree with.  I'm not sure whether you're talking about Ubuntu's print interface or HPLIP Toolbox, but both are very nice.  I was especially pleased with the HPLIP Toolbox, considering the bloated mess that is its Windows counterpart.

I haven't used the nVidia drivers in Windows so I don't know how they look or work, but on Linux the first time I went in it was obvious what needed to be updated to get both Mirrored Displays and Dual Displays to work.  When I selected Mirrored it even gave me the option to select which part of the screen on my desktop to mirror because the resolutions weren't the same between my laptop and the LCD projector.

As for printing, OSX loads some crappy HP driver that loads in the bottom on the launcher, and that's annoying.  If I'm not using it I don't want to see software running that shows me the status of it.  Linux agrees, which I like :)

Sam

---

### Post by HotShotDJ on 2009-09-18
> **samalex said:**
> The only problem I had was with the battery, but that has been resolved with System76 sending me a new battery that is charging at 100% capacity (original battery was at %82 capacity within the second week).Excellent.  I was wondering how that ultimately worked out.  Did you ever get a chance to check out some of the power saving tweeks regarding the video card that I posted to your original Battery Life thread?  Although, I suppose I'll be able to test them out myself soon enough. :D

---

### Post by drewbenn on 2009-09-18
> **tlroche said:**
> Definitely gotta test the touchpad. Gotta find that wiki page. If you know that, please post the link.

Assuming that's a typo and you meant fingerprint reader, the reference is [http://knowledge76.com/index.php/Panp4/Panp5](http://knowledge76.com/index.php/Panp4/Panp5) . The System76 driver is pretty trivial to install (instructions are in many posts in these forums, like [http://ubuntuforums.org/showthread.php?t=962793](http://ubuntuforums.org/showthread.php?t=962793)).

> **tlroche said:**
> What is a good app for recording the audio input? e.g. to an MP3.

I've only used Audacity, and only in a very limited fashion: I don't know it well enough to help with what settings would need to be changed.  Audacity is more for in-depth audio editing, though, and I'm sure there's a simpler program for testing audio.
If you do use Audacity, there's an issue with using it to record directly to OGG, but I can't remember if that's only on EeePCs or if it's a general issue. You shouldn't have any problems recording to MP3 with it (provided you have installed restricted drivers support already), though.

> **tlroche said:**
> ```

info@system76.com Fri, Sep 18, 2009 at 10:23 AM
> We do [not] supply system restore CD's or DVD's as this can be down
> loaded for free. Please contact System76 support for further
> information on this.
```

which I have.

I just realized, I may have misunderstood what you meant by a restore DVD. I assumed you were going to do a fresh install of Ubuntu. Did you have something else in mind?


> **tlroche said:**
> Indeed I have problems with automounting (i.e. plug the Sansa into the USB port -> Thunar opens /media/disk) my Sansa m250 on xubuntu 9.04 on my TP Z61t:

Your symptoms sound different from what I've experienced.  But here is the link (if it is really related to gPhoto, you didn't have gPhoto on your Xubuntu box, and the m series is affected, you might suddenly see more problems when you start using Ubuntu): [https://bugs.launchpad.net/ubuntu/+bug/345916](https://bugs.launchpad.net/ubuntu/+bug/345916) .  The fix is basically to remove the sections that list your player from /usr/share/hal/fdi/preprobe/10osvendor/20-libgphoto2.fdi .

---

### Post by tlroche on 2009-09-21
> **drewbenn said:**
> I've only used Audacity, and only in a very limited fashion: I don't know it well enough to help with what settings would need to be changed.  Audacity is more for in-depth audio editing, though, and I'm sure there's a simpler program for testing audio.

That's my impression, so I put up [a separate thread]("http://ubuntuforums.org/showthread.php?t=1271730") on that.

> **drewbenn said:**
> I may have misunderstood what you meant by a restore DVD. I assumed you were going to do a fresh install of Ubuntu. Did you have something else in mind?

"[Restoring Your [Laptop or Desktop]]("http://knowledge76.com/index.php/Restoring_Your_System")": fresh install of Ubuntu is the first part (probably the largest part) of that.

---

