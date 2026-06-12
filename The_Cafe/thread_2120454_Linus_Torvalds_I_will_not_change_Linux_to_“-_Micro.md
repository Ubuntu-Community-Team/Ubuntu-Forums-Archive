---
title: "Linus Torvalds: I will not change Linux to “****-****** Microsoft”"
date: 2013-02-26
forum: The Cafe
---

### Post by mips on 2013-02-26
:biggrin: Man has a way with words but I agree with him.

[http://arstechnica.com/information-technology/2013/02/linus-torvalds-i-will-not-change-linux-to-deep-throat-microsoft/](http://arstechnica.com/information-technology/2013/02/linus-torvalds-i-will-not-change-linux-to-deep-throat-microsoft/)

> The Linux kernel development process may welcome all those who love open source software and have the right coding chops, but one man remains the ultimate authority on what does and doesn't go into Linux—and he isn't afraid to let everyone know it.

The rants of Linux creator Linus Torvalds often become public through the Linux Kernel Mailing List archive. That's the open source way, and it gives us a glimpse into the thinking of the people behind one of the world's most widely used technologies.

The latest example comes from an argument between Torvalds and other Linux developers over whether the Linux kernel should include code that makes it easier to boot Linux on Windows PCs. This goes back to Microsoft requiring that PCs designed to run Windows 8 use UEFI firmware with the Secure Boot feature enabled. This has complicated the process of booting Linux on PCs that shipped with Windows 8, but it hasn't prevented people from doing so. There are workarounds, but some people are looking for a solution in the Linux kernel itself.

[Read more...]("http://arstechnica.com/information-technology/2013/02/linus-torvalds-i-will-not-change-linux-to-deep-throat-microsoft/")

**[COLOR="Red"]Warning: Graphic language ahead[/COLOR]**

---

### Post by MadmanRB on 2013-02-26
Yeah I am surprised no one is fighting microsoft here, UEFI is just a tool for microsoft to take our liberties away and its too bad no one sees it.
I have always opposed secureboot, its anti competitive.
But hey what do I know, its getting rid of old school bios and that is all that matters right?
Screw the ability to use what operating system I want, that would be stupid!

---

### Post by Rokkross on 2013-02-26
> **MadmanRB said:**
> UEFI is just a tool for microsoft to take our liberties away and its too bad no one sees it.
Well, it isn't. First, UEFI != Secure Boot. Read more here: [http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Second, Secure Boot isn't necessarily bad if users have control over it. Microsoft signing the keys without giving people control is the problem, not the existence of a security feature. I mean, it's a security feature that most people don't have a use for, but I'm sure somebody wants it. 
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Secure_boot](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Secure_boot)

---

### Post by MadmanRB on 2013-02-26
Bah, it still forces people to use windows.
Thus why its bad, and no one fought it which makes matters worse.

---

### Post by sdowney717 on 2013-02-26
To more securely boot windows!:p
Alone

---

### Post by MadmanRB on 2013-02-26
Thusd is the issue, we should not bow down to microsoft, linux is a competitor not a lap dog.
There should be a antitrust lawsuit here, but it wont happen becase most linux companies including canonical rather pay blood money then stand up for linuxes right to exist.

---

### Post by Rokkross on 2013-02-26
> **MadmanRB said:**
> Bah, it still forces people to use windows.
Thus why its bad, and no one fought it which makes matters worse.
Unless you set it up not to. My point is that you shouldn't say f*** UEFI and f*** security features. In theory you -could- use this to set up a secure linux system. Microsoft's use of it is the problem, like I said.

---

### Post by MadmanRB on 2013-02-26
Yes but it forces linux to give blood money to microsoft.
This would not happen if the linux community was not so fragmented.

---

### Post by iamkuriouspurpleoranj on 2013-02-26
Call me stupid but I'm completely lost in the whole UEFI-Microsoft-Canonical-Red_Hat-Linux_Foundation saga.

If I buy a new PC now from a common-or-garden high street retailer will I be able to replace Windows 8 with a GNU/Linux OS? Will my choice be restricted to Fedora/Ubuntu? Does "Ubuntu" include other distros that use the Ubuntu repositories e.g. Mint?

---

### Post by Rokkross on 2013-02-26
> **iamkuriouspurpleoranj said:**
> Call me stupid but I'm completely lost in the whole UEFI-Microsoft-Canonical-Red_Hat-Linux_Foundation saga.

If I buy a new PC now from a common-or-garden high street retailer will I be able to replace Windows 8 with a GNU/Linux OS? Will my choice be restricted to Fedora/Ubuntu? Does "Ubuntu" include other distros that use the Ubuntu repositories e.g. Mint?
Just to be on the safe side, try finding something that either doesn't have an OS on it directly from a manufacturer, or buy something with a GNU OS already on it. 

[System 76]("https://www.system76.com/") comes to mind.

EDIT: Keep in mind, this doesn't mean there aren't workarounds for UEFI Secure Boot. The most -restrictive- use of it seems to be M$'s Surface tablets (so far you can't bypass it; a vulnerability needs to be found), but I'm pretty sure most OEMs shipped with workarounds.

---

### Post by tgalati4 on 2013-02-26
The issue is:

Turn off secure boot, install linux and it will boot, but Win8 will not.  Turn on secure boot, Win8 will boot, but linux will not.  It makes dual-booting a pain without some in-kernel, microsoft-controlled certification.  That's the main issue that Linus has.  There is no good, third-party solution, nor is there a clean work-around.  In this case, we (the linux community) really do have to follow (or perform some bodily function) what microsoft demands.

---

### Post by matt_symes on 2013-02-26
IMO, as a technology, the idea is great. 

It would be much better in the hands of a truly independent body though.

---

### Post by UltimateCat on 2013-02-26
The Linux Foundation has released a Windows Secure Boot fix.

And BTW, it's not exactly for a beginner to use and understand.

