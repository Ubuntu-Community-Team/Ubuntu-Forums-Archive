---
title: "File checksums &quot;temporarily&quot; wrong?"
date: 2016-05-22
forum: Security
---

### Post by elagabalus2 on 2016-05-22
I'll preface this post by saying that I'm a layman when it comes to security in general and cryptography in particular, so please forgive me if anything that follows comes off as particularly uninformed.

I am using a fresh (installed yesterday) copy of 16.04 MATE and verified the [MD5]("http://cdimage.ubuntu.com/ubuntu-mate/releases/xenial/release/MD5SUMS"), [SHA1]("http://cdimage.ubuntu.com/ubuntu-mate/releases/xenial/release/SHA1SUMS") and [SHA256]("http://cdimage.ubuntu.com/ubuntu-mate/releases/xenial/release/SHA256SUMS") hashes of the [disc image]("http://cdimage.ubuntu.com/ubuntu-mate/releases/16.04/release/ubuntu-mate-16.04-desktop-amd64.iso") multiple times before burning. I downloaded the image again onto a shared partition when the install was complete in order to start a new VM, and everything seemed to check out when I checked the image's sums again.

Something strange happened during and after the install itself, though. I checked the sums again as the VM was installing and found that the SHA1 and SHA256 sums of the file had changed; running it again all three of the sums were different. I was concerned by this and continued to check the sums to see if they changed again- and they did, back to what they were supposed to be. Later in the day they seem to have changed yet again though, even after the VM was closed, before returning to their originals (as they seem to be right now).

My question is: should I be concerned about the fact that these hash functions periodically returned incorrect sums, and could this indicate that something on my system is maliciously modifying files in some way? I tend to be paranoid about this sort of thing and I'm pretty sure I must be overreacting to something innocuous, but I would like to defer to someone with more expertise on these things in any case.

FWIW debsums -c returns the following on this and my other 16.04 installs:
```

/boot/vmlinuz-4.4.0-21-generic
/usr/lib/python3/dist-packages/cupshelpers/__pycache__/__init__.cpython-35.pyc
/usr/lib/python3/dist-packages/cupshelpers/__pycache__/config.cpython-35.pyc
/usr/lib/python3/dist-packages/cupshelpers/__pycache__/cupshelpers.cpython-35.pyc
/usr/lib/python3/dist-packages/cupshelpers/__pycache__/installdriver.cpython-35.pyc
/usr/lib/python3/dist-packages/cupshelpers/__pycache__/openprinting.cpython-35.pyc
/usr/lib/python3/dist-packages/cupshelpers/__pycache__/ppds.cpython-35.pyc
/usr/lib/python3/dist-packages/cupshelpers/__pycache__/xmldriverprefs.cpython-35.pyc

```

Thank you for the help!

---

### Post by papibe on 2016-05-22
Hi elagabalus2.

A few thoughts...

The installation process may be creating temp files on the ISO, but I'm not really sure of this. If the sums change while the ISO is not mounted, then I would be concern.

My  guesses would be:
[LIST]
[*]If it is a network drive (samba, nfs), I would think you have problems with bad cables or low Wifi signal,
[*]If it is local, I'd suspect a dying hard drive. I would check if the drive is falling.
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by elagabalus2 on 2016-05-22
Thank you for the quick reply papibe.

To address your guesses: the drive in question is an NTFS partition of a solid state drive which is shared between Windows 10 on one "half" and 16.04 on the other. The Windows has not been booted in a few days. I have checked the sums of the file in question throughout the day but they don't seem to have changed at all since yesterday; the Ubuntu install doesn't seem to be acting strangely in any other way either.

Where might you suggest I go from here? Do you think it would be more appropriate to start looking into the health of the drive, or to look for other security concerns?

---

### Post by elagabalus2 on 2016-05-23
Just to be sure I checked the image file in question with two different live CDs I had burned months ago. In both cases the sums of the file were no different from what they are supposed to be, and they've remained so according to the 16.04 install as well.

I feel fairly confident saying that the contents of the file are intact but I'm still concerned about the incorrect sums from before- creating a second VM with the same image didn't seem to recreate the problem, either. At this point should I rule out the possibility of tampering and chalk it up to a disk error or something similar?

---

### Post by elagabalus2 on 2016-05-23
I ran checked the file's sums again today and *again* they were correct- for about half an hour. I ran them thereafter and the sums were once again changed!

I unmounted the partition, remounted it and checked the sums once more only to find that they had gone back to normal. Virtualbox had not been running at the time; clamav was scanning the partition but that doesn't seem to reproduce the errors.

So it seems that something is temporarily either changing the file or interfering with the hash functions themselves...? The latter seems unlikely not least because I used them all while all this was happening and they returned correct values on other .isos in the directory.

Does anyone have any suggestions or ideas at this point? This is beginning to make me nervous... especially considering that this installation is less than 72 hours old.

---

### Post by bashiergui on 2016-05-24
> **elagabalus2 said:**
> My question is: should I be concerned about the fact that these hash functions periodically returned incorrect sums, and could this indicate that something on my system is maliciously modifying files in some way? I tend to be paranoid about this sort of thing and I'm pretty sure I must be overreacting to something innocuous, but I would like to defer to someone with more expertise on these things in any case.
The purpose of comparing hashes of files you download is to ensure you got a legitimate unaltered copy from the internet. You do that when the download is complete. I don't know why you would want to keep checking the hash after the download has completed and passed the initial hash check. I see no value or reason.

Yes I expect the hash would change on a file being accessed. As it's being read by the system then the hash would probably change quite a bit. That's expected and not at all alarming. And it's why no one would recommend comparing hashes during installation.

---

### Post by haplorrhine on 2016-06-06
I think self-hashing, read-only switched flashdrives would alleviate this and other concerns.  I'm not yet aware of such a thing.

---

