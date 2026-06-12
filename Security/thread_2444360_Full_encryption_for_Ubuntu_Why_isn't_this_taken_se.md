---
title: "Full encryption for Ubuntu: Why isn't this taken seriously?"
date: 2020-05-29
forum: Security
---

### Post by Paddy Landau on 2020-05-29
**Warming: Contentious issue**

I have come back to this issue again and again, and I am frankly bewildered and disconcerted as to why Canonical isn't taking the issue of [full encryption for an Ubuntu installation]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1773457") seriously.

Ubuntu is supposed to be a system "for humans", and it's what attracted me to Ubuntu in the first place and allowed me to successfully convert several other non-technical people to it.

So, I find it both disappointing and frustrating that, in an age when encryption has become vital, and in many cases is required legally or contractually (or both), that encryption seems to be an afterthought, where only experienced people with technical expertise can manage this. It's actually worse now than when I started using Ubuntu, thanks to the deprecation of [FONT=lucida console]ecryptfs[/FONT].

As much as I love *buntu, I can no longer recommend it to other people, telling them instead to go for Windows, Mac or Chromebook. So sad.

Ubuntu does allow an encrypted installation — excluding [FONT=&amp]/boot[/FONT], bizarrely — as long as you choose the entire hard disk, thereby wiping any other extant system (whether Windows, another Linux installation, or whatever). But, the vast majority of users use a dual-boot system. If you install a dual-boot, you can't encrypt Ubuntu, especially since [FONT=lucida console]ecryptfs[/FONT] has been deprecated. In any case, ecryptfs only encrypts data, and doesn't protect the rest of the system against bad actors.

It's not as if full encryption (including [FONT=lucida console]/boot[/FONT]) can't be done — it's been repeatedly [proven possible]("https://help.ubuntu.com/community/ManualFullSystemEncryption") to [encrypt everything]("https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019") apart from Grub itself.

So, what's going on? Why the reluctance to implement this? More importantly, what can we do about it? (I'm not a programmer, otherwise I'd program it myself, with the help of others, and submit the patch to Canonical.)

---

### Post by TheFu on 2020-05-29
I agree with most of Paddy's statements, but disagree on a few too.
ecryptfs is a bad implementation. LUKS is far better for so many reasons.

All portable devices should be encrypted by default and users given the opportunity to deselect encryption if they choose.  This stance assumes that all users will also create proper backups of the encrypted storage.  After all, if anything bad happens to storage that is encrypted, no data recovery is possible. Restoring the data from backups is really the only viable answer.

OS upgrades and migrations of encrypted storage has always been a little challenging.  Fortunately, LUKS is extremely stable, so the underlying code between OS upgrades almost certainly will be compatible.

I'd never recommend someone concerned with security run either Windows or OSX.  A chromebook running chromeos is probably the most secure networked OS available today.  For non-technical people, ChromeOS is probably the best option from a security standpoint.  Terrible for privacy, but great for security.

I don't know many people who dual boot.  Most of my friends use Linux on dedicated systems. I can understand why someone trying to dual boot might want encryption, but I also understand the added boot complexities that brings which MSFT will likely screw up for the Linux-side being able to boot.

Canonical seems to want simple solutions and lets that override other considerations.  By limiting encryption to only dedicated systems, they'd removed a tremendous amount of complexity from the boot and install process.  After all, encryption is extremely platform specific.

---

### Post by Paddy Landau on 2020-05-29
@TheFu, thank you for those viewpoints. You make a lot of sense particularly in your last point.
> **TheFu said:**
> ecryptfs is a bad implementation. LUKS is far better for so many reasons.
Absolutely, yes. The problem is that for your "average" user, who won't understand the problems and who dual-boots with Windows, [FONT=lucida console]ecryptfs[/FONT] seems to be the only usable option. It takes someone with experience to be able to create an encrypted installation with dual-boot.
> **TheFu said:**
> I'd never recommend someone concerned with security run either Windows or OSX. … I don't know many people who dual boot.
Some businesses use Windows-only applications in addition to Linux, and so they require Windows.

On thinking about this, I suggest that the best answer is to use a full-disk encryption (including [FONT=lucida console]/boot[/FONT]), with UEFI enabled of course, and then run Windows if required in a virtual machine within Linux. Of course, this does increase the hardware requirements, although that shouldn't be onerous for basic business tasks. Anything requiring heavy processing such as video-editing will be affected.
> **TheFu said:**
> A chromebook running chromeos is probably the most secure networked OS available today.
If this is true, that doesn't say much about Windows or OSX, does it! You'd think that two of the richest companies in the world could figure this out. Doesn't BitLocker do this on Windows?

Canonical uses full-disk encryption for an entire disk, but without encrypting /boot. Do you know why [FONT=lucida console]/boot[/FONT] is omitted? It seems to be a silly omission.

---

### Post by TheFu on 2020-05-29
Bitlocker has all sorts of issues, the biggest is that if a login uses a MSFT account, then the key to unlock the storage is stored on MSFT servers.
Apple has always been behind on security, because they are just a little different from other OSes.  Linux can't do that since most servers in the world today and almost 70% of smartphones run Linux.  Linux is huge in the non-desktop area.  Windows is huge in desktops.  Apple is ... well ... they make some nice phones and tablets.  iOS is very secure, until any 3rd party application is loaded.

