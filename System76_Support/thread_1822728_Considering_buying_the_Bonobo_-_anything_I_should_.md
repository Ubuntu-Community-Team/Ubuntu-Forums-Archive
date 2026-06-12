---
title: "Considering buying the Bonobo - anything I should know first?"
date: 2011-08-10
forum: System76 Support
---

### Post by CaptSaltyJack on 2011-08-10
I'm strongly considering getting the Bonobo. I have a few questions:

1. Ubuntu comes pre-installed. Does it have any kind of S76 "bloatware"? I heard S76 has their own drivers. What if I want to wipe it clean and reinstall Ubuntu myself? Will it work fine, or will I need special S76 .deb files?

2. Security/anti-theft question: is it possible to, say, prevent someone who has stolen the laptop to boot on a CD and reformat the laptop? (e.g. password protect the BIOS and disable the DVD-ROM in the boot sequence)

3. Does the fingerprint reader work out of the box? What if I wipe the machine and install Ubuntu myself, how easy is it to get working?

I think that's it. If there's anything else unexpected I should know about, let me know. :)

---

### Post by Flyers2391 on 2011-08-11
> **CaptSaltyJack said:**
> I'm strongly considering getting the Bonobo. I have a few questions:

1. Ubuntu comes pre-installed. Does it have any kind of S76 "bloatware"? I heard S76 has their own drivers. What if I want to wipe it clean and reinstall Ubuntu myself? Will it work fine, or will I need special S76 .deb files?

2. Security/anti-theft question: is it possible to, say, prevent someone who has stolen the laptop to boot on a CD and reformat the laptop? (e.g. password protect the BIOS and disable the DVD-ROM in the boot sequence)

3. Does the fingerprint reader work out of the box? What if I wipe the machine and install Ubuntu myself, how easy is it to get working?

I think that's it. If there's anything else unexpected I should know about, let me know. :)

I don't know specifics but I believe the fingerprint reader requires the System76 driver.  If you wipe your system you would want to re-install the driver from them (directions [here]("http://www.knowledge76.com/index.php/Restoring_Your_System")).  According to [http://www.knowledge76.com/index.php/BonP5](http://www.knowledge76.com/index.php/BonP5) their driver fixes a lot:

Restore
Suspend & Resume
Ethernet stability
Mute internal speakers with headphones

hope that helps you somewhat!

---

### Post by CaptSaltyJack on 2011-08-11
Dude. Majorly helpful, thanks! I kinda expected to find some sort of "downloads" section on system76.com.. didn't see it though. Now I know about knowledge76.com and planet76.com.

---

### Post by jml on 2011-08-12
To try and answer your other questions:

2.  Security:  Assuming that the Bonobo is like other System 76 laptops, before you get to the Ubuntu splash screen, you should see (for a few seconds at least,) The BIOS boot screen.  Near the bottom there should be a mention of what keys to press to enter the BIOS set up screen.  There you should be able to set a BIOS password.  Then look around to see if you find an item called boot device, or boot sequence.  Then set you hard drive as the first boot device.  That will protect someone from running a live CD on your laptop.  Sometimes, that setting is not on the BIOS setup screen, but activated by another key binding at bootup.  I have one computer that lists one key for BIOS setup and another key for Boot sequence.

3.  Fingerprint reader:  Usually if a hardware feature is not supported on a System 76 computer, it will be mentioned on the product web site.  I just checked and there is no mention of lack of support.  However, the last page of this thread on this forum:

[http://ubuntuforums.org/showthread.php?t=1669245&page=4](http://ubuntuforums.org/showthread.php?t=1669245&page=4)

may give you additional information.

4.  Just two other points.  The Bonobo is really meant to be a movable desktop replacement.  With emphasis on desktop.  It's weight is rather substantial, and due to the high power hardware, battery life is relatively short.  But from what I have read, it is a very good laptop.  Hope that this helps.

Joe

---

### Post by CaptSaltyJack on 2011-08-12
Great, thanks! And yes, I'm completely aware of its weight and size. :) It's exactly what I need. I'm looking for a desktop replacement that I can take to a contract job, and leave there for a few months so I can just go into work and there it is. When the contract is over, pack it up and take it home.

---

### Post by nichins on 2011-08-13
I don't think the fingerprint reader works with 11.04. Check out: [http://knowledge76.com/index.php/Fingerprint_Reader_Usage](http://knowledge76.com/index.php/Fingerprint_Reader_Usage)

---

### Post by CaptSaltyJack on 2011-08-15
Bonobo ordered! :D

---

### Post by iandouglas on 2011-08-26
I got my Bonobo laptop with this new job a few days ago, and I love it. Having Ubuntu out of the box, with driver support all ready to go was unbelievable.

Work even bought me a gigantic monitor at 2500x1440 resolution, and several of my coworkers stood around in awe as the Bonobo's video configuration was sufficient to get native resolution on the screen where several of them said the only other systems in the office that would drive native resolution were MacBook Pros.

The only upgrade I got on the system was a RAM upgrade to 8GB. As others have said, the machine is definitely a desktop replacement. Sitting in a meeting the other day, it drained half of the battery just sitting on wifi and being mostly idle. And it's odd that the battery drain is always "estimating" when discharging seems a little odd. But otherwise, this is by far a wonderful investment.

:KS

---

### Post by CaptSaltyJack on 2011-08-26
I love mine too! It was a bit wonky out of the box, nothing serious, but the Linux "locate" command wouldn't work, gave me a permission denied because the 'avahi' group owned the mlocate.db or something odd like that. I reformatted, reinstalled Ubuntu myself, then installed the System76 drivers and was good to go.

I also got the 8GB RAM upgrade along with the 80GB SSD drive. This thing screams! Upon login, everything auto-starts nearly at the same time and it's done and ready to go. Super slick.

The only thing I don't like is the trackpad. It's super twitchy. Try just resting your finger on it, and the mouse jitters like it's on caffeine. Also, two-finger and three-finger taps are difficult sometimes.

FYI, I got drag lock working in case you're interested. Create the file ~/.xinput.d/en_US and paste this into it:

```

#!/bin/sh

xinput set-prop 12 259 1
xinput set-prop 12 260 350

```

Then log out and back in and you should have drag lock. Adjust the '350' (350ms) if you like a longer delay before it auto unlocks your drag.

---

