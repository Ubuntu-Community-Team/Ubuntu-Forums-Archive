---
title: "QA cadence week 5 begins now"
date: 2013-01-26
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2013-01-26
Based on this:

[https://wiki.ubuntu.com/QATeam/Cadence/Raring](https://wiki.ubuntu.com/QATeam/Cadence/Raring)

And the fact that all but the "upgrade" tests on [the QA Tracker]("http://iso.qa.ubuntu.com/qatracker/milestones/243/builds") are at "20130126" I think this is correct info :D

---

### Post by ventrical on 2013-01-26
The daily iso's have been a horror. They do not even detect displays correctly and are putting nvidia drivers in with ATi graphics cards.

  I have always had really good  experience/luck with the isos bit this cycle has been rough. especially after the Nov22 phenom release.

---

### Post by kansasnoob on 2013-01-28
I got nowhere with the installer:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1107541](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1107541)

---

### Post by kansasnoob on 2013-01-28
> **kansasnoob said:**
> I got nowhere with the installer:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1107541](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1107541)

It looks like this has been a problem since November 19th :(

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701)

This certainly stifles testing efforts. It would be nice to have an Alpha to roll back on instead of using the mini.iso or upgrading a fresh Quantal install.

---

### Post by ronacc on 2013-01-28
the installer has been particularly troublesome this cycle .

---

### Post by kansasnoob on 2013-01-28
> **ronacc said:**
> the installer has been particularly troublesome this cycle .

And it really does make cadence testing nearly impossible ............ it's basically a bad joke that I just can't find the humor in :(

I'm subscribed to the applicable bug reports so I'll just bow out of testing until I see a fix released or until Beta 1 I guess.

---

### Post by ronacc on 2013-01-28
I lucked out and got a good install a couple of weeks ago and have just been keeping it updated , I keep the daily zsync'd and try every few days, I saw some updates to usb creator today , hopefully that will work now I'm bored of burning coasters .

---

### Post by kansasnoob on 2013-01-29
I have two Ubuntu-GNOME-Remix installs that I did with the mini.iso (CLI installs + gnome-shell + ubuntu-gnome-desktop), one pretty much "out-of-box" and the other with the Gnome3 and Staging PPA's, that I've kept alive.

But I wanted to do some specific testing with both Lubuntu and Xubuntu knowing that what I'm going to try will likely blow things up :D

Lubuntu still has alternate images so I'll try one of those.

---

### Post by kansasnoob on 2013-01-29
I added a comment to that bug report after a couple of days of intense testing:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701/comments/47](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701/comments/47)

> 

What I seem to be finding is that if 3 primary partitions and one extended partition exist the installer stalls at "Preparing to install". The number of logical partitions within the extended partition seems to make no difference.

But the plot thickens a bit with two drives connected. If I have only one drive connected with two primary partitions and one extended partition (containing any number of logical partitions) the installer proceeds as expected, but if I connect another drive with even one additional existing primary partition the installer stalls.

I need to do quite a bit more testing to see if that applies to three drives or not, eg; three drives with one primary partition on each, and at least one extended partition on one drive, but so far it doesn't seem to matter what file system is in use on any existing partition.


But I also went back in time testing older iso's (that's why I still use discs so I have archives) and I'd guess the problem actually began here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1053030/comments/4](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1053030/comments/4)

> 

This bug was fixed in the package ubiquity - 2.13.4

