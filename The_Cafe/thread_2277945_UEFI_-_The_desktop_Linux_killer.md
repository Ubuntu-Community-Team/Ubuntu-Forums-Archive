---
title: "UEFI - The desktop Linux killer?"
date: 2015-05-12
forum: The Cafe
---

### Post by vpiercy on 2015-05-12
UEFI is making life very hard on Linux users. Every computer  manufacturer seems to have its own way of setting up what used to be the  BIOS. This has to affect how many casual users will throw a Live CD  into their computer and give Ubuntu a spin. 

A few questions: 

Why can't I flash a ROM or NVRAM with Linux friendly code on any PC? That would allow users to do what they want with their hardware and OS options.

Why is UEFI designed to make life difficult for computer users, especially Linux users? I guess it's ostensibly to protect machines against malware and viruses.

What's the smartest, most current UEFI demystifying post/blog/thread that users such as myself can go to to get schooled? 

I know I probably so hopelessly naive and noobish. I'm really hoping to see conversation (here in the happy, friendly Cafe) from Ubuntu community members about UEFI and ways they currently handle it (aside from just buying machines with Linux pre-installed. Dell, for example, has higher end Linux machines. They are pricey, but they are an option for some users.). 

Thank you!

---

### Post by sudodus on 2015-05-12
You are not alone. UEFI makes it hard for many of us. Here are a few links, where you can start learning how to manage to dual boot Ubuntu and Windows. It is fairly easy in some new computers, when you know how to do it, but hard in other computers, particularly when the computer's system does not comply to the UEFI standard.

