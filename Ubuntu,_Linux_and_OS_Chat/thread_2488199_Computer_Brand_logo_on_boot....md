---
title: "Computer Brand logo on boot..."
date: 2023-06-26
forum: Ubuntu, Linux and OS Chat
---

### Post by hexbolt86 on 2023-06-26
I've noticed some distros do this and others don't, and this is something that's puzzled me for a while...

What is the behind-the-scenes magic so that when Ubuntu boots, you see the same manufacturer's logo as you do when booting Windows?

---

### Post by ne29914 on 2023-06-26
What you're seeing is *before* boot and comes from the BIOS. It's nothing to do with the OS.

---

### Post by hexbolt86 on 2023-06-26
Actually, it *does.* Not all distros show the hardware mfg's logo.

---

### Post by SeijiSensei on 2023-06-29
I began noticing this when distributions like Kubuntu starting putting their logo further down on the initial page rather than in the middle as they used to do. Started maybe a year or two ago. So now I see the manufacturer's logo with Kubuntu underneath. It is not there during the BIOS sequence obviously, but it appears once the computer starts the boot code. Probably a kernel-level feature.

---

### Post by #&amp;thj^% on 2023-06-29
> **SeijiSensei said:**
> I began noticing this when distributions like Kubuntu starting putting their logo further down on the initial page rather than in the middle as they used to do. Started maybe a year or two ago. So now I see the manufacturer's logo with Kubuntu underneath. It is not there during the BIOS sequence obviously, but it appears once the computer starts the boot code. Probably a kernel-level feature.

+1 I find exactly the same.

---

### Post by DuckHook on 2023-06-30
My understanding is that it's a UEFI function. I can't remember what it's called, but if the distro hooks into the UEFI function that allows the display, then the manufacturer's logo gets displayed. If the distro bypasses this function, then no manufacturer's display.

I sorta like it, TBH, but it's not really a big deal either.

---

### Post by guiverc on 2023-06-30
I assume you're talking about when  plymouth is showing.

Many OEMs wanted to include Ubuntu etc. on their systems as an option on order, but they don't just want Ubuntu showing, but also their OEM logo (ie. Dell what the Dell logo, HP want their HP to show etc)...  As a consequence the plymouth was adjusted to allow for this many cycles ago.

This maybe what you're asking about.. (*then again it may not be*)...

It was a requested change by OEMs (*if you're talking about plymouth*) and impacts all ISOs using the updated plymouth packages (*but not older ISOs using older packages*).

*It was some time ago (many cycles**) that this change was implemented, thus my memory of it is minor, but if I wanted details I'd explore the plymouth changelogs as I recall doing some QA relating to it many cycles ago.*

---

### Post by DuckHook on 2023-07-01
> **guiverc said:**
> I assume you're talking about when  plymouth is showing.
Interesting.

I assumed it was the display that comes up even before GRUB kicks in. I get an overlay with both the OEM logo and Ubuntu, then the GRUB selection afterwards. I assume this is well before Plymouth, but maybe I'm mistaken.

@OP

Where in the boot process are you referring to?

---

### Post by guiverc on 2023-07-01
Duckhook...

No the plymouth logo doesn't appear before grub as you're expecting..

The altered plymouth screens occur afterwards, and allow an OEM brand (HP, Dell, etc) to appear on the ~'half' of the plymouth screen, whilst the Ubuntu (or *flavor*) logo shows in the other half.

If you're seeing anything before grub, that'll be *firmware* related I bet, and I have no special knowledge there (*I see it on some boxes, not on others, firmware settings on some boxes give me some control but no control on others*).

--
Additional thoughts.

I've not noticed any change, or at least don't recall any changes on the hardware I QA test with over various Ubuntu releases before grub shows (*not sure I'd trust my recall though*). 

I have noticed differences in how GRUB shows varies on releases/ISOs (eg. on a sony vaio *thingy* I have, on older releases grub would be full screen, now it uses only a small portion of the screen (*casper version specific if I recall correctly here*), but that's not before grub.

---

