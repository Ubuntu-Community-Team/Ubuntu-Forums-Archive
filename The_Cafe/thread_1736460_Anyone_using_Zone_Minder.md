---
title: "Anyone using Zone Minder?"
date: 2011-04-22
forum: The Cafe
---

### Post by samalex on 2011-04-22
We live in a fairly quiet neighborhood, but now that we're getting a Neighborhood Watch going I'm starting to hear all sorts of problems people have had lately which has me kinda freaked.  We already have a security system, but I'm looking at building a camera system to monitor the outside of our house.

Of course my first place to look was the Open Source community for software, and as expected there's an awesome package called Zone Minder that has SO many bells and whistles.  I'm just curious, does anyone use this?  If so what type of setup do you have?  I might download it to my laptop and run some IP software on my DroidX to test it.  I'll have to build a box and of course get some cameras to do it prime time, but anyone have experience with it?

Thanks --

Sam

---

### Post by Artemis3 on 2011-04-22
I do, and if you can instead get a stand alone pvr, you'll be done in no time.

Zoneminder is pain. Its hard to make it work, unfriendly and buggy, expect weeks or even months to have a stable working config. I do have a cron script to restart zoneminder every 6 hours, else it crashes (could be in a day, or a couple of weeks) causing a kernel panic; just to give you an idea...

Also analog cameras are not worth it, you will need a lot of cpu power (unless using a network digitizer), and finding the (compatible) multi input capture card is difficult, plus you need to run both power and coax to each of them. NOT nice.

Get digital (network) cameras with lots of IR leds for night viewing (or the other night vision thing), and a standalone PVR OR a Zoneminder/pc if you can take the stress of setting it up. Domes are best to resist vandalism, put them out of reach!

BTW: Firefox and Zoneminder don't get along. Have Opera or Chromium around.

---

### Post by tgalati4 on 2011-04-22
Zoneminder is fiddly to set up, but once it's set up, I have found it to be reliable.  Because it is scanning analog cameras, it can do things that IP cameras can't, image motion detection.  With Zoneminder, you can set a region of your field-of-view (say the driveway in your front yard) and only record activity when changes occur in that area.

For a basic system, you would need a PCI card that has a 4-port analog input.  Check the zoneminder forums for hardware recommendations.  Security PVR's are convenient, but then you have to review the captures.  With Zoneminder, only captures that you care about are recorded (say a gate opening) rather than a cat walking across the fence.

---

### Post by wirepuller134 on 2011-04-22
We have several zoneminder 1.23 and 1.24 systems up and running at this time.  It's not that hard to setup and once familiar with the software is quite easy to configure.  We built our own image that we use, based off Ubuntu.  There are several preconfigured images listed on the Zoneminder forums.  I think 1.23 is based off Mandriva.  One of the 1.24 images is based off Ubuntu(not sure if it's still available).  The other is done using Arch.  They are listed in the Zoneminder distributions section of the forums, with a lot of information to set them up.

Our systems use 1 or 2 of the following cards (depending on how many analog cameras are needed and tower/server preferred by customer) PV-155, PV-183, or PV-981  capture cards.  We prefer to use IBM servers.  Motion detection takes quite a bit of resources if using Ip cameras, so that has to be considered when selecting the tower/server.  

  On a side note though, Bluecherry has developed their own capture cards and software based on Ubuntu that does a very good job and we highly recommend it as well.  They also give excellent support as well for their hardware/software.  They also sell Zoneminder supported hardware.

---

### Post by oregonbob on 2011-04-25
I found a downloadable ISO of a complete zoneminder install and config on Ubuntu 10.04. Zoneminder version is latest 1.24.3. So far it looks good and the creator already did all the install work. All you have to do is plug in your cameras and go.

I made a virtualbox appliance from that ISO. I may make that downloadable too soon. The link where I got the ISO is:
More Info: [http://www.awdmesh.com/zoneminder-installation-dvd/](http://www.awdmesh.com/zoneminder-installation-dvd/)

I read about this preconfigured ISO on the zoneminder forum: [http://www.zoneminder.com/forums/viewtopic.php?t=12915](http://www.zoneminder.com/forums/viewtopic.php?t=12915)

It sure beats installing zoneminder by hand.

UPDATE: Maybe I spoke too soon as now zoneminder stalls and won't run.

---

### Post by dellsweig on 2012-12-10
Ok - been using ZM for a while on Ubunu 12.1 - kernel3.5.0.19 with no issues.

Today I updated via update center to 3.5.0.20 and can no longer start zoneminder - I get the following:

root@river:/etc/init.d# ./zoneminder start
Starting ZoneMinder: Bareword "ZM_PATH_LOGS" not allowed while "strict subs" in use at /usr/share/perl5/ZoneMinder/Logger.pm line 153.
BEGIN not safe after errors--compilation aborted at /usr/share/perl5/ZoneMinder/Logger.pm line 168.
Compilation failed in require at /usr/share/perl5/ZoneMinder.pm line 34.
BEGIN failed--compilation aborted at /usr/share/perl5/ZoneMinder.pm line 34.
Compilation failed in require at /usr/bin/zmpkg.pl line 37.
BEGIN failed--compilation aborted at /usr/bin/zmpkg.pl line 37.
failure

root@river:/etc/init.d# 


ANY IDEAS??

---

### Post by dannyboy79 on 2012-12-10
no idea but hopefully you saved the previous kernel, just boot into the kernel that worked. sorry i couldn't help more.

---

### Post by dellsweig on 2012-12-10
> **dannyboy79 said:**
> no idea but hopefully you saved the previous kernel, just boot into the kernel that worked. sorry i couldn't help more.

Booted back in the last kernel and the same issue.. Something else is going on.......

---

### Post by dannyboy79 on 2012-12-10
see if you can view the update logs somewhere to find out what was all updated besides the kernel.

---

### Post by bbiandov on 2013-02-17
Tracking how evasive everyone is on the zonemidner.com forums I think 1.25 has major problems and running it on 12.04 LTS is most definitely NOT working properly. 

The zones are NOT working for me. The only way to make it work somehow is to NOT define any zones and let it capture and analyze the entire frame.

If any zones are defined then the sources show up in orange and no motion analysis is performed hence zero captured events:

[IMG]http://cognitivekipple.com/store/zones.png[/IMG]

There is also another bug which causes a lot of log entries with errors. Thankfully there is a great fix which worked for me:

[http://lachlanmiskin.com/blog/2012/06/24/zoneminder-shared-data-size-conflict-in-shared_data-for-monitor/#comment-49]("http://lachlanmiskin.com/blog/2012/06/24/zoneminder-shared-data-size-conflict-in-shared_data-for-monitor/#comment-49")

---

### Post by zerofloat on 2013-02-17
I've had  zoneminder 1.25 running on 12.04 for few months. IP cameras seem to be easier to get installed. Zones are working OK with the six Foscams we have. There is a log error that I get because of the way foscam formats video but it has no effect on operation.
[http://wallyandsue.blogspot.com/search/label/Zoneminder]("http://wallyandsue.blogspot.com/search/label/Zoneminder")
I just reloaded it on a quad core and plan to install a couple megapixel cams.

---

