---
title: "Trying to understand Ubiquity Encryption on Install &amp; how to backup LUKS Headers"
date: 2015-11-08
forum: Security
---

### Post by mikodo on 2015-11-08
1. Is it this?  [https://help.ubuntu.com/community/encryptedZfs](https://help.ubuntu.com/community/encryptedZfs)

2. Different? 

3. With the installer directed to encrypt the full disk, How does one backup the LUKS Header. What Ubuntu Community tutorials are there on that?

4. And, to you experts, how do *you backup the LUKS Header(s)?

Thank you.

---

### Post by matt_symes on 2015-11-08
Hi

> **mikodo said:**
> 1. Is it this?  [https://help.ubuntu.com/community/encryptedZfs](https://help.ubuntu.com/community/encryptedZfs)

No it's not zfs encryption. 

It's dm-crypt with a LUKS volume on top as dm-crypt is *block level* encryption.

BTW: ext4 *file system level* encryption is coming.

[http://lwn.net/Articles/639427/](http://lwn.net/Articles/639427/)

> 3. With the installer directed to encrypt the full disk, How does one backup the LUKS Header. What Ubuntu Community tutorials are there on that?

4. And, to you experts, how do *you backup the LUKS Header(s)?

Thank you.

I'm not using LUKS at the moment but in the past i used to image the entire hard drive. Not really backing up the LUKS headers but just as effective.

Kind regards

---

### Post by mikodo on 2015-11-08
Thank you, matt_symes!

> **matt_symes said:**
> No it's not zfs encryption. 

It's dm-crypt with a LUKS volume on top as dm-crypt is *block level* encryption.

Good. I understand dm-crypt with LUKS enough but, hadn't learned anything about what zfs encryption is.

> **matt_symes said:**
> BTW: ext4 *file system level* encryption is coming.

[http://lwn.net/Articles/639427/](http://lwn.net/Articles/639427/)

I'll be happy to read about that!

> **matt_symes said:**
> I'm not using LUKS at the moment but in the past i used to image the  entire hard drive. Not really backing up the LUKS headers but just as  effective.

By image, was that something like plain dm-crypt maybe? No LUKS header to encrypt. Or, something else?

[https://wiki.archlinux.org/index.php/Dm-crypt/Encrypting_an_entire_system#Plain_dm-crypt](https://wiki.archlinux.org/index.php/Dm-crypt/Encrypting_an_entire_system#Plain_dm-crypt)

---

### Post by matt_symes on 2015-11-08
Hi

> By image, was that something like plain dm-crypt maybe? No LUKS header to encrypt. Or, something else?

What i mean by images is that i would use Clonezilla to perform a byte by byte copy of my laptop's hard drive to an image file on another computer on the network. Clonezilla is great for these types of network backups. You can use ssh.

I used to do this in one of two ways, either by booting into a LiveUSB of Clonezilla on the laptop or by PXE booting Clonezilla onto the laptop at boot time.

It's not backing up LUKS headers but was, and still is, part of my backup strategy.

Kind regards

---

### Post by mikodo on 2015-11-08
Hi, again.

> **matt_symes said:**
> What i mean by images is that i would use Clonezilla to perform a byte by byte copy of my laptop's hard drive to an image file on another computer on the network. Clonezilla is great for these types of network backups. You can use ssh.

I used to do this in one of two ways, either by booting into a LiveUSB of Clonezilla on the laptop or by PXE booting Clonezilla onto the laptop at boot time.

It's not backing up LUKS headers but was, and still is, part of my backup strategy.

I see.

I did some reading after your post. I was under the understanding, (erroneously) that one could not image Dm-Crypt with the LUKS headers. But, I see from that reading one can. I think I got that idea from reading something in the past, that one cannot use image tools to image Ecryptfs, and the likes, that encrypt above the data.

I am not sure about any of that except now, I know one can use image tools with Dm-Crypt and LUKS headers.

And, I know now what is used with Ubiquity!

On to my next learning. Imaging.

Thank you.

---

### Post by matt_symes on 2015-11-08
Hi

I hope i helped clarify what i personally do, for you.

I think on that last point we may have been having two slightly different conversations for a while there.

If you're happy, i'll mark the thread as solved.

Kind regards

---

### Post by mikodo on 2015-11-08
Hi.

I apologize. I was popping in and out of here with reading and "real" life.

Thank you, for marking the thread solved.

For Posterity, on the subject of imaging Dm-Crypt Headers, here is what I had read:

[http://ubuntuforums.org/showthread.php?t=2002237](http://ubuntuforums.org/showthread.php?t=2002237)

Kind regards.

---

### Post by matt_symes on 2015-11-08
Hi

> **mikodo said:**
> Hi.

I apologize. I was popping in and out of here with reading and "real" life.

Thank you, for marking the thread solved.

For Posterity, on the subject of imaging Dm-Crypt Headers, here is what I had read:

[http://ubuntuforums.org/showthread.php?t=2002237](http://ubuntuforums.org/showthread.php?t=2002237)

Kind regards.

Interesting thread and thanks for posting it.

Not really applicable for an image backup but maybe a potential problem if you are creating one image for multiple machines.

A thought provoking read.

Kind regards

---

