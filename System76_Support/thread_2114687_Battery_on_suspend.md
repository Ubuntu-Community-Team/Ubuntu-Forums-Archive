---
title: "Battery on suspend"
date: 2013-02-10
forum: System76 Support
---

### Post by Arioch on 2013-02-10
Hi all,

I have recently purchased a Lemur Ultra (i7, 16Gb RAM). I am overall very pleased with this machine, except for the screen (but that belongs to another topic).

This is my production machine, I use it at work everyday and carry it back home everyday. Because of that I use suspend many times a day. It just works fine, it resumes flawlessly and not once it has frozen or corrupted. But my question is regarding battery life on suspend mode. I have noticed that on 12.10 my new machine can barely withstand a weekend on suspend mode (friday evening to monday morning). Is that normal? Does more RAM memory consume more power on suspend mode?

My old Dell XPS 1530 with Ubuntu 12.04 could go over the weekend easily (4Gb RAM).

Any tip would be appreciated. Sometimes I have many open documents and applications while going to suspend to resume work on Monday, but I have found that battery often don't last long enough and in a few cases lost some unsaved changes on documents.

Thanks!

---

### Post by isantop on 2013-02-11
> **Arioch said:**
> Hi all,

I have recently purchased a Lemur Ultra (i7, 16Gb RAM). I am overall very pleased with this machine, except for the screen (but that belongs to another topic).

This is my production machine, I use it at work everyday and carry it back home everyday. Because of that I use suspend many times a day. It just works fine, it resumes flawlessly and not once it has frozen or corrupted. But my question is regarding battery life on suspend mode. I have noticed that on 12.10 my new machine can barely withstand a weekend on suspend mode (friday evening to monday morning). Is that normal? Does more RAM memory consume more power on suspend mode?

My old Dell XPS 1530 with Ubuntu 12.04 could go over the weekend easily (4Gb RAM).

Any tip would be appreciated. Sometimes I have many open documents and applications while going to suspend to resume work on Monday, but I have found that battery often don't last long enough and in a few cases lost some unsaved changes on documents.

Thanks!

The battery life while in suspend varies depending on how much RAM is installed, and the exact implementation of S3 in the system BIOS. That said, your times seem normal for a Lemur. If you don't plan on using the system for extended periods (i.e. longer than 24 hours), I'd recommend powering off completely.

We are looking into providing hybrid suspend for 13.04, which means that the system both suspends and hibernates at the same time. Thus, if you resume before the battery dies, you get the fast resume from suspend. If the battery dies, then the system will resume from disk after you plug it back in, preventing loss of unsaved changes.

---

