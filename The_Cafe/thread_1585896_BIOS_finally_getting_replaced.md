---
title: "BIOS finally getting replaced?"
date: 2010-10-01
forum: The Cafe
---

### Post by Naiki Muliaina on 2010-10-01
Saw this on the BBC website today, thought it was a good read.

[http://www.bbc.co.uk/news/technology-11430069](http://www.bbc.co.uk/news/technology-11430069)

Would be nice if we had PC's booting almost instant on. My Jaunty install was going from Grub to Desktop in less than 10 seconds I think... No BIOS bit would be eeks fast! :)

---

### Post by Lucradia on 2010-10-01
Goodbye BIOS. :(

---

### Post by Sslaxx on 2010-10-01
[http://ubuntuforums.org/showthread.php?t=1572745](http://ubuntuforums.org/showthread.php?t=1572745) - been talked about on these forums before.

---

### Post by Tibuda on 2010-10-01
I heard on those forums before that you don't really need a BIOS if you are running Linux. "GRUB and the kernel take care of the work that the BIOS would normally take care of". :popcorn:

---

### Post by Lucradia on 2010-10-01
> **Tibuda said:**
> I heard on those forums before that you don't really need a BIOS if you are running Linux. "GRUB and the kernel take care of the work that the BIOS would normally take care of". :popcorn:

When using some video cards though, you need the BIOS to set PCI first, as well as to change boot order (CD-ROM nowadays is put below the first harddrive for the boot order, by default.)

---

### Post by Tibuda on 2010-10-01
> **Lucradia said:**
> When using some video cards though, you need the BIOS to set PCI first, as well as to change boot order (CD-ROM nowadays is put below the first harddrive for the boot order, by default.)

that was a joke. see the :popcorn:

---

### Post by Lucradia on 2010-10-01
> **Tibuda said:**
> that was a joke. see the :popcorn:

jokes =/= sarcasm

---

### Post by blueturtl on 2010-10-01
Macs have had EFI since the early 00's. I wonder what has kept the PC industry locked to BIOS for so long...

This is going to be a big change for those of us who've been using PCs since they were introduced. Not seeing that memory counter right at first... Oh dear. Times change. :D

---

### Post by ssam on 2010-10-01
my desktop take long to get from power button to grub, than grub to login. its a tyan S2696 (workstation/server board). i have a slight temptation to try coreboot, but too scared.

---

### Post by ubunterooster on 2010-10-01
*whew*
I am so ready to get rid of the BIOS

---

### Post by endotherm on 2010-10-01
see, I like the BIOS, just because it is not controlled by OS manufactures. that in itself provides us options for dealing with more the tyrannical vendors that shoot for "Trusted Computing". without a bios how would you build a PC from scratch? without a bios how would you boot from Floppy/CD/USB/Network?

---

### Post by ubunterooster on 2010-10-01
The UEFI takes care of the same functions

---

### Post by psusi on 2010-10-01
> **blueturtl said:**
> Macs have had EFI since the early 00's. I wonder what has kept the PC industry locked to BIOS for so long...


In a word, Windows.  Windows doesn't boot using EFI, so manufacturers have had to keep around the BIOS.

---

### Post by Roasted on 2010-10-01
> **blueturtl said:**
> Macs have had EFI since the early 00's. I wonder what has kept the PC industry locked to BIOS for so long...

This is going to be a big change for those of us who've been using PCs since they were introduced. Not seeing that memory counter right at first... Oh dear. Times change. :D

If that's the case, why do Macs boot just as fast as standard Windows/Linux PCs with BIOS? I have seen *zero* obvious boot differences from my Mac laptop to my work laptop or desktop at home.

---

### Post by psusi on 2010-10-01
> **Roasted said:**
> If that's the case, why do Macs boot just as fast as standard Windows/Linux PCs with BIOS? I have seen *zero* obvious boot differences from my Mac laptop to my work laptop or desktop at home.

Because you are comparing apples to oranges.  The time between power on and OSX *starting* to boot is much less than the time between power on and when grub gets control from the bios.

---

### Post by NCLI on 2010-10-01
The good news: No more agonizingly slow BIOS loading!!!
The bad news: Now I'll have to postpone buying a new laptop :(

---

### Post by Roasted on 2010-10-01
> **psusi said:**
> Because you are comparing apples to oranges.  The time between power on and OSX *starting* to boot is much less than the time between power on and when grub gets control from the bios.

I know I'm comparing apples to oranges, and I understand that OSX's boot process may seem more streamlined. But here's the catch.

Power on to login screen = nearly identical on Mac vs Linux vs Windows. Nothing stands out. I was just wondering if this new thing is "that good" and if Mac already has had it for a decade why it didn't seem any better on Mac at this time.

---

### Post by Naiki Muliaina on 2010-10-01
> **Sslaxx said:**
> [http://ubuntuforums.org/showthread.php?t=1572745](http://ubuntuforums.org/showthread.php?t=1572745) - been talked about on these forums before.

That's not discussing BIOS being replaced ;)

---

### Post by blueturtl on 2010-10-01
When it comes to boot speed, I guess BIOSes have been improved over the ages.

I know for certain that older systems had a considerable boot delay, especially if you had to wait through a full memory test.
My HTPC on the other hand; I can't even see the BIOS boot information before it get's to GRUB. They have all sorts of things today to make BIOS boot faster.

EFI does bring other benefits, though the article seems to indicate these benefits are mostly seen by system builders. Regular users probably won't be able to tell if a BIOS is used or not under normal circumstances.

---

### Post by psusi on 2010-10-01
> **Roasted said:**
> I know I'm comparing apples to oranges, and I understand that OSX's boot process may seem more streamlined. But here's the catch.

Power on to login screen = nearly identical on Mac vs Linux vs Windows. Nothing stands out. I was just wondering if this new thing is "that good" and if Mac already has had it for a decade why it didn't seem any better on Mac at this time.

Then it sounds like OSX takes longer to boot that Linux or Windows.

These days Ubuntu makes it from grub to desktop in about 10 seconds, but power on to grub is typically 10-15 seconds.  If an EFI system can get that time down to 5 seconds, then that will mean at least 25% faster total boot time.

---

### Post by pizza-is-good on 2010-10-01
My BIOS takes about 5 seconds to boot.

UEFI sounds interesting, but a) how will that work with GRUB (I saw it called a bootloader)? and b) how can the boot time go to 0 if the OS still has to load?

---

### Post by mips on 2010-10-01
> **pizza-is-good said:**
> 
UEFI sounds interesting, but a) how will that work with GRUB (I saw it called a bootloader)?

Grub2 has EFI support.

---

### Post by pizza-is-good on 2010-10-01
> **mips said:**
> [QUOTE=pizza-is-good;9912841]
UEFI sounds interesting, but a) how will that work with GRUB (I saw it called a bootloader)?

