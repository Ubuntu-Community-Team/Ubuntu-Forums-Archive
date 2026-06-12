---
title: "Call for Testing wubi"
date: 2012-02-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by balloons on 2012-02-23
Weee! The testers life is never finished eh? Here's an opportunity to test wubi, the windows ubuntu installer. If you've got a windows partition handy, give it a whirl. We all want our beta1 iso's to be bug free -- this is a jump start on that ;-)

[http://www.theorangenotebook.com/2012/02/call-for-testing-wubi.html](http://www.theorangenotebook.com/2012/02/call-for-testing-wubi.html)

FYI, if you like twitter and want to be aprised of what's going on in the testing world, feel free to follow @UbuntuTesting. I'm cloning these announcements there as well.

---

### Post by arpanaut on 2012-02-23
>  In addition, the computer will need at least 4 gb of ram.
from your posting.

Since when does wubi need that much Ram?
Or do you mean at least 4 gb of available HD space?

Curious...

---

### Post by balloons on 2012-02-24
> **arpanaut said:**
> from your posting.

Since when does wubi need that much Ram?
Or do you mean at least 4 gb of available HD space?

Curious...

If that's the only mistake I made while posting I'll consider it a win.. So tired was I yesterday :-) LONG day. Thanks for catching it! Your right, only 4 gb of HD space needed, not ram.

---

### Post by bcbc on 2012-02-24
Make that 5GB and you'll be okay ;) (This was bumped from 4GB when 11.10 was released). 

This will cause failures when installing to FAT32 partitions (only if you run wubi.exe standalone). Bug [lpbug]882393[/lpbug]

---

### Post by balloons on 2012-02-24
> **bcbc said:**
> Make that 5GB and you'll be okay ;) (This was bumped from 4GB when 11.10 was released). 

This will cause failures when installing to FAT32 partitions (only if you run wubi.exe standalone). Bug [lpbug]882393[/lpbug]

You guys are awesome! Thanks.. where would I be without you :D I updated the post again..

---

### Post by bcbc on 2012-02-26
> **guitara said:**
> You guys are awesome! Thanks.. where would I be without you :D I updated the post again..

Do you know what is happening with Edubuntu? It's been added to the Wubi installer, but it doesn't work (bug [lpbug]925882[/lpbug]). There's also no mention of it under the [edubuntu test cases]("http://iso.qa.ubuntu.com/qatracker/milestones/208/builds/12530/testcases") or for the [standard Wubi test cases]("http://iso.qa.ubuntu.com/qatracker/milestones/208/builds/12546/testcases")

There are actually a confusing array of options for installing with Wubi and very few of these seem to have their own testcases.

1. Wubi.exe standalone for Ubuntu. Downloads diskimage, 1 phase install.
2. Wubi.exe standalone for (Ku)(Myth)(Edu)(Lu)(Xu)buntu. Downloads ISO. 2 phase install.
3. Wubi.exe standalone with ISO in same dir. 2 phase install.
4. Wubi.exe from a CD.
5. Wubi.exe from a USB. Fails if partition is > 852MB (except in alpha/beta/release candidate testing as there is a bypass that ignores it).
6. Wubi.exe standalone when an Ubuntu USB is plugged in - don't get the install inside windows option.
7. Wubi.exe when an Ubuntu ISO is in the root of a drive (thinks it's a CD).
...
That doesn't include the CD boot helper.

The above is just a brain dump (details maybe hazy in parts). But my point is there are quite a confusing array of options - some probably accidental, some don't work. It's not clear what the intention is, but maybe if someone defined what was expected in these situations it'd be easy to identify and fix bugs.

Also, traditionally most Wubi code changes seem to come at the end of the release cycle, so all the alpha/beta (even release candidate) testing is often wasted (interesing fact: wubi.exe was changed on day of 11.10 release, and there are 2 different release versions for 11.10 - rev241 on the ISOs and rev245 as standalone). (Technically, no testing is wasted, but Wubi testing can be time consuming and it'd be better to get bug fixes and feature changes in earlier in the dev cycle).

Hope that helps ;)

---

### Post by kansasnoob on 2012-02-26
I typically do perform Wubi testing beginning with Beta 1 since the live installer (ubiquity) began offering that option if four primary partitions already exist.

But my testing is going to be delayed this time due to hardware failures as described here:

[https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/941275](https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/941275)

The past few months hardware and financial problems have just been kicking my butt!

---

### Post by kansasnoob on 2012-02-26
Oh, and also Lubuntu is supposed to be supported now ;)

More testers needed.

---

### Post by bcbc on 2012-02-27
With 10.04, *ago*'s "call for testing wubi" was posted as a sticky in the Installation and Upgrades part of the forum and it saw a lot of activity. See [http://ubuntuforums.org/showthread.php?t=1439526](http://ubuntuforums.org/showthread.php?t=1439526)

Don't know if the 'hardened' dev testers here in the +1 forum even run windows ;)

---

