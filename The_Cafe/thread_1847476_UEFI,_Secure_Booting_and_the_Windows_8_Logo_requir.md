---
title: "UEFI, Secure Booting and the Windows 8 Logo requirements locking out GNU / Linux"
date: 2011-09-20
forum: The Cafe
---

### Post by Dr. C on 2011-09-20
The real threat here is that Windows 8 Logo computer will prevent GNU / Linux from booting as part of the "secure boot" process. When combined with anti circumvention legislation it could even make it illegal in certain countries to install  GNU / Linux on certain computers since one would have to crack the DRM in the UEFI boot loader in order to boot an "untrusted" binary. The legal situation would not be different for example to cracking the DRM on a PS3 in order to install GNU / Linux on it. 

Here are some articles with some the early warning signs. 

[http://www.itwire.com/opinion-and-analysis/open-sauce/49889-will-windows-8-succeed-in-locking-out-gnulinux]("http://www.itwire.com/opinion-and-analysis/open-sauce/49889-will-windows-8-succeed-in-locking-out-gnulinux") 
[UEFI Secure Booting by Mathew Garrett ]("http://mjg59.dreamwidth.org/5552.html") 
[UEFI and "secure boot"]("http://lwn.net/Articles/447381/")

---

### Post by SirDrexl on 2011-09-20
Well, it makes me glad I build my own computers, but this could be an  issue for laptops and the like which have to be bought with an OS  already installed.  When I need to get a new netbook, I should be able  to find one with Linux.  Perhaps manufacturers will even offer more  options because of this?
 
 What really concerns me is that people who buy a system with Windows 8 could be unable to even try Linux, which would in turn hurt the  potential userbase.  Even if a way around it is found, it might be  beyond the scope of an average user (like permanently getting around  Windows' protection now), or make would-be users nervous that it's a  "crack."

---

### Post by Thewhistlingwind on 2011-09-20
Don't forget:

[Microsoft locks Metro-style apps to Windows Store, developers and enterprise keep sideloading privileges -- Engadget]("http://www.engadget.com/2011/09/19/microsoft-locks-metro-style-apps-to-windows-store-developers-an/#disqus_thread") 

:popcorn:

War time.

[http://futureoftheinternet.org/](http://futureoftheinternet.org/)

---

### Post by IWantFroyo on 2011-09-20
Oh gosh. There go all my fancy laptop dreams.

I build my own desktops, but I don't know of any way to build my own laptop.

Anyone know any resources? Or is it just not possible?

Also, doesn't this sort of kill the point of those "Happy Birthday Linux" videos MS made?

---

### Post by Dangertux on 2011-09-21
This won't be the first time Microsoft has been dragged into court for anti-trust and I doubt it will be the last. lol.

---

### Post by szymon_g on 2011-09-21
> **Dangertux said:**
> This won't be the first time Microsoft has been dragged into court for anti-trust and I doubt it will be the last. lol.

what does it have to do with MS? lemme guess- its all their fault, right?

but, seriously:
1. trusted boot can be used on linux
2. it will be used on workstations, not on 'home pc'
3. it will be supported by the higher versions of Windows /enterprise, ultimate etc/
4. in overall, it is a great feature /shame that it's not supported as easily /for end user/ as on windows/

---

### Post by Retlol on 2011-09-21
This will not happen in the EU, MS would get smacked around by Neelie Kroes.

---

### Post by Lars Noodén on 2011-09-21
> **Dangertux said:**
> This won't be the first time Microsoft has been dragged into court for anti-trust and I doubt it will be the last. lol.

Don't rely on antitrust action to resolve any problems in a timely manner.  The [WordPerfect/Quattro](http://www.groklaw.net/article.php?story=20110919044802339) case from 1994 is just getting started.  It's good that this is going forward, but in the case of locking down the boot process, other measures are needed.

---

### Post by Canis familiaris on 2011-09-21
Couldn't it just be that the set of keys for Windows 8 be pre-authorized, while instead of blocking the other operating system which are not authorized, there could be a simple warning that "this key is not recognized, wanna continue?" similar to SSH logins? Pardon me if I am completely missing the point, but isn't this the most practical approach.

---

### Post by undecim on 2011-09-21
> **Canis familiaris said:**
> Couldn't it just be that the set of keys for Windows 8 be pre-authorized, while instead of blocking the other operating system which are not authorized, there could be a simple warning that "this key is not recognized, wanna continue?" similar to SSH logins? Pardon me if I am completely missing the point, but isn't this the most practical approach.

If your goal was to allow multiple operating systems to boot, then yes. However, I really doubt that Microsoft, and anyone they can pressure (read "OEMs") would have this goal in mind.

Then you also have to consider that secure boot (in theory) is supposed to prevent rootkits that the average user (let's call them "newbies") might get infected with.

Now, suppose that secure boot IS implemented this way. What happens when a newbie gets the "this key is not recognized" screen? (hint: they don't know what a cryptographic key is, and only really care about getting to their desktop). In this case, the proposed purpose of secure boot is completely circumvented.

Another option might be to have a bright red warning. e.g. something to the effect of "WARNING: This boot file is not recognized. This may be due to a virus infection. It is recommended to not continue booting until a PC technician has examined your system." But then the newbies would see this right after installing Ubuntu and tell all their friends that it's a virus. (especially if they're unlucky enough to take it to someone that doesn't know what Linux is)

---

### Post by SuperFreak on 2011-09-21
Apologies if this link has already been posted but it warrants more discussion here


[http://www.theregister.co.uk/2011/09/21/secure_boot_firmware_linux_exclusion_fears/](http://www.theregister.co.uk/2011/09/21/secure_boot_firmware_linux_exclusion_fears/)

---

### Post by cap10Ibraim on 2011-09-21
> 
New secure boot process leaves unsigned Linux out in the cold
Red Hat's Matthew Garrett was one of the first to notice that according to the new logo rules, all Windows 8 machines will need to be have the Unified Extensible Firmware Interface (UEFI) instead of the venerable BIOS firmware layer. BIOS has been pretty much the sole firmware interface for PCs for a long time.

The EFI system has slowly been making headway in recent years, and right now EFI firmware is compatible with Windows supporting the GUID Partition Table (GPT), OS X/Intel, and Linux 2.6 and beyond machines. EFI is seen as a better hardware/software interface than BIOS, since it is platform-agnostic, runs in 32- or 64-bit mode, and GPT machines can handle boot partitions of up to 9.4 zettabytes. (That's 9.5 billion terabytes to you and me.)

EFI, and the later UEFI specification, is not the problem for Linux. The problem is Microsoft's other requirement for any Windows 8-certified client: the system must support secure booting. This hardened boot means that "all firmware and software in the boot process must be signed by a trusted Certificate Authority (CA)," according to slides from a recent presentation on the UEFI boot process made by Arie van der Hoeven, Microsoft Principal Lead Program Manager.
 [continue reading]("http://www.itworld.com/it-managementstrategy/205255/windows-8-oem-specs-may-block-linux-booting")
[more at the register.co.uk]("http://www.theregister.co.uk/2011/09/21/secure_boot_firmware_linux_exclusion_fears/")

---

### Post by marin123 on 2011-09-21
I think they went for minimizing pirated versions of Windows, not killing Linux.

I guess it will be impossible to reinstall Windows in the future. And in my experience it should be once a year, to get rid of junk, missing files etc, and that's the year of Linux :)

Now, I guess, people will start looking to buy a computer without preinstalled Windows.

---

### Post by Beacon11 on 2011-09-21
That's okay-- just buy from people like System76, or heck-- a Mac. Keep in mind that Windows 8 is being developed with mobile devices in mind. While I don't trust Microsoft in the least, I think this speaks more to locking down tablets and phones than desktops and laptops.

---

### Post by SuperFreak on 2011-09-21
So building a custom machine with UEFFI won't work. Not liking that much.

---

### Post by 3Miro on 2011-09-21
Wait, I don't understand this. Linux already works with EFI and there is nothing in the EFI that blocks Linux.

"must support secure booting" is different from "requires secure booting" or "doesn't support any other booting". From what I understand this is just support for a Windows feature.

Furthermore, what is preventing Linux from being digitally signed? From what I understand the Ubuntu repositories are digitally signed. Is this something that smaller distos would not be able to handle or is this somehow going to prevent custom kernels?

---

### Post by del_diablo on 2011-09-21
The problem is that Windows 8 will require a UEFI "bootlocker" to be present, and this bootlocker will make it impossible to install new OS, or install Linux.
Most likely all that will happen is that some of the worst manifactureres will lock some of their computers, but most will never implent it.

---

### Post by sffvba[e0rt on 2011-09-21
Threads merged :) (times two)


404

---

### Post by tjeremiah on 2011-09-21
if true, someone will figure out a way around this.

---

### Post by Beacon11 on 2011-09-21
> **3Miro said:**
> Wait, I don't understand this. Linux already works with EFI and there is nothing in the EFI that blocks Linux.

"must support secure booting" is different from "requires secure booting" or "doesn't support any other booting". From what I understand this is just support for a Windows feature.

Furthermore, what is preventing Linux from being digitally signed? From what I understand the Ubuntu repositories are digitally signed. Is this something that smaller distos would not be able to handle or is this somehow going to prevent custom kernels?

Read this article: [http://mjg59.dreamwidth.org/5552.html](http://mjg59.dreamwidth.org/5552.html) . To quote:

> Firstly, we'd need a non-GPL bootloader. Grub 2 is released under the GPLv3, which explicitly requires that we provide the signing keys. Grub is under GPLv2 which lacks the explicit requirement for keys, but it could be argued that the requirement for the scripts used to control compilation includes that. It's a grey area, and exploiting it would be a pretty good show of bad faith. Secondly, in the near future the design of the kernel will mean that the kernel itself is part of the bootloader. This means that kernels will also have to be signed. Making it impossible for users or developers to build their own kernels is not practical. Finally, if we self-sign, it's still necessary to get our keys included by ever OEM.

---

### Post by SirDrexl on 2011-09-21
> **SuperFreak said:**
> So building a custom machine with UEFFI won't work. Not liking that much.

No, you will be able to buy motherboards that don't have the secure boot  set up for Windows 8.  This is only for complete computers with Win8  preinstalled.  And, I assume you would be able to reinstall Win8 on those systems, since the key would still match.

Heck, even if I predominantly used Windows, I wouldn't buy a system like this because I would be unable to do things that require a boot USB flash/CD like a SSD secure erase, or full partition management (Gparted).

---

### Post by 3Miro on 2011-09-21
> **Beacon11 said:**
> Read this article: [http://mjg59.dreamwidth.org/5552.html](http://mjg59.dreamwidth.org/5552.html) . To quote:

Thanks, this clarifies things.

---

### Post by madmax75 on 2011-09-21
This is just... *evil*.

"We are losing a bit of the market share, so let's just go and shove our products down people's throats by force!" This is the bottom line. They don't even care anymore what kind of publicity they will get. This is just arrogance, nothing more. "We make the rules, and you have to obey them either you like it or not, because we say so!"

Sorry, I have to stop writing right here. I'm just too angry. Thanks Microsoft for ruining my day yet once more!

---

### Post by Copper Bezel on 2011-09-21
> That's okay-- just buy from people like System76, or heck-- a Mac. Keep in mind that Windows 8 is being developed with mobile devices in mind. While I don't trust Microsoft in the least, I think this speaks more to locking down tablets and phones than desktops and laptops.
It speaks to the locked-down style of phones and tablets finally making its way onto the desktop.

I don't like System76's case styles - or prices. I have to admit that Apple and Asus are the most attractive hardware brands to me and the most likely not to present this problem. Still, costs become a serious consideration, and even if it *were* only my choices being limited, I'd be a bit miffed about it. 

I'm more angry about the principle of the thing than concerned about the practical repercussions for myself. This top-down model that everyone seems so willing to accept is just *wrong*.

---

### Post by madmax75 on 2011-09-21
> **Copper Bezel said:**
> It speaks to the locked-down style of phones and tablets finally making its way onto the desktop.

Yeah, it's yet another "one model will fit all" thing. But that is not the way reality actually works. People are different, with different priorities and different needs. This includes also their choice of software and the way they use it.

Like, what happened to the idea of individual customization? These sort of top-down locking-down schemes are the equivalent of forcing everybody to use the same kind of jumpsuit, regardless of size differences and personal preferences. This is taking away choice from people, because "Big Brother knows what is best for everybody". It's the age-old story repeating itself *ad nauseam*. Why do we as people allow this?

---

### Post by del_diablo on 2011-09-21
> **Beacon11 said:**
> Read this article: [http://mjg59.dreamwidth.org/5552.html](http://mjg59.dreamwidth.org/5552.html) . To quote:

Or C: We rip every key, move the GRUB2 projects to somewhere in Europa, and include all the keys, directly ignoring the problems.
I don't see the immoral or non-legal part for this.

---

### Post by Beacon11 on 2011-09-21
> **Copper Bezel said:**
> I'm more angry about the principle of the thing than concerned about the practical repercussions for myself. This top-down model that everyone seems so willing to accept is just *wrong*.

Amen. I couldn't say it better myself.

While this does indeed limit my choices, the choices I've always made in the past have been a custom-built desktop (avoids this issue as long as Asus doesn't build the lock into their motherboards... which would make *no* sense) an Asus netbook, and a Mac laptop. It's just so... typical, which is depressing.

---

### Post by Erik1984 on 2011-09-21
> **Copper Bezel said:**
> It speaks to the locked-down style of phones and tablets finally making its way onto the desktop.

I don't like System76's case styles - or prices. I have to admit that Apple and Asus are the most attractive hardware brands to me and the most likely not to present this problem. Still, costs become a serious consideration, and even if it *were* only my choices being limited, I'd be a bit miffed about it. 

I'm more angry about the principle of the thing than concerned about the practical repercussions for myself. This top-down model that everyone seems so willing to accept is just *wrong*.

Hear Hear!

---

### Post by el_koraco on 2011-09-21
Please, people are installing Linux on dead badgers. There's no secure boot in the world that's gonna stop that. The UEFI move could be beneficial in that it will force the Grub development to rethink mangling the MBR, or distros to rethink the bootloader. EXTLinux boots from the MBR code already, I don't think porting it to GPT would be much harder, so it's not like an unachievable dream.

---

### Post by Lars Noodén on 2011-09-21
> **copper bezel said:**
> i'm more angry about the principle of the thing than concerned about the practical repercussions for myself. This top-down model that everyone seems so willing to accept is just *wrong*.

+1

---

### Post by BlacqWolf on 2011-09-21
> **marin123 said:**
> I guess it will be impossible to reinstall Windows in the future. And in my experience it should be once a year, to get rid of junk, missing files etc, and that's the year of Linux :)

You won't have to reinstall Windows on a computer running Windows 8. In Control Panel, there are two options, one for completely wiping the system and reverting it to factory state, and one for removing everything except personal files.

But, back to the case on Microsoft locking an EFI to Windows 8... I really hate it when people do stuff like that. I mean, it removes the idea that a computer can be whatever you want it to be. I want a computer that works well with whatever I want, not this dictatorship environment that says "do it our way with our products or don't do it at all!"

---

### Post by SuperFreak on 2011-09-21
I am still not completely clear on this. Will it be possible to build a computer with UEFFI motherboard and install a dual boot Win 8 and Linux? Or will it only be possible to install either Linux or Win 8 not both?

---

### Post by Linuxratty on 2011-09-21
> **madmax75 said:**
> This is just... *evil*.

 "We make the rules, and you have to obey them either you like it or not, because we say so!"



 Yup,it is indeed. 
I've always said they see the world is their sandbox and they don't want anyone else in it...The megalomaniac, unimaginable greed,arrogance and control freakish nature of this company astounds me. I've always thought Monsanto and Apple were the most evil..Looks like Microsoft has outdone Apple.

---

### Post by Primefalcon on 2011-09-21
> **SuperFreak said:**
> I am still not completely clear on this. Will it be possible to build a computer with UEFFI motherboard and install a dual boot Win 8 and Linux? Or will it only be possible to install either Linux or Win 8 not both?
Windows will be signed with MS's private key so no problem there.... Linux I cant see MS signing so either jailbreak it or forget about linux lol

---

### Post by disabledaccount on 2011-09-21
Remember Processor Serial Number? -> Failure. Remember DRM? -> very expensive Failure (piracy still happily exist, "good" customers are paying the price). Some of You maybe know about Dell theft protection system -> Failure - due to leak of Dell service tool set.
UEFI: At least 2 obvious ways are possible:
- keygen (not legal I suppose), but open src GRUB can offer interface to enter "legal", "proprietary" key, f.e. during bootable pendrive creation.
- BIOS modification/update - quite easy task these days, especially if we take into account that exactly the same motherboards are released in several versions.
- BIOS override - not at boot time (loading bootloader), but just after booting it should be possible.

Instead of sling mud at MS, I must say that they have just put another argument in my hands that I can use to show peoples how they are traeted by this self-crowned, arrogant monopolist.

And finally: did I mention before that vendors are paying for the right to use Windows Logo? (I must find that post) It was presumption at that time - now I have the proof.

---

### Post by Primefalcon on 2011-09-21
being able to be cracked is irrelevant, this will stop 90% of users trying Linux in the first place, which IS A BAD THING!

---

### Post by BlacqWolf on 2011-09-21
> **SuperFreak said:**
> I am still not completely clear on this. Will it be possible to build a computer with UEFFI motherboard and install a dual boot Win 8 and Linux? Or will it only be possible to install either Linux or Win 8 not both?

Well, unless the EFI for some reason is set to only recognize Windows 8, it would be impossible for Windows 8 to interfere with a Linux installation if Windows 8 isn't installed. If it were a thing with Windows 8 itself, then of course I'm sure someone would come up with a workaround with it. 

I think it will be a thing with OEMs using an EFI that locks the system to only being able to boot Windows 8, at which maybe installing Ubuntu or another distro alongside Windows using something like Wubi may still work, or you may be able to get a hacked EFI and flash it so that it allows any OS.

---

### Post by Mark Phelps on 2011-09-21
This is clearly geared towards OEMs further "locking down" their products to prevent customers from "tampering" with them (e.g., installing their own OSs).

Guess they figured the current policy of unnecessarily loading a hard drive with the maximum of 4 Primary partions would not work with UEFI -- so they had to come up with some other way to prevent "dual-booting" when the OTHER OS was not Windows.

---

### Post by disabledaccount on 2011-09-21
> **Primefalcon said:**
> being able to be cracked is irrelevant, this will stop 90% of users trying Linux in the first place, which IS A BAD THING!The question is if reading of existing windows installation key and the transferring it to WUBI illegal? (It's legal to read and reuse existing CD-KEY). Or another one: If I'm able to refuse agreement during installation of Win8, then should I get alternate key from MB manufacturer?
I suppose not, until MS will lose another Anti-trust case...

---

### Post by KiwiNZ on 2011-09-21
Until Windows 8 is closer to release, it's only pre beta now, I would not be too concerned. Remember all the "new" features that were dropped from Vista and Win 7 when they went Gold?

However,donning an OEM hat I can see why Vendors would back this feature, why?

More tartgeted development of their products.
Less variation of component models needed.
Streamlined driver development.
Reduced post sales support cost.

For the majority of MSFT and the OEM's customers there would be no downside. They would have a better  ownership experience, a machine the "boots" faster ( I wish I see he all the time) after all a boot time improved from 30 seconds to 20 seconds seems to be vitally important.

The increased security will be seen as a plus  for a lot of consumers, however in the end the vast majority of the client base will not notice it or  even care about it.

If the Linux sector is truely innovative it will innovate to compete.

---

### Post by Copper Bezel on 2011-09-21
[QUOTE=Primefalcon]being able to be cracked is irrelevant, this will stop 90% of users trying Linux in the first place, which IS A BAD THING![/QUOTE]
Exactly. If the implications are accurate, then while it doesn't affect enterprise desktop and server applications, it makes home use of Linux distinctly non-kosher. If it doesn't become a TOS violation, it'll certainly feel like one in practice.

Edit:

[QUOTE=KiwiNZ]If the Linux sector is truely innovative it will innovate to compete.[/QUOTE]
Even if Linux had OEM installs competitive with MS, this would still mean buying the OS with the hardware, etc, which reduces your options. As it is, it sounds like some seriously calcified vertical integration.

And is there *any* real security advantage to this?

---

### Post by ewz on 2011-09-21
Didn't something similar to this happen back around 2003/4 I think it was to do with a Windows only CPU, the computer would sell cheaper than computers with standard CPU's in them, sorry I can't remember anymore about it I was using Redhat 9 at the time.

Also I wonder "from the conspiracy files" In which when we talk about MS they often come true, will this be more leverage to get Linux based distos to sign up to there Patent deals

...hmm, lured over to the dark side...

---

### Post by SuperFreak on 2011-09-21
a little more info...

[http://www.readwriteweb.com/enterprise/2011/09/windows-8-spells-trouble-for-l.php](http://www.readwriteweb.com/enterprise/2011/09/windows-8-spells-trouble-for-l.php)

---

### Post by disabledaccount on 2011-09-21
> **KiwiNZ said:**
> Until Windows 8 is closer to release, it's only pre beta now, I would not be too concerned. Remember all the "new" features that were dropped from Vista and Win 7 when they went Gold?

However,donning an OEM hat I can see why Vendors would back this feature, why?

More tartgeted development of their products.
Less variation of component models needed.
Streamlined driver development.
Reduced post sales support cost.
(...)
The increased security will be seen as a plus  for a lot of consumers, however in the end the vast majority of the client base will not notice it or  even care about it.

If the Linux sector is truely innovative it will innovate to compete.
It's better to see potential threats before they became reality...
Please explain me how driver development can be affected with something else than change of HW specification or driver model for particular OS?
Security?
Increased security? ...as plus for a lot of cusomers? You must be kidding - virus developers will be the first who will use cracked keys :LOL: take a look at WHQL signing...

I'm not affraid of Linux software sector, I'm affraid that I will need more tweaking to run my linux on newest HW...


> **Copper Bezel said:**
> Even if Linux had OEM installs competitive with MS, this would still  mean buying the OS with the hardware...oh, because they don't really care if their os is perfect, or even if You are using it - the most important part is **buying** the hardware with pre-paid Winows Logo on it.


> **ewz said:**
> Didn't something similar to this happen back around  2003/4 I think it was to do with a Windows only CPU ...I suppose You're talking about Processor Serial Number, but it was started with Pentium3 :)

---

### Post by Copper Bezel on 2011-09-21
[QUOTE=tomazzi]...oh, because they don't really care if their os is perfect, or even if You are using it - the most important part is **buying** the hardware with pre-paid Winows Logo on it.[/QUOTE]
To clarify, I just meant the obvious - that, again, if this goes the way it's being presented, the hardware and OS are a bundle you can't break up, so you don't get to choose them independently. That's anti-competitive.

---

### Post by srs5694 on 2011-09-21
> **el_koraco said:**
> The UEFI move could be beneficial in that it will force the Grub development to rethink mangling the MBR, or distros to rethink the bootloader. EXTLinux boots from the MBR code already, I don't think porting it to GPT would be much harder, so it's not like an unachievable dream.

UEFI boots in a very different way than does BIOS. In particular, no code in the MBR is involved (signing or no signing), nor is there boot code in partition boot records (PBRs). Instead, boot loaders exist as regular files on the EFI System Partition (ESP). This is true of all current EFI boot loaders of which I'm aware, GRUB included, and it's likely to remain true in the future.

There's already a version of Syslinux that installs to the MBR of a GPT disk; however, this version, like other versions of Syslinux I know about, is for BIOS-based systems. The "secure boot" feature is part of UEFI, so it affects only UEFI-based computers. (I have no idea if it interacts with booting legacy BIOS OSes in some way or if it might disable that feature.)

[quote=SuperFreak]I am still not completely clear on this. Will it be possible to build a  computer with UEFFI motherboard and install a dual boot Win 8 and Linux?  Or will it only be possible to install either Linux or Win 8 not both?[/quote]

You'll almost certainly be able to create a dual-boot Windows 8/Linux computer. Certainly you can do that today, using the Developer Preview version of Windows 8. AFAIK, the final version of Windows 8 will boot on a computer that doesn't use secure boot -- certainly today it pretty much has to, since few or no shipping computers implement this technology. This means that if Windows 8 were to *require* the secure boot feature, they'd be locking themselves out of the existing installed base of computers, which I don't think Microsoft would be willing to do.

From [an article on the topic:](http://mjg59.dreamwidth.org/5552.html)

> Microsoft [requires]("http://video.ch9.ms/build/2011/slides/HW-457T_van_der_Hoeven.pptx") that machines conforming to the Windows 8 logo program and running a client version of Windows 8 ship with secure boot enabled.

This wording suggests that the secure boot feature can be disabled. It also suggests that server computers are exempt from the requirement, and of course Microsoft can't coerce vendors who don't care about the Windows 8 logo program into enabling this feature.

Thus, there are likely to be several ways around this limitation, although of course I can make no guarantees:


[list]
[*]It may be possible to disable the secure boot feature in the firmware, or perhaps by flipping a switch or setting a jumper.
[*]There are likely to be technical workarounds, ranging from new (signed) boot loaders to custom firmware to cracks against the keys that are in common use.
[*]As just noted, servers, plain motherboards, computers with no OS installed, and perhaps other computer categories don't fall under Microsoft's ruling.
[/list]


My suspicion -- and it's only that -- is that most vendors of desktop and laptop computers will provide some sort of user-accessible "off switch" for the secure boot functionality. The reason is that not providing a way to disable this feature will be very limiting to users. Without such an off switch, users won't be able to install old or exotic OSes (including, but by no means limited to, Linux) and they won't be able to boot most repair and recovery tools. These limitations will translate into additional support calls and returns. Although Microsoft might not care about these problems, the hardware manufacturers will, and they won't want to incur the added expenses that such problems will create. Thus, unless Microsoft exerts a lot of pressure on them to do otherwise, they'll provide off switches on most of their products.

An exception might be products that are sold as subscription-based appliances (cell phones, eBook readers, etc.). With those, the vendor has an interest in maintaining ongoing control of the product, and such control is of course easier if they can control what software is installed on it. This contrasts with PCs, for which the vendor has little or no ongoing revenue stream or interest in the product once the customer has bought it.

Of course, we're all going on very little information. My speculation that there'll be an off switch on most PCs certainly qualifies as that, just as do the more conspiracy-theory posts. Unfortunately, we won't know more until Windows 8 PCs begin shipping, presumably sometime in 2012. If you're concerned, you could try contacting your favorite vendors today and ask how they intend to implement this. If you do, please be calm and respectful; I can't see them reacting well to wild accusations. Just make it plain that you want to run Linux on computers that you plan to buy in retail stores in a year or two, and you want them to consider your needs, and those like you, when implementing the "secure boot" feature.

---

### Post by disabledaccount on 2011-09-21
> **srs5694 said:**
> If you're concerned, you could try contacting your favorite vendors today and ask how they intend to implement this. If you do, please be calm and respectful; I can't see them reacting well to wild accusations. Just make it plain that you want to run Linux on computers that you plan to buy in retail stores in a year or two, and you want them to consider your needs, and those like you, when implementing the "secure boot" feature.Although I agree with You, the above is rather unlikely to happen - vendors are not responding to users questions in general (or in 99.9999% of cases.)

---

### Post by Atamisk on 2011-09-21
The above post regarding contacting vendors is a great idea. We can't change how Microsoft conducts business, but we CAN influence the actions of hardware manufacturers. I'm game. 

Failing that, i'm fully prepared to go to war with Microsoft in any way the *nix/BSD community can, because this is unacceptable.

> Although I agree with You, the above is rather unlikely to happen -  vendors are not responding to users questions in general (or in 99.9999%  of cases.)This is true of individual concerns, but if well over a million of your customers voice a concern, you listen.

However, if current developers fail to listen, an entire new hardware market literally appears out of nowhere, and companies like System76 will thrive. I'd bet this is the best news Sys76 has had in a long time :P

---

### Post by Dr. C on 2011-09-21
This is from the official UEFI site. [http://www.uefi.org/learning_center/]("http://www.uefi.org/learning_center/") The following: [http://www.uefi.org/learning_center/UPFS11_P2_SecureBoot_Insyde.pdf]("http://www.uefi.org/learning_center/UPFS11_P2_SecureBoot_Insyde.pdf") deals with secure boot. In particular > OEM-ACTION
Policy must lock-out un-trusted
code including all legacy 16-bit code
• But User Experience is key to acceptance:
– We ship locked-down secure systems but how much freedom should I give users to reconfigure?
– How does my UI design minimize confusion from users used to “less secure” systems?
 from Implementing a Secure Boot Path with UEFI 2.3.1, UEFI Summer Plugfest – July 6-9, 2011 Presented by Jeff Bobzin, Insyde Software page 16. 

The implication is clear The OEM is to lock out all "untrusted" code and not permit the end user to override this. This is nothing more that implementing part of the Apple iPad model or SONY PS3 model on the desktop. We already have the the requirement for signed drivers in 64 bit Windows. The only thing left is the requirement that all applications be signed and the lockdown is complete.

---

### Post by Atamisk on 2011-09-21
> **Dr. C said:**
> 
The implication is clear The OEM is to lock out all "untrusted" code and not permit the end user to override this. This is nothing more that implementing part of the Apple iPad model or SONY PS3 model on the desktop. We already have the the requirement for signed drivers in 64 bit Windows. The only thing left is the requirement that all applications be signed and the lockdown is complete.

The only issue is that PS3 and the iPad (yes, really) are designed to be entertainment devices. This so-called lockdown is poised to make Microsoft the One True content provider for enterprise workstations. Not only does this stifle competition, it actively denies the userbase any recourse in the same thread as the illegality of cracking a PS3. 

So, now my question: How can the *nix community organize against this building threat? Is the best option lobbying hardware manufacturers for an opt-out, or do more active measures (litigation, etc.) need to be considered? If it came to it, WHO would push this?

---

### Post by walt.smith1960 on 2011-09-21
> **srs5694 said:**
> 
<snip>
An exception might be products that are sold as subscription-based appliances (cell phones, eBook readers, etc.). With those, the vendor has an interest in maintaining ongoing control of the product, and such control is of course easier if they can control what software is installed on it.[B] This contrasts with PCs, for which the vendor has little or no ongoing revenue stream or interest in the product once the customer has bought it.
[/B] 
Of course, we're all going on very little information. My speculation that there'll be an off switch on most PCs certainly qualifies as that, just as do the more conspiracy-theory posts. Unfortunately, we won't know more until Windows 8 PCs begin shipping, presumably sometime in 2012. If you're concerned, you could try contacting your favorite vendors today and ask how they intend to implement this. If you do, please be calm and respectful; I can't see them reacting well to wild accusations. Just make it plain that you want to run Linux on computers that you plan to buy in retail stores in a year or two, and you want them to consider your needs, and those like you, when implementing the "secure boot" feature.

It's seems too early to panic about this but something to keep an eye on. One trick I could see Microsoft employing is a dual price for Windows licenses.  "Okay, Mr. Dell,  Here's what we can do.  If you make it difficult or impossible to install any other OSs on your notebooks, your Windows licenses will cost $15 each.  If you don't want to exclude other OSs, your Windows licenses will cost you $49 each and our software support people might be slower to return your company's calls.  Do what you think is best".  That seems perfectly in character and I'm not sure it would be illegal.

---

### Post by SirDrexl on 2011-09-21
Is there any chance this could affect OEM system builder copies of Windows?  Could these be locked to secure boot systems?

---

### Post by disabledaccount on 2011-09-21
> **walt.smith1960 said:**
> It's seems too early to panic about this  but something to keep an eye on. One trick I could see Microsoft  employing is a dual price for Windows licenses.  "Okay, Mr. Dell,   Here's what we can do.  If you make it difficult or impossible to  install any other OSs on your notebooks, your Windows licenses will cost  $15 each.  If you don't want to exclude other OSs, your Windows  licenses will cost you $49 each and our software support people might be  slower to return your company's calls.  Do what you think is best".   That seems perfectly in character and I'm not sure it would be  illegal.
Oh, for sure it's only one small step that takes us closer and closer to hegemony of world-wide companies. However, the windows logo phenomenon works in a bit different way: "*Mr Dell, of course You don't have to pay us, but how do You explain Your customers the lack of this great sticker? Average user would notice that every other HW manufacturer has our Windows 8 Logo - so it's compatible...* "
But wait - there is an option: HW manufacturers should join their forces and say: f.u. MS, we are HW masters - if you want to get certification for your OS then pay for it !!!
This can, but won't happen due to human nature (we are able to unite mostly when it's too late).

---

### Post by Atamisk on 2011-09-21
The more I read, the more angry I get. What can be DONE to try and CHANGE this?

---

### Post by Docaltmed on 2011-09-21
This is a bit off-topic, but it speaks to the heart of this thread.

Back in the mid-80s, I was Senior Editor at a newspaper called "PC Week." Most of you will say lagjhljljlafjglal LULZ?, but a  few who are a little bit older will remember that it was a stone-cold powerhouse in its time. We were producing 220 tabloid-size pages *weekly*. in short, if you were a reporter or editor for PC Week back than, as far as the industry went, you were the ****. 

I was out at COMDEX -- anybody remember that? -- and while I was there, interviewed Bill Gates over lunch, who proceded to leave me with the check.

If any of you have any experience in PR, you know that stiffing an editor is a major-league faux pas. It's about the stupidest thing you can do.

To me, that act completely speaks to the culture Bill Gates created at MS and that he left behind. No hard feelings, the publisher picked up the miniscule tab, but holy crap. This is how MS thinks. Let's take every freakin' little dollar that we can.

---

### Post by Atamisk on 2011-09-21
^^ That's sad, but funny. 

From what the talking heads are saying, there's little doubt that some manufacturers will have suitable firmware to switch off the secure-boot. I think that dual-loyalty manufacturers like Dell will have this option. 

It's still terrible though.

---

### Post by johnnybgoode83 on 2011-09-21
I honestly can't see this being allowed, not here in the EU at any rate.  MS have already been told that they must allow a choice between web browsers on new computers.  Just imagine if the appropriate authorities caught wind of this.  
 
It is sad though that the industry today does not embrace the ideals with which computers and networking were first developed.

---

### Post by Rasa1111 on 2011-09-21
Surprise!
more excellency from microsoft. 
wouldn't surprise me a bit. 
but thanks to ubuntu , i don't need ms for anything. 
so, yea, whatever.

---

### Post by srs5694 on 2011-09-21
> **Dr. C said:**
> This is from the official UEFI site. [http://www.uefi.org/learning_center/](http://www.uefi.org/learning_center/) The following: [http://www.uefi.org/learning_center/UPFS11_P2_SecureBoot_Insyde.pdf](http://www.uefi.org/learning_center/UPFS11_P2_SecureBoot_Insyde.pdf) deals with secure boot. In particular  from Implementing a Secure Boot Path with UEFI 2.3.1, UEFI Summer Plugfest – July 6-9, 2011 Presented by Jeff Bobzin, Insyde Software page 16. 
> OEM-ACTION
Policy must lock-out un-trusted
code including all legacy 16-bit code
• But User Experience is key to acceptance:
– We ship locked-down secure systems but how much freedom should I give users to reconfigure?
– How does my UI design minimize confusion from users used to “less secure” systems? 			 		

The implication is clear The OEM is to lock out all "untrusted" code and not permit the end user to override this.

Point #1 (locking out untrusted code) is certainly clear in the quote, but point #2 (not permitting an end-user override) is *not* clear in what you've quoted. In fact, the quote leaves the question of whether to permit such a user override very explicitly as a question. It sounds like this was a page from a PowerPoint presentation, so presumably the speaker actually said something on the topic, but we don't know what was said. I would argue that the context ("User Experience is key to acceptance") implies that an inability to change the default lock-out mode is likely to be a negative, and could therefore hinder acceptance. Maybe the marketing types are hard at work trying to figure out how to get people to accept this -- but maybe the software engineers are hard at work trying to figure out how best to implement a way for users to switch off the feature while minimizing the risk of its being accidentally disabled.

Keep in mind that manufacturers desperately need consumer acceptance of their products. I expect that a return wipes out not only the profit margin for the returned computer, but for several more. Thus, a few consumers who are dissatisfied enough with a computer to return it to the store because it won't run Linux could have a major effect on the product's viability. Unlike other practices, like omitting a Windows installation DVD or putting four primary partitions on a computer, a totally locked-down computer *will* cause returns if a customer expected to be able to install another OS on it. This is why I'm skeptical that this will affect more than a few mainstream PCs, and also why making the unacceptability of a totally locked-down machine known now is important.

---

### Post by whatthefunk on 2011-09-21
One question:
Motherboards come with BIOS installed.  If Microsoft goes the UEFI way, wouldnt motherboards also have to come with this installed?  Wouldnt it affect people who build their own pcs as well?

---

### Post by Lucradia on 2011-09-21
> **Atamisk said:**
> The more I read, the more angry I get. What can be DONE to try and CHANGE this?

Contact senators, governors, etc: [http://www.senate.gov/general/contact_information/senators_cfm.cfm](http://www.senate.gov/general/contact_information/senators_cfm.cfm)

Tell them that it infringes on constitutional rights. Freedom of Choice / Speech.

---

### Post by SirDrexl on 2011-09-22
> **whatthefunk said:**
> One question:
Motherboards come with BIOS installed.  If Microsoft goes the UEFI way, wouldnt motherboards also have to come with this installed?  Wouldnt it affect people who build their own pcs as well?

My understanding is that this only affects computers with Windows 8 preinstalled.  Of course they are going to sell retail copies of Win8 that can be installed on current systems and don't require UEFI.  Motherboards you buy to build systems won't have the secure boot enabled.

---

### Post by drawkcab on 2011-09-22
There are vendors that are selling notebooks sans OS and I expect that, if this becomes an issue, there will either be more vendors appearing or the existing vendors will expand their range to cater to the Linux crowd.

This bodes well for outfits like System 76.  Hell, it might be the perfect time to start a similar business and get into the game.

Nevertheless, Win7 will be the last MS operating system I will ever use.  Enough is enough.

---

### Post by Lars Noodén on 2011-09-22
> **SirDrexl said:**
> No, you will be able to buy motherboards that don't have the secure boot  set up for Windows 8.  This is only for complete computers with Win8  preinstalled.  And, I assume you would be able to reinstall Win8 on those systems, since the key would still match.

Heck, even if I predominantly used Windows, I wouldn't buy a system like this because I would be unable to do things that require a boot USB flash/CD like a SSD secure erase, or full partition management (Gparted).

And how many computers are sold nowadays without the "latest" version of Windows?  If that does not change then the locked down nature of the new machines will be a problem for everybody.

---

### Post by Copper Bezel on 2011-09-22
He's not discounting that. He's saying that those two cases (total reinstall and building your own machine) wouldn't be affected. He says even in the bit you quoted that it's still a bad thing, even for Windows users.

---

### Post by whatthefunk on 2011-09-22
Its my understanding that in order for hardware makers to get the coveted Windows 8 logo on their products they have to comply with Microsoft rules.  For motherboards, this would mean having UEFI.

---

### Post by 8_Bit on 2011-09-22
Can someone clarify this - does this affect LiveCDs, or only OS'es installed already on the hard drive?

Because if it affects both, then that means all the people who use Linux liveCDs to rescue their Windows partitions are going to be very irate. Even the AVG Antivirus rescue disk is Linux-based.

---

### Post by sanderd17 on 2011-09-22
> **IWantFroyo said:**
> Oh gosh. There go all my fancy laptop dreams.

I build my own desktops, but I don't know of any way to build my own laptop.

Anyone know any resources? Or is it just not possible?

Also, doesn't this sort of kill the point of those "Happy Birthday Linux" videos MS made?


I have seen several small computer shops that have their own clevo hardware computers. So they buy the case and the motherboard at Clevo and build their own computer around it.

I don't think Clevo will ship you a case for 1 laptop, but I guess they deal in not-so-big quantities.

The computer manufacturers I know are
[qForce]("http://www.q-force.be/notebooks.htm")
[Ahtec]("http://www.ahtec.nl/product/main/index.jsp?label=")
[Pointer Systems]("http://www.pointersystems.be/index.php?tab=producten&page=notebooks&PHPSESSID=f9a3d36bddda68f4896e008859b837e0")
and the shop CC@PS ( a little shop, one village away from where I live) also has a house-branded laptop.

Ahtec and Pointer Systems both ship no-os laptops (but geographically limited to Belgium and a few other European countries). I've bought an Ahtec in February.

Here an old list of Clevo resellers: [http://forum.notebookreview.com/sager-clevo/91510-clevo-guide-v2-0-faq-reseller-info.html#nl](http://forum.notebookreview.com/sager-clevo/91510-clevo-guide-v2-0-faq-reseller-info.html#nl)

The laptop models aren't up to date anymore, but I guess that the biggest part of the resellers will still exist, and some might just ship you a barebones system if you ask for it. Most of those resellers are small companies anyway.

---

### Post by kurt18947 on 2011-09-22
I will lay bare my layman's ignorance here.  My understanding is that UEFI uses a boot partition in lieu of firmware in a BIOS chip.  There must be some sort of hardware/software interface but what's to prevent someone from modifying or replacing the EFI/UEFI partition? That seems easier than if the "trusted" whatever is in firmware, or is the "trusted" part in hardware/firmware?  This seems more of annoyance than problem with desktops -I'd be surprised if MoBo manufacturers don't offer a way around this - but it could be a pain for portables where the MoBo is proprietary.

---

### Post by srs5694 on 2011-09-22
> **kurt18947 said:**
> I will lay bare my layman's ignorance here.  My understanding is that UEFI uses a boot partition in lieu of firmware in a BIOS chip.

Not quite. In UEFI, there is a special partition on the disk (the EFI System Partition, or ESP) that holds EFI boot loaders, drivers, and applications. This is used *in addition to* the firmware in the chip on the motherboard, not instead of it. In other words, UEFI replaces BIOS, and the ESP replaces (and greatly expands upon) the boot code that the BIOS places in the hard disk's MBR.

> There must be some sort of hardware/software interface but what's to prevent someone from modifying or replacing the EFI/UEFI partition?

Nothing, but it will do nobody any good. If you install an untrusted boot loader on the ESP, it simply won't boot if the "trusted boot" feature is enabled.

> I'd be surprised if MoBo manufacturers don't offer a way around this - but it could be a pain for portables where the MoBo is proprietary.

As I've written before, there *will* be ways around it for servers and custom-built PCs; the Linux (and BSD and ReactOS and legacy OS and so on) market is big enough to support demand for such features. My suspicion is that an "off switch" will exist in most commodity PCs, too, but I'm far from certain of that. Until hardware manufacturers speak out or begin shipping Windows 8 systems, we won't know for sure.

---

### Post by SirDrexl on 2011-09-22
> **whatthefunk said:**
> Its my understanding that in order for hardware makers to get the coveted Windows 8 logo on their products they have to comply with Microsoft rules.  For motherboards, this would mean having UEFI.

Motherboards typically don't have the Windows logo, do they?  I just went through the manuals for my last two, and I don't see it anywhere.  The only place I see Windows at all is where they show screenshots in the section on setting up the OS, but I don't think that qualifies as "bearing the logo."

---

### Post by SuperFreak on 2011-09-22
SUA Deprecated In Windows 8?
[http://tech.slashdot.org/story/11/09/22/1354258/SUA-Deprecated-In-Windows-8](http://tech.slashdot.org/story/11/09/22/1354258/SUA-Deprecated-In-Windows-8)

perhaps not the best example of MS plans as apparently this software is very outdated

---

### Post by Beacon11 on 2011-09-22
> **SirDrexl said:**
> Motherboards typically don't have the Windows logo, do they?  I just went through the manuals for my last two, and I don't see it anywhere.  The only place I see Windows at all is where they show screenshots in the section on setting up the OS, but I don't think that qualifies as "bearing the logo."

I believe you're correct-- the only people who get Windows stickers are computer vendors. Of course, they use motherboards, so the motherboards they get will need to have the locked bootloader. Does that mean that the majority of motherboard manufacturers will begin incorporating this? I hope not, or if they do, they allow one to turn it off.

---

### Post by whatthefunk on 2011-09-22
A lot of hardware has some sort of "Ready for Windows Vista/7/8" type windows logo on the box.  Im just wondering if in order to get this logo on their packaging they have to meet Microsofts standards and if thats true then in order to get the Windows 8 logo on their packaging motherboard manufactures will have to come with UEFI.

---

### Post by Lucradia on 2011-09-22
> **SuperFreak said:**
> SUA Deprecated In Windows 8?
[http://tech.slashdot.org/story/11/09/22/1354258/SUA-Deprecated-In-Windows-8](http://tech.slashdot.org/story/11/09/22/1354258/SUA-Deprecated-In-Windows-8)

perhaps not the best example of MS plans as apparently this software is very outdated

Guess Microsoft wants to be as far away from UNIX as possible? Guess the Command Line is next to go from inside windows. Maybe make you boot into command-line by pressing / holding down a button rather than allowing it through non-safe-mode windows.

---

### Post by SirDrexl on 2011-09-22
> **Beacon11 said:**
> I believe you're correct-- the only people who get Windows stickers are computer vendors. Of course, they use motherboards, so the motherboards they get will need to have the locked bootloader. Does that mean that the majority of motherboard manufacturers will begin incorporating this? I hope not, or if they do, they allow one to turn it off.

I would assume that locking the bootloader would be done by the OEMs, just like the custom BIOS that allows Windows to be activated offline in current systems.  This secure boot might even be the new method they use to activate offline, stopping people from being able to modify the BIOS to get around activation.

If that's the case, and maybe I don't understand it correctly, but if they enable the secure boot in a standalone board with the Windows 8 key, won't that just make it easy to install a bootleg copy of the OS?

Also, the motherboard companies won't want to restrict their boards to Windows 8 only and shut out those that want to install Windows 7 or earlier (or Linux, of course).

---

### Post by Dragonbite on 2011-09-22
Might have to end up getting Ubuntu from System76/ZaReason since they can either add the license, or disable that features since they don't give a rats ### about the Windows 8 logo! :guitar:

---

### Post by zekopeko on 2011-09-22
> **Lucradia said:**
> Contact senators, governors, etc: [http://www.senate.gov/general/contact_information/senators_cfm.cfm](http://www.senate.gov/general/contact_information/senators_cfm.cfm)

Tell them that it infringes on constitutional rights. Freedom of Choice / Speech.

This does not appear to infringe on freedom of speech in any way nor does freedom of choice exist in the US Constitution.

---

### Post by Lucradia on 2011-09-22
> **zekopeko said:**
> nor does freedom of choice exist in the US Constitution.

Well that's just sad.

---

### Post by zekopeko on 2011-09-22
> **Lucradia said:**
> Guess Microsoft wants to be as far away from UNIX as possible? Guess the Command Line is next to go from inside windows. Maybe make you boot into command-line by pressing / holding down a button rather than allowing it through non-safe-mode windows.

Instead of guessing (and being wrong) you could simply read one of the articles detailing Microsoft's plans for Windows Server 8. By doing so you would see they are heavily moving toward using PowerShell command line.

It is also unclear how UNIX is relevant to Microsoft. I know they kinda support POSIX but that is about it.

---

### Post by zekopeko on 2011-09-22
> **Lucradia said:**
> Well that's just sad.

You basing your opinions on wishful thinking is sad. It is pretty funny seeing how many people have no idea what the US Constitution contains.

---

### Post by Dr. C on 2011-09-22
There is also a very disturbing comment in > There may be no choice in some circumstances; the Windows 8 mobile computers with ARM SoCs that have been announced will only ever be available as Class 3 devices. On these devices, however, Microsoft plans to increase platform security by allowing only apps from the app store that have been checked and signed to be installed on the Metro user interface.from [Community fears Windows 8 Secure Boot will block Linux]("http://www.h-online.com/open/news/item/Community-fears-Windows-8-Secure-Boot-will-block-Linux-1347997.html")

The will effectively ban may popular GPL / LGPL applications such as VLC media player, LibreOffice etc on the Windows Metro user interface. It can also be used to ban bit torrent clients for example or any software that Microsoft may wish to censor for any reason. We must also keep in mind that Microsoft recently changed its terms for its Windows Mobile Store to effectively ban GPL applications. Check the following section l from the [Microsoft Provider Agreement]("http://create.msdn.com/downloads/?id=638")

> l. “Excluded License” means any license requiring, as a condition of use, modification and/or distribution of the software subject to the license, that the software or other software combined and/or distributed with it be (i) disclosed or distributed in source code form; (ii) licensed for the purpose of making derivative works; or (iii) redistributable at no charge. Notwithstanding the foregoing, the following software licenses are not considered Excluded Licenses: CDDL 1.0 (Common Development and Distribution License); CPL 1.0 (Common Public License); Eclipse Public License; Microsoft Reciprocal License (MS-RL); and MPL 1.1 (Mozilla Public License). The GNU General Public License version 3, the GNU Affero General Public License version 3, the GNU Lesser General Public License version 3, and any equivalents to the foregoing are considered Excluded Licenses. 

The ban on GPL v3 and related licenses is explicit but this also bans LGPL 2.1, GPL v2, and GPL v2+ code. When one considers that software under the GPL and related licenses is very common in products the are competitive to Microsoft's products that case for anti trust action here may actually be very strong. It is not only GNU / Linux that is targeted here but the vast majority of FLOSS.

---

### Post by Atamisk on 2011-09-22
I was going to scratch-build my next desktop in 2013 anyhow... this just gives me a good reason to :P

---

### Post by Dragonbite on 2011-09-22
My understanding is that it will require some sort of certificate included in order to boot.  What's stopping Linux distributions from getting one of these certificates?

Especially the commercially backed distributions (Red Hat, SUSE, Ubuntu) and vendors (IBM, HP, Oracle) from making sure theirs still work!

That is also *if* vendors actually follow through with this, governments don't scream "antitrust" and other legal wranglings don't kill it in its tracks or vendors off two types of systems (one with and one without)?

IF Intel does it, maybe AMD won't, knowing that it will have access to a market Intel isn't. Maybe ARM chips will push forward as more open?  Maybe IBM will move their G chips (G6 now?) to consumer systems again (since Apple switched to Intel)?

There's a lot of parties involved and Microsoft doesn't have the same pull they used to.  Especially in servers.

---

### Post by debd on 2011-09-22
> This will have an impact on both hardware and software - hardware that  does not have the right key to communicate with the firmware cannot be  added to the machine in question. 

what about that? no hardware peripherals if not signed?? :)

---

### Post by nothingspecial on 2011-09-22
Let's keep this thread nice ladies and gentlemen :)

---

### Post by Dr. C on 2011-09-22
> **nothingspecial said:**
> Let's keep this thread nice ladies and gentlemen :)

Thank you.

---

### Post by srs5694 on 2011-09-22
> **Dragonbite said:**
> My understanding is that it will require some sort of certificate included in order to boot.  What's stopping Linux distributions from getting one of these certificates?

One issue is practical: There's no central clearinghouse for the relevant keys, so Red Hat (or whoever) would have to negotiate with dozens or hundreds of computer companies to either sign their boot loaders with the manufacturers' keys or to get the RH keys included in the firmware. This isn't so much of an issue for Microsoft because the manufacturers all come to them for the Windows certification anyhow.

Another issue is legal: The GPL v3, under which GRUB 2 is licensed, includes terms that are incompatible with the way UEFI's secure boot feature is designed. Thus, GRUB 2 is out, and even GPL v2 programs are iffy on that score, as I understand it. This in turn creates a new technical hurdle: Writing a new boot loader that would be acceptable to the Linux community while also working with secure boot from a licensing perspective. Perhaps some code could be salvaged or adapted from somewhere, but at the very least it's an annoying obstacle.

> IF Intel does it, maybe AMD won't, knowing that it will have access to a market Intel isn't. Maybe ARM chips will push forward as more open?  Maybe IBM will move their G chips (G6 now?) to consumer systems again (since Apple switched to Intel)?

Neither Intel nor AMD is directly relevant to the issue, although both are peripherally involved as members of the UEFI Forum, and for all I know one or both might be pushing things behind the scenes.

The companies that are most directly responsible for turning this into a big nothing or a big mess (whichever way it ultimately goes) are the computer manufacturers -- Dell, HP, Toshiba, eMachines, Sony, etc. *They* are the ones who are responsible for the features in the firmware on their own computers, including details of the secure boot implementation, such as whether or not users can disable it.

Microsoft has its finger pretty deeply in the pie, too, since it's the requirements of the Windows 8 logo program that have touched off this rampant speculation. It's the desire to meet those requirements that *might* (and I emphasize that word: *might*) cause computer manufacturers to lock down their machines in such a way that they can only run Windows. Nonetheless, it's the computer vendors who decide whether they want the Windows 8 logo on their computers, and they'll have *some* leeway in how they implement it. As I have yet to see details of what the program requires on this score, I can't say how restrictive Microsoft is being in its Windows 8 certification terms.

Please, remember this: We know next to nothing about the details of the Windows 8 logo program's requirements or about what manufacturers' intentions are. Without that knowledge, all we can do is speculate. Many people in this thread are jumping to very shaky conclusions. It's not time to panic just yet. If you're concerned (and some concern *is*, IMHO, warranted), please *write to major PC manufacturers*. A few letters might be enough to tip the balance if a manufacturer is uncertain how to proceed.

---

### Post by MonolithImmortal on 2011-09-22
Sounds to me like it's the GPL that's the problem in this instance.

Why are you guys moaning about grub 2? Just use LILO (BSD licensed) and side step the GPL issue all together.

EDIT: Er, you'd want to use elilo for UEFI.

---

### Post by srs5694 on 2011-09-22
> **MonolithImmortal said:**
> Sounds to me like it's the GPL that's the problem in this instance.

Why are you guys moaning about grub 2? Just use LILO (BSD licensed) and side step the GPL issue all together.

EDIT: Er, you'd want to use elilo for UEFI.

Many of the source files in the ELILO source distribution state that the software is licensed under the terms of the GPL (version unspecified). The [Sourceforge page](https://sourceforge.net/projects/elilo/) also states that it's licensed under the GPL. I don't see a copy of the actual copy of the GPL in the source package, but given all the other evidence, I'd say that ELILO is GPLed.

---

### Post by MonolithImmortal on 2011-09-22
> **srs5694 said:**
> Many of the source files in the ELILO source distribution state that the software is licensed under the terms of the GPL (version unspecified). The [Sourceforge page]("https://sourceforge.net/projects/elilo/") also states that it's licensed under the GPL. I don't see a copy of the actual copy of the GPL in the source package, but given all the other evidence, I'd say that ELILO is GPLed.
Then fork LILO and make ELILO2 or something like that. Meh, I just don't see what all the fuss is about.

---

### Post by Dr. C on 2011-09-22
The fundamental question here is not if a GNU / Linux distributor or an end user for that matter can sign binaries with a key (and yes contrary to some of the comments this is possible and is compatible with the GPL v3) but rather who decides if the key is be trusted by the computer, the owner (as is effectively the case with BIOS because of physical possession) or a hardware vendor who is is controlling hardware they no longer own.

The solution here is to ensure that the owner of the hardware and only the owner of the hardware to allow or revoke software keys regardless of whether they are from a propriety software vendor, a FLOSS vendor, or self signed etc. So for example a computer owner must be able to allow software signed by the FSF and not Microsoft or vice versa for that matter. 

One way to do this is to allow the owner to place a computer back into "setup mode" under the UEFI specification by use of a hardware switch for example.

As long as the end owner is in a position to allow or revoke software keys there are no GPL v3 issues with UEFI since this effectively provides the "installation instructions"

---

### Post by KiwiNZ on 2011-09-22
> **Dr. C said:**
> The fundamental question here is not if a GNU / Linux distributor or an end user for that matter can sign binaries with a key (and yes contrary to some of the comments this is possible and is compatible with the GPL v3) but rather who decides if the key is be trusted by the computer, the owner (as is effectively the case with BIOS because of physical possession) or a hardware vendor who is is controlling hardware they no longer own.

The solution here is to ensure that the owner of the hardware and only the owner of the hardware is a position to allow or revoke software keys regardless of whether they are from a propriety software vendor, a FLOSS vendor, or self signed etc. So for example a computer owner must be able to allow software signed by the FSF and not Microsoft or vice versa for that matter. 

One way to do this is to allow the owner to place a computer back into "setup mode" under the UEFI specification by use of a hardware switch for example.

As long as the end owner is in a position to allow or revoke software keys there are no GPL v3 issues with UEFI since this effectively provides the "installation instructions"

That is a good point, when you buy Software you buy a license to use, when you buy Hardware you making an all out purchase and take ownership you are not buying a license to in accordance with an EULA.

---

### Post by Old_Grey_Wolf on 2011-09-22
Having read about UEFI, I don't know if most of the people posting in either thread have actually read about what UEFI is. Unless you have a belief in a conspiracy theory, I don't know how Microsoft is associated with UEFI.

---

### Post by Quadunit404 on 2011-09-22
> **Old_Gray_Wolf said:**
> Having read about UEFI, I don't know if most of the people posting in either thread have actually read about what UEFI is. Unless you have a belief in a conspiracy theory, I don't know how Microsoft is associated with UEFI.

Agreed. The lack of knowledge about what UEFI is and how it works in this thread disturbs me.

---

### Post by Copper Bezel on 2011-09-22
Yeah, it's getting interchanged with the idea of a locked or signed bootloader, which will lock out Linux (or any other OS) and is the problem being discussed in the thread. The article itself makes that distinction.

---

### Post by KiwiNZ on 2011-09-22
> **Quadunit404 said:**
> Agreed. The lack of knowledge about what UEFI is and how it works in this thread disturbs me.

Agreed

UEFI (EFI) has been around in various implementations for some time, HP,Apple and IBM have been using for a while on various Devices.

It has the potential to be used in the manner feared, but the reality is, it wont.

---

### Post by jwbrase on 2011-09-22
> **Dr. C said:**
> As long as the end owner is in a position to allow or revoke software keys there are no GPL v3 issues with UEFI since this effectively provides the "installation instructions"

And indeed, if the owner can allow or revoke arbitrary keys, the lockdown capability is actually a very good thing: A user could do his own kernel compile, sign it with a personal key, and not allow anything without his personal key to boot.

---

### Post by Dr. C on 2011-09-22
We may actually be already having an impact on whether or not UEFI is used in the manner feared in this thread. I just did a search for > Microsoft Windows 8 logo requirements on Google and this thread came up as the second result. Almost all the other results on the first page also relate to this GNU / Linux issue.

---

### Post by el_koraco on 2011-09-22
It's probably mostly just the Red hat dev blowing off some steam. If you read his blog a little, he's been having headaches with implementing boot programs to EFI, so he's probably inclined to think the worst by default.

---

### Post by Dr. C on 2011-09-22
Here is a recent blog posting from Microsoft. [http://blogs.msdn.com/b/b8/archive/2011/09/22/protecting-the-pre-os-environment-with-uefi.aspx]("http://blogs.msdn.com/b/b8/archive/2011/09/22/protecting-the-pre-os-environment-with-uefi.aspx") The following maybe is significant: > Who is in control?

At the end of the day, the customer is in control of their PC. Microsoft’s philosophy is to provide customers with the best experience first, and allow them to make decisions themselves. We work with our OEM ecosystem to provide customers with this flexibility. The security that UEFI has to offer with secure boot means that most customers will have their systems protected against boot loader attacks. For the enthusiast who wants to run older operating systems, the option is there to allow you to make that decision.

This was just posted today. One is left with the impression that the fuss that has kicked up over this may be having already be having a positive impact. Still what about a version of GNU / Linux that is newer than Windows 8? Vigilance on the part of the FLOSS community remains paramount.

---

### Post by dniMretsaM on 2011-09-22
> **Dr. C said:**
> Still what about a version of GNU / Linux that is newer than Windows 8? Vigilance on the part of the FLOSS community remains paramount.

My guess is that when they mention older operating systems, they're just meaning other operating systems. Saying "older" implies they are inferior. Just a guess though. One never knows with Microsoft...

---

### Post by Copper Bezel on 2011-09-22
The Ubuntu home page used to refer to software for Windows, like the U1 client, as intended for "legacy systems" in the workplace. So yes, just taking a very nasty stab at a competitor that isn't held in much respect.

---

### Post by Dr. C on 2011-09-23
> **dniMretsaM said:**
> My guess is that when they mention older operating systems, they're just meaning other operating systems. Saying "older" implies they are inferior. Just a guess though. One never knows with Microsoft...

I suspect there are many at Microsoft that are not very comfortable mentioning GNU or Linux. They could simply have said: > Older Microsoft operating systems or operating systems from other vendors. 

and avoid any possible mis-understanding.

---

### Post by whatthefunk on 2011-09-23
Older versions of Windows would definitely be allowed by the secure boot feature.  Who knows if other, non-Microsoft OSs will be allowed.  Hopefully there will be some sort of switch.

---

### Post by Copper Bezel on 2011-09-23
If the statement is true, then there's nothing to lock out Linux installs, either. Windows 7 isn't going to be re-released with a signed bootloader. It remains to be seen how universally those "off switches" will be provided by the OEMs, but as several (not me, I admit) have been saying since the start, it doesn't seem to be an evil plot.

[QUOTE=Dr. C]I suspect there are many at Microsoft that are not very comfortable mentioning GNU or Linux. They could simply have said:[/QUOTE]
I think the answer provided conveyed the *entire* intended message in a way that a statement written in language that reflected reality wouldn't have.

---

### Post by Dr. C on 2011-09-23
> **whatthefunk said:**
> Older versions of Windows would definitely be allowed by the secure boot feature.  Who knows if other, non-Microsoft OSs will be allowed.  Hopefully there will be some sort of switch.

It is not technically simple to allow something like Windows NT Workstation 4.0 and block GNU / Linux using UEFI.

---

### Post by beew on 2011-09-23
> **Dr. C said:**
> Here is a recent blog posting from Microsoft. [http://blogs.msdn.com/b/b8/archive/2011/09/22/protecting-the-pre-os-environment-with-uefi.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/22/protecting-the-pre-os-environment-with-uefi.aspx) The following maybe is significant: 

This was just posted today. One is left with the impression that the fuss that has kicked up over this may be having already be having a positive impact. Still what about a version of GNU / Linux that is newer than Windows 8? Vigilance on the part of the FLOSS community remains paramount.


I am not assured. As usual MS passes the buck to the OEM (thus pre-empting antitrust lawsuits?) but the problem remains, it is the OEMs that control how you are going to use your hardware, not you the user. If they are nice you may get an off switch but then you may not, there is no mention of allowing users the power to approve or revoke software keys. The user should be able to control what he/she allows to boot in his/her computer and no one else.  We must continue to make noises. 

It is pathetic that one company should have so much power in controlling our access to technology.

P.S. Why is this thread being moved to "recurring"? I cannot think of a more timely and important topic on Ubuntu forums (or any Linux forum for that matter)

---

### Post by el_koraco on 2011-09-23
> **beew said:**
> I am not assured. As usual MS passes the buck to the OEM (thus pre-empting antitrust lawsuits?) but the problem remains, it is the OEMs that control how you are going to use your hardware, not you the user. If they are nice you may get an off switch but then you may not, there is no mention of allowing users the power to approve or revoke software keys. The user should be able to control what he/she allows to boot in his/her computer and no one else.  We must continue to make noises. 

It is pathetic that one company should have so much power in controlling our access to technology.

P.S. Why is this thread being moved to "recurring"? I cannot think of a more timely and important topic on Ubuntu forums (or any Linux forum for that matter)

From the article: 

[I]At the end of the day, the customer is in control of their PC.  Microsoft’s philosophy is to provide customers with the best experience  first, and allow them to make decisions themselves... For the enthusiast  who wants to run older operating systems, the option is there to allow  you to make that decision...

A demonstration of this control is found in the Samsung tablet with  Windows 8 Developer Preview that was offered to //BUILD/ participants.  In the screenshot below you will notice that we designed the firmware to  allow the customer to disable secure boot.

[IMG]http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-01-29-43-metablogapi/0624.Figure_2D00_5_2D002D002D00_Samsung_2D00_PC_2D00_secured_2D00_boot_2D00_setting_5F00_thumb_5F00_02016A69.jpg[/IMG]
[/I]

---

### Post by Dragonbite on 2011-09-23
> **Dr. C said:**
> Here is a recent blog posting from Microsoft. [http://blogs.msdn.com/b/b8/archive/2011/09/22/protecting-the-pre-os-environment-with-uefi.aspx]("http://blogs.msdn.com/b/b8/archive/2011/09/22/protecting-the-pre-os-environment-with-uefi.aspx") The following maybe is significant: 

This was just posted today. One is left with the impression that the fuss that has kicked up over this may be having already be having a positive impact. Still what about a version of GNU / Linux that is newer than Windows 8? Vigilance on the part of the FLOSS community remains paramount.

> **el_koraco said:**
> From the article: 

[I]At the end of the day, the customer is in control of their PC.  Microsoft’s philosophy is to provide customers with the best experience  first, and allow them to make decisions themselves... For the enthusiast  who wants to run older operating systems, the option is there to allow  you to make that decision...

A demonstration of this control is found in the Samsung tablet with  Windows 8 Developer Preview that was offered to //BUILD/ participants.  In the screenshot below you will notice that we designed the firmware to  allow the customer to disable secure boot.

[IMG]http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-01-29-43-metablogapi/0624.Figure_2D00_5_2D002D002D00_Samsung_2D00_PC_2D00_secured_2D00_boot_2D00_setting_5F00_thumb_5F00_02016A69.jpg[/IMG]
[/I]

If there was the "+1" for posts, I'd put one on this one!  This is truly where a picture is worth a 1,000 words (or at least 110 posts).

Now what I would love to see is being able to turn that off, install Linux (if the system doesn't come with it), and then turn it back on with it running Linux!

---

### Post by beew on 2011-09-23
> **el_koraco said:**
> From the article: 

[I]At the end of the day, the customer is in control of their PC.  Microsoft’s philosophy is to provide customers with the best experience  first, and allow them to make decisions themselves... For the enthusiast  who wants to run older operating systems, the option is there to allow  you to make that decision...
..
[/I]


In the best case scenario enough OEMs would implement such a switch so that the user can decide whether to use secure boot or not, but what if the user wants to use secure boot but to approve and disapprove keys of his or her own choice, not that of the OEM or MS?

Still this doesn't address the worry that many (most?) OEMS will probably just do the bare minimum and will decide not to implement the switch off option.

---

### Post by scottishbloke on 2011-09-23
> "After years of trying to cut off Linux growth as a desktop platform on  x86 and x64 PCs, Microsoft may have actually figured out a way to stop  Linux deployments on client PCs dead in their tracks."

[http://www.itworld.com/it-managementstrategy/205255/windows-8-oem-specs-may-block-linux-booting](http://www.itworld.com/it-managementstrategy/205255/windows-8-oem-specs-may-block-linux-booting)

---

### Post by el_koraco on 2011-09-23
> **beew said:**
> 
Still this doesn't address the worry that many (most?) OEMS will probably just do the bare minimum and will decide not to implement the switch off option.

I doubt it, even if Linux doesn't come into play at all. There's a whole sub-universe of professional tools related to Windows (malware removal tools, computer forensics, partition cloning) that not only has a lively audience, but serves strong security functions for companies and individuals. And they all need to boot before the BOOTMGR is even initiated. Going through the hassle of signing all of their bootloaders (the isolinux family is a big part of that) and having to deal with issues that arise is much more of a hassle than shipping computers with a kill switch. 

This whole thing has been a superb example of paranoia generated by a blog post that said "no need for paranoia". As for your other concern, I'm pretty sure with time interfaces will be made to allow the users to dictate the secure boot policies, like adding their own custom signed bootloaders (which would be something like the second feature of UEFI that might be useful for Linux). From everything I can read, this seems to have the potential to become a great feature.

---

### Post by sffvba[e0rt on 2011-09-23
Threads merged...


404

---

### Post by scottishbloke on 2011-09-23
Sorry bout that, Thanks not found.

---

### Post by beew on 2011-09-23
> **el_koraco said:**
> I doubt it, even if Linux doesn't come into play at all. There's a whole sub-universe of professional tools related to Windows (malware removal tools, computer forensics, partition cloning) that not only has a lively audience, but serves strong security functions for companies and individuals. And they all need to boot before the BOOTMGR is even initiated. Going through the hassle of signing all of their bootloaders (the isolinux family is a big part of that) and having to deal with issues that arise is much more of a hassle than shipping computers with a kill switch. 

This whole thing has been a superb example of paranoia generated by a blog post that said "no need for paranoia". As for your other concern, I'm pretty sure with time interfaces will be made to allow the users to dictate the secure boot policies, like adding their own custom signed bootloaders (which would be something like the second feature of UEFI that might be useful for Linux). From everything I can read, this seems to have the potential to become a great feature.

I hope you are right. But the scenarios you described may only apply to high end laptops and desktops. What about cheap laptops and netbooks? I think OEM manufactures would opt for a lock down in these machines. This will create a situation where you will have to pay extra for high end machines to run Linux and the hardware incompatibility is completely artificial,  that would further marginalize Linux for the average users. 

BTW. Why is the thread moved once more to this obscure place???

---

### Post by beew on 2011-09-23
Garrett has responded.

[http://mjg59.dreamwidth.org/5850.html](http://mjg59.dreamwidth.org/5850.html)

> What does this mean for the end user? Microsoft claim that the customer  is in control of their PC. That's true, if by "customer" they mean  "hardware manufacturer". The end user is not guaranteed the ability to  install extra signing keys in order to securely boot the operating  system of their choice. The end user is not guaranteed the ability to  disable this functionality. The end user is not guaranteed that their  system will include the signing keys that would be required for them to  swap their graphics card for one from another vendor, or replace their  network card and still be able to netboot, or install a newer SATA  controller and have it recognise their hard drive in the firmware. The  end user is no longer in control of their PC.

If Microsoft were  serious about giving the end user control, they'd be mandating that  systems ship without any keys installed. The user would then have the  ability to make an informed and conscious decision to limit the  flexibility of their system and install the keys. The user would be told  what they'd be gaining and what they'd be giving up.

The final  irony? If the user has no control over the installed keys, the user has  no way to indicate that they don't trust Microsoft products. They can  prevent their system booting malware. They can prevent their system  booting Red Hat, Ubuntu, FreeBSD, OS X or any other operating system.  But they can't prevent their system from running Windows 8.

---

### Post by Elfy on 2011-09-23
Thread moved to The Community Cafe.

---

### Post by del_diablo on 2011-09-23
I know that most of the "OEM locks hardware on MS request" will likely be considered a crime in Europa, but how is the American legal standards about it?

---

### Post by beew on 2011-09-23
> **del_diablo said:**
> I know that most of the "OEM locks hardware on MS request" will likely be considered a crime in Europa, but how is the American legal standards about it?

MS's strategy seems to deny that it makes such a request, while at the same time giving the OEMS the incentives to do just that. By doing so it passes the buck to the OEMS. 

I wonder if there should be some legal restrictions on OEM arrangements to prevent de facto monopolies like MS from extending their monopolies to the hardware market as well.

---

### Post by s1baker on 2011-09-23
hi,
 Is Windows trying to exclude Linux from PC's?
 Check this article out. I wonder what the experts think about it and if this did come about, if it would affect a dual boot system with Ubuntu and Windows 8.

[http://www.theregister.co.uk/2011/09/21/secure_boot_firmware_linux_exclusion_fears/]("http://www.theregister.co.uk/2011/09/21/secure_boot_firmware_linux_exclusion_fears/")

---

### Post by nothingspecial on 2011-09-23
Merged.

---

### Post by del_diablo on 2011-09-23
> **beew said:**
> MS's strategy seems to deny that it makes such a request, while at the same time giving the OEMS the incentives to do just that. By doing so it passes the buck to the OEMS. 

I wonder if there should be some legal restrictions on OEM arrangements to prevent de facto monopolies like MS from extending their monopolies to the hardware market as well.

I take that as "there is no such thing" then?
Thats quite sad, because then it means we Europeans will have to report this "scam of the marked" to our authorities, which then will deal with it 2-3 months later. Well, in some parts of Europa at the least.
Legal restrictions on what a OEM is allowed to do exists in the world, but the problem is that people are apathic not to not take it to court when a defect product enter the marked, and that since there is no such law in the US you get a ripple effect, which ruins that marked in the first place.



A curious question: How does UEFI compare to BIOS when it comes to firmware and ACPI hacks?

---

### Post by HansKisaragi on 2011-09-23
You can turn of secure booting. Windows 8 is not locking anything.

[IMG]http://www.media.allerinternett.no/php/obj.phpi?o=4093242&w=698&h=392&ee=1316767458[/IMG]

---

### Post by del_diablo on 2011-09-23
> **Viiral said:**
> You can turn of secure booting. Windows 8 is not locking anything.

But the OEMs will.
Have you ever had one of those laptops with a completely broken BIOS, which will never be patched?
Or annoying engineering problems that is obvious to anybody with a minor eye to spot them?
So how do I know that my new ASUS motherboard will actually work?
How do I know that my prefap laptop will actually have the option of turning off secure booting?

---

### Post by Copper Bezel on 2011-09-23
As if. You'd buy a laptop before checking to see if there's information on its Linux compatibility? Seriously? A laptop with a graphics or wireless card that doesn't work is just as useless as one that won't boot.

And if you're the first and it doesn't work with the LiveCD, you return it....

I'm not at all reassured that there is no problem here. It's not, however, likely to be a *practical* one.

---

### Post by beew on 2011-09-23
> **Copper Bezel said:**
> As if. You'd buy a laptop before checking to see if there's information on its Linux compatibility? Seriously? A laptop with a graphics or wireless card that doesn't work is just as useless as one that won't boot.

And if you're the first and it doesn't work with the LiveCD, you return it....

I'm not at all reassured that there is no problem here. It's not, however, likely to be a *practical* one.

Well most graphic cards work OOTB unless you have gotten Optimus or something like that, with wifi the worse case scenario is that you have to dish out $15-$20 to get a usb wifi card,--no biggie if you have already spent a couple of hundred bucks on the computer. But this is completely locked down in that you can't even boot anything at all without a kill switch, and the worst part is, unlike graphic and wifi it theoretically can affect almost all laptops purchased through normal venues. It can potentially be orders of magnitude worse for Linux users than the incompatibility arising from lack of specific drivers.

---

### Post by Old_Grey_Wolf on 2011-09-23
I keep reading OEM this and OEM that in this thread. 

The OEMs like Dell, HP, Aser, etc., license the BIOS they use from four primary BIOS vendors, American Megatrends, Byosoft, Insyde Software, and Phoenix Technologies. They use the BIOS toolkit to customize the BIOS for their hardware.

UEFI will probably work the same way. The OEM will license the UEFI toolkit and customize it for their hardware. If the UEFI vendors include the option to turn Secure Boot off then the OEM customized versions will most likely have it.

Edit:  Since UEFI vendors like BIOS vendors do NOT sell operating systems, they wouldn't have contractual or monetary incentives to do what Microsoft wants. Microsoft would not be likely to force the lookout of GNU/Linux.

---

### Post by del_diablo on 2011-09-23
> **Copper Bezel said:**
> As if. You'd buy a laptop before checking to see if there's information on its Linux compatibility? Seriously? A laptop with a graphics or wireless card that doesn't work is just as useless as one that won't boot.

And if you're the first and it doesn't work with the LiveCD, you return it....

I'm not at all reassured that there is no problem here. It's not, however, likely to be a *practical* one.

Copper Bezel: That depends on the amount of "trying and failing" I am willing to perform.
Lets say there is suddenly a sale, and they are selling a laptop with the specs I want, for quite a bit cheaper. Lets say the sale lasts 1-2 days.
If I ask on the forums, or the IRC somwhere, I may never get a proper answer.
Nor is there anywhere to look for the proper information, well at the least to my knowledge.

So basically it would work something like this:
-You need to see if the critical components(networking, intigrated gpu, ports) is working
-You can't find any way of figuring out how broken the power managment and bios is without a test run, sadly, so that is still a complete gamble.
-Or you can find a year old laptop, and PRAY that those who made the reviews didn't lie out of ignorance(some people ignore power managment problems, other ignore small networking problems, etc).

---

### Post by anewguy on 2011-09-23
The idea that this is firmware based is a little disturbing.  This makes it basically a hardware key in that it will be contained on the motherboard (BIOS - but watch the future - I'll bet they are working towards a key chip, like the password lock chips on some laptops).

Obviously this has anti-trust written all over it, and we know the history at least here in the U.S. of trying to get those cases to trial and then getting them resolved.  The delays the lawyers for Microsoft can cause these things to go on for many, many years.  Basically they try to drag it out long enough the either the OS is outdated or they've already made a boatload of money from it.

I'm not sure what we can do at this point - it's probably getting fairly late in the game.  Perhaps a compaign to force the UEFI and booting with it to be controlled by law - a law that perhaps says you need to know this key, provided by the hardware manufacturer, in order to install an OS on this machine.  Then the key could be hardware base - chip resident - and removed from the OS control.  In this way the OS would ask for the key at installation and if the key doesn't match it wouldn't allow it to be installed.  In this way it would only be the OS installation procedure that would change.  Now suppose you want to boot from something like a CD or USB flash or net based - I'm not sure how to handle that, and that should be what is the biggest concern.  Having an installation process ask you for a vendor supplied key is one thing relatively simply changed, but actual booting from another media should be the real concern.  I'm sure this is part of the idea of having the boot check - it would keep the process simple.  I'm not sure how to handle that - and that is probably where this whole thing originated, with Microsoft's spin of "hey, we can lock them into our OS" being a result if this is not brought into some kind of law.  I'm not any form of expert on this whole idea, so I'm just throwing out stray thoughts there.

However, I would suggest organizing some campaign to collect professional opinions, OS provider opinions, hardware manufacturer opinions and end user opinions, with the warning of what will happen with out regulation, and somehow get this before Congress (at least here in the U.S.).  The problem is I'm stupid - I'd have no way to even begin to do this.  Perhaps what is needed is a group of non-Microsoft OS "vendors" - various reps from each distribution of Linux and hopefully the support of Apple - to do this.    The hardware vendors - even if just for their server products - HP, Dell, et al, who market their servers with Linux should also be an addition to such a group.

If it was brought to attention how many internet servers and business servers currently run Linux, and how this might effectively wipe that out (think about it - the key is in BIOS or a hardware chip - building your own PC won't bypass that).  This should cause great alarm and should add some pretty large players into such a group.  By doing this quickly, we could be ahead of the game by presenting this - and hopefully thereby at least getting a deferral of the implementation until after the legalities are sorted out, and this would/should stop Microsoft from forcing their OS on us.  The hardware vendors - even if just for their server products - HP, Dell, et al, who market their servers with Linux should also be an addition to such a group.

Anyone know of a way to even go about suggesting this to the appropriate vendors, etc., to get the ball rolling on some sort of representative group to contact government preemptively?

I don't know if Canonical would want to be in the position of trying to start such a thing or not.

Just my wandering thoughts.......

Dave ;)

---

### Post by KiwiNZ on 2011-09-23
I don't see why this would be an 'Anti-Trust' issue. Also, it has been around for some time now.

---

### Post by dniMretsaM on 2011-09-23
> **anewguy said:**
> [realtalk]

Anyone know of a way to even go about suggesting this to the appropriate vendors, etc., to get the ball rolling on some sort of representative group to contact government preemptively?

I don't know if Canonical would want to be in the position of trying to start such a thing or not.

Just my wandering thoughts.......

Dave ;)

Nice wall of text lol. It seems to me that this would be the best course of action. As for ideas on how to contact the appropriate bigwigs, maybe emailing the CEO's? As for Canonical, I don't see why not. They have as much interest in this as anyone (at least they should). Because if you can't install an OS, that OS dies real quick.

---

### Post by KiwiNZ on 2011-09-23
MSFT sets the minimum technical requirements for the optimum operation of the Windows OS, they are allowed to do that.

The EUFI Vendors adapt their EUFI to meet these requirements and sell it to the PC makers, again they are allowed to do this.

The  PC makers adapt the EUFI to meet their specifications, They are the  ones who will decide to include or exclude the Secure Boot  enable,unenable switch in EUFI.

Thus it is not an Anti-Trust issue with regards to MSFT.

---

### Post by madmax75 on 2011-09-23
Man, this thread makes me depressed.

---

### Post by del_diablo on 2011-09-23
> **KiwiNZ said:**
> MSFT sets the minimum technical requirements for the optimum operation of the Windows OS, they are allowed to do that.

The EUFI Vendors adapt their EUFI to meet these requirements and sell it to the PC makers, again they are allowed to do this.

The  PC makers adapt the EUFI to meet their specifications, They are the  ones who will decide to include or exclude the Secure Boot  enable,unenable switch in EUFI.

Thus it is not an Anti-Trust issue with regards to MSFT.

All that is needed for a Anti-Trust to happen is that MS either says; "Please lock the boot for the non-corporation users", or that they are implying that by default it SHOULD be locked.
And since every single PC producer all fails at making good BIOSES anyhow, what is the chance of this new generation being better? Who must we sue, and what law must be passed so that there will be a FORCE that FORCES the PC makers to make proper Power Managment schemes?

---

### Post by beew on 2011-09-23
> **KiwiNZ said:**
> MSFT sets the minimum technical requirements for the optimum operation of the Windows OS, they are allowed to do that.

The EUFI Vendors adapt their EUFI to meet these requirements and sell it to the PC makers, again they are allowed to do this.

The  PC makers adapt the EUFI to meet their specifications, They are the  ones who will decide to include or exclude the Secure Boot  enable,unenable switch in EUFI.

Thus it is not an Anti-Trust issue with regards to MSFT.

You sound as though MS is just another player in a vast playing field with different competitors and that the MS OEMS are only a bit player in the market. The picture would be very different if you take into account the real world situation where most people can only get their computers through such OEMS and MS dictates the terms to them through licensing.

I sure hope that informed legal opinions would take into account the reality of concentrated power of MS instead of just talking in abstraction.

BTW it is UEFI, not EUFI.

---

### Post by KiwiNZ on 2011-09-23
> **del_diablo said:**
> All that is needed for a Anti-Trust to happen is that MS either says; "Please lock the boot for the non-corporation users", or that they are implying that by default it SHOULD be locked.
And since every single PC producer all fails at making good BIOSES anyhow, what is the chance of this new generation being better? Who must we sue, and what law must be passed so that there will be a FORCE that FORCES the PC makers to make proper Power Managment schemes?

I have never had issues with the BIOS or EFI's.

You cannot prosecute based on 'implied' well not in a competent Legal system. That is like saying " you have a car capable of 180KMH therefore I will prosecute you for potential speeding"

---

### Post by beew on 2011-09-23
> **del_diablo said:**
> All that is needed for a Anti-Trust to happen is that MS either says; "Please lock the boot for the non-corporation users", or that they are implying that by default it SHOULD be locked.


It won't say that, it wouldn't be that stupid, see the so called clarification posted today by the MS guy and the rebuttal by Mathew Garret I linked to a few posts earlier. But its terms provide strong incentives to OEMs to do exactly that. If MS wishes it could require OEMS to include a kill switch as a part of its licensing agreement and it would calm down all the speculations, but it doesn't and I bet it won't.

---

### Post by KiwiNZ on 2011-09-23
> **beew said:**
> 
BTW it is UEFI, not EUFI.

I have stated in the past I make spelling errors etc because i type vast amounts of script one handed due to my disability...... Learn some manners and we will get on better.:rolleyes::mad:

---

### Post by Old_Grey_Wolf on 2011-09-23
> **dniMretsaM said:**
> As for ideas on how to contact the appropriate bigwigs, maybe emailing the CEO's? 

I think you have a point that should enter into this discussion. I'm not talking about CEO's of operating system vendors; however, CEO's of large companies and government organizations that use a lot of servers that run Linux. 

A large company may place an order for one million Euro of computer equipment and software from a company like HP, Dell, IBM, or SGI for just one of the many projects they have. These OEMs would be hurting their sales if they didn't allow Linux to run on them. Some of these large systems run a high percentage of servers using the Linux operating system. HP and IBM sell software that runs on Linux operating systems for managing these large data-centers.

---

### Post by KiwiNZ on 2011-09-23
> **Old_Gray_Wolf said:**
> I think you have a point that should enter into this discussion. I'm not talking about CEO's of operating system vendors; however, CEO's of large companies and government organizations that use a lot of servers that run Linux. 

A large company may place an order for one million Euro of computer equipment and software from a company like HP, Dell, IBM, or SGI for just one of the many projects they have. These OEMs would be hurting their sales if they didn't allow Linux to run on them. Some of these large systems run a high percentage of servers using the Linux operating system. HP and IBM sell software for managing these large data-centers that run on Linux operating systems.

IBM and HP already use UEFI on their servers

---

### Post by beew on 2011-09-23
> **KiwiNZ said:**
> IBM and HP already use UEFI on their servers

It is not UEFI, but who control the key signing for secure booting. The user or the OEM and MS? Ideally the user should control the security policy on his/her hardware, the kill switch is a less than ideal solution but still better than having windows shoved down your throat without any way to boot from Linux or other alternatives.

---

### Post by Old_Grey_Wolf on 2011-09-23
> **KiwiNZ said:**
> IBM and HP already use UEFI on their servers

Yes, and the UEFI they use would allow the option to turn Secure Booting off. That is the point I am trying to make.

---

### Post by Dr. C on 2011-09-23
> **KiwiNZ said:**
> I have never had issues with the BIOS or EFI's.

You cannot prosecute based on 'implied' well not in a competent Legal system. That is like saying " you have a car capable of 180KMH therefore I will prosecute you for potential speeding"

Of course not, but one can sit in wait with ones speed trap ready and armed. When and if the car goes by at 180 KMH then prosecute. One can also warn the owners of cars capable of going at 180 KMH what the legal consequences are of speeding are going to be.

So yes the GNU / Linux and FLOSS communities need to to have the "speed trap" ready and armed. Whether Microsoft decides to "speed" and set it off that is strictly Microsoft's choice.

---

### Post by KiwiNZ on 2011-09-23
> **Old_Gray_Wolf said:**
> Yes, and the UEFI they use would allow the option to turn Secure Booting off. That is the point I am trying to make.

That feature is included, see screen shot posted earlier in the thread

With regards to Mid range and High end servers, purchares seldom change their OS's as this would invalidate expensive Care Packs or Service Packs.

---

### Post by KiwiNZ on 2011-09-23
> **Dr. C said:**
> Of course not, but one can sit in wait with ones speed trap ready and armed. When and if the car goes by at 180 KMH then prosecute. One can also warn the owners of cars capable of going at 180 KMH what the legal consequences are of speeding are going to be.

So yes the GNU / Linux and FLOSS communities need to to have the "speed trap" ready and armed. Whether Microsoft decides to "speed" and set it off that is strictly Microsoft's choice.

No, the Linux community does need to run around like Demented Reef Fish crying how can we prosecute to stop this. That will annoy our customers and slow development.

What we need to do is think positively and think how can we innovate to mitigate.

---

### Post by Old_Grey_Wolf on 2011-09-23
> **KiwiNZ said:**
> That feature is included, see screen shot posted earlier in the thread

With regards to Mid range and High end servers, purchares seldom change their OS's as this would invalidate expensive Care Packs or Service Packs.

I think we are in agreement; however, we may be misinterpreting each others posts. I really can't determine if you are disagreeing with what I posted or adding additional information supporting the opinion. I think that the risk of not being able to run Linux on a PC is being highly overstated; almost, to the point of a conspiracy theory.

---

### Post by Dr. C on 2011-09-23
> **KiwiNZ said:**
> No, the Linux community does need to run around like Demented Reef Fish crying how can we prosecute to stop this. That will annoy our customers and slow development.

What we need to do is think positively and think how can we innovate to mitigate.

If Microsoft does this it will lead to an anti trust case that will make the [SAMBA case in Europe]("http://fsfe.org/projects/ms-vs-eu/timeline.html") by comparison a walk in the park. This would be anti trust plain and simple. In any even event which customers are we going to annoy? If the SAMBA case is any experience it is the customers that benefited from the anti trust action. 

Raising the alarm now is the right thing to do, since it will allow Microsoft to address the problem now before it gets out of hand.

---

### Post by del_diablo on 2011-09-23
> **KiwiNZ said:**
> I have never had issues with the BIOS or EFI's.

I guess you also only run desktop computers, or buy special made system by Linux computer manifacturers?
I've already had 3 laptops with bad BIOSES, and every single time a PC does not boot up a live CD its a BIOS bug too. Providing the live CD supports the hardware.
I can also think of direct examples: XP has a lot of bad hacks for power managment, and because of that a lot of motherboards came with BIOSes that thought "hey man! This is XP right? So no need to actually implent X and Y in order to get better power managment, fan controll, etc".
Look at it this way: You can not build your own laptop, which means you have to aquire a prefab. Prefabs are designed to only run on for example Windows 7, and might have severe hacks because they was too lazy to do it properly.

Or are your position: "If it only slows down the system, or ruins a part of the system I could care less about, its not a BIOS bug."?
Clarify please.

> You cannot prosecute based on 'implied' well not in a competent Legal system. That is like saying " you have a car capable of 180KMH therefore I will prosecute you for potential speeding"

A poorly weiled threat is still a direct threat.
The question is just how subtle.
If you audiotape somebody saying "You should really get out of the branche you know, if you worry about your daugther", this IS a threat, IF your daugther is missing, or certain other circumstances is present.
And remember: Appropiate context.


KiwiNZ: So telling court "Your honor, they are breaking the law, and here is the evidence." is basically to shame yourself?
Or was your intent something else?

---

### Post by KiwiNZ on 2011-09-23
> **old_gray_wolf said:**
> i think we are in agreement; however, we may be misinterpreting each others posts. I really can't determine if you are disagreeing with what i posted or adding additional information supporting the opinion. I think that the risk of not being able to run linux on a pc is being highly overstated; almost, to the point of a conspiracy theory.

+1

---

### Post by KiwiNZ on 2011-09-23
> **del_diablo said:**
> I guess you also only run desktop computers, or buy special made system by Linux computer manifacturers?
I've already had 3 laptops with bad BIOSES, and every single time a PC does not boot up a live CD its a BIOS bug too. Providing the live CD supports the hardware.
I can also think of direct examples: XP has a lot of bad hacks for power managment, and because of that a lot of motherboards came with BIOSes that thought "hey man! This is XP right? So no need to actually implent X and Y in order to get better power managment, fan controll, etc".
Look at it this way: You can not build your own laptop, which means you have to aquire a prefab. Prefabs are designed to only run on for example Windows 7, and might have severe hacks because they was too lazy to do it properly.

Or are your position: "If it only slows down the system, or ruins a part of the system I could care less about, its not a BIOS bug."?
Clarify please.



A poorly weiled threat is still a direct threat.
The question is just how subtle.
If you audiotape somebody saying "You should really get out of the branche you know, if you worry about your daugther", this IS a threat, IF your daugther is missing, or certain other circumstances is present.
And remember: Appropiate context.


KiwiNZ: So telling court "Your honor, they are breaking the law, and here is the evidence." is basically to shame yourself?
Or was your intent something else?

In my Career (before medical retirement ) I managed a large( Large on New Zealand Standards) IT unit, we had over 200 F&P Servers, 2 Mainframes, 30 App Servers, 11,000 Desktops, 2500 Laptops and sundry other devices like prinetrs etc. I never experienced BIOS issues.

Personally I run a Server ( well It died this week) several desktops, two Laptops and an Ipad, and again no BIOS issues.

Where there is smoke there is not always a fire, sometimes it is just someone smoking.

---

### Post by del_diablo on 2011-09-23
KiwiNZ: You are basically saying you where in a position where you had special made hardware, over contract, with a clausul for the BIOS to be properly fitted, and with at the least 6000 apathic grunts who would not in any situation report that there is some large bugs in the power managment.
And BIOS issues with iPad? please tell me what you are smoking, and why its relevant.

---

### Post by srs5694 on 2011-09-23
> **Old_Gray_Wolf said:**
> The OEMs like Dell, HP, Aser, etc., license the BIOS they use from four primary BIOS vendors, American Megatrends, Byosoft, Insyde Software, and Phoenix Technologies. They use the BIOS toolkit to customize the BIOS for their hardware.

The present tense, not the future tense, is appropriate here -- UEFI is *already* being shipped on many (perhaps most) new PCs. At the moment, many of these UEFIs ship with a BIOS compatibility mode enabled, so they act just like normal BIOSes, either instead of or in addition to working like a UEFI. This point isn't really critical to the discussion, but it is part of the background for what's going on here.

[QUOTE=Old_Gray_Wolf;11279006]UEFI will probably work the same way. The OEM will license the UEFI  toolkit and customize it for their hardware. If the UEFI vendors include  the option to turn Secure Boot off then the OEM customized versions  will most likely have it.

This would be true if the OEMs didn't customize the firmware themselves, or order such customization from the firmware's supplier. In fact they do, and they usually "dumb down" the interface. If you check the firmware on a motherboard bought as such from ASUS or Biostar or whatnot to the firmware on a PC bought from eMachines or Toshiba or whatnot, you'll find that the PC's firmware lacks many options that are present in the "bare" motherboard's firmware. This is true even when the firmware comes from the same company on the two systems you're comparing and has a similar vintage.

Personally, I'd be shocked if "bare" motherboards lacked an "off switch" for the secure boot feature. PCs are another matter, though; their manufacturers might be tempted to disable the off switch because of pressure from Microsoft, an effort to reduce the size of code in the firmware (thus enabling use of smaller-capacity and therefore cheaper chips), a desire to reduce support calls relating to non-Microsoft OSes, or for other reasons.

> **Old_Gray_Wolf said:**
> Yes, and the UEFI they use would allow the option to turn Secure Booting off. That is the point I am trying to make.

Actually, AFAIK few or no currently-shipping systems use UEFI 2.3.1, which is the version that makes a big push on the secure boot features. The ones I've used don't implement secure boot at all, AFAIK. This is an important point that some people (not you, Old_Gray_Wolf) seem to be confusing: UEFI is not the problem. Even secure boot is not the problem. It's the *possible* inability of computers' owners to *disable or control* secure boot that *may become* a problem.

[quote=KiwiNZ][quote=OldGray_Wolf]*Yes, and the UEFI they use would allow the option to turn Secure Booting off. That is the point I am trying to make.[/quote]*
 			 		 	 	 That feature is included, see screen shot posted earlier in the thread[/quote]

The problem is that the screen shot was for *one reference implementation*. Just as modern BIOSes and UEFIs vary greatly in the features they support, so too will future ones. If manufacturers so desire, it will be trivially easy for them to remove that "off switch." Personally, I think that would be a monumentally stupid business decision unless they're under *heavy* pressure to do so, but I might be missing something, or they might be under such pressure, or they might just be run by poorly-trained monkeys.

Now, moving on a bit, I've been advocating that people contact PC manufacturers to express concern over a possible bungled implementation of secure boot. I've now put up [a Web page](http://www.rodsbooks.com/secure-boot/) on this topic with a very brief and mostly non-technical description of the issue, a generic letter that I've sent to a bakers' dozen PC manufacturers, and the US postal addresses for those manufacturers. If anybody reading this would like to do the same, perhaps my work can save you a bit of effort, since I've tracked down the addresses and laid out some key points in the letter. (I don't recommend sending exactly the same letter since a bunch of different letters are likely to carry more weight than a bunch of identical letters.) I recommend emphasizing business reasons why restricting OS use is a bad business idea -- reduced sales, increased returns, increased support costs when people have problems, etc. Let them know why *they* should care about providing an "off switch" and the ability of owners (use that word a lot!) should be able to control the keys in the firmware. If they believe that denying us control of our computers will cost them money, they'll do the right thing.

---

### Post by KiwiNZ on 2011-09-23
> **del_diablo said:**
> KiwiNZ: You are basically saying you where in a position where you had special made hardware, over contract, with a clausul for the BIOS to be properly fitted, and with at the least 6000 apathic grunts who would not in any situation report that there is some large bugs in the power managment.
And BIOS issues with iPad? please tell me what you are smoking, and why its relevant.

I ran an IT Unit /System with a constant 98% approval rating in Customer Satisfaction surveys. We purchased per RFP's .

Where did I state iPad had a Bios. 

Read and comprehend please

---

### Post by Quadunit404 on 2011-09-23
I feel the need to post in this thread again.

It has already been pointed out that this does not mean the end of dual-booting between Windows and Linux or just wiping Windows and putting Linux on your machine (and risking voiding the warranty if your hardware was pre-built.) You can disable "Secure Boot" in the configuration screen and therefore boot whatever the hell you want. However, I have noticed that some members here have completely missed that and still seem to think this'll somehow cause a "freepocalypse" by effectively locking out Linux from booting on all PCs shipping with Windows 8. It won't. When Windows 8, enter the EFI config screen, disable Secure Boot, boot whatever you wish and see if Microsoft cares. If they don't care what people boot on their PCs now that doesn't automagically mean they'll start caring when Windows 8 arrives.

Personally I am not impressed by Windows 8 so far and am planning on sticking to Windows 7 as long as I possibly can (possibly 2015 or later, maybe even 2020, aka the year Windows 7 dies.) This may change as I had only tried out a developer preview of Windows 8 and it's still an OS in its infancy, but maybe by the time it matures and goes gold that'll change.

To be blunt, I actually felt a few brain cells *die* as I read this thread. This thread as a whole disgusts me.

---

### Post by ilovelinux33467 on 2011-09-23
> **Quadunit404 said:**
> I feel the need to post in this thread again.

It has already been pointed out that this does not mean the end of dual-booting between Windows and Linux or just wiping Windows and putting Linux on your machine (and risking voiding the warranty if your hardware was pre-built.) You can disable "Secure Boot" in the configuration screen and therefore boot whatever the hell you want. However, I have noticed that some members here have completely missed that and still seem to think this'll somehow cause a "freepocalypse" by effectively locking out Linux from booting on all PCs shipping with Windows 8. It won't. When Windows 8, enter the EFI config screen, disable Secure Boot, boot whatever you wish and see if Microsoft cares. If they don't care what people boot on their PCs now that doesn't automagically mean they'll start caring when Windows 8 arrives.

Personally I am not impressed by Windows 8 so far and am planning on sticking to Windows 7 as long as I possibly can (possibly 2015 or later, maybe even 2020, aka the year Windows 7 dies.) This may change as I had only tried out a developer preview of Windows 8 and it's still an OS in its infancy, but maybe by the time it matures and goes gold that'll change.

To be blunt, I actually felt a few brain cells *die* as I read this thread. This thread as a whole disgusts me.

Completely agree.

---

### Post by beew on 2011-09-23
> **Quadunit404 said:**
> I feel the need to post in this thread again.

It has already been pointed out that this does not mean the end of dual-booting between Windows and Linux or just wiping Windows and putting Linux on your machine (and risking voiding the warranty if your hardware was pre-built.) You can disable "Secure Boot" in the configuration screen and therefore boot whatever the hell you want. However, I have noticed that some members here have completely missed that and still seem to think this'll somehow cause a "freepocalypse" by effectively locking out Linux from booting on all PCs shipping with Windows 8. It won't. When Windows 8, enter the EFI config screen, disable Secure Boot, boot whatever you wish and see if Microsoft cares. If they don't care what people boot on their PCs now that doesn't automagically mean they'll start caring when Windows 8 arrives.


The point of many posts is that the "off switch" may not even be available in OEM builds (such as laptops) How do you disable secure boot if there is no switch? The screen shot with the off switch is only one model.

> To be blunt, I actually felt a few brain cells *die* as I read this thread. This thread as a whole disgusts me.
How can that be while you obviously haven't read it?

---

### Post by srs5694 on 2011-09-23
> **Quadunit404 said:**
> You can disable "Secure Boot" in the configuration screen and therefore boot whatever the hell you want. However, I have noticed that some members here have completely missed that and still seem to think this'll somehow cause a "freepocalypse" by effectively locking out Linux from booting on all PCs shipping with Windows 8. It won't. When Windows 8, enter the EFI config screen, disable Secure Boot, boot whatever you wish and see if Microsoft cares.

The problem is that the assertion that you'll be able to disable this feature has not been verified, at least not for *all* computers. Matthew Garrett, whose first blog post started this firestorm, stated in his second blog post on the topic:

[quote=Matthew Garrett]we've already been informed by hardware vendors that some hardware will not have this option[/quote]

"This option" being the option to disable secure boot.

Of course, there's a big question of what "some hardware" means. If that's one model of tablet computer, big whoop. If it's 90% of desktop and laptop computers sold in Best Buy, it's a much bigger deal. Personally, I'd just buy from the remaining 10% (or more likely, build my own from parts); but such a big share of locked-down computers would restrict the choices of people who might not think about such things when they buy computers. What if you buy a computer and then, a year later, you decide you want to give Linux a try, only to find that it won't run on your computer?

Personally, I'm doubtful that this issue will affect a lot of desktop and laptop computers. IMHO, it's more likely that tablets and appliances (DVRs, for instance) will be locked down in this way, as most such devices already are. Still, there's a significant risk of the creep of such a locked-down state into desktop and laptop computers, so IMHO it is worth making noise about this to the manufacturers.

It's also occurred to me that getting retailers on our side might have an effect. If Best Buy or (I gag to say it) Wal-Mart were to demand that computer manufacturers provide an "off switch" for the secure boot feature, it would almost certainly exist in most PCs.

---

### Post by Quadunit404 on 2011-09-23
> **beew said:**
> The point of many posts is that the "off switch" may not even be available in OEM builds (such as laptops) How do you disable secure boot if there is no switch? The screen shot with the off switch is only one model.
I do see your point, and it is possible not all OEMs will include the "off switch" but still, Microsoft is giving OEMs the ability to add the "off switch" if they so choose. While this may limit the amount of OEM-made computers that Linux can be installed on, it's still giving the user free choice if such an option exists.

> **beew said:**
> How can that be while you obviously haven't read it?

Have you any evidence that I did not read this entire thread?

---

### Post by del_diablo on 2011-09-24
> **KiwiNZ said:**
> I ran an IT Unit /System with a constant 98% approval rating in Customer Satisfaction surveys. We purchased per RFP's .

[quote]Where did I state iPad had a Bios. 

I interprented what you said as: "I run a Server ( well It died this week) several desktops, two Laptops and an Ipad, and there exists no BIOS issues on either of them."

Lets have a poke at the real world:
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1)
Severe loss of battery life and power managment. What is the problem? The Kernels regression is that it now reallies on the BIOS to set a proper value for power managment, instead of setting a sane value by itself.
As it then turns out: Very few BIOSES actually provides that value, meaning people LOST battery life over a update, and its a BIOS problem.
In the next few years it will be a "UEFI problem", assuming nothing will change beyond that UEFI is the 2009 version of the 1970 BIOS.
Or have you ever had a issue with hardware losing battery life when running Linux? Thats caused by BIOS too.
And thats the usual ones.
Once in a while you will find that OEMs will sell laptops with obscurely configured hardware, who requires special drivers in order to not overheat.
Or you will find that the wireless on/off switch is set to "off" from boot, and that it requires the OS to send special signals to the computer, so that it will turn on the wireless.

I can name other examples too.
And all of them are caused by the BIOS, and very little else.
Even fan control is done via BIOS, and if it turns out the fans sounds like a jetplane, without any sensible reason(did not happen under Windows), we are yet again looking at broken power managment.

Also: The last laptop I had suffered from 3 problems under Linux:
1. Not all distroes would actually boot
2. There was no power managment in the BIOS, meaning that the AMD CPU ran mostly via hacks under Windows.
3. And it has a wireless problem: The BIOS revision the PC shipped with required the OS to turn on the wireless on each boot, and it had to be turned on via the OS sending a call. A BIOS upgrade fixed that, but it a good example of poorly written BIOS.

---

### Post by del_diablo on 2011-09-24
> **Quadunit404 said:**
> I do see your point, and it is possible not all OEMs will include the "off switch" but still, Microsoft is giving OEMs the ability to add the "off switch" if they so choose. While this may limit the amount of OEM-made computers that Linux can be installed on, it's still giving the user free choice if such an option exists.

So you believe in the free marked?
I think there will exist no such thing as a option, and we will all be forced to build large bricks of desktops.

---

### Post by Lars Noodén on 2011-09-24
Matthew Garrett from Red Hat has posted a follow up, [UEFI secure booting (part 2)](http://mjg59.dreamwidth.org/5850.html), to Microsoft's rebuttal.

---

### Post by beew on 2011-09-24
> **Quadunit404 said:**
> I do see your point, and it is possible not all OEMs will include the "off switch" but still, Microsoft is giving OEMs the ability to add the "off switch" if they so choose. While this may limit the amount of OEM-made computers that Linux can be installed on, it's still giving the user free choice if such an option exists.



See Matthew Garret's rebuttal. 

The choice should not be left to the OEMS, or we can reasonably expect most cheap hardware will not offer such a switch and "enthusiasts" would have to dish out extra bucks for models that come with the switch. This is going to be devastating to Linux growth as most new users don't get exposed to Linux by purchasing specialized hardware to put Linux on,--and there is no need to, this new hardware barrier is completely artificial.

In any case the off switch is not a satisfactory solution even if it is universal implemented. The power to decide safe boot policy should reside in the hands of the end users and not the OEMS and MS. Users should not be forced to opt out of a potentially useful new security feature just to avoid a total lock down.

---

### Post by KiwiNZ on 2011-09-24
> **beew said:**
> See Matthew Garret's rebuttal. 

The choice should not be left to the OEMS, or we can reasonably expect most cheap hardware will not offer such a switch and "enthusiasts" would have to dish out extra bucks for models that come with the switch. This is going to be devastating to Linux growth as most new users don't get exposed to Linux by purchasing specialized hardware to put Linux on,--and there is no need to, this new hardware barrier is completely artificial.

In any case the off switch is not a satisfactory solution even if it is universal implemented. The power to decide safe boot policy should reside in the hands of the end users and not the OEMS and MS. Users should not be forced to opt out of a potentially useful new security feature just to avoid a total lock down.

The choice will be with the end user, buy a machine with a switch in the UEFI and disable secure boot.... simple really. This allows those who want secure boot the ability to have with out being dictated to by a <1% market share.

---

### Post by del_diablo on 2011-09-24
KiwiNZ: The "freedom to buy another brand" is something that does not exist in reality.

---

### Post by KiwiNZ on 2011-09-24
> **del_diablo said:**
> KiwiNZ: The "freedom to buy another brand" is something that does not exist in reality.

Say what now????????????????????????????

Acer
Toshiba
Dell
HP
Gateway
Sony
Apple

Are all one brand now, damm when did that happen?

---

### Post by del_diablo on 2011-09-24
And lets say all of those say "We lock boot".
Then what?

---

### Post by Spice Weasel on 2011-09-24
> **del_diablo said:**
> And lets say all of those say "We lock boot".
Then what?

> **Spice Weasel said:**
> Or you could, you know, use LILO or the Microsoft boot loader.

^ This.

---

### Post by del_diablo on 2011-09-24
And then we have lost the game.

---

### Post by KiwiNZ on 2011-09-24
> **del_diablo said:**
> And lets say all of those say "We lock boot".
Then what?

What if the World was flat, what if Columbus got lost.

Innovate to complete, crying no body likes me gets one nowhere.

---

### Post by MonolithImmortal on 2011-09-24
> **del_diablo said:**
> And then we have lost the game.
Politely explain to me how we lost the game if we use a BSD licensed boot loader? Hint, you cant.

---

### Post by beew on 2011-09-24
> **KiwiNZ said:**
> 
Innovate to complete, crying no body likes me gets one nowhere.

Please stop spouting mindless slogans and take a look at reality. It is not that Linux cannot "innovate and compete" on technical ground, we are complaining because MS is trying to massively rig the game with its monopolistic clout, it is MS that fails to "compete and innovate" on an equal playing field. I am sure Linux welcome FAIR competition. Thankfully law makers in places like the EU would have a more nuanced view on this than yours.

---

### Post by Legendary_Bibo on 2011-09-24
> **beew said:**
> Please stop spouting mindless slogans and take a look at reality. It is not that Linux cannot "innovate and compete" on technical ground, it is because the game is massively rigged because of MS's monopolistic clout. Thankfully law makers in places like the EU would have a more nuanced view on this than yours.

He's not just spouting off mindless slogans. Ubuntu is one of Linux's major distributions and look at what they're doing now, they're copying  OS X and Windows. Look at the mess Gnome 3 is. That's not sensible. With Linux it's 2 steps forward 3 steps back, and now lets imitate our competition 99% of the way (with that last 1% being the essential final touches to be presentable), and then after we copy them lets slander them.

---

### Post by KiwiNZ on 2011-09-24
> **beew said:**
> Please stop spouting mindless slogans and take a look at reality. It is not that Linux cannot "innovate and compete" on technical ground, it is because the game is massively rigged because of MS's monopolistic clout. Thankfully law makers in places like the EU would have a more nuanced view on this than yours.

Thankfully many will see your post and mindset as nonsense. That is why Linux makes advances, it is because some believe my mindless slogan and believe we can innovate to compete as opposed to "Please dont hurt me Mr MS, I will cry and give up if your product gets better".

Simply put Linux can progress if innovation is the driver, it wont if crying is the driver.

---

### Post by beew on 2011-09-24
> **Legendary_Bibo said:**
> He's not just spouting off mindless slogans. Ubuntu is one of Linux's major distributions and look at what they're doing now, they're copying  OS X and Windows. Look at the mess Gnome 3 is. That's not sensible. With Linux it's 2 steps forward 3 steps back, and now lets imitate our competition 99% of the way (with that last 1% being the essential final touches to be presentable), and then after we copy them lets slander them.

Well that is your opinion, people have been arguing over UI design on many threads and the gist is that no one is truly original (is Windows8 copying Gnome3? How is Compiz copying anyone?) It belongs to a different thread.

P.S. I read that Windows8 maybe able to run off live usb, is that ground against MS for copycating Linux? How about app stores in Apple and MS?

---

### Post by sffvba[e0rt on 2011-09-24
This topic is very hot at the moment across the Internet.  I hope we can stick closer to the core and start drifting less to the fringes (Linux vs Microsoft vs Etc.) and keep this thread open...


404

---

### Post by beew on 2011-09-24
> **KiwiNZ said:**
> Thankfully many will see your post and mindset as nonsense. That is why Linux makes advances, it is because some believe my mindless slogan and believe we can innovate to compete as opposed to "Please dont hurt me Mr MS, I will cry and give up if your product gets better".

Simply put Linux can progress if innovation is the driver, it wont if crying is the driver.

Repeating doesn't make your point (?) more valid. It has nothing to do with reality and I will ignore your posts until you have a substantial point.

---

### Post by KiwiNZ on 2011-09-24
> **beew said:**
> Repeating doesn't make your point (?) more valid. It has nothing to do with reality and I will ignore your posts until you have a substantial point.

Thank you

---

### Post by Legendary_Bibo on 2011-09-24
> **beew said:**
> Repeating doesn't make your point (?) more valid. It has nothing to do with reality and I will ignore your posts until you have a substantial point.

Translation: I will only respond to you if you share my views.

---

### Post by beew on 2011-09-24
> **Legendary_Bibo said:**
> Translation: I will only respond to you if you share my views.

I responded to you even though you don't share my view. I just don't want to waste my time on useless discussions.

---

### Post by srs5694 on 2011-09-24
> **MonolithImmortal said:**
> Politely explain to me how we lost the game if we use a BSD licensed boot loader? Hint, you cant.

Assume for the moment a worst-case scenario, at least for an individual computer: The secure boot feature cannot be turned off and you as the owner have no ability to add keys to the "white list" of trusted keys. This means that you can only boot using software that the computer's vendor has approved, or at least software that's released by an organization that the computer's vendor has chosen to trust. If only Microsoft's keys are in the firmware, then Microsoft controls the boot process for that computer. You can try any boot loader you like, but if Microsoft hasn't signed it, it won't boot.

Note that Microsoft's boot loader can't load a Linux kernel, even today. It *can* chainload to another boot loader, at least on BIOS systems (I don't know if this is true under UEFI). Under secure boot, though, if Microsoft's boot loader can chainload to another boot loader, and if that feature can be configured by software run on Windows, then the secure boot feature becomes useless for its intended purpose, since a malware author could easily configure the Windows boot loader to redirect the boot process to some piece of malware. I don't think Microsoft is likely to release software that's so phenomenally poorly designed as to permit this, at least not intentionally. (Maybe somebody could find a bug that would permit such a thing, but then Microsoft would issue a bug fix.)

The license issue comes into play if PC vendors start accepting license keys from Canonical, Red Hat, and others. In such a situation, according to what I've read, the GPL v3 would require that the license key used to sign the binary be released publicly, which would mean that any malware author could use it, so of course no PC manufacturer with half a brain would accept such a key. Using some other license might get around this issue, but there's still the major hurdle that there are a significant number of PC manufacturers and a significant number of Linux distribution vendors, and you'd need agreements between all of them to enable the sort of full compatibility we've got today. This seems unlikely to happen. From the PC manufacturer's perspective, it's a lot of paperwork and verification of the security and trustworthiness of a lot of keys, no one of which will be used by many users. From the Linux distributors' point of view, it's a lot of paperwork and hassle, and all but a few of the bigger and more commercial distributions probably lack the financial resources to do this.

It's also unclear to me whether a PC hardware vendor would accept a key that's used to sign a boot loader such as GRUB as it exists today, even ignoring license issues. The problem is that GRUB is highly configurable; it'll boot anything within its technical ability to boot, so once it's signed, a malware author could use the signed binary to boot a customized micro-Linux that does malware-ish things. Similar comments apply to all other Linux-capable boot loaders. Maybe there's a technical way around this (I admit I know next to nothing about how secure boot signs binaries or what sorts of policies PC vendors will use to accept or reject keys), but it seems like it at least might be a hurdle that will take resources to overcome.

So, to sum up, *if* secure boot is commonly implemented in the sort of "dumbed-down" way that many people here fear, the afflicted computers will become Microsoft-only boxes. Perhaps some of the bigger Linux distributions will develop a new locked-down bootloader and get keys accepted with some of the major PC manufacturers, but maybe not. The big question is how common such locked-down PCs will be. If most PC manufacturers give owners the right to shut off secure boot and/or to manage the keys themselves, then would-be Linux users will be able to run Linux much as they can now. If most PC manufacturers don't provide these capabilities, then Linux users will have to search out and buy specific models. This might not be so bad for people who know they want to use Linux when they go computer shopping, but people who decides to try Linux some time after buying their computers might find that Linux won't run on the computers that they nominally own.

---

### Post by Dr. C on 2011-09-24
> **KiwiNZ said:**
> Thankfully many will see your post and mindset as nonsense. That is why Linux makes advances, it is because some believe my mindless slogan and believe we can innovate to compete as opposed to "Please dont hurt me Mr MS, I will cry and give up if your product gets better".

Simply put Linux can progress if innovation is the driver, it wont if crying is the driver.

Innovation and been competitive while essential for the success of GNU / Linux  is not by it self enough when dealing with a competitor that has over 90% market share ***worldwide***. This is a level of monopolistic control unheard of in any other industry. So yes anti trust action will very likely also have to be part of the picture. It is also very likely that the EU is where the anti trust action will take place. There is a reason for the need for anti trust legislation regardless of the product in question being an operating system or a car.

It is in fact a testament to the phenomenal innovation and competitiveness of GNU / Linux that we are where we are when faced with such overwhelming anti competitive odds that by the way would not be tolerated in any other industry.

---

### Post by Spice Weasel on 2011-09-24
> **Dr. C said:**
> Innovation and been competitive while essential for the success of GNU / Linux  is not by it self enough when dealing with a competitor that has over 90% market share ***worldwide***. This is a level of monopolistic control unheard of in any other industry. So yes anti trust action will very likely also have to be part of the picture. It is also very likely that the EU is where the anti trust action will take place. There is a reason for the need for anti trust legislation regardless of the product in question being an operating system or a car.

It is in fact a testament to the phenomenal innovation and competitiveness of GNU / Linux that we are where we are when faced with such overwhelming anti competitive odds that by the way would not be tolerated in any other industry.

You are stuck in 1998.

By the way, it's a monoculture, not monopoly.

If Microsoft had a monopoly Linux and OSX would not exist.

---

### Post by MacUntu on 2011-09-24
We need "Ubuntu Unfriendly" - a public list of OEMs that don't allow their users freedom. >:****)

---

### Post by sffvba[e0rt on 2011-09-24
[s]Thread closed until further notice!

Needs some cleaning up...[/s]


I have removed a few of the more "obvious" trolling posts of the last few pages.  I don't have the time or the patience to do this again.  Next time I won't only move a few posts to the jail :/


404

---

### Post by KiwiNZ on 2011-09-24
What I am trying to say here , we should not be running off to the European Court or the US DOJ,from that there is no winners. 
We should be running off to the development labs and produce products that consumers and Enterprises want , that way user demand will drive the market place.

---

### Post by beew on 2011-09-24
> **KiwiNZ said:**
> What I am trying to say here , we should not be running off to the European Court or the US DOJ,from that there is no winners. 
We should be running off to the development labs and produce products that consumers and Enterprises want , that way user demand will drive the market place.

How would consumers know about Linux if they can't even boot from it?

Antitrust laws exist for a reason, that is to prevent monopolistic entities like MS from denying competitors access to consumers in the first place.

---

### Post by dave01945 on 2011-09-24
i don't know if this has been mentioned yet or not but microsoft have said that *secure boot* needs to be *enabled by default* to have windows 8 certified on the machine.

They have not said it cannot be switched off that decision is down to the OEM's

[http://www.omgubuntu.co.uk/2011/09/microsoft-attempt-address-windows-8-linux-worries/](http://www.omgubuntu.co.uk/2011/09/microsoft-attempt-address-windows-8-linux-worries/)

---

### Post by anewguy on 2011-09-24
> **KiwiNZ said:**
> I have stated in the past I make spelling errors etc because i type vast amounts of script one handed due to my disability...... Learn some manners and we will get on better.:rolleyes::mad:

That was a a cheap shot on their part - I'm disabled as well so I understand.  Maybe it was unintentional in terms of the insult though - you never quite know.  Just sorry it happened to you.

My main concern with all of this is that *IF* Microsoft requires this as part of their licensing agreement with the manufacturers you are essentially going to locked in to Microsoft.  I have nothing against them - I still run XP dual-boot with Ubuntu on my desktop, and Windows 7 dual boot with Ubuntu on my laptop.  *IF* this gets to the point that it is a requirement for licensing, then it does into the legal area of forcing people to only use your OS.  As a person who worked in tech for some large companies for many years, I see-saw on this, because a company should be able to dictate rules for their product - especially when they are licensing it.  But to do this to force your competitors out of business is where gets shaky to me.  We have ANSI, IEEE, etc., so why can't (or perhaps we already do and I don't know about it) a separate group that oversees things like this so that the playing field is even?

As always, understand I'm not arguing with anyone - just exchanging thoughts is all!  ;)

dave ;)

---

### Post by Paqman on 2011-09-24
I'd be very surprised if OEMs didn't include the option to switch off secure boot. Some may not, but those that do will have a (small) competitive advantage against them. That advantage would be largest if most OEMs weren't including the option to boot rogue OSes. So the likelihood of at least one OEM doing it is extremely high IMO, especially in those products catering to parts of the market likely to be building from scratch and installing their own OS (eg: car PCs, HTPCs, barebones servers, etc)

Including the option costs them close to zero, while not including it certainly has a non-zero cost, even if admittedly rather small.

Personally I think history will prove this to be yet another chicken little moment from the Linux fraternity. When will we learn?

---

### Post by MonolithImmortal on 2011-09-24
It seems like the solution is for every distro to use a bsd licensed  bootloader, get it signed, and then have MS's boot loader chain load to  it. WORST CASE SCENARIO.

I still don't know what all the fuss is about.

---

### Post by Dr. C on 2011-09-24
> **Spice Weasel said:**
> You are stuck in 1998.

By the way, it's a monoculture, not monopoly.

If Microsoft had a monopoly Linux and OSX would not exist.

One does not anywhere near Microsoft's market share to trigger anti trust legislation. In Canada it can be as low as 35% for "market dominance" 60% if multiple companies are involved. To place things in perspective. Net Applications gives 92.9% market share to Microsoft for the desktop. [http://marketshare.hitslink.com/operating-system-market-share.aspx?]("http://marketshare.hitslink.com/operating-system-market-share.aspx?") W3Schools which historically has the highest percentage for GNU / Linux places Microsoft's market share at over 85% [http://www.w3schools.com/browsers/browsers_os.asp]("http://www.w3schools.com/browsers/browsers_os.asp"). So yes the situation is better that in 1998, but a drop from 97% to 93% does materially change the issue here when the threshold is in the 35% to 60% range.

---

### Post by David Andersson on 2011-09-24
What I think will happen:

You go to the IT guy at a school or public institution and suggest Linux. You have prepared a live-USB with educational software and some bling. Last year they would have been hesitant at first. You show them the software and the bling. They have a printer or webcam? Plug it in and viola, no hassle downloading drivers or anything. It just works. They are impressed. They'll not switch right now, of course, but in the back of their mind, they know there is an promising alternative to look in to.

Next year, you ask if you can demo this live-USB. Okay. The boot screen beeps and says "Loading of illegal or harmful software has been prevented. Microsoft have saved you." Now, the IT guy has other things to do and ask you to leave. In the back of their mind, they associate Linux with "illegal" and "dangerous", and they associate Microsoft with comfy and safety.

The legislators will love it too. Computers will handle electronic money, electronic voting, many things important that must not be tampered with. Legislators don't know how encryption works, so they think authorities need to supervise all computer devices: desktops, laptops, phones. They will want to make it illegal to connect a jailbroken computer to the internet. Microsoft will fulfill their dreams.

I am not very optimistic.

---

### Post by el_koraco on 2011-09-24
> **Paqman said:**
>  When will we learn?

This is a special case. The Microsoft haters can howl at the big bad wolf, and the Linux haters have a nice "argument" against the GPL. It's a win-win for everybody, you don't get flame war opportunities like this every day.

---

### Post by jerenept on 2011-09-24
> **David Andersson said:**
> What I think will happen:

You go to the IT guy at a school or public institution and suggest Linux. You have prepared a live-USB with educational software and some bling. Last year they would have been hesitant at first. You show them the software and the bling. They have a printer or webcam? Plug it in and viola, no hassle downloading drivers or anything. It just works. They are impressed. They'll not switch right now, of course, but in the back of their mind, they know there is an promising alternative to look in to.

Next year, you ask if you can demo this live-USB. Okay. The boot screen beeps and says "Loading of illegal or harmful software has been prevented. Microsoft have saved you." Now, the IT guy has other things to do and ask you to leave. In the back of their mind, they associate Linux with "illegal" and "dangerous", and they associate Microsoft with comfy and safety.

The legislators will love it too. Computers will handle electronic money, electronic voting, many things important that must not be tampered with. Legislators don't know how encryption works, so they think authorities need to supervise all computer devices: desktops, laptops, phones. They will want to make it illegal to connect a jailbroken computer to the internet. Microsoft will fulfill their dreams.

I am not very optimistic.

Or, use a BSD-licensed bootloader, include the keys and, voila! None of these problems are even considered!

---

### Post by dave01945 on 2011-09-24
> **jerenept said:**
> Or, use a BSD-licensed bootloader, include the keys and, voila! None of these problems are even considered!

or go into the UEFI setting and disable secure boot then proceed as normal

---

### Post by jerenept on 2011-09-24
> **dave01945 said:**
> or go into the UEFI setting and disable secure boot then proceed as normal

Or this. Why does everything have to be a conspiracy theory?

---

### Post by srs5694 on 2011-09-24
> **Paqman said:**
> I'd be very surprised if OEMs didn't include the option to switch off secure boot. Some may not, but those that do will have a (small) competitive advantage against them.

On the face of it, I tend to agree that it would be a very bad business decision to omit this option; however, part of the reason this firestorm began is the claim by Matthew Garrett in his [second blog post on the subject](http://mjg59.dreamwidth.org/5850.html) that "we've already been informed by hardware vendors that some hardware will not have this option" (that is, to disable secure boot). Matthew Garrett is a Red Hat employee, so I take his "we" to refer to communications between Red Hat and hardware vendors. The question is just what "some" means -- it could be one or two models from rinky-dink manufacturers or 99% of all PCs sold at retail.

> So the likelihood of at least one OEM doing it is extremely high IMO, especially in those products catering to parts of the market likely to be building from scratch and installing their own OS (eg: car PCs, HTPCs, barebones servers, etc)

"At least one" doing the right thing is a ridiculously low bar for acceptability. If Linux is to remain competitive, particularly as an option in the home market, it must be able to be installed to the vast majority of PCs. How many people here tried Linux for the first time on a computer that was purchased explicitly to run Linux? Not many, I'd wager. If Joe User can't run Linux on a box originally purchased with Windows, with no original intent to ever run anything else, then Linux loses out big time.

[quote=MonolithImmortal]It seems like the solution is for every distro to use a bsd licensed   bootloader, get it signed, and then have MS's boot loader chain load to   it. WORST CASE SCENARIO.[/QUOTE]

You're glossing over the signing issue. In the worst-case scenario, there are two roads to getting software signed to work on Brand X computers:


[list]
[*]Get Microsoft to sign it.
[*]Get Brand X to sign it.
[/list]


I'd be flabbergasted if Microsoft would be willing to sign a Linux boot loader, especially one that's capable of running *any* distribution's kernel.

That leaves the PC manufacturers themselves. Some of them might be willing to sign Linux boot loaders, but given the number of distributions and the security hurdles to be overcome to ensure that any given boot loader can't be used to load malware, this seems like a major obstacle. Note I'm not saying it's impossible on a case-by-case basis, but it's nowhere near the trivial task you seem to be suggesting. If I were a PC manufacturer being asked to sign a Linux distribution's boot loader, I'd be asking questions like "can the boot loader load a kernel you didn't create" and "can software run on Linux modify the boot options to run malware rather than the usual startup scripts in your distribution?" The answers to these questions with current Linux boot loaders are both "yes," and "yes" answers to these questions would make me, Mr. PC Vendor, *very* reluctant to sign the boot loader. In other words, to get Linux boot loaders signed, the Linux boot process must likely become much more restrictive than it is now.

Furthermore, there's the fact that there are many different PC brands, so a distribution vendor would have to go through the whole process with each and every PC brand. If there were a centralized authority for getting keys signed so that they ended up in every PC, this problem would become more manageable.

The bottom line is this: *If* a PC is locked down with secure boot and *if* the owner of the computer cannot override those settings, then the owner of the computer does *not* control the computer. The owner is at the mercy of those who control the signing keys to determine what software the computer runs. Only if the computers' owners can disable the feature or add keys themselves do the computers truly belong to the people who nominally own them.

---

### Post by srs5694 on 2011-09-24
> **jerenept said:**
> Or, use a BSD-licensed bootloader, include the keys and, voila! None of these problems are even considered!

***If you can!*** That's the whole point! There's no guarantee that you'll have the ability to do this on your own computer!

[quote=dave01945]or go into the UEFI setting and disable secure boot then proceed as normal[/quote]

Ditto. There is no guarantee that manufacturers will include these features. They might. *I* think it would be stupid of them not to do so, but *I'm* not the one who's running PC companies. [Matthew Garret has claimed that he's heard at least "some" computers will lack this ability.](http://mjg59.dreamwidth.org/5850.html) Until we know what "some" means, we won't be able to judge the severity of the threat.

---

### Post by jerenept on 2011-09-24
> **srs5694 said:**
> 
I'd be flabbergasted if Microsoft would be willing to sign a Linux boot loader, especially one that's capable of running *any* distribution's kernel.

They will if they don't want to be beaten over the head by the DOJ. As long as it's not going to compromise the safety of the system (that is, releasing the source of the keys to the public), they have no authority to refuse signing the bootloader.

---

### Post by Copper Bezel on 2011-09-24
[QUOTE=el_koraco]This is a special case. The Microsoft haters can howl at the big bad wolf, and the Linux haters have a nice "argument" against the GPL. It's a win-win for everybody, you don't get flame war opportunities like this every day.[/QUOTE]
Anxieties as much as any "hate," if I can say so, if the PC market is to continue to follow the mobile market.

---

### Post by el_koraco on 2011-09-24
> **Copper Bezel said:**
> Anxieties as much as any "hate," if I can say so, if the PC market is to continue to follow the mobile market.

Hardly, as I've said before, the difference is that a lot of professional software is booted separately, the market is wider and more complicated. IT guys don't necessarily want to fuddle around to much. Of course, If Microsoft wants Malwarebytes and others to take a breather and rely on MSE and Reset and Rewhatever, well... :D

---

### Post by thatguruguy on 2011-09-24
> **KiwiNZ said:**
> What I am trying to say here , we should not be running off to the European Court or the US DOJ,from that there is no winners. 
We should be running off to the development labs and produce products that consumers and Enterprises want , that way user demand will drive the market place.

I understand the point you're making.  However, there is at least *some* historical precedent for lock-outs hindering innovation.  In particular, it's instructive to look at the history of the telephone in the US.  It took governmental intervention to force AT&T to allow people to hook non-Western Electric phones up to the phone lines, which led to the creation of neat things like fax machines, the first dial-up modems, and wireless phones.  Innovation doesn't mean anything without access to the infrastructure that the innovative technology needs.

---

### Post by anewguy on 2011-09-24
But the sky IS falling......and it's a big plot by my neighbors.....oh wait a minute - my glasses are just dirty!  ;)

Dave ;)

---

### Post by srs5694 on 2011-09-24
> **jerenept said:**
> They will if they don't want to be beaten over the head by the DOJ. As long as it's not going to compromise the safety of the system (that is, releasing the source of the keys to the public), they have no authority to refuse signing the bootloader.

What makes you think that Microsoft is required to sign boot loaders from all comers? AFAIK, there's no law that states such a thing. Speculations about antitrust lawsuits are all well and good, but Microsoft has proven time and again that they aren't afraid of the DOJ, so I wouldn't count on the threat of a government antitrust lawsuit to make them sign random distributions' boot loaders. If it does come to a lawsuit, then it'll take years, if not decades, before the issue is resolved, by which time the computer industry will have moved on to other battles, and Microsoft will have won for the intervening time.

Also, as I've stated before, a Linux boot loader as currently written most certainly *would* "compromise the safety of the system" -- its configuration file could be trivially modified to point to a malware-infected Linux kernel, or to a Linux kernel that's configured to run malware. Said malware could then write stuff to the Windows partition. A Linux boot loader that's really fully secure from a Microsoft perspective would necessarily rely on a lot of security measures in Linux that are rather uncommon and that would be restrictive to people who don't want that level of security.

---

### Post by Copper Bezel on 2011-09-24
> **el_koraco said:**
> Hardly, as I've said before, the difference is that a lot of professional software is booted separately, the market is wider and more complicated. IT guys don't necessarily want to fuddle around to much. Of course, If Microsoft wants Malwarebytes and others to take a breather and rely on MSE and Reset and Rewhatever, well... :D

Yeah, but the enterprise sector is different from the home PC market, too.

---

### Post by el_koraco on 2011-09-24
> **Copper Bezel said:**
> Yeah, but the enterprise sector is different from the home PC market, too.

So you'll buy a Thinkpad. You know you want one.

---

### Post by Copper Bezel on 2011-09-24
Can't argue with that. = )

---

### Post by Merk42 on 2011-09-25
> **KiwiNZ said:**
> What I am trying to say here , we should not be running off to the European Court or the US DOJ,from that there is no winners. 
We should be running off to the development labs and produce products that consumers and Enterprises want , that way user demand will drive the market place.
Be more like Firefox (and Chrome) rather than Opera.

---

### Post by Dr. C on 2011-09-25
> **Merk42 said:**
> Be more like Firefox (and Chrome) rather than Opera.

Both the browser and and music player anti trust cases against Microsoft are very different from the SAMBA and this potential case in that innovation and competitiveness alone could and did address the problem. In both of these cases Microsoft did not block the competitive products from being installed in Windows. 

In the SAMBA case on the other hand Microsoft did attempt to block interoperability and no amount of innovation and competitiveness on SAMBA's part could change that. In this case no matter how innovative and  competitive GNU / Linux becomes, if is not allowed to boot, how can it possibly compete? These are critical and very important differences.

---

### Post by Paqman on 2011-09-25
> **srs5694 said:**
> On the face of it, I tend to agree that it would be a very bad business decision to omit this option; however, part of the reason this firestorm began is the claim by Matthew Garrett in his [second blog post on the subject](http://mjg59.dreamwidth.org/5850.html) that "we've already been informed by hardware vendors that some hardware will not have this option" (that is, to disable secure boot). Matthew Garrett is a Red Hat employee, so I take his "we" to refer to communications between Red Hat and hardware vendors. The question is just what "some" means -- it could be one or two models from rinky-dink manufacturers or 99% of all PCs sold at retail.

I think this means we need to wait for the OEMs themselves to clarify their position on the matter. It's good that a big distro with some actual clout like Red Hat is already talking to OEMs about this, we're more likely to successfully plead our case if we get in early.


> 
"At least one" doing the right thing is a ridiculously low bar for acceptability.

Agreed, but I mentioned it to prove my point about competitive advantage acting in our favour, rather than as an expectation of what would happen.

> 
If Linux is to remain competitive, particularly as an option in the home market, it must be able to be installed to the vast majority of PCs.

I wouldn't say Linux does compete with Windows in the home market, except in certain niche areas. It competes *very* effectively in the server market. Linux is primarily a server OS that is also used by a small number of weirdos as a desktop. I say this as an avid desktop Linux fan, by the way. I just think we have to be realistic about how many people actually want to install Linux on their desktop, who those people are, and Linux's track record of attracting anybody new.

Actual worst case scenario is that we'll all end up running our desktops on server hardware, as you can guarantee those will always be able to boot Linux. As you say, that would hurt opportunistic adoption of Linux by the curious, but I don't think we should kid ourselves that we're missing out on the widespread adoption of Linux by home users who originally bought Windows machines.

---

### Post by Lars Noodén on 2011-09-25
Scroll down to "These are the facts"

[http://www.zdnet.com/blog/open-source/microsoft-to-stop-linux-older-windows-from-running-on-windows-8-pcs/9589](http://www.zdnet.com/blog/open-source/microsoft-to-stop-linux-older-windows-from-running-on-windows-8-pcs/9589)

 *    "Windows 8 certification requires that hardware ship with UEFI secure boot enabled."
 *    "Windows 8 certification does not require that the user be able to disable UEFI secure boot, and we’ve already been informed by hardware vendors that some hardware will not have this option."
 *    "Windows 8 certification does not require that the system ship with any keys other than Microsoft’s."
 *    "A system that ships with UEFI secure boot enabled and only includes Microsoft’s signing keys will only securely boot Microsoft operating systems."

---

### Post by beew on 2011-09-25
> **Paqman said:**
> 

I wouldn't say Linux does compete with Windows in the home market, except in certain niche areas. It competes *very* effectively in the server market. Linux is primarily a server OS that is also used by a small number of weirdos as a desktop. I say this as an avid desktop Linux fan, by the way. I just think we have to be realistic about how many people actually want to install Linux on their desktop, who those people are, and Linux's track record of attracting anybody new.
.

I find that a very defeatist attitude. If Mark Shuttleworth thinks that Linux will never compete with Windows on the desktop Ubuntu would not exist at all and Linux would still be a hacker/geek OS (this is not the case since Ubuntu is the most widely used Linux distro and it is aimed at everyday users rather than hackers) I would have never discovered Linux if I were not able to install Ubuntu on my hand me down old laptop about a year ago where Windows XP was pretty useless, that was how I got started and I think that is true for many here ( a large number if not the majority) as well.

---

### Post by Paqman on 2011-09-25
> **beew said:**
> I find that a very defeatist attitude.

Only if you consider the status quo to be a defeat. Personally I find Linux to be a really nice, usable, friendly system that has tons of great apps. I don't really see a problem. Wider adoption would be great, but I think the Linux community has proved that it's not essential to producing a good quality OS with a good application ecosystem.

I'm not advocating the whole elitist thing about not wanting wider adoption, either. I'm just of the opinion that wider adoption isn't likely.

> 
If Mark Shuttleworth thinks that Linux will never compete with Windows on the desktop Ubuntu would not exist at all

Mark Shuttleworth is entitled to his opinion. I admire his optimism and willingness to put his money where his mouth is, but I don't agree that bug #1 is going to get squashed any time soon. I think he's likely to lose a lot of money on desktop Linux, which is why it's nice to see Canonical making some inroads into the server biz, because that's what will keep the company afloat.

---

### Post by srs5694 on 2011-09-25
> **Paqman said:**
> I think this means we need to wait for the OEMs themselves to clarify their position on the matter. It's good that a big distro with some actual clout like Red Hat is already talking to OEMs about this, we're more likely to successfully plead our case if we get in early.

Agreed, but with an important twist: If we wait around passively for PC manufacturers to make a decision, then they might make the wrong decision out of ignorance, pressure from Microsoft, or whatever. That's why I've advocated in this thread that individuals contact PC manufacturers to demand that they include both an "off switch" for the secure boot feature and the ability for users to add and remove keys from the firmware. (Either feature alone is useful, but only the combination of both gives users full control over their computers and all their features.) Red Hat talking to PC manufacturers is all well and good, but those manufacturers must know that at least some of their customers are scrutinizing their decisions on this matter. See [this page of mine](http://www.rodsbooks.com/secure-boot/index.html) for my reasoning on the topic, including an open letter and a baker's dozen PC manufacturer addresses.

> I wouldn't say Linux does compete with Windows in the home market, except in certain niche areas. It competes *very* effectively in the server market. Linux is primarily a server OS that is also used by a small number of weirdos as a desktop.

I didn't use the word "competitive" in the sense of "has significant market share"; I used the word in the sense of "is a viable alternative." In that sense, Linux has been competitive with Windows for years, but if the secure boot feature is implemented in a way that's restrictive to computer owners, Linux will become non-competitive very quickly -- and *not* because of any flaw in Linux.

> Actual worst case scenario is that we'll all end up running our desktops on server hardware, as you can guarantee those will always be able to boot Linux. As you say, that would hurt opportunistic adoption of Linux by the curious, but I don't think we should kid ourselves that we're missing out on the widespread adoption of Linux by home users who originally bought Windows machines.

I'm not arguing that Linux has, should have, or ever will have significant market share. That's irrelevant; it's about the right of the *owners* of computer hardware to *choose* what software they want to run. In terms of the Linux community, however small it is, if secure boot is implemented poorly, the community will suffer, but shrugging it off as unimportant because the community is small is to accept an injustice.

---

### Post by mmsmc on 2011-09-25
> **Dr. C said:**
> The real threat here is that Windows 8 Logo computer will prevent GNU / Linux from booting as part of the "secure boot" process. When combined with anti circumvention legislation it could even make it illegal in certain countries to install  GNU / Linux on certain computers since one would have to crack the DRM in the UEFI boot loader in order to boot an "untrusted" binary. The legal situation would not be different for example to cracking the DRM on a PS3 in order to install GNU / Linux on it. 

Here are some articles with some the early warning signs. 

[http://www.itwire.com/opinion-and-analysis/open-sauce/49889-will-windows-8-succeed-in-locking-out-gnulinux](http://www.itwire.com/opinion-and-analysis/open-sauce/49889-will-windows-8-succeed-in-locking-out-gnulinux) 
[UEFI Secure Booting by Mathew Garrett ]("http://mjg59.dreamwidth.org/5552.html") 
[UEFI and "secure boot"]("http://lwn.net/Articles/447381/")


well, if this happens then i say good luck to them, hacking groups will have fun with microsoft

---

### Post by Dr. C on 2011-09-25
> **mmsmc said:**
> well, if this happens then i say good luck to them, hacking groups will have fun with microsoft

There is doubt in my mind that that hacking groups would have a field day with Microsoft, if what has happened to SONY recently is any indication. The more relevant question in my mind is will people be sued civilly and / or prosecuted criminally for installing GNU / Linux on hardware that they own?

---

### Post by KiwiNZ on 2011-09-25
> **Dr. C said:**
> There is doubt in my mind that that hacking groups would have a field day with Microsoft, if what has happened to SONY recently is any indication. The more relevant question in my mind is will people be sued civilly and / or prosecuted criminally for installing GNU / Linux on hardware that they own?

No

When you buy a PC/Laptop you are purchasing outright an asset, you are not purchasing "rights to use as set buy an EULA"

---

### Post by Dr. C on 2011-09-25
> **KiwiNZ said:**
> No

When you buy a PC/Laptop you are purchasing outright an asset, you are not purchasing "rights to use as set buy an EULA"

... and how is this different from installing GNU / Linux a PS3 for example after breaking the security on the PS3's boot loader in order to install GNU / Linux. Anti circumvention laws do not make a distinction.

---

### Post by Quadunit404 on 2011-09-25
> **Dr. C said:**
> ... and how is this different from installing GNU / Linux a PS3 for example after breaking the security on the PS3's boot loader in order to install GNU / Linux. Anti circumvention laws do no make a distinction.

If Sony didn't want you to put Linux on the PS3, then why did they let people do that? Better yet, why did they promote the *hell* out of said feature?

---

### Post by KiwiNZ on 2011-09-25
> **Dr. C said:**
> ... and how is this different from installing GNU / Linux a PS3 for example after breaking the security on the PS3's boot loader in order to install GNU / Linux. Anti circumvention laws do not make a distinction.

Sony made and promoted the the Linux capability on a PS3, they later stopped providing it themselves due to lack of demand and poor performance.

---

### Post by Dr. C on 2011-09-25
> **Quadunit404 said:**
> If Sony didn't want you to put Linux on the PS3, then why did they let people do that? Better yet, why did they promote the *hell* out of said feature?

They took legal action against those who provided the necessary tools to install GNU / Linux on the PS3. Here is an example: [Sony Lawyers Expand Dragnet, Targeting Anybody Posting PlayStation 3 Hack]("http://www.wired.com/threatlevel/2011/02/sony-lawsuit-factory/")

---

### Post by KiwiNZ on 2011-09-25
> **Dr. C said:**
> They took legal action against those who provided the necessary tools to install GNU / Linux on the PS3. Here is an example: [Sony Lawyers Expand Dragnet, Targeting Anybody Posting PlayStation 3 Hack]("http://www.wired.com/threatlevel/2011/02/sony-lawsuit-factory/")

"Sony’s aggressive pretrial discovery demands come in its lawsuit against George Hotz. The [21-year-old New Jersey hacker]("http://en.wikipedia.org/wiki/George_Hotz"),  who is well known in the jailbreaking community, published the finished  PlayStation 3 code and a how-to YouTube video last month. _[SIZE=2]The code  enables the Playstation 3 to play pirated and homebrewed games."[/SIZE]_

There in is the difference.

---

### Post by Quadunit404 on 2011-09-25
> **Dr. C said:**
> They took legal action against those who provided the necessary tools to install GNU / Linux on the PS3. Here is an example: [Sony Lawyers Expand Dragnet, Targeting Anybody Posting PlayStation 3 Hack]("http://www.wired.com/threatlevel/2011/02/sony-lawsuit-factory/")

That was a HACK involving the bootloader for Linux on the PS3 to run unlicensed software such as homebrew games, pirated games and applications on the console, NOT because they didn't want Linux running on it. Of course, they wanted to protect their intellectual property and removed the Other OS feature to keep the bootloader from being abused for illegal activity.

---

### Post by Paqman on 2011-09-25
> **Quadunit404 said:**
> Of course, they wanted to protect their intellectual property and removed the Other OS feature to keep the bootloader from being abused for illegal activity.

They also wanted to stop the machine being used to build budget-price supercomputers. Consoles are sold at a loss, with the expectation that the premium on games will more than cover it. Clusters of hundreds of PS3's being used to crunch scientific datasets by cunning researchers who never bought any games was very expensive for Sony.

---

### Post by thatguruguy on 2011-09-25
> **KiwiNZ said:**
> "Sony’s aggressive pretrial discovery demands come in its lawsuit against George Hotz. The [21-year-old New Jersey hacker]("http://en.wikipedia.org/wiki/George_Hotz"),  who is well known in the jailbreaking community, published the finished  PlayStation 3 code and a how-to YouTube video last month. _[SIZE=2]The code  enables the Playstation 3 to play pirated and homebrewed games."[/SIZE]_

There in is the difference.

Maybe it's because I've only been practicing law for 20 years, and don't have your vast knowledge of the legalities involved, but I thought that there's nothing illegal in running homebrew games on any platform.  In the citation you have referred to, it appears that it is against the law.  In either event, I fail to see a legal distinction between "hacker enables PS3 owners to play homebrew and pirated games" and "hacker enables PCs to install non-licensed OSes and pirated Windows", which is the claim that will be made if someone figures out how to get around UEFI in order to install Linux on locked-down systems that either don't provide key access to users who want something other than the OEM Windows 8 installation.

---

### Post by KiwiNZ on 2011-09-25
> **thatguruguy said:**
> Maybe it's because I've only been practicing law for 20 years, and don't have your vast knowledge of the legalities involved, but I thought that there's nothing illegal in running homebrew games on any platform.  In the citation you have referred to, it appears that it is against the law.  In either event, I fail to see a legal distinction between "hacker enables PS3 owners to play homebrew and pirated games" and "hacker enables PCs to install non-licensed OSes and pirated Windows", which is the claim that will be made if someone figures out how to get around UEFI in order to install Linux on locked-down systems that either don't provide key access to users who want something other than the OEM Windows 8 installation.

I quoted the entire text from the article so I couldn't be accused of editing. Of course homebrew is OK , I was referring to the Pirated Games in this particular occasion.

---

### Post by KiwiNZ on 2011-09-25
> **thatguruguy said:**
> Maybe it's because I've only been practicing law for 20 years, and don't have your vast knowledge of the legalities involved, but I thought that there's nothing illegal in running homebrew games on any platform.  In the citation you have referred to, it appears that it is against the law.  In either event, I fail to see a legal distinction between "hacker enables PS3 owners to play homebrew and pirated games" and "hacker enables PCs to install non-licensed OSes and pirated Windows", which is the claim that will be made if someone figures out how to get around UEFI in order to install Linux on locked-down systems that either don't provide key access to users who want something other than the OEM Windows 8 installation.

If the OEMs lock down the UEFI to the extent that is is not user accessible, EG unable to install self made programs etc and or Linux and as such making the device a "rented" unit then this will be entirely different. The OEMs will be exposed to legal action and consumer resistance. I don't believe it will be MSFT's liability if the later occurs as the decision to restrict will be that of the OEM's.

---

### Post by Dr. C on 2011-09-25
> **KiwiNZ said:**
> "Sony&#8217;s aggressive pretrial discovery demands come in its lawsuit against George Hotz. The [21-year-old New Jersey hacker]("http://en.wikipedia.org/wiki/George_Hotz"),  who is well known in the jailbreaking community, published the finished  PlayStation 3 code and a how-to YouTube video last month. _[SIZE=2]The code  enables the Playstation 3 to play pirated and homebrewed games."[/SIZE]_

There in is the difference.

The elephant in the room which had not been mentioned until now is of course DRM and the "protection of intellectual property". The combination of a locked boot loader, together with an operating system that only allows applications from a censored "approved" source for example an app store or "trusted" developers that have signed their life away can actually be an effective anti piracy set up until someone decides to install GNU / Linux on the device they own. This blows the DRM to pieces in the process. The GPL v3 in particular is utter poison to this kind of DRM. This lockdown is the fundamental basis for DRM on game consoles, cell phones, tablets etc., regardless of the OS.

The only difference is that for the last 30 years the PC platform has actually being a very open platform. One can install the operating system of one's choice and one can install the software on one choice. The downside in certain circles is that it also makes it very easy to "pirate" software. movies, music etc. There is no fundamental reason why the laptop / desktop market is not locked down in the same fashion as the console or mobile market other than a historical accident. The motivation is both cases is the same. 

Now here is the problem if this open platform is locked down all of a sudden the likely result is a revolution so instead one does it gradually. First one locks does the operating system with DRM starting with Windows XP and to a huge extent with Windows Vista/7. Then one locks down the drivers 64bit Windows. Then one locks down the boot loader but only on certain machines in Windows 8. Then one lock downs the applications to a store but only on class 3 devices (ARM) on Windows 8. It is also imperative to exclude that pesky GPL v3. This was started with Windows Phone 7. The trend is very clear to anyone who is prepared to see the warning signs.

If one places a frog in a pot of boiling water it will jump out right away. If on the other hand one places the frog in a pot of cold water and slowly raises the heat until the water comes to a boil. The frog will stay in the pot and be slowly cooked to death. 

There is a lot more here for GNU / Linux and FLOSS that first meets the eye.

---

### Post by thatguruguy on 2011-09-25
> **KiwiNZ said:**
> If the OEMs lock down the UEFI to the extent that is is not user accessible, EG unable to install self made programs etc and or Linux and as such making the device a "rented" unit then this will be entirely different. The OEMs will be exposed to legal action and consumer resistance. I don't believe it will be MSFT's liability if the later occurs as the decision to restrict will be that of the OEM's.

Does that mean that the Sony PS3 is a "rented" unit?  Where is the legal action and consumer resistance against Sony?

It appears that you are trying, somehow, to assert that the PS3 is a different case, legally, than PCs with a Windows 8 logo, but it strikes me as a distinction without a difference.  There is no law that I know of (at least here in the US) that states that computer manufacturers are required to grant low-level access to users of the kind that would allow circumvention of the UEFI.  In fact, the **opposite is true**, which is why Sony was able to sue Hotz.

Again, all that is necessary to keep new computers tied to Windows 8 is that a claim is made that any circumvention of the UEFI is being done in order to allow running pirated copies of Windows 8.  There doesn't have to be any claim made that they are trying to keep Linux off the desktop or stifle competition, the only claim that needs to be asserted is that they (by "they" I am jointly referring to Microsoft and the OEMs) are trying to prevent illegal activity.

---

### Post by Dr. C on 2011-09-25
> **KiwiNZ said:**
> If the OEMs lock down the UEFI to the extent that is is not user accessible, EG unable to install self made programs etc and or Linux and as such making the device a "rented" unit then this will be entirely different. The OEMs will be exposed to legal action and consumer resistance. I don't believe it will be MSFT's liability if the later occurs as the decision to restrict will be that of the OEM's.

Apple has proven that until now this is not the case with for example the iPad.

---

### Post by KiwiNZ on 2011-09-25
> **Dr. C said:**
> Apple has proven that until now this is not the case with for example the iPad.

can you add some clarity to this statement?

---

### Post by thatguruguy on 2011-09-25
> **KiwiNZ said:**
> can you add some clarity to this statement?

I'll do it for him.  The iPad is completely locked down.  Does that make it a "rented" unit?

Where is the legal action and consumer resistance directed towards Apple?

---

### Post by KiwiNZ on 2011-09-25
> **thatguruguy said:**
> I'll do it for him.  The iPad is completely locked down.  Does that make it a "rented" unit?

Where is the legal action and consumer resistance directed towards Apple?

The iPad is an Appliance PC, it is not a generic PC. It is purchased knowing that it has a specific function and  specification set, much like a Casio watch, a Logitech Uni Remote,Apple TV, Set top Cable TV box for example.

---

### Post by thatguruguy on 2011-09-25
> **KiwiNZ said:**
> The iPad is an Appliance PC, it is not a generic PC. It is purchased knowing that it has a specific function and  specification set, much like a Casio watch, a Logitech Uni Remote,Apple TV, Set top Cable TV box for example.

Oh.  Have I mentioned the whole "distinction without a difference" thing yet?

Why is it so different?  Because one has an on-screen keyboard, and the other one has an external keyboard?  Is the ASUS transformer an "Appliance PC" (which term has ***absolutely no legal significance***, by the way) or a generic PC?

---

### Post by thatguruguy on 2011-09-25
Or is the difference because one unit is capable of running a "general desktop OS" (another term I just made up, to go with the Appliance PC you came up with) vs. a limited "mobile OS"?

If that is the difference, what about the upcoming tablets that will run Windows 8?  Are they Appliance PCs or generic PCs?

---

### Post by srs5694 on 2011-09-25
> **Dr. C said:**
> The elephant in the room which had not been mentioned until now is of course DRM and the "protection of intellectual property". The combination of a locked boot loader, together with an operating system that only allows applications from a censored "approved" source for example an app store or "trusted" developers that have signed their life away can actually be an effective anti piracy set up until someone decides to install GNU / Linux on the device they own. This blows the DRM to pieces in the process. The GPL v3 in particular is utter poison to this kind of DRM. This lockdown is the fundamental basis for DRM on game consoles, cell phones, tablets etc., regardless of the OS.

The only difference is that for the last 30 years the PC platform has actually being a very open platform. One can install the operating system of one's choice and one can install the software on one choice. The downside in certain circles is that it also makes it very easy to "pirate" software. movies, music etc. There is no fundamental reason why the laptop / desktop market is not locked down in the same fashion as the console or mobile market other than a historical accident. The motivation is both cases is the same. 

Now here is the problem if this open platform is locked down all of a sudden the likely result is a revolution so instead one does it gradually. First one locks does the operating system with DRM starting with Windows XP and to a huge extent with Windows Vista/7. Then one locks down the drivers 64bit Windows. Then one locks down the boot loader but only on certain machines in Windows 8. Then one lock downs the applications to a store but only on class 3 devices (ARM) on Windows 8. It is also imperative to exclude that pesky GPL v3. This was started with Windows Phone 7. The trend is very clear to anyone who is prepared to see the warning signs.

If one places a frog in a pot of boiling water it will jump out right away. If on the other hand one places the frog in a pot of cold water and slowly raises the heat until the water comes to a boil. The frog will stay in the pot and be slowly cooked to death. 

There is a lot more here for GNU / Linux and FLOSS that first meets the eye.

Well stated.

The PC world (and I even include many Linux distributions, such as Ubuntu, in this, although to a minor extent) has been slowly moving toward the "computer-as-service" model that's used on cellphones for quite some time. The use of secure boot in the firmware is a big step in this direction. Even if manufacturers include the ability to turn off and control this feature in the computers that will have secure boot in a year or so, there's no guarantee they won't start removing these features the next year, or the year after that.

In the past, I tended to agree with the general principles that Richard Stallman espoused, while at the same time thinking he was a bit of a nut in the degree to which he advocated them. I'm not so sure any more. Time will tell, I suppose. If it's possible to disable and control secure boot on the vast majority of systems that use it, and if there's no "creep" toward more restrictive policies, then the current concerns will prove to be a "big nothing." I hope this will be the case, but I'm concerned it won't be....

---

### Post by dave01945 on 2011-09-25
> **thatguruguy said:**
> Or is the difference because one unit is capable of running a "general desktop OS" (another term I just made up, to go with the Appliance PC you came up with) vs. a limited "mobile OS"?

If that is the difference, what about the upcoming tablets that will run Windows 8?  Are they Appliance PCs or generic PCs?

what is the difference between jailbreaking the ps3 and jailbreaking apples iOS which is not considered illegal 

the only difference i can see is the ps3 was used for copyright infringement (pirated games) but obviously installing linux on your own hardware does not infringe any copyright

---

### Post by KiwiNZ on 2011-09-25
> **thatguruguy said:**
> Or is the difference because one unit is capable of running a "general desktop OS" (another term I just made up, to go with the Appliance PC you came up with) vs. a limited "mobile OS"?

If that is the difference, what about the upcoming tablets that will run Windows 8?  Are they Appliance PCs or generic PCs?

*Sigh*

Thanks for the credit but Appliance PC is a widely used term,

I am not going to allow this thread to be Hi jacked by a Apple Ipad debate

---

### Post by Dr. C on 2011-09-25
> **dave01945 said:**
> what is the difference between jailbreaking the ps3 and jailbreaking apples iOS which is not considered illegal 

the only difference i can see is the ps3 was used for copyright infringement (pirated games) but obviously installing linux on your own hardware does not infringe any copyright

The difference is that in the United States there was an exception granted for "wireless telephone handsets" to the DMCA. So it is legal to jail break an iPhone but not an iPad. Apple of course fought it and lost. [http://www.copyright.gov/1201/]("http://www.copyright.gov/1201/"). Totally arbitrary of course.

---

### Post by dave01945 on 2011-09-25
> **Dr. C said:**
> The difference is that in the United State there was an exception granted for "wireless telephone handsets" to the DMCA. So it is legal to jail break an iPhone but not an iPad. Apple of course fought it and lost. [http://www.copyright.gov/1201/]("http://www.copyright.gov/1201/"). Totally arbitrary of course.

also in the EU circumvention of DRM for interoperability is not illegal for the end user it is only illegal if it is used to infringe copyright and install linux on your own computer is not infringing copyright which would be the purpose of circumventing secure boot which if the OEM's want to be available to the wider market will offer the option to disable it anyway.

---

### Post by Dr. C on 2011-09-25
> **dave01945 said:**
> also in the EU circumvention of DRM for interoperability is not illegal for the end user it is only illegal if it is used to infringe copyright and install linux on your own computer is not infringing copyright which would be the purpose of circumventing secure boot which if the OEM's want to be available to the wider market will offer the option to disable it anyway.

The legal issues surrounding anti circumvention or breaking of the DRM, are very complex and vary widely depending on the jurisdiction. The key issue is that in all cases regardless of whether the device is a cell phone, game console, tablet, laptop, notebook, tower PC, etc, there are both many legitimate reasons for breaking the DRM including installing GNU / Linux and one illegitimate reason copyright infringement. Unfortunately in many jurisdictions, due in large part to lobbying by large copyright interests, attempting to stop the one illegitimate reason has been given a disproportionate weight over allowing the multitude of legitimate reasons.

Making arbitrarily distinctions between different types of devices is pointless since GNU / Linux can run on all of them. Furthermore Windows 8 is actually moving in that same direction.

---

### Post by dave01945 on 2011-09-25
i can agree with that but the only copyright infringement from circumventing secure boot would be pirated copies of an OS but that is not the purpose of secure boot the OS's have different systems for that. the purpose of secure boot is to prevent malicious software running at boot and the user has the right to run whatever software they want on their hardware

---

### Post by thatguruguy on 2011-09-25
> **KiwiNZ said:**
> *Sigh*

Thanks for the credit but Appliance PC is a widely used term,

I am not going to allow this thread to be Hi jacked by a Apple Ipad debate

In other words, you don't have an answer.  My arguments aren't about the iPad per se. Which should be obvious even to you.  In fact, I'm sure that it IS obvious to you.  It's equally obvious to me that you're dodging the issue.  Just in case I'm giving you too much credit, I'll be more explicit.

I can't speak for a lot of office environments, but I can speak about law firms.  Go into any law firm, and you'll notice that while the secretaries still use desktop PCs, fully half of the lawyers (or more) use laptop computers, often with docking stations so they can hook their laptops up to full monitors and keyboards in the office.  Many lawyers are now carrying tablets for convenience (it's the reason I got mine).  I can easily imagine a time when the norm in law firms (and, presumably, other office settings) will be that professionals carry tablets which can be hot-plugged into some kind of dock when they need the conveniences (large monitor, CD/DVD drives, full keyboards) offered by a desktop.

I'm not alone in believing that there will be a "great convergence" as described above.  It's this expectation that is driving operating systems from Windows to Ubuntu to become more "tablet-like".

Assuming that this convergence happens, where will the distinction between Appliance PC and generic desktop PC be drawn?  Will it still be OK that the Appliance PCs be be locked in to one OS that can't be in any way altered by the end user?

---

### Post by KiwiNZ on 2011-09-25
> **thatguruguy said:**
> In other words, you don't have an answer.  My arguments aren't about the iPad per se. Which should be obvious even to you.  In fact, I'm sure that it IS obvious to you.  It's equally obvious to me that you're dodging the issue.  Just in case I'm giving you too much credit, I'll be more explicit.

I can't speak for a lot of office environments, but I can speak about law firms.  Go into any law firm, and you'll notice that while the secretaries still use desktop PCs, fully half of the lawyers (or more) use laptop computers, often with docking stations so they can hook their laptops up to full monitors and keyboards in the office.  Many lawyers are now carrying tablets for convenience (it's the reason I got mine).  I can easily imagine a time when the norm in law firms (and, presumably, other office settings) will be that professionals carry tablets which can be hot-plugged into some kind of dock when they need the conveniences (large monitor, CD/DVD drives, full keyboards) offered by a desktop.

I'm not alone in believing that there will be a "great convergence" as described above.  It's this expectation that is driving operating systems from Windows to Ubuntu to become more "tablet-like".

Assuming that this convergence happens, where will the distinction between Appliance PC and generic desktop PC be drawn?  Will it still be OK that the Appliance PCs be be locked in to one OS that can't be in any way altered by the end user?


Please stop the insulting language

---

### Post by thatguruguy on 2011-09-25
> **KiwiNZ said:**
> Please stop the insulting language

No insult was intended, any more than you meant to be insulting with the condescending "sigh" (which implies that you are speaking to a child who's simply too slow to understand the point you're making) at the beginning of your comment to me.

And you still haven't addressed the actual issue.

---

### Post by el_koraco on 2011-09-25
> **thatguruguy said:**
> In either event, I fail to see a legal distinction between "hacker enables PS3 owners to play homebrew and pirated games" and "hacker enables PCs to install non-licensed OSes and pirated Windows", which is the claim that will be made if someone figures out how to get around UEFI in order to install Linux on locked-down systems that either don't provide key access to users who want something other than the OEM Windows 8 installation.

There's no legal distinction, but the whole Sony debacle proved to be a rather disastrous PR calamity, so it's pretty unlikely that either Microsoft or the OEM's would pursue legal action in such a case. They would be more likely to issue statements, and it would probably be within their legal rights to waive warranties on the "cracked" machines, as is the case with Android and iThings.

---

### Post by thatguruguy on 2011-09-25
> **el_koraco said:**
> There's no legal distinction, but the whole Sony debacle proved to be a rather disastrous PR calamity, so it's pretty unlikely that either Microsoft or the OEM's would pursue legal action in such a case. They would be more likely to issue statements, and it would probably be within their legal rights to waive warranties on the "cracked" machines, as is the case with Android and iThings.

I think the real PR calamity for Sony was when the playstation network was cracked and went down.  I think that most people don't care that Sony doesn't allow you to put Linux on the box any more, and I think they care even less about Sony pursuing Hotz in court.

---

### Post by Dr. C on 2011-09-25
> **dave01945 said:**
> i can agree with that but the only copyright infringement from circumventing secure boot would be pirated copies of an OS but that is not the purpose of secure boot the OS's have different systems for that. the purpose of secure boot is to prevent malicious software running at boot and the user has the right to run whatever software they want on their hardware

No an operating system can do a lot more to "fight piracy" than prevent pirated copies of itself. It can prevent files from being copied, whitelist or blacklist applications, block or downgrade video or sound, block protocols for example bit torrent, restrict access to devices for example a CD burner only to "trusted" applications, the list is endless. Microsoft spent billions of dollars between Windows XP and Windows Vista rewriting major components of Windows in order to implement HDCP and all sorts of DRM restrictions to accommodate the MPAA among others. DRM is the reason for a whole new driver model for Windows Vista / 7, and the real reason to require signed drivers for 64 bit Windows. The DRM plumbing is already in place. 

If the real reason was to prevent malicious software from loading at boot then one simply locks down the system and then provides the owner of the hardware with the keys to unlock the system since in this scenario the owner of the hardware can be trusted, On the other hand if the motivation is DRM then owner of the hardware cannot be trusted and must be kept locked out. 

Trust by the way works both ways which is why I do not trust versions of Microsoft Windows after Windows 2000. I do however trust Windows 2000 and earlier.

---

### Post by thatguruguy on 2011-09-25
Incidentally, the best response to the issue lies within the "great convergence" I referred to earlier.  If one assumes that eventually tablets will be the norm, all of this really *is* a tempest in a teapot.  Currently, Microsoft is, at best, a distant also-ran in the tablet market.  They seek to make significant inroads with Windows 8, because they expect that ultra-portable computing will become the norm, rather than the exception.

If true innovation is to happen, it needs to happen on the new platform, rather than the old one.  Linux needs to continue to expand its reach on ultra-portable devices, not only in the form of Android, but in the form of other traditional "desktop" OSes like Fedora and Ubuntu.  With the widespread acceptance of Android, I think Unity and Gnome Shell can both make significant inroads onto tablets as alternative shells.  In the long run, I think that's where the battle lines will be drawn, rather than on old desktop units.

---

### Post by MonolithImmortal on 2011-09-25
> **Dr. C said:**
> 
I do however trust Windows 2000 and earlier.
This explains a lot.

---

### Post by Merk42 on 2011-09-25
> **thatguruguy said:**
> No insult was intended, any more than you meant to be insulting with the condescending "sigh" (which implies that you are speaking to a child who's simply too slow to understand the point you're making) at the beginning of your comment to me.

And you still haven't addressed the actual issue.

If you're saying that the long term goal of Microsoft is to put Windows only on tablet devices, and those tablet devices would be locked down so no one could install Linux, couldn't people wanting Linux just get an Android tablet and install (a different version of Linux) on that instead?

---

### Post by thatguruguy on 2011-09-25
> **Merk42 said:**
> If you're saying that the long term goal of Microsoft is to put Windows only on tablet devices, and those tablet devices would be locked down so no one could install Linux, couldn't people wanting Linux just get an Android tablet and install (a different version of Linux) on that instead?

No, I was stating that there is no legal difference between an "Appliance PC" and a "generic desktop PC."  KiwiNZ had asserted that it was essentially OK to lock down the iPad (for example) because it's an "Appliance PC", and I wanted to know the legally-recognized difference between an "Appliance PC" and a "generic desktop PC".

As to the issue you raised, I addressed that above.

---

### Post by Dr. C on 2011-09-25
> **thatguruguy said:**
> Incidentally, the best response to the issue lies within the "great convergence" I referred to earlier.  If one assumes that eventually tablets will be the norm, all of this really *is* a tempest in a teapot.  Currently, Microsoft is, at best, a distant also-ran in the tablet market.  They seek to make significant inroads with Windows 8, because they expect that ultra-portable computing will become the norm, rather than the exception.

If true innovation is to happen, it needs to happen on the new platform, rather than the old one.  Linux needs to continue to expand its reach on ultra-portable devices, not only in the form of Android, but in the form of other traditional "desktop" OSes like Fedora and Ubuntu.  With the widespread acceptance of Android, I think Unity and Gnome Shell can both make significant inroads onto tablets as alternative shells.  In the long run, I think that's where the battle lines will be drawn, rather than on old desktop units.

The trouble is that the tablet market is much more locked down than the desktop / laptop market, and Microsoft is by far not the only culprit. Furthermore Android 3.xx is not FLOSS. So convergence will likely bring tyranny and not freedom to the desktop unless things change big time. By the way I will take Windows NT Workstation 4.0 with proper Administrative access over a locked and tivoized Android tablet from a software freedom perspective any day. There is no freedom in Free Software without root.

---

### Post by thatguruguy on 2011-09-25
> **Dr. C said:**
> The trouble is that the tablet market is much more locked down than the desktop / laptop market, and Microsoft is by far not the only culprit. Furthermore Android 3.xx is not FLOSS. So convergence will likely bring tyranny and not freedom to the desktop unless things change big time. By the way I will take Windows NT Workstation 4.0 with proper Administrative access over a locked and tivoized Android tablet from a software freedom perspective any day. There is no freedom in Free Software without root.

I get your point.  However, the desktop market is a mature market, whereas there is still a lot of room for innovation in tablets.

---

### Post by KiwiNZ on 2011-09-25
> **thatguruguy said:**
> No, I was stating that there is no legal difference between an "Appliance PC" and a "generic desktop PC."  KiwiNZ had asserted that it was essentially OK to lock down the iPad (for example) because it's an "Appliance PC", and I wanted to know the legally-recognized difference between an "Appliance PC" and a "generic desktop PC".

As to the issue you raised, I addressed that above.

Would you get a Cable TV set top box then Hack Windows on it ( most have a hybrid Linux)and thus breaking it? I woudl hazard a guess no, why it's an Appliance device.

I used the term "generic PC" to describe non Appliance devices to show the difference. "generic PC maybe the wrong term in your mind, so be it, sue me.

---

### Post by thatguruguy on 2011-09-25
> **KiwiNZ said:**
> Would you get a Cable TV set top box then Hack Windows on it ( most have a hybrid Linux)and thus breaking it? I woudl hazard a guess no, why it's an Appliance device.

I used the term "generic PC" to describe non Appliance devices to show the difference. "generic PC maybe the wrong term in your mind, so be it, sue me.

Personally, I doubt that I would personally hack Windows onto anything.  

However, tablet PCs can run Windows.  Or Linux.  Or iOS.  There are significant engineered-in limitations to devices such as set-top boxes and calculators; these limitations are rapidly disappearing on tablets.  If you look a few posts ago, I made an argument in favor of your earlier "innovation will win out" position; it's just that I don't think that the innovation will happen on the current desktop platform.

---

### Post by Dr. C on 2011-09-25
> **KiwiNZ said:**
> Would you get a Cable TV set top box then Hack Windows on it ( most have a hybrid Linux)and thus breaking it? I woudl hazard a guess no, why it's an Appliance device.

I used the term "generic PC" to describe non Appliance devices to show the difference. "generic PC maybe the wrong term in your mind, so be it, sue me.

A cable TV box is not a good example because in many cases they belong to the cable company. 

Now installing Windows on a rooted TiVo and then presenting said device to RMS. Now that sounds like a really interesting project given the history of the device in the development of GPL v3,  I am talking of course of a proper full retail version of Windows so there are no copyright issues on the Microsoft side.
:lolflag:

---

### Post by KiwiNZ on 2011-09-25
> **Dr. C said:**
> A cable TV box is not a good example because in many cases they belong to the cable company. 

Now installing Windows on a rooted TiVo and then presenting said device to RMS. Now that sounds like a really interesting project given the history of the device in the development of GPL v3,  I am talking of course of a proper full retail version of Windows so there are no copyright issues on the Microsoft side.
:lolflag:

Gawd no thanks;)

---

### Post by dave01945 on 2011-09-25
> **Dr. C said:**
> No an operating system can do a lot more to "fight piracy" than prevent pirated copies of itself. It can prevent files from being copied, whitelist or blacklist applications, block or downgrade video or sound, block protocols for example bit torrent, restrict access to devices for example a CD burner only to "trusted" applications, the list is endless. Microsoft spent billions of dollars between Windows XP and Windows Vista rewriting major components of Windows in order to implement HDCP and all sorts of DRM restrictions to accommodate the MPAA among others. DRM is the reason for a whole new driver model for Windows Vista / 7, and the real reason to require signed drivers for 64 bit Windows. The DRM plumbing is already in place. 

If the real reason was to prevent malicious software from loading at boot then one simply locks down the system and then provides the owner of the hardware with the keys to unlock the system since in this scenario the owner of the hardware can be trusted, On the other hand if the motivation is DRM then owner of the hardware cannot be trusted and must be kept locked out. 

Trust by the way works both ways which is why I do not trust versions of Microsoft Windows after Windows 2000. I do however trust Windows 2000 and earlier.

of course the OS can do more to stop piracy they could stop the user doing anything but that is down to the OS if they let us choose what software we use and if all programs have to be approved by microsoft before they can be used that will not be very good for small software developers 

If microsoft's goal with secure boot was purely for DRM reasons they would have made it a requirement that secure boot cannot be disabled which is not what they have done the decision is left with the OEM's to offer that option 

locking every user out of a system is not going to stop copyright infringement because people who are involved in copyright are not going to be stopped because it is illegal to circumvent secure boot because it is already illegal to infringe the copyright it is only going to affect legitimate companies giving people a choice in what software we use

---

### Post by KiwiNZ on 2011-09-25
I still stand by an earlier comment I made, that is , We should be running to the Developer labs and not running to the DOJ or the European Union equivalent . Innovation to compete.

---

### Post by Dr. C on 2011-09-25
> **KiwiNZ said:**
> I still stand by an earlier comment I made, that is , We should be running to the Developer labs and not running to the DOJ or the European Union equivalent . Innovation to compete.

We need to do both and also a lot more.

---

### Post by KiwiNZ on 2011-09-25
> **Dr. C said:**
> We need to do both and also a lot more.

I disagree, present products and allow market forces to work. Look at the outcome of the European Courts fiasco over Windows, the result MSFT was forced to put a broken unwanted product on the market, it didn't result in consumers selecting Linux products it resulted in consumers finding work round's to have their choice OS, full Windows.

If we present professional working products that meet the full needs of the consumer and allow the consumer to chose we meet the consumer need better. If they want non locked down products they will vote with their wallets , if they want locked down products they again will vote with their wallets.

---

### Post by Dr. C on 2011-09-26
> **KiwiNZ said:**
> I disagree, present products and allow market forces to work. Look at the outcome of the European Courts fiasco over Windows, the result MSFT was forced to put a broken unwanted product on the market, it didn't result in consumers selecting Linux products it resulted in consumers finding work round's to have their choice OS, full Windows.

If we present professional working products that meet the full needs of the consumer and allow the consumer to chose we meet the consumer need better. If they want non locked down products they will vote with their wallets , if they want locked down products they again will vote with their wallets.

Anyone who has used SAMBA has benefited from EU anti trust case. 

Furthermore let us say we only do what is suggested here and succeed. What is going to happen to all the locked products that consumers discard to replace with non locked products? They will end up as as even more e-waste. As if e-waste was not enough of an environmental problem already.

---

### Post by Thewhistlingwind on 2011-09-26
> **KiwiNZ said:**
> I still stand by an earlier comment I made, that is , We should be running to the Developer labs and not running to the DOJ or the European Union equivalent . Innovation to compete.

I've heard you say this many times in many more threads than this one. And every time I have wondered one thing.

What would you like to see improved?

---

### Post by KiwiNZ on 2011-09-26
> **Thewhistlingwind said:**
> I've heard you say this many times in many more threads than this one. And every time I have wondered one thing.

What would you like to see improved?
Ease of use
Better package management
Better hardware support ( I know this involves the H/ware manufacturers)
Better UI
Less Distributions

These are just a few.

---

### Post by Thewhistlingwind on 2011-09-26
> **KiwiNZ said:**
> Ease of use
Better package management
Better hardware support ( I know this involves the H/ware manufacturers)
Better UI
Less Distributions

These are just a few.

1. Agreed, if apple can turn BSD into Mac OS X. I will hear no argument that "Unix can not be intuitive!"

2. On this note specifically, I think the elephant in the room is packages VS. executables. A lot of users WANT executables, but can only get packages. (Or don't know where to get executables.) On a similar note, I think that adding a better interface for managing offline installations in terms of packaging is a must.  (A make shift short term solution might be a python GTK or QT app that acts as a front-end to YUM, APT, Pacman and Portage.)

3. Linux fights an upstream battle here, and likely has more supported hardware than windows. (Not like we can check or anything.) I think this is a problem, but towards the bottom of the top ten. HOWEVER, when one talks about hardware, naturally the topic turns to OEM's. Right now it is very hard to sell computers with Linux installed at prices competitive to those with windows preinstalled. The reason is that windows software vendors subsidize the cost of the computer through endorsements in the form of trials and the like installed on the OEM image. Linux vendors need a way to price their products competitively, or they'll fail in the marketplace. (This should a top if not THE top priority.)

4.  I honestly think that Linux performs very well in the UI arena. You may contest this if you wish.

5. Sorry guys, but he's right. The current distribution "marketplace" makes it very hard for businesses to stay on the train. Even in the enterprise market you have Redhat VS. SUSE VS. Canonical etc etc. On the one hand, the Linux ecosystem in large part depends heavily on the ability to have many distros, but is at the same time weakened by having many distros. I think more work should be put into standards across systems if nothing else. If it's a burden for developers, OEM's, and businesses, it won't see mainstream adoption.

---

### Post by Copper Bezel on 2011-09-26
Do you feel that Ubuntu isn't actively engaging in those areas enough? I mean, they all seem to be Canonical priorities. (Perhaps not "fewer distributions," but all a single distro can do about that is to be ludicrously popular and treat derivative distributions as the silly little friends of the enterprise, which, arguably....)

---

### Post by KiwiNZ on 2011-09-26
> **Thewhistlingwind said:**
> 1. Agreed, if apple can turn BSD into Mac OS X. I will hear no argument that "Unix can not be intuitive!"

2. On this note specifically, I think the elephant in the room is packages VS. executables. A lot of users WANT executables, but can only get packages. (Or don't know where to get executables.) On a similar note, I think that adding a better interface for managing offline installations in terms of packaging is a must.  (A make shift short term solution might be a python GTK or QT app that acts as a front-end to YUM, APT, Pacman and Portage.)

3. Linux fights an upstream battle here, and likely has more supported hardware than windows. (Not like we can check or anything.) I think this is a problem, but towards the bottom of the top ten. HOWEVER, when one talks about hardware, naturally the topic turns to OEM's. Right now it is very hard to sell computers with Linux installed at prices competitive to those with windows preinstalled. The reason is that windows software vendors subsidize the cost of the computer through endorsements in the form of trials and the like installed on the OEM image. Linux vendors need a way to price their products competitively, or they'll fail in the marketplace. (This should a top if not THE top priority.)

4.  I honestly think that Linux performs very well in the UI arena. You may contest this if you wish.

5. Sorry guys, but he's right. The current distribution "marketplace" makes it very hard for businesses to stay on the train. Even in the enterprise market you have Redhat VS. SUSE VS. Canonical etc etc. On the one hand, the Linux ecosystem in large part depends heavily on the ability to have many distros, but is at the same time weakened by having many distros. I think more work should be put into standards across systems if nothing else. If it's a burden for developers, OEM's, and businesses, it won't see mainstream adoption.

My reply is off topic for this thread ans I apologise for this.

When I refer to package management I am meaning as well the whole Software Install process.

In Windows and OSX it is a lot easier and that is a magor issue when wider consumer uptake is concerned. For Windows over 90% of install the consumer can put the CD in the and it auto launches and installs with a few clicks. For downloads they either auto launch of a few clicks done.
In OSX for most it is Click drag drop in the Applications folder, job done or obtained from the App store with auto install.

Things have improved with Linux with the more use of App Stores but in general the perception and reality of installs with Linux is hard and troublesome for the consumer.

Another point I missed earlier was compatibility and interoperability.

---

### Post by aysiu on 2011-09-26
> **KiwiNZ said:**
> 
When I refer to package management I am meaning as well the whole Software Install process.

In Windows and OSX it is a lot easier and that is a magor issue when wider consumer uptake is concerned. For Windows over 90% of install the consumer can put the CD in the and it auto launches and installs with a few clicks. For downloads they either auto launch of a few clicks done.
In OSX for most it is Click drag drop in the Applications folder, job done or obtained from the App store with auto install.

Things have improved with Linux with the more use of App Stores but in general the perception and reality of installs with Linux is hard and troublesome for the consumer.
The problem with package management is entirely in its implementation and marketing and not the concept itself (which is really no different in general, as opposed to specifically, from the iTunes App Store or the Android Market). I love the .dmg-to-Applications-folder system on Mac OS X. It's very simple. But the typical Windows software installation process is a real pain. To install all the applications I want on a fresh Windows installation takes me literally hours of sitting there clicking and clicking and moving the mouse and clicking again.

In Ubuntu, I can mark a list of packages in Synaptic and then click Apply and be done with it. Or, better yet, create an *apt-get* script with a list of software I like. For the vast majority of Mac OS X applications, I can just drag the application icons out of the Applications folder to an external drive and then drag them into the Applications folder of the new drive. With Windows, it's a whole bunch of setup.exe files and wizards and licensing agreements and prompts to reboot the computer--annoying as hell. Not "a lot easier" at all.

---

### Post by KiwiNZ on 2011-09-26
> **aysiu said:**
> The problem with package management is entirely in its implementation and marketing and not the concept itself (which is really no different in general, as opposed to specifically, from the iTunes App Store or the Android Market). I love the .dmg-to-Applications-folder system on Mac OS X. It's very simple. But the typical Windows software installation process is a real pain. To install all the applications I want on a fresh Windows installation takes me literally hours of sitting there clicking and clicking and moving the mouse and clicking again.

In Ubuntu, I can mark a list of packages in Synaptic and then click Apply and be done with it. Or, better yet, create an *apt-get* script with a list of software I like. For the vast majority of Mac OS X applications, I can just drag the application icons out of the Applications folder to an external drive and then drag them into the Applications folder of the new drive. With Windows, it's a whole bunch of setup.exe files and wizards and licensing agreements and prompts to reboot the computer--annoying as hell. Not "a lot easier" at all.

Interestingly I just installed Win 8 on a Desktop and the number clicks was about 6 and the whole thing took about 40 minutes.

The number of reboots is significantly less in Win 7 and Win 8.

I agree Ubuntu is better for installs compared to the RPM based systems.

The App Store and no install media needs to be pushed developed and promoted to rid Linux of it's install bad image.

Like I have said, 'innovate to compete'

---

### Post by Spice Weasel on 2011-09-26
> **Dr. C said:**
> Anyone who has used SAMBA has benefited from EU anti trust case. 

Furthermore let us say we only do what is suggested here and succeed. What is going to happen to all the locked products that consumers discard to replace with non locked products? They will end up as as even more e-waste. As if e-waste was not enough of an environmental problem already.

> implying that users care about locked products. iOS has about 20-60% share (Nobody seems to be sure on the exact number). It would be good if they did care though. Open software in the sense that it isn't locked down in any way by DRM or the like is more important than open source.

---

### Post by Erik1984 on 2011-09-26
> **Spice Weasel said:**
> > implying that users care about locked products. iOS has about 20-60% share (Nobody seems to be sure on the exact number). It would be good if they did care though. Open software in the sense that it isn't locked down in any way by DRM or the like is more important than open source.

Agreed. However free software is the best way to ensure it is not locked down imo.

---

### Post by Copper Bezel on 2011-09-26
> **Spice Weasel]> implying that users care about locked products. iOS has about 20-60% share (Nobody seems to be sure on the exact number). It would be good if they did care though. Open software in the sense that it isn't locked down in any way by DRM or the like is more important than open source.[/QUOTE]
Some do seem to care. That's part of the Android crowd's difference with the iOS crowd. When the vast majority of users don't even know that the operating system *can* be replaced with an alternative one and wouldn't know what to do with one if they did, it's hard to imagine how they could become so concerned on something like this secure boot issue, though.

In practical terms, yeah, I agree - I don't have any problem using commercial software so long as it's a modular thing I have some control over.

[QUOTE=KiwiNZ]The App Store and no install media needs to be pushed developed and promoted to rid Linux of it's install bad image.[/QUOTE]
Clearly. I switched to Ubuntu in 2008 said:**
> Like I have said, 'innovate to compete'
I still think this oversimplifies, though. It's not possible for something like Ubuntu to take on something like Windows head on. It's a niche OS in need of a niche. The present niche seems to be those of us who want to have geek chic without learning to compile anything.

---

### Post by del_diablo on 2011-09-26
> **KiwiNZ said:**
> Like I have said, 'innovate to compete'

And what if you are not allowed to compete in the first place?
Then what?

---

### Post by beew on 2011-09-26
> **KiwiNZ said:**
> Interestingly I just installed Win 8 on a Desktop and the number clicks was about 6 and the whole thing took about 40 minutes.

The number of reboots is significantly less in Win 7 and Win 8.

I agree Ubuntu is better for installs compared to the RPM based systems.

The App Store and no install media needs to be pushed developed and promoted to rid Linux of it's install bad image.

Like I have said, 'innovate to compete'

What was the last time you installed Ubuntu I wonder. The installation is significantly easier in Ubuntu than in WIndows, I did that in about 20 minutes while surfing the internet and posting on this forum,--and that was a multiboot system with 5 Oses,-- try that with WIndoiws. The "app store" is a Linux concept to begin with. It is just that you don't give Linux enough credit. 

But how would easier install process help Ubuntu to "compete" if the hardware doesn't allow Linux to boot in the first place because it is rigged?

Your point about "innovation"  has no relevance on this thread. It is like saying when the Mafia threatens to kill you instead of calling the police you should go practice kung fu. Thankfully no one would take this opinion seriously outside this little sandbox and Ayn Rand's fantasy world. The point is that MS is trying to rig the game so that you cannot even access the market so how do you compete with even the best innovations? The purpose of antitrust is exactly to prevent monopolies (which MS is on the desktop/laptop  market) from avoiding to "innovate and compete" by using unfair means to shut out competitors.

---

### Post by Copper Bezel on 2011-09-26
First off, KiwiNZ is assuming (as most are) that this idea that Microsoft is going to lock other OSs out of the hardware is overblown.

Second, by compete, he means actually compete in the market, with actual OEM installs that people actually buy, where desktop Linux generally or Ubuntu in particular is something that comes as a feature of your new Dell, Lenovo, Acer, or whatnot PC, instead of something you use to save your bricked laptop when you finally break Windows and don't have a restore partition.

Third, by installs, I'm pretty sure this is still in reference to package management, not installing the OS, which no one has to do on an OEM Windows machine and no one would need to do on an OEM Ubuntu machine, either.

I don't personally really get what, again, what desktop Linux generally or Ubuntu specifically has to sell on, what it's "for," to the general public, what it offers them that's worth the switchover cost. But that's a separate thing.

---

### Post by aysiu on 2011-09-26
> **KiwiNZ said:**
> Interestingly I just installed Win 8 on a Desktop and the number clicks was about 6 and the whole thing took about 40 minutes.

The number of reboots is significantly less in Win 7 and Win 8. Wait, so you're talking about installing the OS? I thought you were talking about installing programs. There's no way I can install all the programs I need on Windows 7 with only six clicks.

> I agree Ubuntu is better for installs compared to the RPM based systems. I haven't used an RPM distro for years. I'll take your word for it.

> The App Store and no install media needs to be pushed developed and promoted to rid Linux of it's install bad image.

Like I have said, 'innovate to compete' Innovation's great, but without a ready-to-buy, well-thought-out, preinstalled, and competitively priced **product** to buy, it won't matter. The vast majority of folks aren't going to download a .iso and install their own operating system, nor are they going to buy from a no-name vendor like System76 or ZaReason.

---

### Post by beew on 2011-09-26
> **aysiu said:**
> 
 I haven't used an RPM distro for years. I'll take your word for it.



Fedora 14 and 15 are extremely easy to install too, installation is even faster than Ubuntu (and seems to be less dependent on having internet connection, just need to do 600 updates after install but that takes less than 5 minutes with Yumex), let alone Windows. It is a bit more work to install proprietary stuffs but that is Fedora's quirk.

---

### Post by Lucradia on 2011-09-26
> **KiwiNZ said:**
> I agree Ubuntu is better for installs compared to the RPM based systems.

Unless you have a newer laptop that like, just came out in the past 6 months. Then RPM might be better, as it as more wireless support sooner in Fedora. If you don't, you have to use Ubuntu's +1 until it releases. (Sometimes this doesn't work, and you will have to use the next +1, for whatever reason.)

---

### Post by KiwiNZ on 2011-09-26
> **beew said:**
> What was the last time you installed Ubuntu I wonder. The installation is significantly easier in Ubuntu than in WIndows, I did that in about 20 minutes while surfing the internet and posting on this forum,--and that was a multiboot system with 5 Oses,-- try that with WIndoiws. The "app store" is a Linux concept to begin with. It is just that you don't give Linux enough credit. 

But how would easier install process help Ubuntu to "compete" if the hardware doesn't allow Linux to boot in the first place because it is rigged?

Your point about "innovation"  has no relevance on this thread. It is like saying when the Mafia threatens to kill you instead of calling the police you should go practice kung fu. Thankfully no one would take this opinion seriously outside this little sandbox and Ayn Rand's fantasy world. The point is that MS is trying to rig the game so that you cannot even access the market so how do you compete with even the best innovations? The purpose of antitrust is exactly to prevent monopolies (which MS is on the desktop/laptop  market) from avoiding to "innovate and compete" by using unfair means to shut out competitors.

The last ubuntu install I did was about a week ago, it took approx 50 minutes.

So you are saying we shouldn't innovate, yeah that will work if your aim is to drop from a stellar 1% to 0.000000000000001%

If you had any understanding of sales and marketing you would see how innovation is very relevant in this thread. If we follow what Google has done with Android and produce a product for the Desktop/Laptop that is polished and works and I mean works in as much that it does what the consumer wants not what geeks want then consumer demand will come into play. Market forces will not work for us if we cry, they will work for us if we have a product that is worthy and wanted.

---

### Post by KiwiNZ on 2011-09-26
> **aysiu said:**
> Wait, so you're talking about installing the OS? I thought you were talking about installing programs. There's no way I can install all the programs I need on Windows 7 with only six clicks.

 I haven't used an RPM distro for years. I'll take your word for it.

 Innovation's great, but without a ready-to-buy, well-thought-out, preinstalled, and competitively priced **product** to buy, it won't matter. The vast majority of folks aren't going to download a .iso and install their own operating system, nor are they going to buy from a no-name vendor like System76 or ZaReason.

I was referring to both OS installs and Application installs.

---

### Post by Copper Bezel on 2011-09-26
[QUOTE=KiwiNZ]If you had any understanding of sales and marketing you would see how innovation is very relevant in this thread. If we follow what Google has done with Android and produce a product for the Desktop/Laptop that is polished and works and I mean works in as much that it does what the consumer wants not what geeks want then consumer demand will come into play. Market forces will not work for us if we cry, they will work for us if we have a product that is worthy and wanted.[/QUOTE]
No one is saying that Ubuntu *shouldn't innovate*. A couple of people are saying that it *can't* if it isn't "allowed" to compete at all.

As for Android as an example, it's a fairly indirect one, isn't it? Android offered something Windows didn't, a lightweight, customizable platform for mobiles that didn't exist otherwise; it had an open market to fill. It *wasn't competing* with Windows. I don't see Ubuntu or other desktop, GNU-based Linux distros offering the same kind of unique market opportunity.

---

### Post by KiwiNZ on 2011-09-26
> **Copper Bezel said:**
> 
As for Android as an example, it's a fairly indirect one, isn't it? Android offered something Windows didn't, a lightweight, customizable platform for mobiles that didn't exist otherwise; it had an open market to fill. It *wasn't competing* with Windows. I don't see Ubuntu or other desktop, GNU-based Linux distros offering the same kind of unique market opportunity.

IOS?
RIM/Blackberry OS?
WebOS?
Symbian?

MSFT maybe late to party but there were pre-existing OS's

---

### Post by Copper Bezel on 2011-09-26
Fair enough. I didn't count iOS because it wasn't something that just any vendor could pick up, but there were certainly other vendors in the game. (I really ought to smack myself for not considering RIM in a discussion of smart phones.)

---

### Post by del_diablo on 2011-09-26
If Android was utterly <snip>/bad/crap/low quality, but they did the same PR campaing: what would happen is that a lot of phones would be shipped with Android, but if there ever as a consumer backlash, its popularity would fall to the cold earth.
Its not as simple as Android being good, if it was just markeded by another random nobody company it would never have gotten anywhere in the first place.
Androids innovation was not that it was "great" but that it had Google behind it.
KiwiNZ is right about there existing tons of other Phone OSes before that point, that all filled "those niches".
If Apple had said "meh, we will allow others to use our iOS", then there might never ever have been a marked for Android, considering how important the appstore is.

What Ubuntu has been doing so far is to enjoy a niece marked, and adapt to it.
If I could find decent laptop in stores that shipped with Ubuntu, from a known OEM, the entire marked would change over night.

---

### Post by Dr. C on 2011-09-26
A threat of Anti Trust Action against Microsoft coming from Australia. [Linux users threaten Microsoft with ACCC]("http://www.zdnet.com.au/linux-users-threaten-microsoft-with-accc-339323063.htm")

---

### Post by beew on 2011-09-26
> **KiwiNZ said:**
> The last ubuntu install I did was about a week ago, it took approx 50 minutes.

Well then there was something wrong with your installation, maybe you should start a thread in the support forums so people with a clue can tell you what went wrong. I have installed Ubuntu 10.04, 10.10 and 11.04 on many PCs and the average time is something like 20 -25 mins. 
> 
So you are saying we shouldn't innovate, yeah that will work if your aim is to drop from a stellar 1% to 0.000000000000001%

When did I say that? It is a strawman that doesn't even worth responding to, and when has Linux stopped innovating? You just don't give it enough credit as is evinced by the pattern of your posts. If you want to cheer lead for the big boys, fine, but please don't try to pretend that the playing field is not rigged.

BTW, I have installed Ubuntu for friends who are just your everyday users, they have only good things to say about Ubuntu, at least as good as Windows if not better--only problem is they have never heard of it before because all computers they buy come with Windows, now if MS succeeds in pushing through this travesty they may not even be able to install or try Ubuntu in the first place. How to compete with more innovations? You want me to "innovate" a way to hack their laptops so I can boot a live usb? 

> If you had any understanding of sales and marketing you would see how innovation is very relevant in this thread. 

If you got artificially shut out of the market then all innovations are null, you need to have access first before people can try your product.

---

### Post by Quadunit404 on 2011-09-26
> **beew said:**
> The purpose of antitrust is exactly to prevent **monopolies** (which MS is on the desktop/laptop  market) from avoiding to "innovate and compete" by using unfair means to shut out competitors.

Please stop using that word; Microsoft's dominance over the home computer market is called a [mono*culture*]("https://secure.wikimedia.org/wikipedia/en/wiki/Monoculture_(computer_science)").

---

### Post by beew on 2011-09-26
> **Quadunit404 said:**
> Please stop using that word; Microsoft's dominance over the home computer market is called a [mono*culture*]("https://secure.wikimedia.org/wikipedia/en/wiki/Monoculture_(computer_science)").

As Dr. C explained a few pages back legally it certainly qualifies as such if it is in any other industry. In any case I fail to see the relevance of semantics. The point is it can leverage enough power to massively rig the market in its favour, thus stifling competition and innovations.

---

### Post by KiwiNZ on 2011-09-26
I am closing this thread for review by staff

---

### Post by s.fox on 2011-09-27
The thread will remain closed.

---

