---
title: "Ubuntu version jumps - What's the outcome or the symptoms?"
date: 2011-11-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-11-30
I confess complete ignorance on this: For as far as I can remember, I always have my Ubuntu completely updated when a new version is released, so I just run a do-release-upgrade. But generally I'm on +1 since development, so not even that is needed.

And when installing a new release on other PC, I usually just wipe whatever was in it first and go from the ISO. 

I know jumping versions is not recommended in the documentation. But what really happens when someone Changes Karmic/Lucid/Maverick/Natty repos on sources.list to precise and perform the update/upgrade && do-release-upgrade? I'm inclined to believe it apt may get confused at first, but will eventually resolv and work, (unless someone knows of an specific condition)?

---

### Post by kansasnoob on 2011-11-30
> **effenberg0x0 said:**
> I confess complete ignorance on this: For as far as I can remember, I always have my Ubuntu completely updated when a new version is released, so I just run a do-release-upgrade. But generally I'm on +1 since development, so not even that is needed.

And when installing a new release on other PC, I usually just wipe whatever was in it first and go from the ISO. 

I know jumping versions is not recommended in the documentation. But what really happens when someone Changes Karmic/Lucid/Maverick/Natty repos on sources.list to precise and perform the update/upgrade && do-release-upgrade? I'm inclined to believe it apt may get confused at first, but will eventually resolv and work, (unless someone knows of an specific condition)?

If you try to "jump" versions w/o following the proper upgrade path you'll end up with a bunch of broken, unreliable crap :(

---

### Post by effenberg0x0 on 2011-11-30
> **kansasnoob said:**
> If you try to "jump" versions w/o following the proper upgrade path you'll end up with a bunch of broken, unreliable crap :(

But help me understand it:
1) I edit and update repos on sources.list (let's say Lucid to Precise)
2) When I apt-update, I'll receive the full list of pairs [packages/versions] I should have.
3) When I ran apt-get upgrade, It will propose a solution, like: remove x, install y, upgrade z packages.

As long as I do it completely and don't interrupt the process, why wouldn't it work?

**EDIT:**
Or if I use do-release-upgrade or apt-get dist-upgrade on step 2, wouldn't the process be the same?
It fails because apt is *known* to fail in these situations (a bug, a limitation, etc), or for some other technical restriction?

---

### Post by mc4man on 2011-11-30
Happen to have a lucid install I put in this morning to compare hdd temps vs. OO & PP on this laptop. (OO & PP run a min 10 F higher which unfortunately is a big deal on this laptop, hdd is right underneath left palm rest

Anyway this is what it will propose to do .(pick one or suggest another & we'll see.

---

### Post by effenberg0x0 on 2011-11-30
> **mc4man said:**
> Happen to have a lucid install I put in this morning to compare hdd temps vs. OO & PP on this laptop. (OO & PP run a min 10 F higher which unfortunately is a big deal on this laptop, hdd is right underneath left palm rest

Anyway this is what it will propose to do .(pick one or suggest another & we'll see.

Hi mc4man, thank you for the info. Interesting to see the differences.
```
sudo apt-get upgrade
359 upgraded, 0 newly installed, 0 to remove and 770 not upgraded.
Need to get 132MB of archives.
After this operation, 118MB disk space will be freed.
Do you want to continue

doug@doug-laptop:~$ sudo apt-get dist-upgrade
1084 upgraded, 555 newly installed, 33 to remove and 37 not upgraded.
Need to get 716MB of archives.
After this operation, 1,422kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

doug@doug-laptop:~$ sudo aptitude dist-upgrade
<hell broke loose>

doug@doug-laptop:~$ sudo  do-release-upgrade
Checking for a new ubuntu release
No new release found
doug@doug-laptop:~$ 
```

I would like to see what would happen to the average user, using the most command tool. sudo apt-get update && sudo apt-get upgrade, when using pp sources in this lucid install, if you are up to the test. I believe it has a chance of working.

---

### Post by mc4man on 2011-11-30
> **effenberg0x0 said:**
> 

I would like to see what would happen to the average user, using the most command tool. sudo apt-get update && sudo apt-get upgrade, when using pp sources in this lucid install, if you are up to the test. I believe it has a chance of working.

Whether the aptitude command would complete I don't know, though it's seems the most likely to be recoverable from. 

I'll run the the one you'd like to see..

---

### Post by mc4man on 2011-12-01
So here's what happens with apt-get update & upgrade, not too good though fortuitously it errored out after installing some packages

A reboot was back to lucid+ with lots of broken packages, no browser but but still had network/internet

A following run thru the aptitude command improved slightly, still loads of errors, broken/uninstalled packages. The real hanging point was libc6-dev.

A second run thru aptitude improved, still many broken inc. libc6-dev, 

some manual work was then possible, so all broken are gone, what happens when booting don't know yet, had to go to a OO install to update-grub so the new kernel will show

The gist of it is this isn't really a valid upgrade path, even if it's now a working PP which is 50-50

---

### Post by mc4man on 2011-12-01
Finally to put a capper on - booted to unity-2d, (unity-3d should work) there are a number of upgrades,  Currently the theme or something is from lucid - screen

Is the install saveable - probably, will it have issues - maybe - pretty odd seeing old window decorations

edit = a little work in synaptic & it's PP I guess - no apparent issues but I wouldn't 100% trust

---

