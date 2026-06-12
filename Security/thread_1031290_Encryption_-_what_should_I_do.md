---
title: "Encryption - what should I do?"
date: 2009-01-05
forum: Security
---

### Post by Midahed on 2009-01-05
I'm currently running Hardy 8.04 LTS on a system using RAID 1 for / /home and swap.  A while ago I installed Truecrypt and have used that to encrypt my most sensitive data.  I have two 500 MB Truecrypt volumes, one serving as a backup of the other.  This has worked fine for the limited data that it's had to handle.

Recently, I copied loads of data off my old Windows PC onto my Linux box before consigning Windows to history.  Because I'm a bit of a squirrel and don't like throwing old data away, this included stuff like bank correspondence going back many years.

In short, if my PC were to be stolen, there's an awful lot of personal stuff that could be accessed by trawling through all this old data, so I've been looking at the option of encrypting most, if not all, of the data on the PC.

I could try to find all the personal information and move the files into my Truecrypt volume, but this would be time-consuming and tedious.  There's also the concern that, unless the system is fully encrypted, there will always be the possibility of traces being left here and there, or sensitive data being accidentally consigned to a non-encrypted folder at some point in the future.

Truecrypt is fine for relatively small volumes of data, but the fixed volume size is a bit of a pain when larger amounts of data are involved.  I'd rather use an on-the-fly encryption mechanism that doesn't impose a fixed container size, especially as I use rsync to make regular backups.

So, for the ultimate in privacy, I'm drawn towards full disk encryption.  But I have reservations about the impact on performance and the risks of getting completely locked out of my data.  Apart from making regular backups, is there anything else that can be done to reduce the chances this happening?

What's the best compromise?

I've seen the odd comment that LVM + encryption is not a good idea.  Does anyone have any evidence to the contrary?

What about LVM + encryption + RAID 1?  Is that a step too far?

Thanks,

Mike

---

### Post by hyper_ch on 2009-01-05
LVM + encryption + Raid1 does not work by default well (at least not up to 8.10) as there is no appropriate initrd created.

Question is, do you really need LVM? I mean if you have pictures and videos and stuff, you could put it onto an own harddisk and mount it e.g. as /home/USER/Vids or /home/USER/Desktop/Data or whatever... it doesn't necessarily need to be LVM.

Furthermore, Raid1 is not a backup solution. Raid1 is just there to keep a system up an running if one of the harddisk fails.

If you don't want to worry about personal data anymore, simplest is to get an alternate install cd and just install a fully encrypted system. However make sure to make regurarly backups. I'd rather use a nightly cron doing incremental snapshot-style backups than Raid1 alone.

---

### Post by Midahed on 2009-01-05
Thanks for the response.

Heck, no, I wasn't considering RAID 1 as a backup!  That's there purely because I want the convenience of losing nothing if one of the drives fails.  

My backups are on a separate disk (several, actually) and my most precious data is also backed-up weekly and kept 'off site' in encrypted form on yet another drive just in case my PCs and backup drives all get stolen or the house goes up in smoke.

I only mentioned LVM because I'd seen a couple of how-to threads that used it as the basis of a fully-encrypted system.  I got the impression that it was the standard full encryption solution offered in the alternate CD install.

Having had a look at my data again, I certainly need to encrypt my entire home partition, so I'll look again at what I could set-up using the alternate install CD.

What about the performance implications of full encryption (as opposed to just /home and swap).  Is there a noticeable slow-down?

Also, apart from regular backups, are there any things that I can do to prevent being locked out of my data.  I'm thinking about maybe additional protection against a routine system update that manages to break something critical in the encryption management.  I'm already careful about agreeing to new kernel updates until I see how others get on with them, but I think I'd be a lot more nervous about something going wrong if the entire system was encrypted.

Maybe I'm just paranoid.... ;-)

Mike

---

### Post by hyper_ch on 2009-01-05
well, you don't notice much difference in performance using full disk encryption... you'll most likely notice it if you read/write large chunks of data... but during "normal" operation that is not so much the case IMHO.

I notice a difference when I move movie files accross partitions...

In the alternate install you can either setup all the encryption manually (creating swap, home, root, boot partition) or you can let the installer create an auto-encrypted system (you won't have a seperate home partition there).

It's not really difficult to set it up manually, especially not when you're using 8.10 which does not have the "random key swap bug" anymore.

---

### Post by Midahed on 2009-01-05
> **hyper_ch said:**
> ...It's not really difficult to set it up manually, especially not when you're using 8.10 which does not have the "random key swap bug" anymore.
Thanks for your advice.

What's the "random key swap bug"?  Is it something that affects 8.04 or was it just a bug in the early release of 8.10?

I was considering moving to 8.10 at the same time as doing the re-build, but I use Kubuntu and don't want to get into KDE 4 yet, especially as I gather it's a beta release.  So unless it's a major problem I'll probably stick to 8.04 for the moment.

---

### Post by hyper_ch on 2009-01-05
well, it is not there in 8.10 anymore but in previous releases.

---

### Post by Midahed on 2009-01-06
> **hyper_ch said:**
> well, it is not there in 8.10 anymore but in previous releases.
OK, so it was something that affected 8.04?  What did the bug do - is it one of these?

[https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/223072](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/223072)

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/231451](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/231451)

[https://bugs.launchpad.net/ubuntu/+source/partman-crypto/+bug/268517](https://bugs.launchpad.net/ubuntu/+source/partman-crypto/+bug/268517)

The last one seems to suggest that, under 8.04, the only way to successfully create a fully encrypted environment is to use LVM.  However, it's been at status 'new' for several months with no confirmation from other users....

If I've understood correctly, these bugs seem to affect the use of random key encryption, rather than a passphrase.  I'll be opting to use a passphrase, so maybe it's not an issue and I can stick with 8.04?

---

### Post by hyper_ch on 2009-01-06
that's the one:  [https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/223072](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/223072)

As for the rest, I wrote a simple howto: [http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04](http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04)

This one could also be of interest - if you want to enter you decryption key only once: [http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile](http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile)

---

### Post by Midahed on 2009-01-06
Thanks for your help - those links look useful.

---

