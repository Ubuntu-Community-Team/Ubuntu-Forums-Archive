---
title: "New Windows 10 machines may come without the ability to disable secure boot."
date: 2015-03-25
forum: Ubuntu, Linux and OS Chat
---

### Post by CDR Services on 2015-03-25
According to some recent reports, new Windows 10 equipped machines may not give the end user the ability to disable "Secure Boot" in the bios, preventing installation of an alternate OS!

[http://linustechtips.com/main/page/articles.html/_/articles/oems-allowed-to-lock-secure-boot-on-windows-10-r73](http://linustechtips.com/main/page/articles.html/_/articles/oems-allowed-to-lock-secure-boot-on-windows-10-r73)

Looks like it may become even harder to install Ubuntu or other builds in upcoming machines!

Thoughts??:(

---

### Post by CantankRus on 2015-03-25
> At its WinHEC hardware conference in Shenzhen, China, Microsoft talked about the hardware requirements for Windows 10. The precise final specs are not available yet, so all this is somewhat subject to change, but right now, Microsoft says that the switch to allow Secure Boot to be turned off is now optional. Hardware can be Designed for Windows 10 and can offer no way to opt out of the Secure Boot lock down.
[http://arstechnica.com/information-technology/2015/03/windows-10-to-make-the-secure-boot-alt-os-lock-out-a-reality/](http://arstechnica.com/information-technology/2015/03/windows-10-to-make-the-secure-boot-alt-os-lock-out-a-reality/)
Seems like a very convenient way for microsoft to take ownership of the PC and create a Windows only Appliance.

Also Steve Gibson gives an intersting talk on the bios, UEFI and secure boot in this weeks
podcast of Security Now.
[http://twit.tv/show/security-now/500](http://twit.tv/show/security-now/500)
Starts giving in depth BIOS UFEI info at around the 55min mark.

---

### Post by craig10x on 2015-03-25
Of course, they aren't ordering the manufacturers to lock down their computers from turning off secure boot, it is the manufacturer's decision...so that is what will be what counts...any pressure needs to be put on them to ensure they will continue offering the option, not microsoft...
I haven't bought a new computer since windows 7, but from what i understand, ubuntu can be installed with secure boot on because they pay for the microsoft sign on license...

---

### Post by grahammechanical on 2015-03-25
Ubuntu was the first Linux distribution to be able to install with secure boot enabled. And that was with the release of Ubuntu 12.10. All the latest Ubuntu releases can install with secure boot enabled.

This is how it is dealt with by Canonical

[https://wiki.ubuntu.com/SecurityTeam/SecureBoot](https://wiki.ubuntu.com/SecurityTeam/SecureBoot)

That blog post is not even a storm in a tea cup as far as Ubuntu and its flavours are concerned.

The real problem is with manufacturers modifying their implementation of the UEFI protocol to only boot Windows. Do not forget, if we consider that Microsoft's operating systems are the primary target of the writers of malicious code, then switching off secure boot on a Windows machine is not a good idea. 

Regards.

---

### Post by craig10x on 2015-03-25
Exactly, as grahammechanical mentioned, the REAL concern is whether the manufacturers decide to to modify the UEFI protocol to boot only windows (which is a separate matter from secure boot)...if they do that, well, that could essentially kill off linux distros since most people who use ubuntu, fedora and all the others, most often install them on a windows computer to either dual boot with windows or to wipe out windows and install linux...few of us build our own computers, so we would be "up the creek" without a paddle, as it were...

---

### Post by CantankRus on 2015-03-25
Little by little and before you know it.....

---

### Post by monkeybrain20122 on 2015-03-25
Ubuntu and Fedora are able to boot with secure boot on because they pay to get MS's signature. But it can be revoked in the future. And not all Linux users run Ubuntu or Fedora, how about community distros and smaller distros? Don't think that it doesn't concern us if we stick with Ubuntu. If the Linux ecosystem suffers all Linux users will suffer.

 You can see how this lock down is creeping in, not all at once because  there will be too much outcry and possibly lawsuits, but little by  little to lull people into complacency like slow boiling of the frog.The point is a single company that doesn't make the hardware (like Apple) should not have the power to decide who can and who cannot boot. It is a matter of principle. We shouldn't have to bribe someone to work around it.

It is time to start some publicity campaigns aimed at Dell, HP etc..


> Do not forget, if we consider that Microsoft's operating systems are  the primary target of the writers of malicious code, then switching off  secure boot on a Windows machine is not a good idea. 

First of all, most Windows machines are infected AFTER booting into windows, hijacking the bootloader is very rare.  Secondly having an off switch wouldn't affect that, you can still leave it on.

---

### Post by QIII on 2015-03-25
The OEMs may balk this time - or offer EFI updates to correct this after purchase.  They know that the last bastion of Windows dominance is the PC, but they also know that they have Government and Fortune 500 contracts for Linux capable machines.

My suspicion is that machines may be *sold *that way but the ability to change will be offered post-purchase.

Edit:  Given the EU's track record, this will probably be challenged due to its anti-competitive nature.

---

### Post by monkeybrain20122 on 2015-03-25
> **QIII said:**
> The OEMs may balk this time - or offer EFI updates to correct this after purchase.  They know that the last bastion of Windows dominance is the PC, but they also know that they have Government and Fortune 500 contracts for Linux capable machines.

My suspicion is that machines may be *sold *that way but the ability to change will be offered post-purchase.

And they may charge you extra for the option.

---

### Post by buzzingrobot on 2015-03-25
> **grahammechanical said:**
> 
That blog post is not even a storm in a tea cup as far as Ubuntu and its flavours are concerned.

Everything I've seen on this has been from the hysterical sky-is-falling camp.  This is not good news for Linux, but it isn't catastrophic, either.  At least, not at the moment.

If we assume that images of a slide at a presentation amount to firm Microsoft policy -- that's all this seems to be based on -- then hardware that vendors want certified for Win10, i.e., that sells with it preinstalled, will have the option of removing the toggle to disable Secure Boot. Whether they do or not probably depends on economics.  The PC market is very low margin. If a vendor can save a few dollars by going one way or another, that's the way they will go. 

Individual use of Linux on PC hardware is not on their radar.  But, some very large organizations and businesses are Linux users.  They very likely want to stay Linux users after their next round of hardware upgrades. To do that, they need to be able to buy PC hardware that can disable Secure Boot, or Microsoft must continue to sell keys to Linux flavors that jump through the right hoops.  

> The real problem is with manufacturers modifying their implementation of the UEFI protocol to only boot Windows. Do not forget, if we consider that Microsoft's operating systems are the primary target of the writers of malicious code, then switching off secure boot on a Windows machine is not a good idea. 

Using an approach to 'secure boot' that is not forced on the industry by its most dominant player makes sense for every PC operating system.  The way to handle that is to find some impartial, trusted, third party to set and enforce the standards and hand out the keys.

What concerns me is the reality that every person who is the victim of some kind of online or PC-related attack is one more person willing to consider the most strident measures to lock down all of our personal systems.

---

### Post by SeijiSensei on 2015-03-25
> **buzzingrobot said:**
> Individual use of Linux on PC hardware is not on their radar.  But, some very large organizations and businesses are Linux users.  They very likely want to stay Linux users after their next round of hardware upgrades. To do that, they need to be able to buy PC hardware that can disable Secure Boot, or Microsoft must continue to sell keys to Linux flavors that jump through the right hoops.
I see that argument applying more to servers than to desktops and laptops.  Dell has offered servers with RedHat pre-installed for years now, but finding a desktop machine with Linux is another matter entirely.  I suspect few of those large organizations have transitioned their entire staff to using Linux distributions on the desktop.

---

### Post by craig10x on 2015-03-26
If that's how things would play out (the manufacturers won't care whether or not we can install linux on their desktops and laptops) that would mean that when we all eventually get new computers, we will really have no choice but to return to windows (unless you want to go mac or chrome os)...

---

### Post by craig10x on 2015-03-26
Just found this very interesting article about this:
[http://www.pcworld.com/article/2901262/microsoft-tightens-windows-10s-secure-boot-screws-where-does-that-leave-linux.html](http://www.pcworld.com/article/2901262/microsoft-tightens-windows-10s-secure-boot-screws-where-does-that-leave-linux.html)

I'm getting the impression that things should work out ok...ubuntu and fedora already have the means of working with secure boot and as far as smaller linux distros, this related article seems to indicate they don't really have a problem, either:
[http://www.pcworld.com/article/2027864/secure-boot-loader-now-available-to-allow-linux-to-work-on-windows-8-pcs.html](http://www.pcworld.com/article/2027864/secure-boot-loader-now-available-to-allow-linux-to-work-on-windows-8-pcs.html)

---

### Post by Mike_Walsh on 2015-03-28
Hmmm. I agree with some of the opinions on here.....but certainly not all.

buzzingrobot's right......it IS unfounded hysteria, of the 'sky-is-falling' type.

(Quoted by grahammechanical)
> [COLOR=#000000]That blog post is not even a storm in a tea cup as far as Ubuntu and its flavours are concerned.[/COLOR]

Why should it be? I know I'm from t'other side of 'the Pond', but like many, I've watched MS's sneaky tactics over the years. EVERYTHING MS does, is in pursuit of the almighty dollar. Yes, Canonical CAN purchase the signed keys from MS.....and I suspect they will always be able to do so. If MS decide they're going to push the price up for those keys, they will. They'll sell them to ANYBODY who is prepared to pay that price. I can't see MS refusing to sell to Canonical on principle, merely because of the fact that it's a Linux-based distro. Got NOWT to do with it.

And I'll tell you this much; if it comes to it, and Canonical decide they need to charge us, the end-user, a SMALL amount for the PRIVILEGE (and I use the word in all seriousness) of using this frankly AMAZING operating system (perhaps a 'one-off' donation, after which you can carry on, & download, & upgrade as usual), then I, for one, would be more than willing to cough up. The 'buntus are, and always have been, an incredible 'gift' as they are. 

I cannot EVER see MS turning down the chance to make a buck or two.....regardless of WHO the third party happens to be. And if they, at the same time, can get the perceived satisfaction of 'rubbing' Canonical's nose in it by making them kow-tow, and 'toe the party line', as it were, well.....they'll go for it with even more glee than usual.

They'll NEVER change.....not as long as they have a hole in their backsides; the company 'ethos', after all these years, is TOO deeply ingrained. That, together with the fact that management are well-known for the use of what amounts to bullying tactics on the rank-and-file staff anyway, shows you the kind of people you're dealing with. Sorry, but I tell it like it is..!

 [https://en.wikipedia.org/wiki/Criticism_of_Microsoft](https://en.wikipedia.org/wiki/Criticism_of_Microsoft)

.....subsection 'Labor Practices'. From my perspective, MicroSoft NEED to make as many bucks as they can, simply to cover the astronomical costs of all these court cases they keep landing themselves with!


Regards,

Mike.

---

### Post by buzzingrobot on 2015-03-28
The fee is $99 and goes to Verisign.

I'm not questioning that Microsoft plays for keeps  
 and for money. That's what it was created to do, though. Lions kill and eat baby gazelles, too. In both cases, it's just what we should expect.

In this particular case, Microsoft could have a saintly reputation but the impact of this apparent policy would be the same thanks to Windows market dominance. Consumers prefer and reward that kind of dominance in the OS market.

---

### Post by CantankRus on 2015-03-28
> **buzzingrobot said:**
> The fee is $99 and goes to Verisign.

I'm not questioning that Microsoft plays for keeps  
 and for money. That's what it was created to do, though. Lions kill and eat baby gazelles, too. In both cases, it's just what we should expect.

In this particular case, Microsoft could have a saintly reputation but the impact of this apparent policy would be the same thanks to Windows market dominance. Consumers **prefer and reward** that kind of dominance in the OS market.
In relation to the desktop I think the term "**trapped and fleeced**" is a better description.

---

### Post by buzzingrobot on 2015-03-28
> **CantankRus said:**
> In relation to the desktop I think the term "**trapped and fleeced**" is a better description.

As I said, Microsoft does what the people who run corporations are trained and expected to do. Expecting them to deliberately hobble the corporation in service to a code of ethics they do not share is naive.

Consumers, however, do not want to face a multitude of choices in the PC hardware and the PC software markets. They don't have, don't want, and won't acquire, the skills and knowledge needed to judge which of a wide variety of products meets their needs and is also compatible with whatever they already own. That's why we have a PC market dominated by one de facto standard, and a tablet/phone market dominated by two de facto standards. It's the kind of market consumers wanted and shaped. Sure, MS played rough sometimes.  The irony is that Windows would still have dominated if they had not.

---

### Post by craig10x on 2015-03-28
Also, keep in mind...what it was is that up until now they (microsoft) said to the manufacturers that they had to both ship with secure boot enabled and provide a way to turn it off...the only difference now is they are telling them: "it's up to you (the manufacturer) if you want to include the "off switch" so all they did was lay it on the computer manufacturer to decide...they didn't exert MORE control they are now exerting LESS, actually ;)
So, since the manufacturers now have that choice, let us see how it plays out...will they include it or won't they???

Meanwhile, on the linux end, as is pointed out in the two articles i linked...it doesn't really shut us out of the game at all...And as far as why they require the manufacturer to ship with secure boot on, it's because that plays an important role in windows 10 security, which is their main concern, after all, and would be expected...

---

### Post by monkeybrain20122 on 2015-03-28
> **buzzingrobot said:**
> 
Consumers, however, do not want to face a multitude of choices in the PC hardware and the PC software markets. They don't have, don't want, and won't acquire, the skills and knowledge needed to judge which of a wide variety of products meets their needs and is also compatible with whatever they already own. That's why we have a PC market dominated by one de facto standard, and a tablet/phone market dominated by two de facto standards. It's the kind of market consumers wanted and shaped. Sure, MS played rough sometimes.  The irony is that Windows would still have dominated if they had not.

I don't know about you, but I knew nothing about computers 5 years ago. I was a 'consumer'. Even though I always disliked MS but wasn't seriously looking for an alternative since I was too poor to get a Mac and I didn't use the computer that often. But there was a break. I got an old laptop and read about Ubuntu. It was easy to install 10.04 and in no time I was totally into it and never looked back (Set up a dualboot on my main machine soon after and got rid of XP from the dualboot 6 months later) But if hardware was locked down with all these uefi secure boot nonsense and one almost needs to be a hacker to install a Linux distro I probably wouldn't have made the transition, at least not without a lot of pain. 

If Linux live usb cannot easity boot and install on generic hardware it is going to hurt Linux adoption and further marginalse it in a real way. I suspect a lot of would be new users will not have the entry point that many current users had.

It is great that Ubuntu and Fedora will likely continue to get the cert, and from craigx10's post the option is probably available for generic kernel as well. But it is fundamentally wrong that we should get certified by MS in order to install on generic hardware.Secure boot itself is not a problem provided the user has control over it, not the OEM or MS. It is security if you put a lock on your door and keep the key, but if someone else puts the lock and keeps the key from you it is a jail. I don't think it is 'hysteria' to say that this is not be acceptable.

---

### Post by CantankRus on 2015-03-29
> **buzzingrobot said:**
> As I said, Microsoft does what the people who run corporations are trained and expected to do. Expecting them to deliberately hobble the corporation in service to a code of ethics they do not share is naive.

Consumers, however, do not want to face a multitude of choices in the PC hardware and the PC software markets. They don't have, don't want, and won't acquire, the skills and knowledge needed to judge which of a wide variety of products meets their needs and is also compatible with whatever they already own. That's why we have a PC market dominated by one de facto standard, and a tablet/phone market dominated by two de facto standards. It's the kind of market consumers wanted and shaped. Sure, MS played rough sometimes.  The irony is that Windows would still have dominated if they had not.
Disagree entirely with this. 
Especially .... "It's the kind of market consumers wanted and shaped." pure BS.
You construct informed sounding sentences of tripe.

---

### Post by bcschmerker on 2015-03-29
Thanks for confirming what I read from other sources.  I've contingency plans for both my current (as of 28 March 2015) 'puters; my existing LinUX box is slated to get a-few-gens-back Intel® gear in the form of a Core Processor i5-2600 or i7-2700 Series and an ASRock® Z68 Pro3-M (primarily because I could never get the RT kernel to run stably on the Advanced Micro Devices® Athlon 64® X2 5600+), in addition to a full set of SATA HDD's, for Ubuntu® 15.12a1 (I want it all systems go when 16.04-LTS hits RTM), and the Asus® CM1630-06 as upgraded (full suite of AMD hardware plus an Asus® AV-100 audio DSP on a card) will be treated to new Western Digital® NAS-ready HDD's, a new BIOS ROM for Coreboot if possible, and Ubuntu® 16.04-LTS.  I reckon I'll need new hardware for Microsoft® Windows® 10.0.12000 anyway, so, given my "never the twain shall meet" approach for so dissimilar OS's as LinUX and WinNT, UEFI 2 and its full-time SecureBoot won't be a handicap.

---

