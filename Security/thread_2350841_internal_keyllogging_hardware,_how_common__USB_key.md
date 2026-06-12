---
title: "internal keyllogging hardware, how common?  USB key any better?"
date: 2017-01-28
forum: Security
---

### Post by haplorrhine on 2017-01-28
I am considering this possibility since an invisible keylogger could snag the password to an encrypted system.  I have two questions:

How common are internal hardware keyloggers that I would not see without opening the device?  Suppose I'm encrypting a laptop.  Only USB keyloggers were mentioned in the howtogeek article, giving me the impression that this is very rare.  [http://www.howtogeek.com/180615/keyloggers-explained-what-you-need-to-know/](http://www.howtogeek.com/180615/keyloggers-explained-what-you-need-to-know/)

If I were to circumvent this possibility by keeping the encryption master key on a flashdrive, would I still be vulnerable to a similar sort of attack?

---

### Post by HermanAB on 2017-01-30
If you need to be this paranoid, then you should harden the machine hardware and make it tamper evident.  To do that, you need seals, Locktite and metal boxes, or seals, super glue and plastic boxes.

---

### Post by parkado on 2017-01-31
Internal ones are not that popular - let's be honest, hardware keyloggers in general are not that popular.

And no, any key on USB would be safe from keyloggers since they work a bit differently. 

How to be safe from keyloggers? Use password managers with direct input that send the password directly to inputs without the need for You to type. For anything else, there is only old-school bugsweeping from the room or device. But before this type of paranoia ask Yourself, who is ready to do all that spying on You?

We have usually state-sponsored espionage or industrial espionage (companys after others trade secrets). If You are one of the two then You have way better sources for information than ubuntuforums. So I wouldn't be too worried about it. Of course it doesn't harm anyone to do the casual "walk around the computer" before You sit down : ) But that's just me

---

### Post by haplorrhine on 2017-02-27
It has been happening for some time now.  It is probably father/landlord-condoned or -initiated, but even when legality is questionable I am reluctant to go to the police.  For you see, I was previously diagnosed with a psychotic illness and I could face re-admission, and at the moment diagnosis is complicated by the fact that I'm sort of a friendless schizoid&#8212;I always was&#8212;whose own father won't properly fill out a psychological rating scale.  On the CAARS he circled zero on every item but one.

It does appear that the BIOS firmware might been corrupted on our brand new HP slimline.  All the back panel screws were missing except one, and my Ubuntu Live 12.04 DVD-Rs are running into errors, errors that prevent installation of 12.04 altogether, even though 16.04 runs fine.  Furthermore, the BIOS does not remember my changes when I edit the boot order.  Hopefully I don't have to replace the entire BIOS chip to replace the firmware, for I'll have to do it for two systems with a dirt poor budget.

update

It's a new enough model that it probably uses UEFI + GPT, but commercial attacks against UEFI already exist?  [http://www.intelsecurity.com/advanced-threat-research/ht_uefi_rootkit.html_7142015.html](http://www.intelsecurity.com/advanced-threat-research/ht_uefi_rootkit.html_7142015.html)
I'm wondering whether I would be better off with UEFI or "dual BIOS".

---

### Post by parkado on 2017-03-16
If You do want to be paranoid (which is something to take with precaution) then finding hardware keyloggers is easy. If there is nothing out of the normal outside of the computer then all that is left to do is compare OEM's photos of the inside of the machine with the one You have.

Finding software ones, especially when You suspect firmware based keylogger is not easy. Usually what I've recommended is to throw away the machine. But if that is not possible then one could always try to reinstall and reflash all firmware. CAUTION: this will most likely render Your machine unusable!

What can be done is to install BIOS update or reinstall the latest BIOS. Reinstall the OS and switch out HDD (since there are some APT's that can keep on living on hard drives firmware).

But for domestic situation -  I would use old good counterintelligence techniques. Just keep searching for example how to grow weed and keep an fictional diary how far You are with Your fictional weed business. How You have made enough money so You could start looking for a house and a new car and so forth. If that does not generate some suspicious questions and random visits (hopefully even from law enforcment) then You could find some other creative subject).

PS! Don't over do it - and that goes for everything : )

---