[https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

There is a good wiki page about [booting with UEFI]("https://help.ubuntu.com/community/UEFI"), and a good tutorial thread, [UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295").

It often helps to use BootRepair, [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by benrob0329 on 2015-05-12
My old UEFI desktop worked fine with Ubuntu, however my new laptop has to have CSM boot mode (acts like a BIOS) enabled to get anything other than an ArchLinux install to boot.

---

### Post by cariboo on 2015-05-12
I didn't find setting up Ubuntu on a system with UEFI that much of a problem. I read some of  oldfred's posts on the subject although it wasn't needed. This is on a Toshiba laptop with Windows 8.1 pre-loaded. I used the Toshiba utility to create a working recovery device, before doing the installation just in case.

---

### Post by grahammechanical on 2015-05-12
As far as I can tell UEFI was not brought out to protect the OS from malware. That is what secure boot is for in a limited way. UEFI came out to finally solve the 4 primary partition limit of the BIOS boot system. Which in its turn presented its own difficulties to the inexperienced wouldbe new user.

I wonder how many new computers are returned as broken along with a demand for a refund when the problem was caused by the purchaser not knowing what they were doing and so messed up the OS. Perhaps by trying to install Linux. Computers have become a commodity and are no longer a hobbist's toy. In the past manufacturers tried to prevent overclocking until some of them saw marketing opportunity. A profitable market is what manufacturers and suppliers are looking for.

Regards.

---

### Post by neu5eeCh on 2015-05-12
There's an intriguing little editorial on just this subject [here]("http://www.itwire.com/opinion-and-analysis/open-sauce/67959-microsofts-new-secure-boot-strategy-will-suit-linux-firms"). 

The author seems to suggest that the three main Linux distros have as much to gain from EUFI as windows. When the author tried to contact the distros (including Canonical):

'Canonical, the parent company of Ubuntu, appeared to be somewhat  disoriented about the query. While their PR person said they would "come  back with a response when we can", the next response seemed a bit odd:  "We can't comment on forthcoming updates but we'll be in touch later on  in April to advise on the features of the next update."'

His thought:"...if it was impossible to turn off secure boot on a PC and one  wanted to install Linux on it, then the only option would be to use a  distribution that supported secure boot."

A bit of a conspiracy theory perhaps, but maybe not...

---

### Post by user1397 on 2015-05-12
> **grahammechanical said:**
> UEFI came out to finally solve the 4 primary partition limit of the BIOS boot system.I thought GPT was the answer to the 4 partition limit of MBR partition tables?

---

### Post by night_sky2 on 2015-05-13
> **VTPoet said:**
> There's an intriguing little editorial on just this subject [here]("http://www.itwire.com/opinion-and-analysis/open-sauce/67959-microsofts-new-secure-boot-strategy-will-suit-linux-firms"). 

The author seems to suggest that the three main Linux distros have as much to gain from EUFI as windows. When the author tried to contact the distros (including Canonical):

'Canonical, the parent company of Ubuntu, appeared to be somewhat  disoriented about the query. While their PR person said they would "come  back with a response when we can", the next response seemed a bit odd:  "We can't comment on forthcoming updates but we'll be in touch later on  in April to advise on the features of the next update."'

His thought:"...if it was impossible to turn off secure boot on a PC and one  wanted to install Linux on it, then the only option would be to use a  distribution that supported secure boot."

A bit of a conspiracy theory perhaps, but maybe not...

Canonical has commercial interests, it's a compagny making open source products after all.

While I don't think anyone in the Linux community wishes for a computing future where people are virtually locked out in UEFI altogether with no easy way to disable secure boot, the hard truth is that it won't affect Canonical Ubuntu in any way. As far as I know, all 64x computers with UEFI are supported by Ubuntu Oses, thanks to bootloader instead of Grub 2. This is in no way the ideal scenario but if Linux is to survive or even some day dominate the desktop, it must adapt to the new reality. And the small distros might at some point have to rally under the big banners.

---

### Post by monkeybrain20122 on 2015-05-13
> **night_sky2 said:**
> Canonical has commercial interests, it's a compagny making open source products after all.

While I don't think anyone in the Linux community wishes for a computing future where people are virtually locked out in UEFI altogether with no easy way to disable secure boot, the hard truth is that it won't affect Canonical Ubuntu in any way. As far as I know, all 64x computers with UEFI are supported by Ubuntu Oses, thanks to bootloader instead of Grub 2. This is in no way the ideal scenario but if Linux is to survive or even some day dominate the desktop, it must adapt to the new reality. And the small distros might at some point have to rally under the big banners.

Sorry, this kind of comments make my blood boil. Adapt to reality? Whose reality? Who dictates it? Why would we as a community just accept it without even putting up a fight? At least we can try. Ubuntu (and Fedora) may be able to handle secure boot, but it is at the mercy of MS. Canonical and Redhat may be competing at certain level, but ultimately they live off the same ecology, when the Linux ecology as a whole is threatened, we all get hurt, it is more than about our favourite distros. 

I know RMS is not very popular here where the prevalent attitude is "use whatever works best". But sometimes it wouldn't hurt to have a bit of idealism when called for and take a principled and forceful stand on certain things.

---

### Post by mastablasta on 2015-05-13
UEFI is not the same as secure boot. UEFI is the new improved BIOS. Secure boot (which is actually the thing that is causing the issues) is something Microsoft added and then forced manufacturers to use it.

[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
for example:
> UEFI can support remote diagnostics and repair of computers, even without another operating system

and advantages:
> 
[LIST]
[*]Ability to boot from large disks (over 2 [TB]("http://en.wikipedia.org/wiki/Terabyte")) with a [GUID Partition Table]("http://en.wikipedia.org/wiki/GUID_Partition_Table") (GPT)[SUP][[SIZE=2][13][/SIZE]]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-grub-bios-installation-14")[/SUP][SUP][[SIZE=2][b][/SIZE]]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-note1-15")[/SUP]
[*]CPU-independent architecture[SUP][[SIZE=2][b][/SIZE]]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-note1-15")[/SUP]
[*]CPU-independent drivers[SUP][[SIZE=2][b][/SIZE]]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-note1-15")[/SUP]
[*]Flexible pre-OS environment, including network capability
[*]Modular design
[/LIST]


as you can read only UEFI 2.2 added option for "secure" boot.

moreover UEFI itself is not that new:

> 
[LIST]
[*]The [Linux kernel]("http://en.wikipedia.org/wiki/Linux_kernel") has been able to use EFI at boot time since early 2000,[SUP][[SIZE=2][67][/SIZE]]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-69")[/SUP] using the [elilo]("http://en.wikipedia.org/wiki/Elilo") EFI boot loader or, more recently, EFI versions of [GRUB]("http://en.wikipedia.org/wiki/GNU_GRUB").[SUP][[SIZE=2][68][/SIZE]]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-debiangrubexample-70")[/SUP] Grub+Linux also supports booting from a GUID partition table without UEFI.[SUP][[SIZE=2][13][/SIZE]]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-grub-bios-installation-14")[/SUP] The distribution [Ubuntu]("http://en.wikipedia.org/wiki/Ubuntu_(operating_system)") added support for UEFI secure boot as of version 12.10.[SUP][[SIZE=2][69][/SIZE]]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-h-ubuntusecureboot-71")[/SUP] Further, the Linux kernel can be compiled with the option to run as an EFI bootloader on its own through the EFI bootstub feature.
[*][HP-UX]("http://en.wikipedia.org/wiki/HP-UX") has used (U)EFI as its boot mechanism on [IA-64]("http://en.wikipedia.org/wiki/IA-64") systems since 2002.
[/LIST]
...


---

### Post by night_sky2 on 2015-05-13
> **monkeybrain20122 said:**
> Sorry, this kind of comments make my blood boil. Adapt to reality? Whose reality? Who dictates it? Why would we as a community just accept it without even putting up a fight? At least we can try. Ubuntu (and Fedora) may be able to handle secure boot, but it is at the mercy of MS. Canonical and Redhat may be competing at certain level, but ultimately they live off the same ecology, when the Linux ecology as a whole is threatened, we all get hurt, it is more than about our favourite distros.

The Linux community need it's own preloaded devices on the mainstream market instead of relying on Microsoft's OEM hardware to survive. Until then, you are at the Redmond firm's mercy whether you want it or not.

Look, I am no less concerned than you are, but UEFI is replacing the BIOS (and there are some technological advances in that), this thrend has been going on for some time now. Between Microsoft's anxieties of loosing PC marketshare and the manifacturers' attempts of protecting their customers against the new generation of malware attacks, that's the new reality the Linux community finds itself in.

As for myself, fighting can also mean adapting. I don't see the two concept as necesserely dissociated.

The is the best article (Linux Journal) one can find on the subject of UEFI and it's role in Linux: [http://www.linuxjournal.com/content/growing-role-uefi-secure-boot-linux-distributions](http://www.linuxjournal.com/content/growing-role-uefi-secure-boot-linux-distributions)

---

### Post by QIII on 2015-05-13
If any of you can convince the bean counters at the OEMs that the cost of separate production lines, design teams, QA teams, etc, for a two percent share of the user market is a good business decision, go ahead.

90%+ of the consumer market is Windows.  That is simple reality.  If you want the OEMs to expend a similar level of resources for a 2% share, be prepared to justify a $10 fix to a $1 problem.  That is their reality.

Companies exist to make money, not to support the Open Source ideology.

Best to set aside the pipe and whatever is in it and come up with a strategy that can be implemented in the real world.  Canonical, Red Hat and SUSE have done that.

They have the ability to put pressure back on Microsoft.  They can say "You own the desktop, we own all the other devices and the internet backbone.  How far do you want to push this?  How about a compromise."  Which is exactly what has happened.

The world works on statesmanship and compromise.  Inflexible adherence to ideology leads to breakage.  Usually the unbending thing is broken.

---

### Post by monkeybrain20122 on 2015-05-13
> **night_sky2 said:**
> 
Look, I am no less concerned than you are, but UEFI is replacing the BIOS (and there are some technological advances in that), this thrend has been going on for some time now. Between Microsoft's anxieties of loosing PC marketshare and the manifacturers' attempts of protecting their customers against the new generation of malware attacks, that's the new reality the Linux community finds itself in.


Look, you are mixing a few things up. UEFI is not the same as secure boot, and secure boot is not the same as secure boot with MS holding the key. Linux can handle UEFI and secure boot, the issue is MS holding the key. If I put a lock on my door it is security, if I put a lock on your door and keep the key from you it is illegal confinement, it has nothing to do with 'technological advancement' on either the door or the lock.  I am cool with uefi and even secure boot as long as the owner of the hardware controls the key. This attempted lockdown of generic hardware, if materialises, is simply wrong, there is nothing to 'adapt' to (it is like adapting to the local bully collecting protection money), it is probably illegal too.

---

### Post by user1397 on 2015-05-13
monkeybrain I agree with you wholeheartedly, but what can we as users do? Sign petitions? Write to congress?  Seems like our options are limited/don't work very well anyway.

The only things big enough to try to combat Microsoft on this issue would be other big companies.

---

### Post by monkeybrain20122 on 2015-05-13
> **ubuntuman001 said:**
> monkeybrain I agree with you wholeheartedly, but what can we as users do? Sign petitions? Write to congress?  Seems like our options are limited/don't work very well anyway.

The only things big enough to try to combat Microsoft on this issue would be other big companies.

At least we can try, last time (win8) something happened that got MS to back off and mandated a way to turn secure boot off. 10 years ago they tried to bring in "trusted computing" and that was also defeated. I don't want to analyse what might have been at work in those cases because those are just opinions (sure some wise guys will tell us MS was thwarted in those cases because it stepped on the toes on someone big and powerful, the little guys' actions mean nothing so they should just lay down and die blah blah.. but the world would be a rather hopeless place if we accept this kind of cynicism masqueraded as pragmatism)

One thing that is sure enough though, is that if we don't do anything, don't make any noise and accept it they would only push us around more. Pushing back doesn't mean we will win, but laying down guarantees that we will lose. Also, remember,  it is not only Linux users who should be concerned, if you cannot boot a rescue disk or install a non OEM version of windows, or create an image with something like Acronis, these locked down Windows machines are basically not repairable, I am sure many Windows users will be affected and pissed off too if they know what is at stake; Windows users plus the repair industry constitute a lot more than a '2% market' that the wise men told us. We need to talk to people, including Windows users.

---

### Post by user1397 on 2015-05-14
> **monkeybrain20122 said:**
> At least we can try, last time (win8) something happened that got MS to back off and mandated a way to turn secure boot off. 10 years ago they tried to bring in "trusted computing" and that was also defeated. I don't want to analyse what might have been at work in those cases because those are just opinions (sure some wise guys will tell us MS was thwarted in those cases because it stepped on the toes on someone big and powerful, the little guys' actions mean nothing so they should just lay down and die blah blah.. but the world would be a rather hopeless place if we accept this kind of cynicism masqueraded as pragmatism)

One thing that is sure enough though, is that if we don't do anything, don't make any noise and accept it they would only push us around more. Pushing back doesn't mean we will win, but laying down guarantees that we will lose. Also, remember,  it is not only Linux users who should be concerned, if you cannot boot a rescue disk or install a non OEM version of windows, or create an image with something like Acronis, these locked down Windows machines are basically not repairable, I am sure many Windows users will be affected and pissed off too if they know what is at stake; Windows users plus the repair industry constitute a lot more than a '2% market' that the wise men told us. We need to talk to people, including Windows users.
I hear ya.  Consider me someone willing to try to do something about it.

---

### Post by jeff127 on 2015-05-14
Currently I have three PCs all running Linux (a desktop a laptop and a netbook) so I'm not really concerned about UEFI. Look on the bright side: System76 exists, and now HP is selling Linux PCs in Russia. Secure boot (realistically, **restricted boot**) will most likely put an end to the hobby of recycling old PCs by putting Linux on them. Despite this loss, we will all have the choice to use Linux thanks to System76 and similar companies. It will cost more (especially international shipping fees) but that won't deter me, at least not completely.

---

### Post by night_sky2 on 2015-05-14
> **jeff127 said:**
>  Secure boot (realistically, **restricted boot**) will most likely put an end to the hobby of recycling old PCs by putting Linux on them.

That's not really true since the big three (Ubuntu, Fedora and OpenSUSE) have all found ways to support secure boot. So that means you will still be able to recycle these machines using Linux but you might have a harder time installing smaller community distros on them, at least for the time being. That's the issue the Linux community is facing. Solutions have been proposed and IMO that something I am sure the devs will be able to adapt by getting some sort of mutual agreement with Microsoft OEM.

But as you said, the more preinstalled Linux machines there is on the market, the better. That's the best way for the Linux community to have maximum control over what kind fo hardware they want to throw out into the ring for their (potential) users. Other than that, you'll always have to put up (or some prefer saying 'fight') with Microsoft and it's corporate decisions.

---

### Post by pissedoffdude on 2015-05-16
It's not UEFI in itself, it's just secure boot, but I haven't heard of a scenario where users can't simply disable this (or someone correct me if I'm wrong).  From my understanding, UEFI is light years ahead of the BIOS, and I personally haven't had any issues with it and grub-efi.  And even if linux distros were sort of 'locked out' I really can't imagine that a community that was basically founded by a guy who found out how to hack into a computer and discover every user's password wouldn't be able to find a way around this

---

### Post by buzzingrobot on 2015-05-16
Dedoimodo has a typically opinionated, incisive and instructive look at Secure Boot here ([http://www.dedoimedo.com/computers/windows-10-alt-os-lockout.html](http://www.dedoimedo.com/computers/windows-10-alt-os-lockout.html)).  

I don't always agree with him, but this time I do.

---

### Post by monkeybrain20122 on 2015-05-16
This is not about uefi and secure boot. Even the FSF is okayed with secure boot as long as the user controls the key. This is about who controls the key, not the technology of making keys and locks. Lets stop this misleading  "we have to adapt to new technology" bs once and for all. The "technology" is bullying and shaking down, it has been around even before the caveman, hardly new, and we definitely should not "adapt to it"!  

And let's try not to justify the unjustifiable with "2% market share" and such, money and market are not the standard of right and wrong, at least I hope not. There is a reason why anti-trust laws exist. I don't know if this would contravene the letters of the law, I am not a lawyer, but it definitely violates the spirit.

Oh and the fact that all mobile devices are locked down is supposed to make this more palatable or acceptable? I fail to see the relevance.

---

### Post by buzzingrobot on 2015-05-16
> **monkeybrain20122 said:**
> This is not about uefi and secure boot. Even the FSF is okayed with secure boot as long as the user controls the key. This is about who controls the key, not the technology of making keys and locks. Lets stop this misleading  "we have to adapt to new technology" bs once and for all. The "technology" is bullying and shaking down, it has been around even before the caveman, hardly new.  And let's try not to justify the unjustifiable with "2% market share" and such, money and market are not the standard of right and wrong, at least I hope not. There is a reason why anti-trust laws exist. This may or may not contravene the letters of the law, I am not a lawyer. But it definitely violates the spirit.

Oh and the fact that all mobile devices are locked down is supposed to make this more palatable or acceptable? I fail to see the relevance.

Of course it is. Vendors will do what they think is best for them.  If they want to sell only machines with Windows pre-installed and with an MS sticker on it, then they will sell machines that adhere to *whatever* standards MS enforces. Vendors would do the same thing if they wanted to sell only Ubuntu/RHEL machines and Canonical/RedHat established similar standards.

The market is unlikely to change Microsoft's approach. But, the estimated 10 percent of the market that caters to non-Windows users amounts to non-trivial numbers, given the huge size of the industry.  

I have no idea if an effective legal challenge is possible, given that the notion of hardware vendors being implicitly and explicitly compelled to build hardware conforming to the requirements of the vendors of the software they want to run on their hardware is extremely well established and accepted. (Look at the PC hardware archtiecture we've all been using for decades:  It was specifically designed to run DOS and Windows.) 

If a challenge is mounted, it will likely come from large corporations with deep pockets who need to maintain the ability to use Linux, not from the likes of the FSF, which has no skin in this game (and perhaps no legal standing) except ideological zeal.

The locked-down phones and tablets example is relevant because their locked-down nature hasn't been successfully challenged and it has been completely accepted by consumers (who, by and large, think of a "computer" as something you buy with one particular kind of software already on it.)

In the long run, even if a successful legal challenge is mounted, hardware vendors will make the hardware that turns them the greatest profit. If none of them think they can make more selling Linux hardware that can't run Windows than they can selling Windows-only hardware, they won't sell Linux hardware.

If MS does block key acquisition by makers of Linux distributions that can boot on a Secure Boot machine, like Canonical and Red Hat, that is clearly a differment matter. That seems to me to be clear restraint of trade.  What MS is doing now doesn't. At least by U.S. standards, it is just throwing its market clout around.  (The EU may take a different position.)

---

### Post by mastablasta on 2015-05-17
> **monkeybrain20122 said:**
> 

Oh and the fact that all mobile devices are locked down is supposed to make this more palatable or acceptable? I fail to see the relevance.

yup. they should be unlocked.

---

### Post by vpiercy on 2015-05-17
Thank you everyone, especially for the links. 

And thank you Mastablasta for locking onto and parsing that Wikipedia article on UEFI. Interesting about the history, especially with HP-UX using UEFI since 2002. 

I gave up trying to put Ubuntu on a "debranded" HP 8100 Elite Core-i3 machine. When Windows 8 Pro updated to Windows 8.1 Pro, the machine was nearly bricked. I could only turn it off through Task Manager. I ended up taking out the hard drive and putting in another one, wiping it, and loading Windows 7 on it. The machine is an OEM Windows machine. It runs Win7 fine, but nothing other than Windows (7, & 8.0 only). I guess I'll either wipe the other hard drive (hate to lose the Win8 license) or try to see if it'll run in another machine, which I don't think it will.

---

### Post by mastablasta on 2015-05-17
is that a[SIZE=3] HP  Compaq 8100 Elite[/SIZE]

That PC is certified for Ubuntu:
[http://www.ubuntu.com/certification/hardware/201011-6701/](http://www.ubuntu.com/certification/hardware/201011-6701/)

though this one has BIOS:
[http://h30499.www3.hp.com/t5/Business-PCs-Compaq-Elite-Pro/HP-Compaq-8100-Elite-nvidia-Graphics-and-Linux/td-p/2323857#.VVj_0vBGZSw](http://h30499.www3.hp.com/t5/Business-PCs-Compaq-Elite-Pro/HP-Compaq-8100-Elite-nvidia-Graphics-and-Linux/td-p/2323857#.VVj_0vBGZSw)

HP's are usually Linux compatible. You could try Centos/Fedora or SUSE EL/OpenSUSE.

But you say it has UEFI. did you read the UEFI page and follow the instructions? : [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I also found that people on HP forums can offer good help with getting linux on HP's.

---

### Post by kurt18947 on 2015-05-17
> **pissedoffdude said:**
> It's not UEFI in itself, it's just secure boot, but I haven't heard of a scenario where users can't simply disable this (or someone correct me if I'm wrong).  From my understanding, UEFI is light years ahead of the BIOS, and I personally haven't had any issues with it and grub-efi.  And even if linux distros were sort of 'locked out' I really can't imagine that a community that was basically founded by a guy who found out how to hack into a computer and discover every user's password wouldn't be able to find a way around this

With Windows 8 machines, Microsoft has required that manufacturers include a means to disable secure boot in order to qualify for Windows 8 certification. From what I've read, the same requirement is not yet in place for Windows 10. Even with Microsoft's requirement to disable secure boot, some models still don't want to permit the installation of anything other than Windows. 

If there is not a means to disable secure boot, I wonder if a cottage industry will spring up supplying BIOS patches or 3rd party firmware for popular models to enable installing non-Windows OSs.

---

### Post by monkeybrain20122 on 2015-05-17
> **kurt18947 said:**
> 

If there is not a means to disable secure boot, I wonder if a cottage industry will spring up supplying BIOS patches or 3rd party firmware for popular models to enable installing non-Windows OSs.

And threads on such info on UF will probably be locked for being against the COC (bypassing EULA, circumventing digital locks or some such imaginary crimes) :)

---

### Post by benrob0329 on 2015-05-18
> **monkeybrain20122 said:**
> And threads on such info on UF will probably be locked for being against the COC (bypassing EULA, circumventing digital locks or some such imaginary crimes) :)

Technically, you (and I think just about everyone who uses Ubuntu and descendants) are "breaking" a copyrighted, patented, and DRM-like code known as CSS (using dvdcss2, in the dvdread4 package).

******_***Thanks VideoLan!!!***_ :D

I think it is outrageous, companies locking out users from tampering thier devices. I DON'T care if it voids the warranty, just don't take me to court for something **_I_** did to _**my**_ thing!

---

### Post by monkeybrain20122 on 2015-05-18
> **benrob0329 said:**
> Technically, you (and I think just about everyone who uses Ubuntu and descendants) are "breaking" a copyrighted, patented, and DRM-like code known as CSS (using dvdcss2, in the dvdread4 package).

_***Thanks VideoLan!!!***_ :D



Not necessarily, many new laptops have no DVD drive. :p

---

### Post by user1397 on 2015-05-18
> **monkeybrain20122 said:**
> Not necessarily, many new laptops have no DVD drive. :p
Forreal.  I can't even remember the last time I used a DVD period.

---

### Post by monkeybrain20122 on 2015-05-18
> **ubuntuman001 said:**
> Forreal.  I can't even remember the last time I used a DVD period.

Then you are probably breaking copyright DRM, EULA in some other ways than libdvdcss. :)

---

### Post by cariboo on 2015-05-18
This thread is drifting off topic. You know what to do.

---

### Post by kurt18947 on 2015-05-19
> **benrob0329 said:**
> Technically, you (and I think just about everyone who uses Ubuntu and descendants) are "breaking" a copyrighted, patented, and DRM-like code known as CSS (using dvdcss2, in the dvdread4 package).

_***Thanks VideoLan!!!***_ :D

I think it is outrageous, companies locking out users from tampering thier devices. I DON'T care if it voids the warranty, just don't take me to court for [COLOR=#ee82ee]something **_I_** did to _**my**_ thing![/COLOR]

And that can be a sticking point. I'm not sure about UEFI/BIOS code but we don't actually own some of the things we think we do. You know you don't own any copies of Windows (and probably other proprietary software) on your machines, right? You may be paying for a **license** to use it in accordance with terms stated in said license. it is not yours to do with as you please. At least not legally.

---

### Post by buzzingrobot on 2015-05-19
> **kurt18947 said:**
> You may be paying for a **license** to use it in accordance with terms stated in said license. it is not yours to do with as you please. At least not legally.

Software is licensed, including GPL'd software and elsewhere in the rest of the FOSS universe.  The license protects what the software vendors see as being in their interests.  FOSS developers have one point of view on that, and others have a different view. *Both* rely on copyright and licensing to protect their interests. 

If somone wants to *own* software, then they need to *write* that software, in totality, from scratch, without being encumbered by other licenses, including the FOSS licenses. Because they create it, no one else will have any rights to it, in any form, until they decide to transfer some of those rights, via a license or by selling it to another vendor.

Licensing of what Canonical calls "restricted" codecs and such sometimes has to do with actual use, and sometimes it's about distribution. Those are two different things. In a practical sense, no license holder is going to waste money going after any single individual who happens to violate a license. However, a license holder would have an incentive to go after a commercial corporation that is *distributing* its product in a way that is not compliant with the license.  A company's vulnerablity to that depends on where it is legally located.  E.g., because Red Hat is a U.S, corporation, it is more vulnerable than Canonical.  As a result, these so-called restricted items are not to be found on any server controlled by Red Hat, including Fedora's, nor do RH/Fedora distribute any post-install software that retrieves the restricted files from other servers.

Locked-down small devices:  They've been that way since the beginning and the market has not complained. Vendors are going to continue to market locked-down devices, and we are going to continue to buy them. Vendors want to keep their customers inside their own universe, and mainstream consumers  equate security with the device's locked-down status.

---

### Post by benrob0329 on 2015-05-19
Maybe we should all make our own brand of phones/tablets/computers...

---

### Post by night_sky2 on 2015-05-20
> **benrob0329 said:**
> Maybe we should all make our own brand of phones/tablets/computers...

Canonical already has Hardware OEMs partners like Dell, HP and Lenovo. It can sell preinstalled laptops fully compatible with Ubuntu though it's a small market since 98% of all PC sales in America are Windows certified computers. Therefore, for most of us Linux users it's more convenient to buy a Windows laptop from Microsoft's Hardware OEMs and try to install Ubuntu Linux on it.

---

### Post by monkeybrain20122 on 2015-05-20
> **night_sky2 said:**
> Canonical already has Hardware OEMs partners like Dell, HP and Lenovo. It can sell preinstalled laptops fully compatible with Ubuntu though it's a small market since 98% of all PC sales in America are Windows certified computers. Therefore, for most of us Linux users it's more convenient to buy a Windows laptop from Microsoft's Hardware OEMs and try to install Ubuntu Linux on it.

Obviously if you cannot easily install Linux on a generic machine Linux adoption will take a beating, there is no question about it. So the people who say not to worry as geekesters can get compatible machines, find a hack, or "build your own desktop" are not living in the real world. It is a high barrier for new users if you have to be a bloody hacker to install a Linux OS, if the purpose is too roll back Linux to the 1990's when it was only for geeks, fine, but that is not the direction most of us want to see things go. 

If this ever becomes a reality the wise guys will come and say it is all ok that foo doesn't support Linux because companies  exist to make money why should foo support 0.01% of market share by  geeksters? Low market share would be a self fulfilling prophecy brought on by passivity.

---

### Post by benrob0329 on 2015-05-21
The problem is, Ubuntu OEM phone companies will do the EXACT same thing the Android and iOS ones are doing, locking people out of thier own phones.

That could be a problem, for example lets say one wanted to install another distro (*gasp*) on ones phone, it simply wouldn't be easy. (Jailbreaking doesn't look very easy to me!)

---

### Post by user1397 on 2015-05-21
> **benrob0329 said:**
> The problem is, Ubuntu OEM phone companies will do the EXACT same thing the Android and iOS ones are doing, locking people out of thier own phones.

That could be a problem, for example lets say one wanted to install another distro (*gasp*) on ones phone, it simply wouldn't be easy. (Jailbreaking doesn't look very easy to me!)
jailbreaking is only for iphones, and all it does is it adds a third party repository or app store where you can download many things to further customize your iphone, it is very unlike rooting on an android phone.  

i think it depends on if the ubuntu handsets are more like the nexus line of phones by google, or if they're more like HTC or samsung phones.  I actually don't know about the ones that are currently out, does anyone know how open they are?  By that I mean, for example, on a nexus 5 you can upgrade/downgrade to any version of android (as long as it's not too old) and even put alternative OSs like ubuntu touch and firefox OS and maybe a few others.

---

### Post by Vladlenin5000 on 2015-05-22
The general consensus up until now regarding Meizu is that Meizu phones aren't for modding. I don't expect Meizu to suddenly open it now, regardless of Ubuntu.
I don't know about BQ.

---

### Post by cariboo on 2015-05-22
Now we are really drifting off topic, seeing as no one seems to want to keep things on topic. Thread closed.

---