Don't know about the other things. You'd need to ask someone on the encryption team at Canonical for any reasons.  Perhaps asking in IRC would be best or on Discord?

---

### Post by EuclideanCoffee on 2020-05-29
I agree, but I have another point. I would like to see tpm fully supported. It is not just Ubuntu slow to integrate but also the Linux project. :(

---

### Post by TheFu on 2020-05-29
ChromeOS running on a Chromebook used TPM.
[https://www.chromium.org/developers/design-documents/tpm-usage](https://www.chromium.org/developers/design-documents/tpm-usage)

---

### Post by EuclideanCoffee on 2020-05-29
I didn't say TPM is impossible. Have you integrate it to Ubuntu and had to manage it for a large group of computers? It's a task.

---

### Post by CharlesA on 2020-05-29
> **EuclideanCoffee said:**
> I agree, but I have another point. I would like to see tpm fully supported. It is not just Ubuntu slow to integrate but also the Linux project. :(

That would be nice. When I first got encrypted root (but not /boot) set up, I tried getting it to read the keys off the TPM, but it was more of a pain in the butt than I wanted to deal with.

I tried a few times, but gave up and just enter a passphrase on each boot. My box is a server, so it doesn't get rebooted that often, but it's still annoying that TPM wasn't well implemented.

---

### Post by Ranbunta_Bantubunt on 2020-06-13
Howdy, I am a relative newcomer to ubuntu, but I think I can offer some information here. You *can* encrypt the /boot partition, and you can encrypt partitions even when dual-booting or triple-booting with other OSes. 

A guide to how to do these things is given here:

[https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019)

Now I agree with the OP that full-disk encryption should be more of a focus, and even the solution above is not 100% FDE, as the Grub partition remains unencrypted. But it's getting close. The main problem with having the grub partition unencrypted is that someone could tamper with it if they get access to the laptop. I'm not super worried about that but, it should be protected against. 

However, as OP notes... full disk encryption is an absolute must these days, and actually has always been an absolute must for me at least, even before it existed. :) 

I also agree many people dual-boot. The ubuntu installer offers an encryption option (which excludes /boot :() in the installer, but only if you wipe the whole disk and install only ubuntu. It would be nice to offer this option even with more complex install arrangements.

(While we're talking about the installer, they should remove the reference to "CD"s and rarely are compact disks used. I recall the concept of a "CD" was referenced a few times when I ran the installer for 20.04, such as "Run from this CD" and "You may have received along with this CD" and the like.... uhm.....)

Now I have a question, if I may, the absolutely wonderful, very useful guide to almost-FDE that I linked to earlier, mentions that according to their instructions, one can only use LUKS1 as Grub did not, at the time, support LUKS2. Grub now does support LUKS2. I have looked through the standards for LUKS1 and LUKS2 and I don't see any reason (so far) to think LUKS2 is any more secure but it does offer more features. But next install I do, I'd like to try LUKS2 instead. I am installing a new notebook soon as soon as I get it in the mail. 

Anyone have any insight into whether one can follow the guide above, but use LUKS2 instead of LUKS1? If so, anything else need to be done differently from the guide? I may just give it a shot and see if it works if the notebook comes and I dont have any further insight. 

Thanks all!

---

### Post by Ranbunta_Bantubunt on 2020-06-13
Oh I now see that the OP actually posted a guide to full disk encryption... 

[https://help.ubuntu.com/community/ManualFullSystemEncryption](https://help.ubuntu.com/community/ManualFullSystemEncryption)

A different guide than the one I followed, but very detailed. Sorry I didnt see that before!

At any rate, I would be interested if anyone had insight into whether I can now use LUKS2 with the general method described in the two guides referenced, now that Grub supports it. 

Thanks

---

### Post by Ranbunta_Bantubunt on 2020-06-16
Ok so I did the install, using luks1 to be safe :) I understand that it is possible to convert to LUKS2 in the future so I will consider doing that sometime. :)

---

### Post by kevdog on 2020-06-16
Is it really a big deal that /boot isn't always encrypted?  I think some of the problems may be with the various boot loaders themselves.  I don't think some of the boot loaders are compatible with many types of encryption of than grub with LUKS.

---

### Post by CharlesA on 2020-06-19
> **kevdog said:**
> Is it really a big deal that /boot isn't always encrypted?  I think some of the problems may be with the various boot loaders themselves.  I don't think some of the boot loaders are compatible with many types of encryption of than grub with LUKS.

I don't think it is, but I've been using a USB flash drive as /boot because I've got an internal USB header.

It made my overall partitioning scheme a hell of a lot easier since I was able to encrypt the whole drive instead of just the extended partition.

FWIW, I checked the box I did an install on about 6 months ago and the root device is running luks2.

---

### Post by Ranbunta_Bantubunt on 2020-06-22
> **kevdog said:**
> Is it really a big deal that /boot isn't always encrypted?  I think some of the problems may be with the various boot loaders themselves.  I don't think some of the boot loaders are compatible with many types of encryption of than grub with LUKS.

I agree, for the large majority of users, according to the threat model they are protecting against with encryption, it's not a big deal that /boot is not encrypted. 

There are some, though, for whom it would matter.

---