### Post by balloons on 2012-02-27
> **bcbc said:**
> With 10.04, *ago*'s "call for testing wubi" was posted as a sticky in the Installation and Upgrades part of the forum and it saw a lot of activity. See [http://ubuntuforums.org/showthread.php?t=1439526](http://ubuntuforums.org/showthread.php?t=1439526)

Don't know if the 'hardened' dev testers here in the +1 forum even run windows ;)

Thanks. I will cross-post this there as well.

---

### Post by balloons on 2012-02-27
> **bcbc said:**
> Do you know what is happening with Edubuntu? It's been added to the Wubi installer, but it doesn't work (bug [lpbug]925882[/lpbug]). There's also no mention of it under the [edubuntu test cases]("http://iso.qa.ubuntu.com/qatracker/milestones/208/builds/12530/testcases") or for the [standard Wubi test cases]("http://iso.qa.ubuntu.com/qatracker/milestones/208/builds/12546/testcases")

There are actually a confusing array of options for installing with Wubi and very few of these seem to have their own testcases.

1. Wubi.exe standalone for Ubuntu. Downloads diskimage, 1 phase install.
2. Wubi.exe standalone for (Ku)(Myth)(Edu)(Lu)(Xu)buntu. Downloads ISO. 2 phase install.
3. Wubi.exe standalone with ISO in same dir. 2 phase install.
4. Wubi.exe from a CD.
5. Wubi.exe from a USB. Fails if partition is > 852MB (except in alpha/beta/release candidate testing as there is a bypass that ignores it).
6. Wubi.exe standalone when an Ubuntu USB is plugged in - don't get the install inside windows option.
7. Wubi.exe when an Ubuntu ISO is in the root of a drive (thinks it's a CD).
...
That doesn't include the CD boot helper.

The above is just a brain dump (details maybe hazy in parts). But my point is there are quite a confusing array of options - some probably accidental, some don't work. It's not clear what the intention is, but maybe if someone defined what was expected in these situations it'd be easy to identify and fix bugs.

Also, traditionally most Wubi code changes seem to come at the end of the release cycle, so all the alpha/beta (even release candidate) testing is often wasted (interesing fact: wubi.exe was changed on day of 11.10 release, and there are 2 different release versions for 11.10 - rev241 on the ISOs and rev245 as standalone). (Technically, no testing is wasted, but Wubi testing can be time consuming and it'd be better to get bug fixes and feature changes in earlier in the dev cycle).

Hope that helps ;)

bcbc this is really interesting stuff -- I'll send you a PM and help connect you with some folks who might be able to help you help everyone straighten around how this is working! No one likes having to do last minute wubi updates, but as you say they keep happening. We are trying hard to avoid that this time!

EDIT: can't pm you.. if you see this and are interested, contact me via email, pm, whatev's :-)

---

### Post by kansasnoob on 2012-02-28
There was a bit of a lull in testing today so I gave Lubuntu Wubi a try and all worked well :D

Specifically I wanted to first make sure that ubiquity was still working properly if 4 primary partitions existed, so I booted an Ubuntu live CD (actually DVD due to size) and deleted everything but the Win XP partition using Gparted.

I then created 3 additional NTFS primary partitions, and **importantly** restored the Win mbr, checked to be sure Win booted as it should, and then booted the Ubuntu live CD (actually DVD) again.

Note: I would have used an Lubuntu live CD except for this bug:

[https://bugs.launchpad.net/ubuntu/+source/lubuntu-artwork/+bug/938472](https://bugs.launchpad.net/ubuntu/+source/lubuntu-artwork/+bug/938472)

I was prompted to either "install inside" or "erase all" as I should be. I chose "install inside" and then on reboot I got the expected display in Win XP, then I chose Lubuntu, adjusted size, etc.

Everything just worked as it should :guitar:

Not a proper place on the qa-tracker to report such a test :(

---

### Post by bcbc on 2012-02-28
Cool. Agreed it's hard to confirm things are working without documented test cases.

I managed to install Edubuntu on Wubi last night from a DVD with a few tricks. My technique won't work after release, but it showed that it was possible. Bug [lpbug]913354[/lpbug]

---

### Post by kansasnoob on 2012-02-28
> **bcbc said:**
> Cool. Agreed it's hard to confirm things are working without documented test cases.

I managed to install Edubuntu on Wubi last night from a DVD with a few tricks. My technique won't work after release, but it showed that it was possible. Bug [lpbug]913354[/lpbug]

One thing I'd still like to see redesigned is the way the Wubi install is presented after being offered as an option if 4 primary partitions exist. I'd think the Wubi installer should clearly ask if you want to use an existing CD/DVD rather than downlaod the new image. I mean why download twice?

I'm just not sure how to "wish-list" that :confused: 

I think I did suggest it clear back when you helped me through that first round of testing. Remember that? 

I'll bet I gave you some gray hair :D

---

### Post by bcbc on 2012-02-28
You give the devs grey hair, not me ;)

I agree with you on this one: adding Wubi.exe to the startup folder is not ideal. It would make more sense to popup a message saying: "Boot back into Windows and insert the CD". Which works unless you happen to be booting from an Ubuntu USB.

And that's something which needs fixing too, since you can't (generally) install Wubi from a USB.

---

