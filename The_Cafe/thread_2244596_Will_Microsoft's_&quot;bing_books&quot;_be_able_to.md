---
title: "Will Microsoft's &quot;bing books&quot; be able to run Linux?"
date: 2014-09-17
forum: The Cafe
---

### Post by Dragonbite on 2014-09-17
Microsoft is coming out with a line of cheap laptops ("bing books") to compete with Google's Chromebooks and honestly I think it is going to be a fail.

What I wonder, however, is whether these systems can be bought for cheap (when they drop it down from $300 to maybe $200 or less), am I able to toss Linux on it for a portable & cheap Ubuntu system?

I know it will largely matter what is running on it, I guess. I cannot find the link to the article I know of which mentions Dell's "chromebook-killer" is coming out soon but at $100 more than they had hope ($299 instead of $199).

I'm talking about laptops, just to be clear. I don't now anything about tablets, and installing on tablets, at this point.

---

### Post by tgalati4 on 2014-09-17
Microsoft generally makes decent hardware.  So if the price is right and if you can put your own OS on it, then that might be a win.  But, I think the boot loader will be locked down to prevent that.  If MS puts enough money behind it, they can penetrate any market.  Look at the latest Windows phones--decent hardware (provided by Nokia) and a goofy OS.  Some people like them.

---

### Post by Dragonbite on 2014-09-17
I have an old Netbook that came with Vista "Basic"... yeah, that lasted maybe 15 minutes and most of that time was spent waiting for it to boot up one time to see what was on it (my brother gave it to me).  Now it is running Xubuntu 14.04 and while low-powered, it does the job (being a portable laptop that is easy to carry to meetings and such for notes).

I don't know if they can lock down much more the EUFI does and I think Ubuntu, Fedora and some other major distros can work with that.  Otherwise, switch it to use the older BIOS on first boot.

---

### Post by Erik1984 on 2014-09-17
If it's just x86 hardware I don't see why not. They might even be easier to put Linux on than Chrombooks :P

---

### Post by Dragonbite on 2014-09-17
Could be interesting if they come out with ARM chipped computers for Windows, though  I think that will require Windows RT. Though cheap computers running Windows RT to compete with Chromebooks sounds like it should be the way to compete (Win RT for the low-end market and tablets, Win Pro for the upper end computers and tablets market) I am pretty sure they are using x86_64 based chips.

Even with that, though, my Netbook is running an AMD chip (don't remember which one) and its Linux support is spotty at times, but still completely adequate.

---

### Post by grahammechanical on 2014-09-17
It is not unknown for OEMs to deliberately not follow industry standards. An example of this is to use a 32 bit UEFI on a 64 bit CPU machine and making it next to impossible to install Linux. But then there is this which gives hope:

> [COLOR=#252525][FONT=sans-serif]As of version 3.15, [/FONT][/COLOR][Linux kernel]("http://en.wikipedia.org/wiki/Linux_kernel")[COLOR=#252525][FONT=sans-serif] supports booting of 64-bit kernels on 32-bit UEFI firmware implementations running on [/FONT][/COLOR][x86-64]("http://en.wikipedia.org/wiki/X86-64")[COLOR=#252525][FONT=sans-serif] CPUs, with [/FONT][/COLOR]*UEFI handover support from a UEFI boot loader as the requirement.[SUP][[21]]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-22")[/SUP]UEFI handover protocol deduplicates the UEFI initialization code between the kernel and UEFI boot loaders, leaving the initialization to be performed only by the Linux kernel's [I]UEFI boot stub.*[/I]

[SIZE=2]The quote is from the section Processor Compatibility.[/SIZE]

[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

"Deduplicates." A new word to add to my vocabulary, Get an idea of the scale of this particular problem and do not expect OEMs to make things easy for those of us who want a different OS to what they are selling. Not when they are under pressure from a corporation that can spend big.

[http://askubuntu.com/questions/392719/32-bit-uefi-boot-support](http://askubuntu.com/questions/392719/32-bit-uefi-boot-support)

Regards.

---

### Post by endlessinstant on 2014-09-18
Assuming issues related to UEFI won't make installing Linux needlessly difficult, I suspect the right distro will only increase the value of these bingbooks.   I've gone exclusive to chromebooks for a couple years now and they are great for Linux.  Granted that is in large part because Chrome OS is built on gentoo so it's Linux already.  I'm very excited for bingbooks, not because I particularly want a low-end Windows laptop but because it might be the solution for getting a decent standard keyboard at a rock bottom price.

---

