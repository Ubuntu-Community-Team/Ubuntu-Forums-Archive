---
title: "Encryting Individual Files or Folders"
date: 2010-10-19
forum: Security
---

### Post by Kevin1a on 2010-10-19
So here is the deal.  I want to encrypt only certain files or folders on my hard drive.  Basically I have a documents folder that contains scans of my bank receipts, paychecks, and tax papers.  I don't want to encrypt my entire hard drive, just this one folder.  I have a few reservations:

-must be reasonably secure
-must be syncable to an external drive (I back up my home folder to an external HD)
-should be accessible using Windows (I have almost completely switched to Ubuntu, but I still occasionally, though rarely,  use Windows for some things like a few XPS files I have.)
-must be intermediate user friendly (I'm not a noob, but I'm not a guru either)

Are their add-ons to nautilus that will let me make individual files into .rxf files?
Is there a better solution.

A few things that might help:

I have an Asus eeePC 1000HEB running Ubuntu 10.10 and Windows XP.  I use truecrypt for a few external volumes, but not anything on the actual hard drive.  My desktop environment of choice is Gnome.

I appreciate any help you might be able to give me.

---

### Post by HermanAB on 2010-10-19
Howdy,

Four options that I know of:
[LIST=1]
[*]LUKS is compatible with FreeOTFE on Windows.
[*]GPG is available for both Linux and WIndows
[*]TrueCrypt is available for Linux and Windows.
[*]Windows PkZip can also do encryption and is compatible with gzip on Linux
[/LIST]

---

