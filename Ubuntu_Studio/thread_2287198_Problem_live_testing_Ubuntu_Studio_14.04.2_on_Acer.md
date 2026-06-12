---
title: "Problem: live testing Ubuntu Studio 14.04.2 on Acer Aspire X1420 desktop"
date: 2015-07-17
forum: Ubuntu Studio
---

### Post by dejan8 on 2015-07-17
Hi,
I'm Linux/Ubuntu beginner (installed and using Peppermint OS 5 on one laptop, successfully tested Lubuntu on another one), so my apologies in advance for any lame questions or redundant/missing info.
I'm also neither programmer nor developer, but, let's say, an experienced Windows user.

The device is Acer Aspire X1420 desktop, with:
- Windows 7 Ultimate 64-bit, Service Pack 1
- AMD Athlon II X2 220 dual-core processor
- NVIDIA GeForce 6150SE graphics up to 1919MB
- 1TB Hard Drive
- 4GB DDR3 Memory
- DVD-Super Multi drive
- Multi-in-1 Media Card Reader

HDD has an empty partition with cca 450 GB where I plan to install Ubuntu Studio, intended for home audio production at the first place.

The distro is Ubuntu Studio 14.04.02 64-bit.

I tried to test it by live DVD.

The problem is:
after selecting the option "Try Ubuntu Studio without installing", it freezes - the black screen appears, DVD stops running cca half a minute later (judging by its sound), and nothing happens afterwards.

The solutions I tried: 
any option from the "F6 Other options" menu (except "Free Software only"), selected individually and tried successively, with the same outcome in each individual case as the above described.

Possibly relevant additional information (my wild guess after a little bit of Google-ing) -
in BIOS, in "Integrated Peripherals", there are, among others:
- Onboard SATA Controller: [enabled]
- Onboard SATA Mode: [Native IDE]
but - the [Native IDE] option is not active, I mean, there is no any other option offered to select.
(As I already said, I don't know if this BIOS info is of any relevance for my problem.)

Any suggestions?

Thank you all in advance in any case.

---

### Post by jejeman on 2015-07-18
My guess is to try nomodeset option, but, I'm sure you already tried it.

---

### Post by dejan8 on 2015-07-18
> **jejeman said:**
> My guess is to try nomodeset option, but, I'm sure you already tried it.
Yes, I did try nomodeset, and each of the others "F6 Other options"  individually. Nothing happened, but thank you for your answer.

I  still didn't try two or more "F6 Other options" combined. Does anyone  have any suggestion which options should I try to combine?

I mean, I  could go through the whole matrix of all combinations, but I'm less  worried about time consumption than about risk for the system, 
that's why I ask for Other-options combinations suggestions.

Or any other suggestion. Should I try to change anything in BIOS maybe?

---

### Post by howefield on 2015-07-18
Are you in a position to try booting from a USB stick, or try pressing escape while booting the DVD so you can see the text scroll by, maybe get a clue as to where and why it is having a problem ?

---

### Post by jejeman on 2015-07-18
Also, did you check the ISO and the live medium for errors?

---

