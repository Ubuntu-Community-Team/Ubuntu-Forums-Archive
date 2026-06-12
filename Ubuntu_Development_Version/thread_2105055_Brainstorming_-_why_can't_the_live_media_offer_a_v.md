---
title: "Brainstorming - why can't the live media offer a version downgrade?"
date: 2013-01-15
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2013-01-15
I need to do a great deal of follow-up on this but I began a while back at Launchpad Answers in hopes that a member of the installer team would comment:

[https://answers.launchpad.net/ubuntu/+source/ubiquity/+question/217832](https://answers.launchpad.net/ubuntu/+source/ubiquity/+question/217832)

Particularly the second reply is exemplary of the general lack of knowledge surrounding the fact that ubiquity does provide both upgrade and replace options if only one Ubuntu based release is recognized on the existing drives.

I've personally found these options to be almost bullet proof .... they're in no way related to a "release-upgrader" version upgrade or to the old alternate image style upgrades.

I don't totally understand how it works but the basic outlines of [the design spec]("https://docs.google.com/a/canonical.com/document/preview?id=1bZ4yQIVgGaUGSYu3qiUHnQt3ieBZoqunP_DcleHCr3I&pli=1#") say:

> Ubuntu {same version} on it. ...
&#9679; Reinstall Ubuntu {same
version} [maps to reuse]
Documents, music, and other
personal files will be
kept. Installed software will be
kept where possible. System-wide
settings will be cleared.


Or:

> Ubuntu {older version} on it. ...
&#9679; Upgrade Ubuntu to {this
version} [maps to reuse]
Documents, music, and other
personal files will be kept.
Installed software will be kept
where possible. System-wide
settings will be cleared.


I can tell you that the results are quite different than what you'd expect from a distro-upgrade via the update manager. There are no old config files to deal with but typically browser profiles are saved along with everything that's NOT a hidden "dot" file or folder in /home.

Additionally no older kernels seem to be retained so you end up with a truly fresh install which results in a much cleaner upgrade or replacement, but you retain all of the stuff you don't want to have to restore from a back-up. **But always remember that the data you'll lose is the data you don't have backed up!!!!**

So I'm just wondering why ubiquity can't offer a downgrade, eg; Replace Ubuntu 12.10 with Ubuntu 12.04 :confused:

Does anyone else think this is worthy of a brainstorm idea?

---

### Post by dino99 on 2013-01-15
Ubiquity is not an app i can trust: too many issues, act like a russian roulette.
If the brainstorm place is able to make the buzz for rewriting ubiquity, then we might use it.
It should offer to install from scratch, upgrade and also downgrade of course.
Wonder which other distro(s) is/are using ubiquity and how things goes for them.

---

### Post by ventrical on 2013-01-15
I aksed this question over a year ago and there was also some chatter about a system restore.

 For the most part ubiquity has been very solid for me.  I have had some real doozers with precise, ocelot and quantal but they always work out.

  I'm just asking .. but wouldn't it be easier to extend Lucid for another 3 years of LTS support so current users (and noobs) can make realistic adjustments to the comming changes? I mean ... isn't this  "Linux for Human Beings" and not "Linux for Executive  Toy PlayThings" ?

---

### Post by castrojo on 2013-01-15
I would think any kind of downgrade would require btrfs to be finished and shipping as default, so you can just snapshot back to a previous state, at that point it'd be relatively simple.

---

### Post by dino99 on 2013-01-15
> **castrojo said:**
> I would think any kind of downgrade would require btrfs to be finished and shipping as default, so you can just snapshot back to a previous state, at that point it'd be relatively simple.

it even can be simpler: allowing to overwrite a greater version, aka doing an installation from scratch

---

### Post by castrojo on 2013-01-15
That's what the installer does already when you reinstall, but it it still sucks to wait the 10 minutes or whatever for that to happen, a nice rollback/snapshot would be instant.

---