Grub2 has EFI support.[/QUOTE]

Well then, no more concerns from me. When are computers going to start using it?

---

### Post by psusi on 2010-10-01
I hear all newer Intel motherboards support it.

---

### Post by Windows Nerd on 2010-10-02
Will my PS/2 Keyboard which I _refuse_ to replace still work with this? What about my super old printer that uses a serial port (it still works!)?

What about floppy drives?

Will this UEFI be friendly to overclockers?

The BIOS is really old, but as long as they continue support for the old stuff I have no problem.

---

### Post by Paddy Landau on 2010-10-02
How do you pronounce UEFI?

"Wee-fee" would be good as a counter-point to Wi-fi.

---

### Post by lisati on 2010-10-02
> **ubunterooster said:**
> The UEFI takes care of the same functions
^^^ This
Regardless of how the technology changes, I anticipate a need for providing some kind of basic functionality that helps get the bootloader (and its successors) started for some time yet.
> **Paddy Landau said:**
> How do you pronounce UEFI?

"Wee-fee" would be good as a counter-point to Wi-fi.
Something similar to "way-fee" comes to mind, partly due to my regularly associating with speakers of Maori and Samoan.

---

### Post by tadcan on 2010-10-02
Will this make it easier to install mac OSX on a standard PC.

---

