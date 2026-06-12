---
title: "Saucy Monthly Snapshot Rolling Release."
date: 2013-04-27
forum: Ubuntu Development Version
---

### Post by serdotlinecho on 2013-04-27
So we're not gonna have alpha/beta/rc release anymore? [URL="https://launchpad.net/ubuntu/saucy"]

https://launchpad.net/ubuntu/saucy[/URL]

---

### Post by dino99 on 2013-04-27
that was decided a few weeks back : go for rolling, each month will see a stable release till the end of final 13.10

---

### Post by jppr on 2013-04-27
> **serdotlinecho said:**
> So we're not gonna have alpha/beta/rc release anymore? [URL="https://launchpad.net/ubuntu/saucy"]

https://launchpad.net/ubuntu/saucy[/URL]



What do you do or what you need apha or beta release? you just update your system so you'll always have the latest version of the system. The system goes forward all the time, and is updated as and at least I think that's the most important thing.

---

### Post by serdotlinecho on 2013-04-27
> **jppr said:**
> What do you do or what you need apha or beta release? you just update your system so you'll always have the latest version of the system. The system goes forward all the time, and is updated as and at least I think that's the most important thing.

Yes, I know how to update and upgrade. I've been using ubuntu development release since 11.10 alpha and zsync to update daily image. I'm just asking whether we gonna have beta release or not. That's it.

---

### Post by grahammechanical on 2013-04-27
Ah! So that is how they are going to do it. 13.04; 13.05; 13.06 etc., up to 13.10. and then? 13.11 and onwards up to 14.04? Does it matter? Not really. But people will need jumping in points. And if things get so broken or we want an easy fix, then we can download the latest monthly image and fresh install.

We are on our way to the future.

---

### Post by craig10x on 2013-04-27
How is that going to work?...the first image for 13.10 would be available 1 month after 13.04 was released, so if you download and install it, then it will upgrade each month after that?
I guess i am a bit confused...i thought they weren't going to do this, but now it looks like they are...is this the rolling release they were originally talking about?
And what would happen when 13.10 goes final...is that it? or does it continue to the next ubuntu version (14.04)?

---

### Post by grahammechanical on 2013-04-27
The development branch is the same as what it always has been. That has not changed. What has been clarified it that the development branch is the Ubuntu equivalent  to what others call a rolling release. It seems that we will not have daily images. Or instead of Alpha1, Alpha2, etc., there will be a monthly image for download - snapshots of the code base. Ubuntu 14.04 is the target for so much of what Canonical wants to do. What happens after then, is anybody's guess. A lot can happen in a year. Things move fast. But we know there will be a 13.10 release and a 14.04 LTS release. And the code base for those releases will have to be closed except for support updates.

---

### Post by craig10x on 2013-04-27
Oh, i get it now...monthly isos instead of daily isos for development branch..the first one will be May 25th according to the schedule...Thanks for the clarification...
Yes, a lot is happening and will be between now and 14.04...i guess that is why sometimes it gets confusing, since we don't get official reports from them on what they are doing ;)

---

### Post by ventrical on 2013-04-27
> **grahammechanical said:**
> The development branch is the same as what it always has been. That has not changed. What has been clarified it that the development branch is the Ubuntu equivalent  to what others call a rolling release. It seems that we will not have daily images. Or instead of Alpha1, Alpha2, etc., there will be a monthly image for download - snapshots of the code base. Ubuntu 14.04 is the target for so much of what Canonical wants to do. What happens after then, is anybody's guess. A lot can happen in a year. Things move fast. But we know there will be a 13.10 release and a 14.04 LTS release. And the code base for those releases will have to be closed except for support updates.


 I wonder in what ways (if any) this will affect cadence testing?

---

### Post by grahammechanical on 2013-04-27
Imagine that it is July 2015 and someone wants to install the development branch and the last available image for download was 14.04. Think of all the after install updates. But if there was an image dated June 2015, then that would be a much better way to jump into a daily updated development branch. But as you have noticed we are having to play intelligence officers. If Ubuntu really became what others call a rolling release, we would still need snaps shots of the code base as jumping in points and the code would need to be tested if we were to still have 2 yearly LTS releases. Which we will have because support = service revenue for Canonical.

This is how I imagine things. Expect me to be wrong. No inside information. Just trying to puzzle things out in my own mind.

---

### Post by dino99 on 2013-04-27
now, each monthly iso is supposed to be "stable". This should help to fix the issues more dynamically and narrow down the bugs inheritance flow (new quality job design ) (aka avoid false positive bug reports)

---

### Post by Mathor on 2013-04-27
> **grahammechanical said:**
> The development branch is the same as what it always has been. That has not changed. What has been clarified it that the development branch is the Ubuntu equivalent  to what others call a rolling release. It seems that we will not have daily images. Or instead of Alpha1, Alpha2, etc., there will be a monthly image for download - snapshots of the code base. Ubuntu 14.04 is the target for so much of what Canonical wants to do. What happens after then, is anybody's guess. A lot can happen in a year. Things move fast. But we know there will be a 13.10 release and a 14.04 LTS release. And the code base for those releases will have to be closed except for support updates.

You are mistaken. Monthly snapshots will be made, and if you are running the development release (like if you are in saucy now), then you will continue to roll over into 14.04 after 13.10 is released.

Also, daily isos and updates will continue as normal, as that was cited at UDS of one of the biggest reasons why the development branch has been so successful.

---