### Post by zika on 2013-01-15
When are we to see BTRFS recommended for widespread usage?
Is it safe now to convert from ext4 to BTRFS?

---

### Post by kansasnoob on 2013-01-15
> **castrojo said:**
> That's what the installer does already when you reinstall, but it it still sucks to wait the 10 minutes or whatever for that to happen, a nice rollback/snapshot would be instant.

I was going to ask if the procedure you're talking about is not totally different than what I'm talking about, but I think you just answered that ;)

I don't understand the technical aspects but just today I decided to install Lubuntu Quantal over an Ubuntu-GNOME-Remix Quantal that I'd been using to perform benchmark testing of window managers (mutter - metacity - muffin - marco) on hardware that won't run Compiz+llvmpipe. The existing installation size was:

```
lance@lance-VIA-desktop:~$ df -H
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        41G  **[COLOR="Red"]6.0G[/COLOR]**   33G  16% /
udev            485M  4.1k  485M   1% /dev
tmpfs           197M  852k  197M   1% /run
none            5.3M     0  5.3M   0% /run/lock
none            493M   91k  493M   1% /run/shm
none            105M     0  105M   0% /run/user
/dev/sr0        726M  726M     0 100% /media/lance/Lubuntu 12.10 i386

```

So I used the Lubuntu Quantal live media to reinstall and I was offered these options:

[ATTACH]230104[/ATTACH]

I chose the selected "Reinstall" and all data was saved :D

But going from Ubuntu-GNOME-Remix to Lubuntu notably saved my .mozilla profile even though Firefox was NOT reinstalled by default, so it's not fool-proof :)

I assume that the "reuse" process reinstalls only those apps available on the live media :confused:

It's very common to see a warning regarding the fact that not all apps could be reinstalled/restored just before you're offered the options to reboot or continue running the live DE ...... but the spec does say, "Installed software will be kept **[COLOR="Red"]where possible[/COLOR]**."

I just don't see why this can't work for a "downgrade" :confused:

Oh, and look at the new size:

```
lance@lance-VIA-desktop:~$ df -H
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb5        41G  **[COLOR="Red"]5.0G[/COLOR]**   34G  13% /
udev            485M  4.1k  485M   1% /dev
tmpfs           197M  799k  197M   1% /run
none            5.3M     0  5.3M   0% /run/lock
none            493M     0  493M   0% /run/shm
none            105M  8.2k  105M   1% /run/user

```

No cruft at all! She's a clean. mean fightin' machine with no data loss :guitar:

---

### Post by MacUntu on 2013-01-15
Everything other than a rollback is error-prone and the process to recover from a broken downgrade is anything but human-friendly. ;)

---

### Post by kansasnoob on 2013-01-15
> **MacUntu said:**
> Everything other than a rollback is error-prone and the process to recover from a broken downgrade is anything but human-friendly. ;)

Calling this procedure a downgrade (or an upgrade for that matter) is probably somewhat inaccurate. In those cases where either a reinstall or upgrade is offered ubiquity does "map to reuse".

---

### Post by kansasnoob on 2013-01-15
Hmmm, I was trying to get more of an idea how "map to reuse" actually works and I was surprised to find no installer log in /var/log.

A bit more looking revealed that the applicable logs are in /ubiquity/apt/clone :D

---

### Post by kansasnoob on 2013-01-15
> **castrojo said:**
> I would think any kind of downgrade would require btrfs to be finished and shipping as default, so you can just snapshot back to a previous state, at that point it'd be relatively simple.

I see Evan Dandrea reflected on the same basic idea here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/752415](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/752415)

---

### Post by kansasnoob on 2013-01-15
Aha, as I study this I ran across an SRU for 12.04.2 that needs verification:

