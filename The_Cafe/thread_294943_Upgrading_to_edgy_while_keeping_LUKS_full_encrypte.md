---
title: "Upgrading to edgy while keeping LUKS full encrypted system"
date: 2006-11-07
forum: The Cafe
---

### Post by zetetic on 2006-11-07
Hi, I'm an ubuntu nob and this is my first post here, so please forgive my lack of knowledge.

I'm running Ubuntu dapper LTS and I'm very pleased with the system. I'm finally feeeling windows free and that is a great sensation!

I have followed the "EncryptedFilesystem" (by Mikhail Lukyanchenko) and "EncryptedFilesystemHowto5" (by John Bindel) HOWTOs and I managed to get a perfectly working encrypted system.

My system (a Pentium 4 desktop, 120 GB hard drive with just Ubuntu on it) has the following partitions:
a) hda1 (unencrypted -> /boot)
b) hda2 (encrypted -> /)
c) hda3 (encrypted -> /home)
d) hda5 (encrypted -> swap)
e) hda6 (encrypted -> /cryptokeys)

I have both desktop environments: GNOME and KDE.

Everything is working perfectly but now I want to upgrade to Edgy, using the internet method described on "EdgyUpgrades" (I mean using the <gksu "update-manager -c"> method).

When rebooting for the first time after upgrading to Edgy, I want to keep the perfectly working encrypted system I have now.

So it would be nice if someone could please describe here how can this be accomplished.
If you don't mind please post the commands one must enter on terminal in order to keep the perfectly working encrypted system when upgrading to Edgy.

---

### Post by PriceChild on 2006-11-07
*Hopefully*, everything should work fine and the encryption shouldn't matter.

However, upgrades may not always go smoothly. - You are advised to backup ALL data before starting the official upgrade process.

I STRONGLY advise you to contact the authors of those howtos so see if they have any experience of upgrading, whether they are aware of any issues etc.

Good luck, Pricey

---

### Post by zetetic on 2006-11-07
Hi, thanks for your answear.

I have good reasons to be afraid of performing an edgy upgrade with my actual full encripted dapper system (except /boot).
I'm relying on the following threads:
[http://www.ubuntuforums.org/showthread.php?t=286311&highlight=luks%2Bedgy](http://www.ubuntuforums.org/showthread.php?t=286311&highlight=luks%2Bedgy)
[http://www.ubuntuforums.org/showthread.php?t=287958&highlight=luks%2Bedgy](http://www.ubuntuforums.org/showthread.php?t=287958&highlight=luks%2Bedgy)
[http://www.ubuntuforums.org/showthread.php?t=270919&highlight=edgy%2Bluks](http://www.ubuntuforums.org/showthread.php?t=270919&highlight=edgy%2Bluks)
[http://www.ubuntuforums.org/showthread.php?t=287375&highlight=luks%2Bedgy](http://www.ubuntuforums.org/showthread.php?t=287375&highlight=luks%2Bedgy)

As you see, I like to read the whole forum before asking for help or advice. :)

Unfortunately those threads are not self explanatory.

So I would be delighted if the authors of the mencioned HowTos or someone with experience of upgrading from dapper to edgy with a previous LUKS full encripted system could through some light on this subject.

Have a nice day,
zetetic

---

### Post by QCompson on 2006-11-07
I think it may be wise to wait a bit.  There is currently a problem with Edgy's cryptsetup, as you have discovered, and you are not asked your password at boot.  Someone please (please!) correct me if I'm wrong.

Although I only have an encrypted home and swap under Dapper, I am waiting until things are working smoothly before I upgrade to Edgy.  There are apparently work-arounds using pam_mount and such, but I prefer the way it is handled in dapper.

Incidentally, I recently tried out the debian-installer beta for debian-testing, and there are options for encrypting the whole system.  It's fairly easy to setup and works wonderfully.  I hope that eventually Ubuntu can have the same functionality in it's installer.

---

