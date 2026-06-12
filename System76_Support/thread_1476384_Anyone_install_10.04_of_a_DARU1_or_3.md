---
title: "Anyone install 10.04 of a DARU1 or 3?"
date: 2010-05-07
forum: System76 Support
---

### Post by jml on 2010-05-07
The title says it all.  I have both a first and third generation Darter.  I am curious if anyone has successfully upgraded or clean installed on either of these two laptops?  If yes, how did it go?  Were there any problems?  Are you satisfied with the result?  Thanks for your time answering.

Joe

---

### Post by icewater on 2010-05-07
Hi, yes, I installed it on my Darter Ultra (DARU3) yesterday, and updated the System76 drivers.  Unfortunately I've lost all sound.  Aside from that, everything seems to work (inasmuch as I've tried it).

---

### Post by riseringseeker on 2010-05-08
> **jml said:**
> The title says it all.  I have both a first and third generation Darter.  I am curious if anyone has successfully upgraded or clean installed on either of these two laptops?  If yes, how did it go?  Were there any problems?  Are you satisfied with the result?  Thanks for your time answering.

Joe

I don't have it installed on the hard drive of either my Daru1 or Wild Dog as of yet, I am waiting until I have enough days off to not rush through it.  I have been playing with 10.04 since beta 2 that I installed on a external USB drive (clean install obviously).  I wanted to get a head start on seeing what the differences were, and make sure everything ran OK.

I have most (but not all) of the apps that I run on the 9.10 installed on the "brick", and they all run fine.  Sound, wireless, video, passwordless ssh key all work as they should.

I did make a few changes to the default.  Decided I didn't like the window controls on the left, so changed themes (would have to boot into it to tell you what it was, but very similar to the default except the button location).  I also prefer the old method of update notifications, so I changed that as well.  While I was at it, got rid of the shutdown timer, but Lucid now pops up a little "Are you sure?" box when I go to log out/shut down that doesn't seem to be able to be eliminated - so far my only minor gripe.

Overall I am quite happy with 10.04 running on the Darter (via the brick), and am looking forward to a week from now when I will have sufficient time do a "real" install on both the boxes.  

I am in the habit of doing clean installs, as I've read too many people with problems doing an upgrade.  Also it gives me a chance to do some "house cleaning" of my files.

---

### Post by jprainey on 2010-05-08
I installed 10.04 on my darter ultra - since then it has been a continuous battle to either connect wireless or maintain a wireless connection.  Looking all over the place for a solution - still haven't found one.

---

### Post by jml on 2010-05-08
Thanks for all of the feedback.  I now have 10.04 installed on both my DARU 1 and 3.  This is the procedure that worked for me.

I downloaded the live CD to use as a plan B if the upgrade hosed my systems.  I then backed up all of my data.  I chose to upgrade rather than do a clean install this time because I did not want to have to reinstall the applications that were not installed by default with 10.04.

I then did an update via System--> Administration--> Update Manager.  I rebooted the system and then again launched update manager and clicked on upgrade.  I clicked through one or two error messages and the update successfully completed.

Installing the System 76 drivers could not be performed as outlined on this forum.  The System 76 repository was not listed under the other sources tab as described.  I had to download and install the driver manually.  That went without problem.

So far, sound works well, as does my wireless and wired network connection.  Not sure if this is because I did an upgrade rather than a clean install, or if it was just luck.  Again, thanks to those who took the time to answer my post.

Joe

---

### Post by thomasaaron on 2010-05-10
> Unfortunately I've lost all sound.

Go to Sound Preferences (click on the speaker icon) and click the Output tab. Make sure the Connector is set to Analog Speakers.

---