[https://bugs.launchpad.net/ubuntu/+source/apt-clone/+bug/1066347](https://bugs.launchpad.net/ubuntu/+source/apt-clone/+bug/1066347)

---

### Post by kansasnoob on 2013-01-16
Here's an expired bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068657](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068657)

I'm thinking before I address this "downgrade" thing I should create a new bug report regarding that. I mean it's no big deal to me because I use the same apps all the time so I have post-installation scripts written to install needed PPA's and then "apt-get install" all desired packages but I guess an upgrade or reinstall should check and then inform a user of what will NOT be restored before proceeding.

Or, at the very least, just strengthen the warning; **Installed software will be kept where possible**. I can't quite think what's appropriate there :-k

---

### Post by kansasnoob on 2013-01-17
> **kansasnoob said:**
> Aha, as I study this I ran across an SRU for 12.04.2 that needs verification:

[https://bugs.launchpad.net/ubuntu/+source/apt-clone/+bug/1066347](https://bugs.launchpad.net/ubuntu/+source/apt-clone/+bug/1066347)

I've been working on the verification of this off and on for about 36 hours and in order to prove that "verification failed" I need to record some info. Thus I'm now in Oneiric and for some reason I don't care about I can't save what I need to save to other external sources from the live CD so I'm using some of the free electronic ink here ;)

[ATTACH]230178[/ATTACH]

[ATTACH]230179[/ATTACH]

I hope this works.

---

### Post by kansasnoob on 2013-01-17
> **kansasnoob said:**
> I've been working on the verification of this off and on for about 36 hours and in order to prove that "verification failed" I need to record some info. Thus I'm now in Oneiric and for some reason I don't care about I can't save what I need to save to other external sources from the live CD so I'm using some of the free electronic ink here ;)

[ATTACH]230178[/ATTACH]

[ATTACH]230179[/ATTACH]

I hope this works.

It worked! This is a nightmare :(

Here's Oneiric -> Precise:

[ATTACH]230181[/ATTACH]

[ATTACH]230182[/ATTACH]

Now to complete that ;)

---

### Post by kansasnoob on 2013-01-17
> **kansasnoob said:**
> It worked! This is a nightmare :(

Here's Oneiric -> Precise:

[ATTACH]230181[/ATTACH]

[ATTACH]230182[/ATTACH]

Now to complete that ;)

Time for a break (long break) but then I'll hammer down on both the original 12.04 image and the latest 12.04.2 proposed image. I know it's borked but I must be able to explain it ;)

---

### Post by kansasnoob on 2013-01-17
Trying to compile the proper info to fail that SRU is becoming convoluted ;)

I'm going to need to post numerous images at the bug report so I'm stealing still more electronic ink. The original 12.04 image, the 12.04.1 image, and the most recent 12.04.2 image all fail to offer: 

> Reinstall Ubuntu {same
version} [maps to reuse]
Documents, music, and other
personal files will be
kept. Installed software will be
kept where possible. System-wide
settings will be cleared. 

[ATTACH]230227[/ATTACH]

[ATTACH]230228[/ATTACH]

[ATTACH]230229[/ATTACH]

Now I'm testing a fresh install of that newest image to see if I'm offered the option to "reinstall w/o erasing everything" after I reboot with the same image.

Man this is more fun than I've had in a long time :lolflag:

---

### Post by kansasnoob on 2013-01-17
Time to break out the bourbon ](*,)

I did a fresh install of Ubuntu 12.04.2 20130117.1-i386 and still no reinstall option:

[ATTACH]230230[/ATTACH]

But to make things worse I can't report a new bug against ubiquity because it's no longer an official package:

[ATTACH]230231[/ATTACH]

Maybe the devs beat me to the bourbon :lolflag:

---

### Post by kansasnoob on 2013-01-18
I hope this gains the proper attention:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1101073](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1101073)

I did also comment here:

