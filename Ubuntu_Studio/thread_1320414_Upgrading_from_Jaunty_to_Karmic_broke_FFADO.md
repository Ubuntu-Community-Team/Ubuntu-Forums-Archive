---
title: "Upgrading from Jaunty to Karmic broke FFADO"
date: 2009-11-09
forum: Ubuntu Studio
---

### Post by blakew on 2009-11-09
The title says it all. I upgraded from Ubuntu Studio 9.04 to 9.10, and FFADO now claims that it can't create a streaming device, when called identically to the way it was in Jaunty.
With verbosity up to 3, jackd reports that "No firewire adapters (ports) found.". That to me suggests an issue with backwards compatibility in the new firewire stack. I've heard of others having success with FFADO in Karmic, however I have no idea whether they upgraded from Jaunty or not.
Do I have to run any specific arguments when calling jackd, or should FFADO just work?

---

### Post by trulan on 2009-11-09
The upgrade probably broke your permissions and security limits settings.  I'd go through setting things up as you would a fresh install.  Here's a guide:
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

In my experience, Ffado in Karmic works far better than it did in Jaunty.  I am using a Presonus Firepod.

One thing I have had to do on occasion, after upgrades, is to boot the computer with the firepod turned on and plugged in.  It seemed to have to do this to properly initialize the device - one bootup like that and then everything worked.  I did not have to do this on my fresh install, only after a few of my upgrades.

---

### Post by blakew on 2009-11-10
Seems that either rebooting did the trick, or whatever settings I fiddled with. Now, to get me-tv working with jackd... :p

---

### Post by trulan on 2009-11-10
Glad it's working for you!

I'll bet rebooting fixed it.  The problem occurs when raw1394 is only accessible with root permissions.  To use it properly (without running Jack as root) it needs to be accessible via the video group.  And for some reason, even though Ubuntu Studio Controls writes the permissions line properly, raw1394 is not actually added to the video group unless you reboot with the 1394 device connected.

Like I said, I have only seen this problem on the two upgrades I did.  Everything worked properly when I did a fresh install of 9.10.

I would think that there should be a command that would initialize things properly without booting with the device connected.  But I don't know what it would be.

---

### Post by blakew on 2009-11-10
Well, it's not working again :S

---

### Post by trulan on 2009-11-10
Can you post the output of
```
ls -al /dev/raw1394
```
and
```
groups
```
and maybe post a screenshot of your Jack settings?

---

### Post by blakew on 2009-11-11
It seems to indeed be a chown'ing problem, I checked and /dev/raw1394 was root:root.
My user is definitely in the video and audio groups, I'd say it's a security setting that I've neglected to alter.
EDIT: aha, I toggled the setting in Ubuntu Studio Controls for raw1394 off, applied, then on again, and after a reboot it seems to be working... I'll try rebooting again to see what happens.

---

### Post by Stochastic on 2009-11-11
There is a small bug in Ubuntu Studio Controls (has existed there since Jaunty) [Bug #455239]("https://bugs.launchpad.net/ubuntu/+source/ubuntustudio-controls/+bug/455239") that describes the permissions rule of raw1394 as being erased every now and then.

This app is slated for a bit of an overhaul for the Lucid cycle (if we have time), so hopefully things will change in the near future.

---

### Post by kayosiii on 2009-11-11
I have found it easier to make the udev rule as a seperate file...
this stops it from being overwritten.

The file I use is written as
/lib/udev/rules.d/50-raw-firewire.rules
and contains....
```
KERNEL=="raw1394",      NAME="raw1394", GROUP="video"
```

---

### Post by trulan on 2009-11-13
The problem I saw was a bit different.  Even though the udev raw1394 line was in place and written properly, it would not go into effect unless I booted with my firepod attached.  This happened for me several times during the Karmic development cycle, and once with a 9.04 to 9.10 upgrade.

So I was wondering:  Is there a command to run that would invoke the udev rules, or can this only be done by rebooting?

---