---------------
ubiquity (2.13.4) raring; urgency=low

  [ Colin Watson ]
  * Huge pile of minor changes to make ubiquity compatible with pep8 1.3.

  [ Dmitrijs Ledkovs ]
  * Clear "Read release notes or update the installer" if neither action
    are possible. (LP: #1066302)
  * If there is only one disk & use_device recipe is used, change next step
    button to "Install Now". (LP: #1050044)
  * When auto-partitioning is not possible, allow to manually partition
    the same drive installation medium is on. (LP: #1053030)
  * Fix the question_dialog height-for-width (LP: #862270)
  * Fonconfig-voodoo is gone, not sure if some other "fontconfig"ury
    should be called instead. (LP: #1043031)
  * Fix partman test_windows_only: if resize option is available, use_disk
    should be available as well.
  * Fix test_translated, after moving question dialog into glade from
    construction by hand.
  * Automatic update of included source packages: base-installer
    1.122ubuntu14, debian-installer-utils 1.91ubuntu6, flash-kernel
    3.0~rc.4ubuntu28.

  [ Martin Pitt ]
  * ubiquity/gtkwidgets.py: Don't use GObject.constants, just use the
    constants from GObject as intended. Fixes a crash with pygobject
    3.7.2.
  * Use glib API from the GLib GI module instead of GObject. The latter
    has been deprecated for a long time and triggers warnings with pygobject
    3.7.2.
 -- Dmitrijs Ledkovs <dmitrij.ledkov@ubuntu.com> Tue, 27 Nov 2012 11:47:01 +0000


Now I need to take a shower so the dogs will associate with me again :lolflag:

---

### Post by kansasnoob on 2013-01-29
Hmmmmm, more likely here:

> ubiquity (2.13.2) raring; urgency=low

  * Try to copy signed kernel from vmlinuz.efi in preference to
    vmlinuz.efi.signed; vmlinuz.efi is friendlier to archaic 8.3 file name
    restrictions which apply to isolinux.
  [B]* Automatic update of included source packages: partman-auto 105ubuntu1,
    partman-auto-lvm 46ubuntu1, partman-crypto 55ubuntu1, partman-lvm
    82ubuntu1.[/B]

 -- Colin Watson <cjwatson@ubuntu.com>  Mon, 12 Nov 2012 15:11:08 +0000

I need to see if I can downgrade that version of "partman" and then see what happens :guitar:

---

### Post by ventrical on 2013-01-29
> **ventrical said:**
> The daily iso's have been a horror. They do not even detect displays correctly and are putting nvidia drivers in with ATi graphics cards.

  I have always had really good  experience/luck with the isos bit this cycle has been rough. especially after the Nov22 phenom release.


 @ ronac

 Like I said .. I kept the Nov 22 .iso... only problem was that is is 64 bit and not 32 so I can't
get any type of reasonably working .iso for i386... hmmm guess I'll zsync todays daily.

---

### Post by screaminj3sus on 2013-01-31
installed from the 29th iso yesterday, only problem I had was the dconf-service crash which should be fixed with today's updates.

well I also had another issue where for some reason it wouldn't boot when put on usb via unetbootin, kept giving me corrupt kernel image error, I had to dd the iso which worked, I had burned some older dailyies fine with it. I would have used startup disk creator but its too much of a buggy mess in 12.10 (what I was running at the time) and kept freezing/crashing/being weird. (on a blank usb it would finish "copying files" impossibly quick, and then just get stuck on "installing bootloader" forever)

---

### Post by ventrical on 2013-01-31
it will work good on some machines and freeze up on others.

---

### Post by kansasnoob on 2013-02-01
[The Lubuntu alternate 20130131 i386 image]("http://iso.qa.ubuntu.com/qatracker/milestones/243/builds/36476/downloads") works well :D

But the next image will have a new kernel, meaning a rebuild, so 20130201 may or may not work as well ;)

I only encountered one minor problem. There's a duplicate entry for the installation image in software sources:

[ATTACH]230900[/ATTACH]

I'm going to try some CLI installs with this image since [this bug]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701") prevents me from installing in the manner I'd like.

I'm sure glad that Lubuntu kept the alternates :D

---

### Post by ventrical on 2013-02-01
It's now fixed with Intel graphics installs. I haven't hasd time to do much else.  Have had quite a cold up here in the Great Lakes. Low productivity :)

---