### Post by 3rdalbum on 2010-10-02
> **blueturtl said:**
> Macs have had EFI since the early 00's. I wonder what has kept the PC industry locked to BIOS for so long...

Macintoshes have had EFI since the transition to Intel processors, in 2006. Before that, they used Open Firmware.

> Will this make it easier to install mac OSX on a standard PC.

Yes, probably, but you're missing the point. EFI is a lot more flexible, a lot more modern. For instance, I don't believe you can use a Bluetooth keyboard to change settings in your BIOS - with EFI you can, because it's much less basic and much more fully-featured.

---

### Post by mobilediesel on 2010-10-02
I've been reading about EFI replacing BIOS "within the next couple years" for almost 15 years now.

---

### Post by ubunterooster on 2010-10-02
> **mobilediesel said:**
> I've been reading about EFI replacing BIOS "within the next couple years" for almost 15 years now.
It did for Macintoshes, from what I hear

---

### Post by ubunterooster on 2010-10-02
[http://www.uefi.org/about/](http://www.uefi.org/about/)

**Q:** [B]How does UEFI differ from BIOS? 

[/B]A: The Basic Input/Output System (BIOS) served as the OS-firmware  interface for the original PC-XT and PC-AT computers. This interface has  been expanded over the years as the "PC clone" market has grown, but  was never fully modernized as the market grew. UEFI defines a similar  OS-firmware interface, known as "boot services" and "runtime services",  but is not specific to any processor architecture. BIOS is specific to  the Intel x86 processor architecture, as it relies on the 16-bit "real  mode" interface supported by x86 processors.  

 **Q:** [B]Does UEFI completely replace a PC BIOS?

[/B]A: No. While UEFI uses a different interface for "boot services" and  "runtime services", some platform firmware must perform the functions  BIOS uses for system configuration (a.k.a. "Power On Self Test" or  "POST") and Setup. UEFI does not specify how POST & Setup are  implemented.   

 **Q:** **How is UEFI implemented on a computer system? **  

A: UEFI is an interface. It can be implemented on top of a traditional  BIOS (in which case it supplants the traditional "INT" entry points into  BIOS) or on top of non-BIOS implementations.

---

### Post by Sslaxx on 2010-10-02
> **ubunterooster said:**
>  [B]Q: Does UEFI completely replace a PC BIOS?

[/B]A: No. While UEFI uses a different interface for "boot services" and  "runtime services", some platform firmware must perform the functions  BIOS uses for system configuration (a.k.a. "Power On Self Test" or  "POST") and Setup. UEFI does not specify how POST & Setup are  implemented.

So BIOS is really only being mostly replaced. So it's not being replaced altogether just yet.

---

### Post by cascade9 on 2010-10-02
> **ubunterooster said:**
> [QUOTE=mobilediesel;9915611]I've been reading about EFI replacing BIOS "within the next couple years" for almost 15 years now.
It did for Macintoshes, from what I hear[/QUOTE]

Not really...the PPC Macs didnt use BIOS (they used open firmwear) then when apple moved to intel based macs, they used EFI. 

A cynical (or prehaps realistic) view is that appple used EFI because it made it easier for them to 'lock' the hardware, stopping people using cheap, standard x86 parts on the systems.

---

### Post by mobilediesel on 2010-10-02
> **ubunterooster said:**
> It did for Macintoshes, from what I hear

True enough. I can certainly agree that BIOS probably SHOULD have been replaced back when I first heard of EFI (now UEFI). Microsoft tried to eliminate all the IRQ setup with Plug-n-Play when they should have been telling hardware makers to do something different.

---

### Post by psusi on 2010-10-02
> **mobilediesel said:**
> True enough. I can certainly agree that BIOS probably SHOULD have been replaced back when I first heard of EFI (now UEFI). Microsoft tried to eliminate all the IRQ setup with Plug-n-Play when they should have been telling hardware makers to do something different.

You seem to be under the impression that EFI somehow means there doesn't need to be any plug and play configuration of system resources including IRQs.  That would be incorrect.

---

### Post by bash on 2010-10-02
> **mobilediesel said:**
> I've been reading about EFI replacing BIOS "within the next couple years" for almost 15 years now.

Yea probably right around the time, when there is an organised and coordinated switch to IPv6.

---

### Post by mobilediesel on 2010-10-02
> **psusi said:**
> You seem to be under the impression that EFI somehow means there doesn't need to be any plug and play configuration of system resources including IRQs.  [COLOR="Blue"]That would be incorrect[/COLOR].

[COLOR="Blue"][citation needed][/COLOR]

---

### Post by psusi on 2010-10-02
> **bash said:**
> Yea probably right around the time, when there is an organised and coordinated switch to IPv6.

Since EFI is already here, I'd say it's got IPv6 beat.

---

### Post by limestone on 2010-10-04
According to the swedish magazine IDG.se [http://www.idg.se/2.1085/1.343697/slutet-nara-for-bios](http://www.idg.se/2.1085/1.343697/slutet-nara-for-bios) BIOS is going to be replaced after new year! They say that BIOS have been the main start program for 25 years and is now 2011 being replaced with the new "uefi", (unified extensible firmware interface), which supposed to be faster and supports more functionality. One is an hard drive wipe out function. Fujitsu that develop their own motherboard will be fast on the transfer to uefi.

Personally, I hope the new system will act like those on Apple computers. They are fast and don't flash you 200 info-screens before boot up.

---

### Post by CharlesA on 2010-10-04
Threads merged.

---

### Post by psusi on 2010-10-04
> **mobilediesel said:**
> [COLOR="Blue"][citation needed][/COLOR]

How about you come up with one.  Hardware still has interrupt requests, io ports, and memory that that has to be assigned.  Mechanisms for doing this are part of the PCI bus specification, which isn't going away.

---

### Post by Calash on 2010-10-04
> **psusi said:**
> Since EFI is already here, I'd say it's got IPv6 beat.

IPv6 is here.  Google has already shifted several of it's main sites over, as have several ISP's.  Connections between IPv4 and IPv6 are already in place allowing you to convert your house while maintaining the old connectivity.

The real push will be in the next couple of years when we start running out of IPv4 addresses.  The estimate is 2012.  At that point we are going to see a huge push by web service providers and ISP's.

I never got the reason to move from BIOS myself. There is a level of flexibility that I miss any time I work on a Mac.

---

### Post by psusi on 2010-10-04
There has been an experimental ip6 network for years, tunneled over the IP4 backbones, but AFAIK, none of the major backbones have yet started routing ip6 and my cable company doesn't.

---

### Post by del_diablo on 2010-10-04
> **ubunterooster said:**
> [http://www.uefi.org/about/](http://www.uefi.org/about/)
 **Q:** [B]Does UEFI completely replace a PC BIOS?

[/B]A: No. While UEFI uses a different interface for "boot services" and  "runtime services", some platform firmware must perform the functions  BIOS uses for system configuration (a.k.a. "Power On Self Test" or  "POST") and Setup. UEFI does not specify how POST & Setup are  implemented.  

The hard truth? Vendor must find a way to do POST & Setup themself.
So yeah, it replaces BIOS.

> **Windows Nerd said:**
> Will my PS/2 Keyboard which I _refuse_ to replace still work with this? What about my super old printer that uses a serial port (it still works!)?

What about floppy drives?

Will this UEFI be friendly to overclockers?

The BIOS is really old, but as long as they continue support for the old stuff I have no problem.

Your PS/2 keyboard should be fine after using a convertor device.
The printer will be fine, if you can get a USB serial port and drivers.
Floopies will also be fine, if you can hook it somewhere.

UEFI just replaces BIOS, so how could it be unfriendly? Same ****, and dropping of several ages of not needed clobbering legacy.

---

### Post by endotherm on 2010-10-04
> **del_diablo said:**
> 
UEFI just replaces BIOS, so how could it be unfriendly? Same ****, and dropping of several ages of not needed clobbering legacy.

well, the bios presents a limitation to the vendors of software, because they have to coexist with it. that means we have a layer where they are not in control. there have been several occasions where having control of my bios has allowed me to skirt some of the locks and limitations imposed by higher layer software. 

There are a number of vendors including the dominant OS vendor, who would love to sell you a "computer" that they control top to bottom, to prevent you from doing things like installing linux...

not saying UEFI is bad, just saying the BIOS is one of those things that may save us from "Trusted Computing" by virtue of the fact that no one party controls them, and that they are impossible to avoid.

---

### Post by psusi on 2010-10-04
> **endotherm said:**
> 
not saying UEFI is bad, just saying the BIOS is one of those things that may save us from "Trusted Computing" by virtue of the fact that no one party controls them, and that they are impossible to avoid.

Not really.  Trusted computing can be ( and has been ) implemented with BIOS as easily as EFI.  They also do not differ any in level of "control"; they are both controlled by the manufacturer of your motherboard.  The difference is that one is a pile of hacks, extensions, and kludges to a crippled 16 bit firmware dating back to the apple IIe days, and the other is properly designed interface that is 64 bit when on a 64 bit cpu.

---

### Post by mobilediesel on 2010-10-04
> **psusi said:**
> How about you come up with one.  Hardware still has interrupt requests, io ports, and memory that that has to be assigned.  Mechanisms for doing this are part of the PCI bus specification, which isn't going away.

You said I was wrong and provided no info as to why I'm wrong.

---

### Post by cprofitt on 2010-10-04
> **psusi said:**
> In a word, Windows.  Windows doesn't boot using EFI, so manufacturers have had to keep around the BIOS.


Windows XP was capable of EFI booting -- and so was Vista and WIndows 7.

---

### Post by psusi on 2010-10-04
> **mobilediesel said:**
> You said I was wrong and provided no info as to why I'm wrong.

You just quoted it:  hardware resources including IRQs aren't going anywhere, they are part of the PCI bus specification.

> **cprofitt said:**
> Windows XP was capable of EFI booting -- and so was Vista and WIndows 7.

No, they aren't, which is why apple had to make rEFIt, which emulates a bios system on EFI so an intel mac and boot windows.

---

### Post by mobilediesel on 2010-10-04
> **psusi said:**
> You seem to be under the impression that EFI somehow means there doesn't need to be any plug and play configuration of system resources including IRQs.  That would be incorrect.
UEFI is abstracting all of that so the OS doesn't have to do anything about it.
> **psusi said:**
> How about you come up with one.  Hardware still has interrupt requests, io ports, and memory that that has to be assigned.  Mechanisms for doing this are part of the PCI bus specification, which isn't going away.
The OS doesn't have to do any of that with UEFI.
> **psusi said:**
> You just quoted it:  hardware resources including IRQs aren't going anywhere, they are part of the PCI bus specification.
Who said hardware resources were going away?

---

### Post by psusi on 2010-10-04
> **mobilediesel said:**
> UEFI is abstracting all of that so the OS doesn't have to do anything about it.

No, it doesn't.  ACPI is still used to describe and control the hardware power management and assign io, memory, and irq resources.  EFI just provides a different mechanism to pass the ACPI tables to the OS at boot time rather than calling a bios interrupt to get the root DSDT pointer.

> **mobilediesel said:**
> 
The OS doesn't have to do any of that with UEFI.


See above.

---

### Post by mobilediesel on 2010-10-04
> **psusi said:**
> No, it doesn't.  ACPI is still used to describe and control the hardware power management and assign io, memory, and irq resources.  EFI just provides a different mechanism to pass the ACPI tables to the OS at boot time rather than calling a bios interrupt to get the root DSDT pointer.

See above.

[http://www.uefi.org/specs/](http://www.uefi.org/specs/)

---

### Post by psusi on 2010-10-04
> **mobilediesel said:**
> [http://www.uefi.org/specs/](http://www.uefi.org/specs/)

And?

---

### Post by mobilediesel on 2010-10-04
> **psusi said:**
> And?

and if you're not going to read that and tell me where I'm wrong, I'll unsubscribe from this thread.

---

### Post by BuffaloX on 2010-10-05
> **blueturtl said:**
> When it comes to boot speed, I guess BIOSes have been improved over the ages.

I know for certain that older systems had a considerable boot delay, especially if you had to wait through a full memory test.
My HTPC on the other hand; I can't even see the BIOS boot information before it get's to GRUB. They have all sorts of things today to make BIOS boot faster.

EFI does bring other benefits, though the article seems to indicate these benefits are mostly seen by system builders. Regular users probably won't be able to tell if a BIOS is used or not under normal circumstances.

Mine (Abit AN9) takes 18 seconds just to get to Grub.
I have disabled everything I don't use, tried manual PCI config nothing helps.
I refuse to buy anything this slow ever again, but no Mobo vendor I can find state post times, or any other measure of how fast the BIOS is.

I would be very interested to hear what make your Bios and Mobo are.

---

### Post by blueturtl on 2010-10-05
> **BuffaloX said:**
> Mine (Abit AN9) takes 18 seconds just to get to Grub.
I have disabled everything I don't use, tried manual PCI config nothing helps.
I refuse to buy anything this slow ever again, but no Mobo vendor I can find state post times, or any other measure of how fast the BIOS is.

I would be very interested to hear what make your Bios and Mobo are.

I'm using a Fujitsu Scaleo EVI2535 that has a FIC PTBG965SFN-LF motherboard. Unfortunately this is a non-retail motherboard, or at least I have not been able to find anything related to this board outside of the Fujitsu support pages.

There are good sides and bad to this: I can barely get a glimpse of the Fujitsu Siemens logo before I'm off to GRUB, but on the other hand the BIOS has no updates available and very few settings to tinker with.

I think the problem you have may be related to all the fancy stuff they have on the new mobos. With many integrated controller firmwares to cycle through, the boot sequence can get quite lengthy.

---

### Post by psusi on 2010-10-05
> **mobilediesel said:**
> and if you're not going to read that and tell me where I'm wrong, I'll unsubscribe from this thread.

I already did.  You can also go actually boot an EFI system, like my wife's macbook, and poke about in /proc and /sys and still see all of the pci/acpi knobs, including those for hardware resource assignment, or run lspci and setpci to reconfigure them.

If you don't care to listen, then by all means, unsubscribe.

---

### Post by psusi on 2010-10-05
> **blueturtl said:**
> 
I think the problem you have may be related to all the fancy stuff they have on the new mobos. With many integrated controller firmwares to cycle through, the boot sequence can get quite lengthy.

Bingo.  Especially since it has to do it all one step at a time since it's running in real 16 bit 8086 mode.  Would be nice if it would initialize all the hardware in parallel.

---

### Post by 98cwitr on 2010-10-05
it's about freakin time. Loading BIOS is the longest process in my boot sequence. Now if we can keep a running list of UEFI motherboards that'd be great.

---

### Post by whiskeylover on 2010-10-05
> **mobilediesel said:**
> and if you're not going to read that and tell me where I'm wrong, I'll unsubscribe from this thread.

> **psusi said:**
> ...

If you don't care to listen, then by all means, unsubscribe.

Yay, internet warz :popcorn:

---

### Post by endotherm on 2010-10-05
> **whiskeylover said:**
> Yay, internet warz :popcorn:
no doubt. what happened to the good old days when arguments were godwinned long before they got this annoying.

---

### Post by CharlesA on 2010-10-05
> **endotherm said:**
> no doubt. what happened to the good old days when arguments were godwinned long before they got this annoying.

I lol'd.

FYI: Stick to the CoC, else the thread is going to be closed.

Not directed at you, endotherm, but everything in the thread.

---

### Post by BuffaloX on 2010-10-05
> **blueturtl said:**
> I'm using a Fujitsu Scaleo EVI2535 that has a FIC PTBG965SFN-LF motherboard.
I think the problem you have may be related to all the fancy stuff they have on the new mobos. With many integrated controller firmwares to cycle through, the boot sequence can get quite lengthy.

Thanks for the info, too bad it's probably some custom Fujitsu thing.

I don't think it's much about the amount of advanced hardware, but rather the amount of single threaded 16 bit code, that just sit around waiting for timeout.

---

