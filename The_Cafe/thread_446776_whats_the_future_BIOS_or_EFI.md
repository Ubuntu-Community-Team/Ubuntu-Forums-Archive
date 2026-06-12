---
title: "whats the future? BIOS or EFI"
date: 2007-05-17
forum: The Cafe
---

### Post by racoq on 2007-05-17
We all know that apple is using it on their mac family.  

Apple claims it uses an "ultra-modern industry standard technology called EFI to handle booting. Sadly, Windows XP, and even Vista, are stuck in the 1980s with old-fashioned BIOS."

So after reading this i decided to visit the official EFI standard site from intel at this link:

[http://www.intel.com/technology/efi/](http://www.intel.com/technology/efi/)

And i've saw this

"EFI Specifications page was updated to include Microsoft related EFI specifications. The Presentations page was updated with Microsoft Winhec EFI presentations from 2004."

So if this technology is even supported by Microsoft since 2004, (who have been contributing to the standard EFI specification), and we are in 2007 and we still have the same old BIOS system that we have had for more than 20 years. So will we see the PC's architecture using the EFI instead of the same old legacy BIOS system in the future? 

Leave here your opinion an arguments also.

---

### Post by mips on 2007-05-17
How about [OpenBIOS]("http://openbios.info/Welcome_to_OpenBIOS") or [LinuxBIOS]("http://www.linuxbios.org/Welcome_to_LinuxBIOS") rather ???

---

### Post by BoyOfDestiny on 2007-05-17
> **mips said:**
> How about [OpenBIOS]("http://openbios.info/Welcome_to_OpenBIOS") or [LinuxBIOS]("http://www.linuxbios.org/Welcome_to_LinuxBIOS") rather ???

I'll take LinuxBIOS please :)

I do not want EFI! I've had enough BS from regular BIOSes as is...

"It is not really possible to build a full open-source BIOS if EFI is involved. The Tiano system, which Intel claims is an open source BIOS, can not be used to build a BIOS unless it is attached to proprietary, binary-only BIOS code provided by a vendor.

Another important thing to realize about EFI is that it also contemplates enabling chipset features that will trap certain OS operations to an EFI-based control system running in System Management Mode. In other words, under EFI, there is no guarantee that the OS owns the platform."

[http://www.fosdem.org/2007/interview/ronald+g+minnich](http://www.fosdem.org/2007/interview/ronald+g+minnich)

---

### Post by sicofante on 2007-09-08
It seems upcoming Vista SP1 will support EFI. Former lack of MS true support has been probably the number one reason for manufacturers not using EFI instead of BIOS. We should see more EFI motherboards next year since MS will be supporting it in Vista then.

I also wish GPT replaces Master Boot Record soon (I can dream, can't I?)

I'm not quite sure how much power EFI takes away from the user or the OS, but one thing is clear: BIOS is a prehistoric approach to booting and it needs replacement. LinuxBIOS, as with so other many things relating Linux, will be there when/if Linux reaches critical mass to entice manufacturers.

---

### Post by SunnyRabbiera on 2007-09-08
> **sicofante said:**
> 
I'm not quite sure how much power EFI takes away from the user or the OS, but one thing is clear: BIOS is a prehistoric approach to booting and it needs replacement.

well my philosophy is why fit it if it aint broken, there must be some valid reason why BIOS is still here after so long.
Its a old standard yes but by your reasoning we should have replaced the microchip by now.

---

### Post by Darkhack on 2007-09-08
EFI sounds like a big step forward, but the fact that it is so heavily locked up is quite scary.  Vendors can program their EFI so that we can only run the operating system they want us to, and they can lock us out from using certain hardware.  Imagine buying a computer that can only run Windows and you can only use your CD/DVD burner a few times a day to "prevent mass piracy".  I'll stick with BIOS until EFI becomes more open.  We need the Free Hardware Foundation to become just as well known as the Free Software Foundation and get companies to support open standards.

---

### Post by starcraft.man on 2007-09-08
If I knew the future, I'd be a millionaire... so no to the question, I don't know and can't vote on a guess.

That said, I agree with Darkhack. I don't want EFI if it's used as a means of restriction. I have no problems with BIOS at this time, and until there is a compelling useful feature to switch to EFI (that isn't about companies) and is open, I'll be staying with what I got.

---

### Post by sicofante on 2007-09-08
> **SunnyRabbiera said:**
> well my philosophy is why fit it if it aint broken,
It is broken. Booting a PC is a lot of hacking nowadays just because of BIOS, besides other number of issues.

>  there must be some valid reason why BIOS is still here after so long.
Microsoft didn't support anything else (EFI is many years old now). And because Microsoft will support EFI with Vista SP1 early next year, we will have EFI. Sad but that's how things are today.

> Its a old standard yes but by your reasoning we should have replaced the microchip by now.In fact we have replaced the "microchip" that powers our personal computers a good number of times already (unless you haven't heard of anything after the Intel 8086...)

):P

---

### Post by starcraft.man on 2007-09-08
> **sicofante said:**
> It is broken. Booting a PC is a lot of hacking nowadays just because of BIOS, besides other number of issues.


Excuse me but what exactly is this "hacking" your talking about? My BIOS works fine (after 5+ years I might add) with little effort, it does everything I need it to do. And it's not broke, it's limited (to be expected with such an old tech). Please use the right words.

I've seen some of the enhancements that EFI offers, which are welcome (and in some cases much needed). It doesn't come lightly though, and you shouldn't be so quick to move. From what I read up, EFI in conjunction with other new technologies being implemented will give the manufacturers and companies much more control over what exactly you can and more importantly can't do with your PC. It makes me uneasy.

In addition, with companies pushing for draconian restrictions against consumers, don't think they wouldn't try it. Just look at Vista... I am wary to say the least.

EDIT: HA! Forget about serious adoption of EFI in the short term sicofante... [EFI support is apparently only being delivered to 64 bit Vista. ]("http://en.wikipedia.org/wiki/Windows_Vista#Service_Pack_1")

---

### Post by BoyOfDestiny on 2007-09-08
> **starcraft.man said:**
> Excuse me but what exactly is this "hacking" your talking about? My BIOS works fine (after 5+ years I might add) with little effort, it does everything I need it to do. And it's not broke, it's limited (to be expected with such an old tech). Please use the right words.

I've seen some of the enhancements that EFI offers, which are welcome (and in some cases much needed). It doesn't come lightly though, and you shouldn't be so quick to move. From what I read up, EFI in conjunction with other new technologies being implemented will give the manufacturers and companies much more control over what exactly you can and more importantly can't do with your PC. It makes me uneasy.

In addition, with companies pushing for draconian restrictions against consumers, don't think they wouldn't try it. Just look at Vista... I am wary to say the least.

EDIT: HA! Forget about serious adoption of EFI in the short term sicofante... [EFI support is apparently only being delivered to 64 bit Vista. ]("http://en.wikipedia.org/wiki/Windows_Vista#Service_Pack_1")

I rather have an open BIOS any day too. I think a proprietary BIOS can be crappy, and Linux has to work around that (i.e. gee why doesn't this machine hibernate/suspend properly... broken ACPI implementation in the BIOS... Guess which company we can attribute much of that to... ;) )

Anyway, take a gander at my earlier post in the thread, the interview is interesting...

---

### Post by starcraft.man on 2007-09-08
> **BoyOfDestiny said:**
> I rather have an open BIOS any day too. I think a proprietary BIOS can be crappy, and Linux has to work around that (i.e. gee why doesn't this machine hibernate/suspend properly... broken ACPI implementation in the BIOS... Guess which company we can attribute much of that to... ;) )

Anyway, take a gander at my earlier post in the thread, the interview is interesting...

Oh didn't notice that link... off I go to read. Thanks for pointing it out.

---

### Post by Nano Geek on 2007-09-08
Is there any difference?

---

### Post by starcraft.man on 2007-09-08
> **asjdfwejqrfjcvm msz34rq33 said:**
> Is there any difference?

LOL! Course there is, if there weren't nobody would want to move to EFI. There are good (removal of limitations of BIOS) and bad changes (increased control of computer functions) though. Best to read up on differences yourself...

[EFI]("http://en.wikipedia.org/wiki/Extensible_Firmware_Interface")
[BIOS]("http://en.wikipedia.org/wiki/BIOS")

---

### Post by stmiller on 2007-09-08
BIOS is old and out of date. It must be almost 20 years old or more. EFI has many modern enhancements and is perhaps the direction hardware is heading.

But I've read bad stuff about EFI and DRM. A hardware manufacturer could set restrictions to what you can do with an EFI machine as far as operating system, content, or other things. Bleh.

---

### Post by starcraft.man on 2007-09-08
> **stmiller said:**
> BIOS is old and out of date. It must be almost 20 years old or more. EFI has many modern enhancements and is perhaps the direction hardware is heading.

But I've read bad stuff about EFI and DRM. A hardware manufacturer could set restrictions to what you can do with an EFI machine as far as operating system, content, or other things. Bleh.

It's not just EFI to add. Have you seen Intel's new vPro? TPM? A few others... It seems little seperate but it is growing and I fear there may be a day when it's no longer "your computer" but the "company's computer".

---

### Post by Polygon on 2007-09-08
bios is old a decrepit. EFI or some other modern thing is going to (and needs) to take its place.

---

### Post by Frak on 2007-09-09
(U)EFI is my favorite, it's very fast. I see it taking over BIOS very soon.

---