[https://bugs.launchpad.net/ubuntu/+source/apt-clone/+bug/1066347/comments/8](https://bugs.launchpad.net/ubuntu/+source/apt-clone/+bug/1066347/comments/8)

I find it almost incomprehensible that apport doesn't recognize ubiquity as an official package, and it's equally maddening that the QA tracker doesn't have options to report bugs against the "reinstall or upgrade via live media" options :(

Bug, bug, bug ............... buggity bugs :mad:

---

### Post by mc4man on 2013-01-18
I've got a 12.04.1 install I did the other day & if booting to either that live image (usb) or the 12.04.2 image (usb also) can't say I even see any "reinstall" options
Only get the 'older' 3 option partitioning window (Install alongside of, ect.

---

### Post by kansasnoob on 2013-01-19
> **mc4man said:**
> I've got a 12.04.1 install I did the other day & if booting to either that live image (usb) or the 12.04.2 image (usb also) can't say I even see any "reinstall" options
Only get the 'older' 3 option partitioning window (Install alongside of, ect.

Ditto that. I even went back as far the original 12.04 iso and there is NO reinstall option to be found in Precise, but Oneiric was basically OK:

[http://ubuntuforums.org/attachment.php?attachmentid=230178&d=1358427210](http://ubuntuforums.org/attachment.php?attachmentid=230178&d=1358427210)

Sort of goofy calling it an upgrade but it worked OK :D

I was surprised to see it didn't work in Precise, guess I need to be sure and run that test everytime there's an official release.

I think Nick is working on some new test-cases for ubiquity so we'll be reminded ;)

---

### Post by mc4man on 2013-01-19
If you look at the descrip on bug report which was filed on 12.10 it says
TEST CASE:
1. Install Ubuntu 12.10 or 12.04.1 once
2. Install [COLOR="Blue"]it[/COLOR] a second time and in the partitioning step select "Reinstall Ubuntu 12.10"

Don't get what "it" means unless it's - 
install 12.04.1/2 (no 12.10 install
boot to 12.10 live & select "Reinstall Ubuntu 12.10"

---

### Post by kansasnoob on 2013-01-19
> **mc4man said:**
> If you look at the descrip on bug report which was filed on 12.10 it says
TEST CASE:
1. Install Ubuntu 12.10 or 12.04.1 once
2. Install [COLOR="Blue"]it[/COLOR] a second time and in the partitioning step select "Reinstall Ubuntu 12.10"

Don't get what "it" means [B]unless it's - 
install 12.04.1/2 (no 12.10 install
boot to 12.10 live & select "Reinstall Ubuntu 12.10"[/B]

In that case it would be called an upgrade:

[ATTACH]230310[/ATTACH]

But something else just dawned on me ........ no auto-resize option:

[ATTACH]230311[/ATTACH]

Maybe because it's already a dual-boot :confused:

I need to swap drives and see what happens ;)

But first of all it's time for a shower and a shave, the dogs won't even get close to me :lolflag:

---

### Post by kansasnoob on 2013-01-19
Wow, life is better w/o a neck-beard ;)

Anyway I'm starting very simple this time. This drive has only a fully updated Precise on it, including proposed updates, and I see no updates to ubiquity since the 10th:

> ubiquity (2.10.24) precise; urgency=low

  [ Jesse Sung ]
  * Fix multiple issues with Back/Stop and Continue/Connect buttons on
    wireless page (LP: #883615).

  [ Kent Baxley ]
  * Hide the back button at the beginning of oem-config (LP: #1095692).

 -- Colin Watson <cjwatson@ubuntu.com>  Thu, 10 Jan 2013 12:32:41 +0000

An installation can't get much simpler than this, one drive, one OS {Ubuntu 12.04.1 LTS "Precise Pangolin" - Release i386 (20120817.3)}:

[ATTACH]230329[/ATTACH]

So we'll see what happens :D

But this may take a while because I'm moving part of my office to the kitchen and another part to the bedroom because the landlord is rebuilding part of the foundation due to the drought causing the foundation to shift :shock:

So please be patient.

---

### Post by mc4man on 2013-01-19
Could be wrong but - 
I think that bug you're looking at started as one thing - the "re-install" option in 12.10 failing (why he mentioned 12.04.1 no clue

This exposed an issue in apt-clone for both 12.10 & 12.04, so the verification for 12.04.x is whether apt-clone works, not whether the "re-install" option works as so far there doesn't appear to be one in 12.04.x (unless you find it somehow..

---

### Post by kansasnoob on 2013-01-19
> **mc4man said:**
> Could be wrong but - 
I think that bug you're looking at started as one thing - the "re-install" option in 12.10 failing (why he mentioned 12.04.1 no clue

This exposed an issue in apt-clone for both 12.10 & 12.04, so the verification for 12.04.x is whether apt-clone works, not whether the "re-install" option works as so far there doesn't appear to be one in 12.04.x (unless you find it somehow..

That is exactly correct :D

But the reinstall option did actually exist beginning with Maverick. Somewhere between Oneiric and Precise it got totally borked, and I'm fairly certain that even the "auto-resize" option got borked too :(

---

### Post by kansasnoob on 2013-01-19
OK, as applies to the setup in [post #25]("http://ubuntuforums.org/showpost.php?p=12463482&postcount=25") "auto-resize" does appear as an option if only one OS exists:

[ATTACH]230333[/ATTACH]

But still no "reinstall" which did work in Oneiric even though it said "upgrade Oneiric to Oneiric" ......... that's a regression :(

So *dino99* was right here:

[http://ubuntuforums.org/showpost.php?p=12456186&postcount=2](http://ubuntuforums.org/showpost.php?p=12456186&postcount=2)

If the alternate images still existed I'd recommend never installing with the live image! It's an absolute crap shoot!

---

### Post by kansasnoob on 2013-01-19
I don't know whether to laugh or cry. What I was requesting already existed in Oneiric:

[ATTACH]230345[/ATTACH]

I'll grant you the naming was wrong because 12.04.1 to 11.10 is NOT an upgrade but I'll complete that to see what happens.

This whole thing is looking like a major regression to me, not that convincing the installer-team will be easy :cry:

In my experience they're possibly the most insular team in Canonical/Ubuntu :(

---

### Post by kansasnoob on 2013-01-19
> **kansasnoob said:**
> I don't know whether to laugh or cry. What I was requesting already existed in Oneiric:

[ATTACH]230345[/ATTACH]

I'll grant you the naming was wrong because 12.04.1 to 11.10 is NOT an upgrade but I'll complete that to see what happens.

This whole thing is looking like a major regression to me, not that convincing the installer-team will be easy :cry:

In my experience they're possibly the most insular team in Canonical/Ubuntu :(

That worked fine other than needing to tweak the theme afterwards, oh and you do always get an error message like this:

[ATTACH]230354[/ATTACH]

So that could be improved upon, but that's another issue.

The thing is that Oneiric offered "reuse", always called "upgrade" regardless of what version of Ubuntu was installed, but Precise is pretty much borked.

Was that intentional?

I see it as a regression :(

---

### Post by kansasnoob on 2013-01-19
I'm working on something else ATM but I'm trying to imagine a somewhat time efficient test scenario for ubiquity. This was easy prior to Maverick but we are where we are :)

So I'm thinking to test the installer fairly thoroughly you could do this (if any step fails you should stop and file the appropriate bugs):

Step #1: Install any previous stable release, preferably an entire disc install. Import some docs, pictures, etc. Create or import a browser profile, eg; .mozilla.

Step #2: Test the live session:

[http://iso.qa.ubuntu.com/qatracker/testcases/1303/info](http://iso.qa.ubuntu.com/qatracker/testcases/1303/info)

Note: the testcase doesn't say so but IMHO disc integrity should be checked at that point.

Step #3: Try to install and see if you're offered an upgrade. If so complete that and make sure all is well. No testcase exists yet.

Step #4: Boot the live media again and then try to install and see if you're offered a reinstall. If so continue. Once it's complete yada-yada. No testcase exists yet.

Step #5: Boot the live media then try to install and see if you're offered an auto-resize. If so continue:

[http://iso.qa.ubuntu.com/qatracker/testcases/1301/info](http://iso.qa.ubuntu.com/qatracker/testcases/1301/info)

Step #6: Boot the live media again and use Gparted to delete the previous "auto-resize" install, then start the installation and perform a "use largest free space" install. This is not clearly defined, you can only tell the installer plans to use free space due to the button in the lower right hand corner changing from Continue to Install now:

[ATTACH]230427[/ATTACH]

No testcase exists.

Step #7: Perform a manual partitioning install:

[http://iso.qa.ubuntu.com/qatracker/testcases/1302/info](http://iso.qa.ubuntu.com/qatracker/testcases/1302/info)

Step #8: Perform an entire disc install, preferably with no less than 2 internal drives installed:

[http://iso.qa.ubuntu.com/qatracker/testcases/1300/info](http://iso.qa.ubuntu.com/qatracker/testcases/1300/info)

And more ................

The "more" includes:

* If you have Windows installed and four primary NTFS or FAT partitions exist you should be offered a Wubi install.

---

### Post by zika on 2013-01-20
> **kansasnoob said:**
> I don't know whether to laugh or cry. What I was requesting already existed in Oneiric:

[ATTACH]230345[/ATTACH]

I'll grant you the naming was wrong because 12.04.1 to 11.10 is NOT an upgrade but I'll complete that to see what happens.

This whole thing is looking like a major regression to me, not that convincing the installer-team will be easy :cry:

In my experience they're possibly the most insular team in Canonical/Ubuntu :(I thought that my old mind was playing tricks on me but I did remember that all of this was already seen by eyes of mine... That was not a déjà vu of mine... Nice...

---

### Post by kansasnoob on 2013-01-20
> **zika said:**
> I thought that my old mind was playing tricks on me but I did remember that all of this was already seen by eyes of mine... That was not a déjà vu of mine... Nice...

Yeah, my memory stinks so I guess my brainstorm was actually a brain fart :lolflag:

I'm going to go ahead and test some Raring images soon just to see where we're at now. I do know that "reinstall" and "upgrade" both worked in Quantal, but apparently something got borked in Precise and no one noticed it :(

---

### Post by kansasnoob on 2013-01-20
I did an upgrade from Precise Ubuntu to Raring Lubuntu, yes - Ubuntu to Lubuntu, and ***all worked quite well***.

It seemed to take a long time for the "reinstalling apps" part of the upgrade but it does appear to have restored all apps, and I didn't get that error message saying not all apps could be reinstalled :D

And "ubiquity-apt-clone" now appears in /var/log/installer which seems more appropriate, so my initial thought is that dev is continuing to improve the "reuse" option :biggrin:

I'll try a "reinstall" just to see how it works, but this seems pretty great to me.

---

### Post by kansasnoob on 2013-01-20
The "reinstall" with the Lubuntu 13.04 20130119-i386 live image worked flawlessly other than being called an upgrade:

[ATTACH]230380[/ATTACH]

I sort of wonder if it wouldn't just make sense to replace the term "upgrade" with the term "replace" rather than have a bunch of "ifs" in place that change the term from "upgrade" to "reinstall" or "downgrade" :)

---

### Post by kansasnoob on 2013-01-20
OK Quantal does not offer a downgrade:

[ATTACH]230408[/ATTACH]

So in summary:

Oneiric; The 11.10 final image offers upgrade, reinstall, and downgrade - BUT all are referred to as upgrades.

Precise; The 12.04 final, 12.04.1 final, and 12.04.2 (20130117.1) images only offer upgrades - no reinstall or downgrade.

Quantal; The 12.10 final image offers upgrade and reinstall, named appropriately - but no downgrade. 

Raring; The 13.04 (20130119) image offers both upgrade and reinstall - BUT both are referred to as upgrades.

---