[http://www.zdnet.com/linux-foundation-releases-windows-secure-boot-fix-7000011084/](http://www.zdnet.com/linux-foundation-releases-windows-secure-boot-fix-7000011084/)

Also; for what it's worth in another Linux group that I belong to their are a lot of folks that are highly P***** - off about this after purchasing a new computer with Win's 8 on it. Some in fact have returned the computer for a full refund from the manufacturer.

I heard that some computer manufacturers are not giving folks the option of purchasing a computer w/o an OS on it. At least Tiger Direct stopped- 
Don't know about the rest.

---

### Post by MadmanRB on 2013-02-26
> **tgalati4 said:**
> The issue is:

Turn off secure boot, install linux and it will boot, but Win8 will not.  Turn on secure boot, Win8 will boot, but linux will not.  It makes dual-booting a pain without some in-kernel, microsoft-controlled certification.  That's the main issue that Linus has.  There is no good, third-party solution, nor is there a clean work-around.  In this case, we (the linux community) really do have to follow (or perform some bodily function) what microsoft demands.
We shouldn't have to though.

we should fight this move not cater to it.

---

### Post by slickymaster on 2013-02-26
> **matt_symes said:**
> IMO, as a technology, the idea is great. 

It would be much better in the hands of a truly independent body though.

Agree with you 100%.

---

### Post by nikonian on 2013-02-26
Maybe the Linux community needs to wake up and realise that, whether "good or bad"(?), the mainstream use Macs and Windows PCs - the machine manufacturers main objective is not to market platforms for tinkerers and geeks; their main objective is to create uniform, consistent and predicable products for the masses, who just want prolific and easily installable software to work with little, if any fuss at all. Do you think the "average" user knows about, let alone *cares* about a bootloader, any more than the average customer in "PC World" or "Target" care about what code created their video drivers? Of course not.

Linux is amazing, but lest we forget, Mac OS X and Windows are dominant, and Linux is a long way off from becoming anything near a competitive threat to Apple or Microsoft - I'm sorry if that is not what you wanted to hear as Linux lovers, but them's the hard facts. iPhone users don't generally install Linux or Android on their iPhones, because it is nigh-on impossible, but do the majority of owners care? Of course not.

---

### Post by MadmanRB on 2013-02-26
But why restrict if linux really is "not a threat"?
Its clear to me that linbux is a threat to MS if thery are the ones pulling the strings on secureboot.

---

### Post by nikonian on 2013-02-26
> **MadmanRB said:**
> But why restrict if linux really is "not a threat"?
Its clear to me that linbux is a threat to MS if thery are the ones pulling the strings on secureboot.

Who knows?

The bottom line is, they don't care about Linux, and from their perspective, they are not obliged to care about it.

---

### Post by leclerc65 on 2013-02-26
Ubuntu already has a get around (I think Fedora too), the other distros' users might have to wait

[http://www.h-online.com/open/news/item/Secure-Boot-comes-to-Ubuntu-12-04-2-LTS-1804203.html](http://www.h-online.com/open/news/item/Secure-Boot-comes-to-Ubuntu-12-04-2-LTS-1804203.html)

---

### Post by First Taste Hooks You on 2013-02-26
Apple has it in their Macs and have for awhile, as I see it on my 2007 MacBook when I boot Ubuntu, but it says it is not on. But on my current motherboard it made dual booting a pain and I gave up and just leave Windows 7 on it and Ubuntu 12.10 on my MacBook. As it is in control of Microsoft it is a problem and used to benefit their main product not so much to protect its users as it is sold to us as. Intel designed it to protect against booting of unsigned code, still I hear faking a signing is not too hard.

---

### Post by mikewhatever on 2013-02-26
IMHO, these rants by Linus are an embarrassment. Can't he express his thoughts without swearing like a drunk sailor? Looks like the man is bored to death, so he writes obscene emails to insult people.

---

### Post by dave2001 on 2013-02-26
> **MadmanRB said:**
> Thusd is the issue, we should not bow down to microsoft, linux is a competitor not a lap dog.
There should be a antitrust lawsuit here, but it wont happen becase most linux companies including canonical rather pay blood money then stand up for linuxes right to exist.

Microsoft has beaten worse anti-trust raps than this UEFI business. They would do it again with no problem. 

UEFI is in many respects an improvement on BIOS. The issues with the "secure boot" aspect are from Microsoft having undue influence with OEM's, and I agree with Mr. Torvalds that the linux community should not "play ball" with Microsoft on this.

Hack it, dismantle it, flash it, recode it, or build it yourself, whatever it takes to make your hardware work. THAT is what the linux community has always been doing.. not saying "please let me" to microsoft.

---

### Post by MadmanRB on 2013-02-26
And that is the issue here, really we should be fighting this not catering to the whims of one of the most anti competitive companies of all time.

---

### Post by tgalati4 on 2013-02-26
I sat through Matt Garrett's thoughful presentation:  The Secure Boot Journey.  There will be a video posted soon, but the slides are available:

[https://www.socallinuxexpo.org/scale11x/presentations/secure-boot-journey](https://www.socallinuxexpo.org/scale11x/presentations/secure-boot-journey)

It's a complex issue.  Generally useful technology, but not helpful to have Microsoft hold and issue the keys.

---

### Post by mamamia88 on 2013-02-27
The conspiratorial side of me says that they are trying to stop linux from being installed easily. But then the rational side of me comes into play.  Even if a user buys a windows pc and installs linux Microsoft still technically made money off that sale.  So preventing a user from installing linux helps windows how?   Most people who want to use linux will find a work around and those who would never touch Linux with a 10 foot pole feel a little bit more secure (even if not much)

---

### Post by stinkeye on 2013-02-27
> **mamamia88 said:**
> So preventing a user from installing linux helps windows how?
Well in my case, after dual booting for a while, realized I didn't need MS 
products at all. Last purchased Microsoft OS was XP.

---

### Post by mastablasta on 2013-02-27
he could have expressed himself more politely. but he is right. 
 
it is also the problem of Linux distributions (the major ones particluary) that they do not want to sign or to take this upon themselves. then again it might have something to do with costs or something. i wouldn't know that far.

---

### Post by iamkuriouspurpleoranj on 2013-02-27
> **mikewhatever said:**
> IMHO, these rants by Linus are an embarrassment. Can't he express his thoughts without swearing like a drunk sailor? Looks like the man is bored to death, so he writes obscene emails to insult people.

Agreed. NVidia f- you! was refreshing. Now it's just boorish. Perhaps he's preparing for a future career as an after-dinner speaker.

---

### Post by prodigy_ on 2013-02-27
> **Rokkross said:**
> the existence of a security feature
Please stop spreading misinformation. So-called "Secure Boot" has nothing to do with security. It's a just a marketing name for a vendor lock-in attempt Microsoft tries to muscle using its monopoly position. And UEFI is merely a tool MS has chosen to facilitate the attempt. UEFI itself has no real advantage over BIOS and comes with a host of issues (from plain bugs to limiting end user's control over their PC).

---

### Post by iamkuriouspurpleoranj on 2013-02-27
> **nikonian said:**
> Maybe the Linux community needs to wake up and realise that, whether "good or bad"(?), the mainstream use Macs and Windows PCs - the machine manufacturers main objective is not to market platforms for tinkerers and geeks; their main objective is to create uniform, consistent and predicable products for the masses, who just want prolific and easily installable software to work with little, if any fuss at all. Do you think the "average" user knows about, let alone *cares* about a bootloader, any more than the average customer in "PC World" or "Target" care about what code created their video drivers? Of course not.

Linux is amazing, but lest we forget, Mac OS X and Windows are dominant, and Linux is a long way off from becoming anything near a competitive threat to Apple or Microsoft - I'm sorry if that is not what you wanted to hear as Linux lovers, but them's the hard facts. iPhone users don't generally install Linux or Android on their iPhones, because it is nigh-on impossible, but do the majority of owners care? Of course not.

Not true. More and more **ordinary** users are using systems like Ubuntu and Mint and technical skills are becoming increasingly mainstreamed. The estimated 2% world market share still impacts Microsoft's bottom line. 2% is a lot on a global scale and in the context of declining desktop computing margins, every penny counts.

You're right though in the sense that it's probably more a case of collateral damage to Linux, which Microsoft and the OEMs who run after them don't care about, rather than a conspiracy as such.

However, if Linux users had no commercial value why would AMD bother to make drivers?

The fact is we know now we don't need Microsoft to do amazing productive things with computers. If we can just get this message across to more people, we can oblige Microsoft to cut their prices and everyone will be better off for it.

---

### Post by fdrake on 2013-02-27
i don't really see the issue here. It is microsoft right to secure/lock their system if they feel it is in danger. Of course that doesn't prevent somone to get acces to their data, but so what? it's their choise, good or bad...

I personally think that if you need to dualboot, it is  already a time wasting process, so stopping first at the UEFI screen won't really change that much time in the end. 

loading the foreign secretely compiled keys into the kernel directly it's a huge risk ! Period. I don't care if you want to attract new users etc... it just goes against the whole idea of opensource and security. They should let the end user choise if they want these keys to be signed and loaded into their kernel or not. For some security is a choise/option, for others is a neccessity.

> 
Garrett replied that he can't see Red Hat getting into the key signing business. Peter Jones, a Red Hat software engineer and member of the Fedora Engineering Steering Committee, agreed: " Red Hat will not sign kernel modules built by an outside source. We're simply not going to sign these kernel modules. That's one of the big reasons we want a setup where they can sign their own modules in the first place."

from : [http://www.zdnet.com/torvalds-strongly-objects-to-windows-8-secure-boot-keys-in-the-linux-kernel-7000011811/](http://www.zdnet.com/torvalds-strongly-objects-to-windows-8-secure-boot-keys-in-the-linux-kernel-7000011811/)

---

### Post by Mathor on 2013-02-27
> **iamkuriouspurpleoranj said:**
> Call me stupid but I'm completely lost in the whole UEFI-Microsoft-Canonical-Red_Hat-Linux_Foundation saga.

If I buy a new PC now from a common-or-garden high street retailer will I be able to replace Windows 8 with a GNU/Linux OS? Will my choice be restricted to Fedora/Ubuntu? Does "Ubuntu" include other distros that use the Ubuntu repositories e.g. Mint?

I purchased a brand new HP machine preloaded with Windows 8 on it about a week ago. HP allows the user (and Microsoft leaves this option up to the vendor) to easily turn off UEFI by just a simple right arrow selection in BIOS.  Once you have done this, you can boot from a USB, CD, or whatever you would normally boot using Linux.  HP and Dell allow you to turn off secureboot very easily.  I have heard on other machines that it is possible to turn off secureboot, but I have heard that it is a tragically difficult process.

I appreciate HP and Dell allowing their users to have a choice. After all, even without Linux being involved, downgrading to Windows 7 is also prevented on machines with secureboot.  Users have the same amount of control over their computer as they do over their XBOX machines, in that case.

You can only thank Ubuntu for this, and their friendship with Dell and HP.  That being said, once secureboot is disabled, you can boot any distro you'd like.

EDIT:  And why exactly would one want to boot back into Windows 8?? It is a useless piece of UI. Even for schoolwork and occupations that use proprietary software, dualbooting with Windows 7 is not only much easier, but a more sensible solution.  I seriously doubt you will ever see a school library or an office building that uses Windows 8. Linus is right. It's a waste of code.

---

### Post by Paqman on 2013-02-27
> **MadmanRB said:**
> And that is the issue here, really we should be fighting this not catering to the whims of one of the most anti competitive companies of all time.

And how exactly would we do that? We're a tiny minority of computer users, we don't really have enough clout to bother Microsoft.

As for why they implemented Secure Boot, it was nothing to do with perceiving desktop Linux as a threat. Secure Boot was put there because:
[list]
[*]It's actually a good idea.
[*]It could be used to lock down their ARM-based Win8 machines, which would allow Win8 to get a foot in the door against Android.
[/list]

So I'll concede that Microsoft do consider Linux a threat, if you mean Android Linux. The idea that they'd actually bother taking action against desktop Linux is a bit silly. It would be like the Pentagon making preparations to defend the US against invasion by Fiji.

---

### Post by prodigy_ on 2013-02-27
All in all this story proves once again that no corporation, be it RedHat, Google or any other, can be a true supporter of Linux and FOSS community. They make money on Linux one way or another, but they care **only** about money, never about Linux.

---

### Post by fdrake on 2013-02-27
> **prodigy_ said:**
> All in all this story once again proves that no corporation, be it RedHat, Google or any other, is a true supporter of Linux and FOSS community. They make money on Linux one way or another, but they care **only** about money, never about Linux.

you know what they say: you get what you give.Microsoft and google did not come from the sky, ppl made them rich and powerful.
people around the world don't give a damn about FOSS, opendsource and linux, and that is why we endup having this kind of problem and being monotored by big companies. Man is a lazy, opportunistic being....

we could have better technologies if it wasn't for the copyright and propietary software licenses.

---

### Post by MadmanRB on 2013-02-27
> **fdrake said:**
> i don't really see the issue here. It is microsoft right to secure/lock their system if they feel it is in danger. Of course that doesn't prevent somone to get acces to their data, but so what? it's their choise, good or bad...

I personally think that if you need to dualboot, it is  already a time wasting process, so stopping first at the UEFI screen won't really change that much time in the end. 

loading the foreign secretely compiled keys into the kernel directly it's a huge risk ! Period. I don't care if you want to attract new users etc... it just goes against the whole idea of opensource and security. They should let the end user choise if they want these keys to be signed and loaded into their kernel or not. For some security is a choise/option, for others is a \

What a flip flopper, on one hand you seem pro microsoft but on the other hand seem supportive of opensourse.
MAKE UP YOUR MIND!
Support for UEFI is support for microsofts anti competitive behavior and must be called out for the bullcrap that it is.

> **Paqman said:**
> 
[*]It could be used to lock down their ARM-based Win8 machines, which would allow Win8 to get a foot in the door against Android.


Well yes microsoft is scared of android, thats because windows 8 is a sick pathetic OS.

---

### Post by fdrake on 2013-02-27
> **MadmanRB said:**
> What a flip flopper, on one hand you seem pro microsoft but on the other hand seem supportive of opensourse.
MAKE UP YOUR MIND!
:D 
i don't support Microsoft , i am just saying that they are not doing anything wrong or illegal.

> Support for UEFI is support for microsofts anti competitive behavior and must be called out for  the bullcrap that it is.that's where you are wrong.UEFI has nothing to do or to be blamed about it. 

I just think that if you want linux you can still install it on your pc. UEFI is not the real problem here, nor microsoft. The  market knows that the average user is dump. they just want to give their costumer a box that lets them use facebook, youtube and tweeter. that's all the market cares about. Possibly making this box a secure and not accessible with the minimum amount of efford from the end user.

---

### Post by zombifier25 on 2013-02-27
> **MadmanRB said:**
> What a flip flopper, on one hand you seem pro microsoft but on the other hand seem supportive of opensourse.
MAKE UP YOUR MIND!
Support for UEFI is support for microsofts anti competitive behavior and must be called out for the bullcrap that it is.

Why don't you try to be a reasonable person for once instead of all these close-minded rants about how Microsoft and UEFI is going to doom the world and we should use BIOS for another 30 years? Thanks but no thanks, I would rather stick with a modern and up-to-date bootloader rather than a hopelessly outdated piece of software that should have went out 10 years ago. Remember, UEFI != Microsoft.

I agree with Paqman; Secure Boot is put there because it's a good idea, and it can be used to help lockdown Windows tablets. Also, it's put there because  most of the users will not care what the heck it is, and those who do either are too insignificant or know how to work around it anyway. NTLDR and BOOTMGR does not recognize Linux, and we don't see people complaining about that, because most of us don't care. If we are installing Linux on a Windows machine, then we know this would happen. Heck, let's complain how new Windows machines don't come loaded with a option allowing you to choose between Windows or Linux.

If you want a Linux computer, then you'll buy a empty or Linux-loaded machine, or you'll buy a Windows machine and manually install Linux on it. It has been that way.

I'm not saying that Microsoft is the good guy; yes, they may be taking advantage of UEFI to make it harder for install Linux, but you should try to look at this from another perspective other than this usual anti-Microsoft goggles that some of us have been refusing to take off.

---

### Post by Paqman on 2013-02-27
> **MadmanRB said:**
> 
Support for UEFI is support for microsofts anti competitive behavior and must be called out for the bullcrap that it is.


No it isn't.

[list]
[*]UEFI is NOT a Microsoft technology. It was originally developed by Intel.
[*]UEFI can be implemented without Secure Boot. Apple have been using it for years.
[*]UEFI is the replacement for BIOS. BIOS is old and broken and has been in need of replacement for years. Whether we use UEFI or not has NOTHING to do with Microsoft or Secure Boot. Secure Boot is just part of Microsoft's particular implementation of UEFI.
[/list]

TL;DR: Your problem is with Secure Boot, not UEFI. UEFI is a good thing.

---

### Post by mamamia88 on 2013-02-27
> **stinkeye said:**
> Well in my case, after dual booting for a while, realized I didn't need MS 
products at all. Last purchased Microsoft OS was XP.

True your last purchase was xp.   But 99% of people stick with whatever came with the computer.  And even the ones who don't chances are it started out with windows.  So yeah what does Microsoft care if I use linux as long as I bought a computer with windows on it originally?  It's the greatest business model in the world for them anyway. And paqman what is broken about bios?  Honestly I couldn't care less if my pc uses bios or uefi as long as it boots up properly.

---

### Post by Paqman on 2013-02-27
> **mamamia88 said:**
> [b]And paqman what is broken about bios?

Just about everything. It doesn't support booting of modern operating systems on modern-sized disks (ie: >8.5GB), for a start. That's a pretty crucial weakness.

The only reason we've been able to continue using BIOS for so long is because individual vendors have hacked it ruthlessly. That's not a solution that can or should be extended indefinitely, however. There's only so long you can keep adding hacks to coax a broken system into working.

It's way past time for a system designed for modern systems that have things like USB and big disks.

> 
  Honestly I couldn't care less if my pc uses bios or uefi as long as it boots up properly.

Me neither. Dealing with this kind of thing is a technical issue for OEMs. How often do you delve into BIOS/UEFI really?

---

### Post by ssam on 2013-02-27
Matthew Garretts explanation of the patch he submitted.
[http://mjg59.dreamwidth.org/23400.html](http://mjg59.dreamwidth.org/23400.html)

Its worth noting that the issue being discussed now is not about booting linux on a secureboot machine. its about how you trust third party binary kernel modules (eg Nvidia drivers).

---

### Post by nikonian on 2013-02-27
Hey, guess what Apple did, to make a computer that runs perfectly with their OS? They conceived and designed their OWN machine specifications; why doesn't the Linux community do the same thing, and stop all this self-entitled complaining about why companies that make hardware to support *specific* software, doesn't allow their non-supported software to run? 

Did anyone promise you it *would*? You may well have bought the PC or Mac; you may well own it, but you bought it with your free will, knowing full well that Linux is a hackers paradise, and that you'd have to experiment a little... or a lot - Microsoft, Apple, Dell, HP... whoever, do not owe the Linux community one single thing - they make hardware that works with "X" version(s) of Windows, and Windows that works with "X" hardware devices.

If I buy a car garage, can I complain that my bus won't fit inside it? Yes, I *can* complain, but the garage was not designed for it.

If Canonical can release pointless Ubuntu phones, maybe they'd be better off making computers instead, seeing as there are so many people complaining that their hardware is not supported - were you promised it WOULD be?

In fact, if there are SO many Linux fans worldwide, many of whom have, collectively, hundreds of millions of dollars - if it means so much to them, why don't they pool their resources and start a company? I'll tell you why - it's not a good business model, there's not enough consistency in Linux releases, there's too much transience and the wider world uses Windows and Macs. There is not enough high quality software on Linux, to the level of that which Adobe, Apple etc release - there may be FOSS *alternatives*, but I'd prefer efficiency and the ease of use of a paid product, than the alternative of a headache caused by a "It's free - fix it yourself" approach.

---

### Post by mamamia88 on 2013-02-27
> **ssam said:**
> Matthew Garretts explanation of the patch he submitted.
[http://mjg59.dreamwidth.org/23400.html](http://mjg59.dreamwidth.org/23400.html)

Its worth noting that the issue being discussed now is not about booting linux on a secureboot machine. its about how you trust third party binary kernel modules (eg Nvidia drivers).

almost never but then again most manufacturers gimp their bios so there really aren't any valuable options to change.

---

### Post by grahammechanical on 2013-02-27
> They conceived and designed their OWN machine specifications; why doesn't the Linux community do the same thing,

This is what Canonical is trying to achieve and look at the way that all these friendly FOSS people have spat hate at Ubuntu.

If people choose to buy a Windows machine, then that is their choice. But many then expect to easily install a Linux distribution on it. When was that ever easy? Put to one side UEFI and Secure Boot. Think instead about Microsoft using up the four allowed primary partitions or setting the disk as a dynamic disk. It is not easy for a non computer educated person to install any Linux distribution. Unless it is on a blank disk.

We should be thankful that some people are doing something to make it possible to install Ubuntu or other Linux distributions on this hardware. Of course, those of us who are fanatical in our beliefs can continue to be so.

Regards.

---

### Post by Roasted on 2013-02-27
> **nikonian said:**
> *snip*

Since the beginning, you've been able to install compatible operating systems on the hardware from any vendor. Apple is working with an Apple OS on Apple hardware. That's a different beast altogether. On the flip side, you have all of these hardware companies that are essentially forced into abiding to Microsoft's ridiculous secure boot, and it's completely understandable why these companies succumb to those terms. If 98% of your sales are based on Windows, and you disagree with what Microsoft is doing, it's an easy calculation to come to: Abide by Microsoft, increase my changes of staying in business substantially. 

While you do bring up some valid points that are worth noting, under no circumstances do I agree with them in the slightest order of magnitude. I know I'm a small blip on the radar, but when I purchase hardware, I purchase hardware that I know will work with my operating system of choice. If *insert-company-here* chooses to lock out alternative operating systems, I won't support them. I know my lack of support for their gear won't put them out of business, but that's not my goal. My goal is to support the companies out there that deserve it. A company that supports only Microsoft 100% of the way is not an organization I want to be associated with in the slightest.

---

### Post by graabein on 2013-02-27
Go Linus!

---

### Post by Gyokuro on 2013-02-27
Hi

It is Linus again with strong words but he is right - I want to have full control of my hardware/software and if you look at past security problems with stolen certificates or hacked certificate authorities nobody can assure me that this do not happen again.  Stux, flame demonstrated what is possible with people which are skilled enough to play with such technologies and nobody knows how long it would take that such altered keys get revoked. But the problems with UEFI are old as it be - Coreboot could be a much better replacement for a BIOS but Microsoft and other big players are interested that UEFI get used. They have much more control over the hardware as in the past.

---

### Post by nikonian on 2013-02-27
With all respect, I feel many Linux users are blinded by their demands for "freedom" of the hardware. Computers are manufactured specifically to use Windows or Mac OS X; if there was a demand for Linux PCs, they would make them, and they don't - doesn't that tell you something?

You can approach this debate from any angle you want to push your agenda, but the fact is simple; most people DO NOT CARE about Linux, and why would the hardware manufacturers spend money - LOTS of it - just to keep a tiny minority happy?

Wake up Linux.

---

### Post by MadmanRB on 2013-02-27
> **nikonian said:**
> With all respect, I feel many Linux users are blinded by their demands for "freedom" of the hardware. Computers are manufactured specifically to use Windows or Mac OS X; if there was a demand for Linux PCs, they would make them, and they don't - doesn't that tell you something?

You can approach this debate from any angle you want to push your agenda, but the fact is simple; most people DO NOT CARE about Linux, and why would the hardware manufacturers spend money - LOTS of it - just to keep a tiny minority happy?

Wake up Linux.

Bah your pro Microsoft stance, it goes beyond redundant

---

### Post by prodigy_ on 2013-02-27
> **nikonian said:**
> Computers are manufactured specifically to use Windows
O'rly? Last time I checked I had to pay for my hardware. And I want to be free to do whatever I please with it.

---

Back to topic: a Linus post from lkml.org:

> > Our users want to be able to boot Linux. If Microsoft blacklist 
> a distribution's bootloader, that user isn't going to be able to 
>boot Linux any more. How does that benefit our users?


How does bringing up an unlikely and bogus scenario - and when people call you on it, just double down on it - help users?

Stop the fear mongering already.

So here's what I would suggest, and it is based on REAL SECURITY and on PUTTING THE USER FIRST instead of your continual "let's please microsoft by doing idiotic crap" approach.

So instead of pleasing microsoft, try to see how we can add real security:

- a distro should sign its own modules AND NOTHING ELSE by default. And it damn well shouldn't allow any other modules to be loaded at all by default, because why the f*ck should it? And what the hell should a microsoft signature have to do with *anything*?

- before loading any third-party module, you'd better make sure you ask the user for permission. On the console. Not using keys. Nothing like that. Keys will be compromised. Try to limit the damage, but more importantly, let the user be in control.

- encourage things like per-host random keys - with the stupid UEFI checks disabled entirely if required. They are almost certainly going to be *more* secure than depending on some crazy root of trust based on a big company, with key signing authorities that trust anybody with a credit card. Try to teach people about things like that instead. Encourage people to do their own (random) keys, and adding those to their UEFI setups (or not: the whole UEFI thing is more about control than security), and strive to do things like one-time signing with the private key thrown out entirely. IOW try to encourage *that* kind of "we made sure to ask the user very explicitly with big warnings and create his own key for that particular module" security. Real security, not "we control the user" security.

Sure, users will screw that up too. They'll want to load crazy nvidia binary modules etc crap. But make it *their* decision, and under *their* control, instead of trying to tell the world about how this should be blessed by Microsoft.

Because it really shouldn't be about MS blessings, it should be about the *user* blessing kernel modules.

Quite frankly, *you* are what he key-hating crazies were afraid of. You peddle the "control, not security" crap-ware. The whole "MS owns your machine" is *exactly* the wrong way to use keys.

---

### Post by prodigy_ on 2013-02-27
[cut]

---

### Post by forrestcupp on 2013-02-27
People should take a step back and look at things from a normal user's perspective. By far, the biggest majority of desktop Linux installs is going to go onto a Windows PC. From now on, every Windows PC is going to have Windows 8 or later on it. Why in the world would you *not* want to make it easier to install Linux on a Windows PC at the kernel's level?

Like it or not, this is a new way of life. If you want to intentionally make it harder to install Linux because you don't like this, then don't go crying about nobody wanting to install Linux. But know one thing, a few people whining about this isn't going to change anything.

---

### Post by sunfromhere on 2013-02-27
> **nikonian said:**
> With all respect, I feel many Linux users are blinded by their demands for "freedom" of the hardware. Computers are manufactured specifically to use Windows or Mac OS X; if there was a demand for Linux PCs, they would make them, and they don't - doesn't that tell you something?

You can approach this debate from any angle you want to push your agenda, but the fact is simple; most people DO NOT CARE about Linux, and why would the hardware manufacturers spend money - LOTS of it - just to keep a tiny minority happy?

Wake up Linux.

You're from the US?
I'm from a soon-to-be-in-EU, and I can tell you, when I look at our local online hardware store, almost 50% of laptops and premade desktops have Linux preinstalled. Yes, they do that in order to reduce the price and probably believe that people will put (pirated) Windows on that, but the fact is that I have the same choice range as Windows users if I want to buy a Linux computer. 

(In fact, some Dell laptops available are Ubuntu only, no preinstalled Windows.)

---

### Post by stinkeye on 2013-02-27
> **nikonian said:**
> With all respect, I feel many Linux users are blinded by their demands for "freedom" of the hardware. Computers are manufactured specifically to use Windows or Mac OS X; if there was a demand for Linux PCs, they would make them, and they don't - doesn't that tell you something?

You can approach this debate from any angle you want to push your agenda, but the fact is simple; most people DO NOT CARE about Linux, and why would the hardware manufacturers spend money - LOTS of it - just to keep a tiny minority happy?

Wake up Linux.
Whose blind? People like you don't even see when your being corralled
for the fleecing.

---

### Post by Lisiano on 2013-02-27
Well, this was a interesting thread to read.
My 2 cents:
As people say UEFI != Secure Boot || Microsoft, I actually want my next PC to have UEFI, more flexibility and faster boot up speeds (Maybe I'm mistaken but I did read somewhere that instead of initializing everything, UEFI just inits the boot device and GPU then gives control directly to the bootloader).
As for Secure Boot, I totally agree with Linus, why the hell should the Kernel cater to the will of Microsoft!? If a user truly wants to get Linux on their PC, they will get it, just look at the Beginner section of this forum! People who don't want to bother with Linux are usually driven away after they are told they need to burn a DVD/USB! Plus OEMs will provide tools to disable Secure Boot. Why? Because if your random Bob will have a problem with a PC, they won't go to Microsoft, they'll bug the OEM! Actually... They will bug whatever store they bought the PC from. But an Alice will just find a way to get Linux installed.
It's kind of the same in the Android world, if a person wants to run custom roms or just get plain root, they will either stop at a "Download this and do this" tutorial and think "Nah" or they will go through the whole process and get the thing they want, I like to think of Secure Boot kind of like a locked bootloader on an Android device, a pain in le cushion-for-your-body-to-sit-on-chair but "fixable" :popcorn:
Also, if Secure Boot stops more whiny users that can't even think outside the tools given to them, cool, let them stay with MS, less work keeping those people happy.

---

### Post by JDShu on 2013-02-27
> **ssam said:**
> 
Its worth noting that the issue being discussed now is not about booting linux on a secureboot machine. its about how you trust third party binary kernel modules (eg Nvidia drivers).

Everybody reading this thread, please take note. This is the crux of the issue. Linus is arguing that users should make their own decisions about whether to trust third party modules such as NVidia drivers. Garrett is arguing that we should make things as easy to use and secure for Linux users as possible, even if it means needing MS specific code in the kernel. They are both reasonable positions.

---

### Post by fdrake on 2013-02-27
> **JDShu said:**
> Everybody reading this thread, please take note. This is the crux of the issue. Linus is arguing that users should make their own decisions about whether to trust third party modules such as NVidia drivers. Garrett is arguing that we should make things as easy to use and secure for Linux users as possible, even if it means needing MS specific code in the kernel. They are both reasonable positions.

=D>

that's the point of all the discussion. same thing like for private codecs , drivers and so on. We should be the one deciding for it , not the kernel's developers/mantainers.

LINUS is still protecting our right as users(our freedom and privacy). If we cannot appriaciate that , we should not deserve it.

Please do not make this thread another linux vs windows fight..

---

### Post by nikonian on 2013-02-27
> **prodigy_ said:**
> O'rly? Last time I checked I had to pay for my hardware. And I want to be free to do whatever I please with it.

---

Back to topic: a Linus post from lklm.org:

You are free to do whatever you want ***with*** your hardware, in the same respect that the manufacturers of that hardware are equally as entitled to put whatever restrictions on it that they wish, for whatever reason, since they designed it and sold it. 

I can buy a cake, but that doesn't mean I am "entitled" to an exact secret recipe; I can cut the cake, eat it, give it away or throw it away, my free will extends as far as I like, but the baker doesn't have to make that cake to my specific recipe, NOR do they have to give me a concise list of ingredients and cooking times.

Would you complain if you bought a car, but found out that it doesn't have suitable wheels to run on a railway track? Don't be  naive - you can do whatever you will with it, but no company is obliged to ensure that the hardware they sell is TOTALLY compatible with every conceivable software environment that any one user, or users, may choose to attempt to make it work with.

If **you** want to hack it and get it to work, go for it and share the fruits all you like; after all - is that not what Linux was intended to do? You're not "owed" a single thing - _you_ paid for it knowing full well it may OR may not be compatible, so you have no recourse or reason for complaint.

The computer experience for most users is:

1/ Research computer and capabilities

2/ Buy chosen model

3/ Turn on, install software and use computer


With all due respect to the FOSS community, the people likely to buy a PC or other hardware, and then want to make it work with non-supported software, are such an insignificant sprinkling, that it is not worth the manufacturers while to make it happen. Linux and FOSS are all very well, but hardware and software companies in the mainstream, real world, are in business to make money, not to cater for every possible hobbyist or fringe exception user.



Take care.

---

### Post by JDShu on 2013-02-27
> **fdrake said:**
> =D>
LINUS is still protecting our right as users(our freedom and privacy). If we cannot appriaciate that , we should not deserve it.


To be honest, not really. My understanding is that what Linus is protecting is the purity of the Linux Kernel. In his view, there's no point in parsing Windows specific binaries in the Linux kernel when the standard is already supported. As I think he mentions in the thread, this is why various other parts of the kernel were taken out over time - they were not directly related to kernel functions. This is very much an engineering argument.

Personally I use all open source software on the hardware level, with the exception of firmware binaries. However, if I *were* an NVidia or AMD Catalyst user, I would probably be a bit more comfortable if the disputed code was merged. It is at least one more attack vector that I wouldn't need to worry about.

Finally, it's not like this would really give control to Microsoft from a user perspective. If you didn't want them calling the shots about what binaries are secure, then you could simply disable Secure Boot.

---

### Post by pqwoerituytrueiwoq on 2013-02-27
> **stinkeye said:**
> Well in my case, after dual booting for a while, realized I didn't need MS 
products at all. Last purchased Microsoft OS was XP.
same here, i just never bought a license key unless it came with the system i got, and i build my all my desktops so i don't get a key when i do that, i have not seen any retail motherboards with secure boot enabled by default (i have built 2 system with UEFI BIOS)
i also used virtualbox for windows for some time, but have found i rarely if ever use it

---

### Post by Roasted on 2013-02-27
> **nikonian said:**
> With all respect, I feel many Linux users are blinded by their demands for "freedom" of the hardware. Computers are manufactured specifically to use Windows or Mac OS X; if there was a demand for Linux PCs, they would make them, and they don't - doesn't that tell you something?

You can approach this debate from any angle you want to push your agenda, but the fact is simple; most people DO NOT CARE about Linux, and why would the hardware manufacturers spend money - LOTS of it - just to keep a tiny minority happy?

Wake up Linux.

If I buy a computer, I want to do with it as I please. This is why I do not support Apple and why I will not support vendors who lock their hardware to correspond with Microsoft's ridiculous boot loader requirements.

Candid side note: Your stance is rather illogical and irritating on many levels.

---

### Post by nikonian on 2013-02-27
> **Roasted said:**
> If I buy a computer, I want to do with it as I please. This is why I do not support Apple and why I will not support vendors who lock their hardware to correspond with Microsoft's ridiculous boot loader requirements.

Candid side note: Your stance is rather illogical and irritating on many levels.

Passive aggression doesn't help much.

I don't think Apple or Microsoft or anyone else will lose a picosecond of sleep over whether you will or won't "support" them, in a protest of non-purchase; they have MANY MANY more who will, that is the POINT here.

Maybe it is mindsets like this that have prevented Linux from moving any further into mass adoption; too much self-entitlement and faux "protests" that are basically arrogance, foot stamping and tunnel vision. If you do not like how computers are made, why not give them up? Noone cares, with due respect - it's not a moral issue, it's a geeky, willfully pedantic one, and the majority of the world are blissfully ignorant of this ghastly aspect of computing!

---

### Post by JDShu on 2013-02-27
> **nikonian said:**
> Passive aggression doesn't help much.

I don't think Apple or Microsoft or anyone else will lose a picosecond of sleep over whether you will or won't "support" them, in a protest of non-purchase; they have MANY MANY more who will, that is the POINT here.

Maybe it is mindsets like this that have prevented Linux from moving any further into mass adoption; too much self-entitlement and faux "protests" that are basically arrogance, foot stamping and tunnel vision. If you do not like how computers are made, why not give them up? Noone cares, with due respect - it's not a moral issue, it's a geeky, willfully pedantic one, and the majority of the world are blissfully ignorant of this ghastly aspect of computing!

I don't understand the relevance of your posts. Do you actually have a stance on the issue Linus and Garrett have brought up, or are you just being sanctimonious?

---

### Post by mörgæs on 2013-02-27
I have jailed a post from the thread.

Everybody, please stay on topic and take care only to post contents of value to the reader. Post in a manner that provides people insight and widens their view.

---

### Post by Roasted on 2013-02-27
> **nikonian said:**
> 
I don't think Apple or Microsoft or anyone else will lose a picosecond of sleep over whether you will or won't "support" them, in a protest of non-purchase; they have MANY MANY more who will, that is the POINT here.


> **Roasted said:**
> I know I'm a small blip on the radar, but when I purchase hardware, I purchase hardware that I know will work with my operating system of choice. If *insert-company-here* chooses to lock out alternative operating systems, I won't support them. _I know my lack of support for their gear won't put them out of business, but that's not my goal. My goal is to support the companies out there that deserve it._ A company that supports only Microsoft 100% of the way is not an organization I want to be associated with in the slightest.

Derp derp.



In other news, am I understanding correctly that if Linux *would* do this, they would have to dish out some cash to Microsoft? Would this in theory be a cost per license, or simply one flat charge for a single key to boot an infinite number of distros?

---

### Post by JDShu on 2013-02-27
> **Roasted said:**
> 
In other news, am I understanding correctly that if Linux *would* do this, they would have to dish out some cash to Microsoft? Would this in theory be a cost per license, or simply one flat charge for a single key to boot an infinite number of distros?

Source for why you think this is the case? I think that can't be true.

---

### Post by Linuxratty on 2013-02-27
> **MadmanRB said:**
> Thusd is the issue, we should not bow down to microsoft, linux is a competitor not a lap dog.
There should be a antitrust lawsuit here, 

 I agree. I've said the same thing since the whole monstrosity started.

Why do so few people see the elephant in the room?
 That being said, all future machines I purchase will be from a Linux vendor like Zareason.

---

### Post by Roasted on 2013-02-27
> **JDShu said:**
> Source for why you think this is the case? I think that can't be true.

I don't have a source. It was just online discussion with other users. Some people seem to be under different interpretations of exactly what this would entail if Linux would go for it.

---

### Post by JDShu on 2013-02-27
> **Roasted said:**
> I don't have a source. It was just online discussion with other users. Some people seem to be under different interpretations of exactly what this would entail if Linux would go for it.

Ah ok, in that case they are wrong. For one, there is no way Microsoft could enforce such a cost unless they sue with a patent that they own. Copyright law definitely doesn't apply as the code that would be merged is written by Red Hat.

---

### Post by codingman on 2013-02-28
> **mikewhatever said:**
> IMHO, these rants by Linus are an embarrassment. Can't he express his thoughts without swearing like a drunk sailor? Looks like the man is bored to death, so he writes obscene emails to insult people.

I totally agree. *Anger Issues* *Anger Issues*

---

### Post by codingman on 2013-02-28
> **prodigy_ said:**
> All in all this story proves once again that no corporation, be it RedHat, Google or any other, can be a true supporter of Linux and FOSS community. They make money on Linux one way or another, but they care **only** about money, never about Linux.

It's so true. It proves greed. I have only seen the word Linux once in the android os which is in the dev options, and very hidden.

---

### Post by ikt on 2013-02-28
> **codingman said:**
> I totally agree. *Anger Issues* *Anger Issues*

The man writes emails all day, 99.99999% of all emails he writes don't get noticed, it's only because he's taken a particularly hard stance and been vocal about a particular issue that it makes the news.

---

### Post by codingman on 2013-02-28
> **Paqman said:**
> Just about everything. It doesn't support booting of modern operating systems on modern-sized disks (ie: >8.5GB), for a start. That's a pretty crucial weakness.

The only reason we've been able to continue using BIOS for so long is because individual vendors have hacked it ruthlessly. That's not a solution that can or should be extended indefinitely, however. There's only so long you can keep adding hacks to coax a broken system into working.

It's way past time for a system designed for modern systems that have things like USB and big disks.



Me neither. Dealing with this kind of thing is a technical issue for OEMs. How often do you delve into BIOS/UEFI really?

Sorry to tell ya, but I have had an old build with regular BIOS and it loads faster than this stupid UEFI thingamajig that is on my new build. The dumb UEFI has TONS of graphical additions that make it a billion times slower than the BIOS, as well as it braking more. I think that the old BIOS was good because it had been mastered as far as usability and not crashing.

---

### Post by codingman on 2013-02-28
> **ikt said:**
> The man writes emails all day, 99.99999% of all emails he writes don't get noticed, it's only because he's taken a particularly hard stance and been vocal about a particular issue that it makes the news.

I'm not surprised. I really don't care what he has to say as long as he maintains the kernel. :)

---

### Post by codingman on 2013-02-28
Oh, just shutup and put the code in the kernel, we're all happier without the hassle of cracking secure boot manually. Face it, the future generation of computers are gonna have w8 or later w/ secure boot. You can say Linus is protecting our freedom but rather just standing up for no reason. Swallow your pride, Torvalds, and I won't have to go back to looking at the "Please Wait..." of W7.

---

### Post by Redalien0304 on 2013-03-01
Linux needs to develop ther own own way of of dealing with UFEI Secure Boot Instead of using Microsoft Junk. I have Totally Dumped Windows. Istill have Win 7 But dontr use it though. i will NOT Windows 8 for sure iv seen it & it's pure Junk

---

### Post by UltimateCat on 2013-03-01
Here's how The Linux Foundation is dealing with it for now-

[http://www.zdnet.com/linux-foundation-releases-windows-secure-boot-fix-7000011084/](http://www.zdnet.com/linux-foundation-releases-windows-secure-boot-fix-7000011084/)

---

### Post by Erik1984 on 2013-03-01
> **alien0304 said:**
> Linux needs to develop ther own own way of of dealing with UFEI Secure Boot Instead of using Microsoft Junk. I have Totally Dumped Windows. Istill have Win 7 But dontr use it though. i will NOT Windows 8 for sure iv seen it & it's pure Junk

How? It's not easy, UEFI + secure boot is a fact on most new motherboards. Without a signed boot loader you can't boot Linux with secure boot enabled. AFAIK Torvalds' alternative for signed modules only applies to systems where you can disable UEFI secure boot. Do you really think Red Hat *likes* to get their stuff signed by MS?

---

### Post by forrestcupp on 2013-03-01
> **alien0304 said:**
> Linux needs to develop ther own own way of of dealing with UFEI Secure Boot Instead of using Microsoft Junk. I have Totally Dumped Windows. Istill have Win 7 But dontr use it though. i will NOT Windows 8 for sure iv seen it & it's pure JunkWindows 8 is not all junk. If you install a 3rd party Start menu that bypasses the ModernUI and goes straight to the desktop, it's actually better than Windows 7. Win 8 is faster and more stable than Win7, and it actually has some great updated features in desktop mode. Since I installed the 3rd party Start menu, I don't think I've hardly looked at ModernUI once.

---

### Post by mips on 2013-03-01
> **forrestcupp said:**
> Windows 8 is not all junk. If you install a 3rd party Start menu that bypasses the ModernUI and goes straight to the desktop, it's actually better than Windows 7. Win 8 is faster and more stable than Win7, and it actually has some great updated features in desktop mode. Since I installed the 3rd party Start menu, I don't think I've hardly looked at ModernUI once.

+1

I tried out all the start menus you get and think Pokki is the best out of the lot.
[http://www.pokki.com/windows-8-start-menu](http://www.pokki.com/windows-8-start-menu)

---

### Post by sdowney717 on 2013-03-01
The regular population will want secure boot. They will think it is better, more secure, safer for their data. When they hear that to boot Linux they cant do a secure boot they will reject Linux even irrationally. Just tell them you got to turn off a secure boot to boot Linux and turn on a secure boot to boot good old normal windows and it will be a no brainer choice to make in favor for a more secure boot. Just another obstacle in the path to Linux, IMO!

Cant boot it Linux OS securely means to them something not right, not as good.

---

### Post by Ender Shadow on 2013-03-01
> **Paqman said:**
> Just about everything. It doesn't support booting of modern operating systems on modern-sized disks (ie: >8.5GB), for a start. That's a pretty crucial weakness...


I have to disagree.
I had an almost 14 year old motherboard (with BIOS) and 20 GB hdd with Ubuntu 10.04 on it, and it booted just fine.
Now, I have a less than 2 month old motherboard (with UEFI) that sometimes fails to even recognize the hard drive.

---

### Post by iamkuriouspurpleoranj on 2013-03-02
> **sdowney717 said:**
> The regular population will want secure boot. They will think it is better, more secure, safer for their data. When they hear that to boot Linux they cant do a secure boot they will reject Linux even irrationally. Just tell them you got to turn off a secure boot to boot Linux and turn on a secure boot to boot good old normal windows and it will be a no brainer choice to make in favor for a more secure boot. Just another obstacle in the path to Linux, IMO!

Cant boot it Linux OS securely means to them something not right, not as good.

You could be right. Communication is essential. Just point out that the US Army is a Red Hat customer and that the London Stock Exchange is a SUSE customer.

---

### Post by aquarius18 on 2013-03-02
> **MadmanRB said:**
> Thusd is the issue, we should not bow down to microsoft, linux is a competitor not a lap dog.
There should be a antitrust lawsuit here, but it wont happen becase most linux companies including canonical rather pay blood money then stand up for linuxes right to exist.

Yep, agree to the fullest.

They (M$) got everything to worry about when you look at the stats of the top 500 super computers: > 93% Linux, a few mixed and 3 or 4 M$ based.

Linux has made progress in leaps and bounds since I have been using various flavours and distros from 2009 onwards (yes, I am a newbee...).

Mobile phones are dominated by Android and growing in numbers, M$ is nowhere to be seen in the stats of the mobile phone market.

How many TV's are powered by M$???

There are still a few hurdles to jump before mums and dads changing their desktops from M$ to Linux, but lets face it: numbers are growing but fast.

M$ is trying to keep Linux out of machines with vendor installed Secure Boot Win 8 OS's as they can see the end of their time. And that's the only reason they have chosen this path - they are sh.. scared!

---

### Post by prodigy_ on 2013-03-02
> **sdowney717 said:**
> Just another obstacle in the path to Linux, IMO!
While "Secure" Boot is a misnomer (pure marketing, it should have been something like Controlled Boot or, even better, Restricted Boot) and the current implementation is an atrocity, it's not such a big obstacle. Anyone with half a brain can read a couple of articles on the subject and decide for themselves. And anyone who can't probably won't bother with migrating to Linux anyway.

---

### Post by mJayk on 2013-03-02
> **prodigy_ said:**
> While "Secure" Boot is a misnomer (pure marketing, it should have been something like Controlled Boot or, even better, Restricted Boot) and the current implementation is an atrocity, it's not such a big obstacle. Anyone with half a brain can read a couple of articles on the subject and decide for themselves. And anyone who can't probably won't bother with migrating to Linux anyway.



 I believe this is true, idiots who see the word Secure and therefore think they require it / its better.

---

### Post by Paqman on 2013-03-02
> **Ender Shadow said:**
> I have to disagree.
I had an almost 14 year old motherboard (with BIOS) and 20 GB hdd with Ubuntu 10.04 on it, and it booted just fine.
Now, I have a less than 2 month old motherboard (with UEFI) that sometimes fails to even recognize the hard drive.

That doesn't refute my point that BIOS is an outdated hacky mess, and is in need of a modern replacement. My point wasn't that BIOS couldn't boot a machine, it was that the code that it required to do so was a nightmare.

It's a bit like the situation with X. Changing such a fundamental component is not likely to be bug-free, but continuing to use it past it's use-by date becomes an ever-increasing maintenance headache, and holds back innovation.

---

### Post by alexfish on 2013-03-02
This is off the hip. well not so much as off the hip.

and No pun intended.

Linux as a Kernel is secure By It's self, it does no need a Key, or anything that gives sight of what the kernel is doing !

had seen a few posts relating to this article a while back , proof is about facts ,

Linus as the person is correct, and entitled to his thoughts , or opinion , end of.

Dual boot if you wish. that is at your request, give a key to do so , that is your honour. 

Single boot with Linux then that be honour , 

There is only one way for Linux and it's way ,Linux. Free open and secure.

Time to decide . Linux and accept it. There are many institutions will baulk at the thought of introducing a foreigner, as in a separate key,

Linux boot , Linux will boot. No key required.

UEFI is not is not new in concept. Linux already has is it. 

Another aspect, Licience , paid for once , or given free ,then what, all of your system then becomes *PROPIORTY, in only one sence.**PROPIORTY.*

BR

Alex

---

### Post by darkcrimson on 2013-03-03
I love how it's being marketed as "Secure" boot. I suppose nobody would want it if it were called "Limited" boot or "Proprietary" boot.

---

### Post by Paqman on 2013-03-03
> **darkcrimson said:**
> I love how it's being marketed as "Secure" boot. I suppose nobody would want it if it were called "Limited" boot or "Proprietary" boot.

Well, it does have both a security and a limiting role, so they're not actually wrong to call it that. But yes, one can't help but wonder which aspect of it got Microsoft most interested. Certainly they've shown no great urgency to replace BIOS until now.

---

