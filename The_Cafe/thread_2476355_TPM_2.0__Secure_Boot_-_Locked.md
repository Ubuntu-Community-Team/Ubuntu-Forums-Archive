---
title: "TPM 2.0 / Secure Boot - Locked"
date: 2022-06-23
forum: The Cafe
---

### Post by Shibblet on 2022-06-23
A friend of mine was "trying out" Ubuntu in a dual-boot purpose.  He had Windows 11 on one partition, and Ubuntu on another.

This is the story...  He claimed that he booted into Windows 11 to play a couple of online games, and while he was in Windows, it did some updates in the background.

When he did a reboot, Windows said "wait while we install updates..."  You know, standard fare.

Then, his computer would not boot to Grub.  He forced the UEFI to boot from a specific partition, and it would not do that either.  So, he threw in a USB drive, with Ubuntu on it, and the computer again refused to boot from the USB Drive.  Blank Screens all around.

He could, however, boot to Windows 11.

So, he went into the BIOS to look at the settings.  All of the settings for Secure Boot, and TPM were locked, and could not be changed.  Secure Boot had an "Enabled" or "Disabled" option, but now says "Windows" instead.

I couldn't figure this out... the only conclusion I could come up with is that Microsoft dropped a Windows 11 update that locked his Secure Boot / TPM 2.0...  I mean, I'm saying this, but still in disbelief.

---

### Post by grahammechanical on 2022-06-23
It might be possible to use a utility in Windows to access the TPM settings. 

> Starting with Windows 10 and Windows 11, the operating system automatically initializes and takes ownership of the TPM.

[https://docs.microsoft.com/en-us/windows/security/information-protection/tpm/trusted-platform-module-overview](https://docs.microsoft.com/en-us/windows/security/information-protection/tpm/trusted-platform-module-overview)

Regards

---

### Post by Shibblet on 2022-06-23
> **grahammechanical said:**
> It might be possible to use a utility in Windows to access the TPM settings. 

[https://docs.microsoft.com/en-us/windows/security/information-protection/tpm/trusted-platform-module-overview](https://docs.microsoft.com/en-us/windows/security/information-protection/tpm/trusted-platform-module-overview)

Regards

He contacted the hardware manufacturer... I believe he said "Asus," (not Acer).

They claimed they were aware of the situation, and did not have a solution.  He said they claimed that they were "working" with Microsoft to find a solution.  But in the mean time, he would "have to" run his PC with only Windows 11.

---

### Post by #&amp;thj^% on 2022-06-23
> **Shibblet said:**
> He contacted the hardware manufacturer... I believe he said "Asus," (not Acer).

They claimed they were aware of the situation, and did not have a solution.  He said they claimed that they were "working" with Microsoft to find a solution.  But in the mean time, he would "have to" run his PC with only Windows 11.

This has happened a couple of times from my views: [https://docs.microsoft.com/en-us/windows/security/information-protection/tpm/manage-tpm-lockout](https://docs.microsoft.com/en-us/windows/security/information-protection/tpm/manage-tpm-lockout)

---

### Post by Shibblet on 2022-06-23
> **1fallen said:**
> This has happened a couple of times from my views: [https://docs.microsoft.com/en-us/windows/security/information-protection/tpm/manage-tpm-lockout](https://docs.microsoft.com/en-us/windows/security/information-protection/tpm/manage-tpm-lockout)

Thanks for the info... but I'm not sure this qualifies.

There have literally been changes in his computer BIOS.  He can't turn off Secure Boot, and cannot adjust his TPM settings in Bios anymore.  His Secure Boot used to say "Enabled" or "Disabled."  Now it just says "Windows," and is greyed out.  He's rebooted a multitude of times, and even gone so far as to unplug his computer and reset the BIOS.

---

### Post by #&amp;thj^% on 2022-06-23
> **Shibblet said:**
> Thanks for the info... but I'm not sure this qualifies.

There have literally been changes in his computer BIOS.  He can't turn off Secure Boot, and cannot adjust his TPM settings in Bios anymore.  His Secure Boot used to say "Enabled" or "Disabled."  Now it just says "Windows," and is greyed out.  He's rebooted a multitude of times, and even gone so far as to unplug his computer and reset the BIOS.

keep reading it tells how to fix that..
Their's also a "reg" hack he can use but I'll add a warning to this "Furthermore, by disabling the TPM 2.0 requirement, you are effectively reducing the security in Windows 11."
anyway look here as well: [https://www.bleepingcomputer.com/news/microsoft/how-to-bypass-the-windows-11-tpm-20-requirement/](https://www.bleepingcomputer.com/news/microsoft/how-to-bypass-the-windows-11-tpm-20-requirement/)
I'm aware this for Installing and bypassing TPM but it should still work for your friend's lockout.
Remember he's going to blame you, for listening to me, if things goes sideways...:lolflag:

---

### Post by Shibblet on 2022-06-23
> **1fallen said:**
> keep reading it tells how to fix that..
Their's also a "reg" hack he can use but I'll add a warning to this "Furthermore, by disabling the TPM 2.0 requirement, you are effectively reducing the security in Windows 11."
anyway look here as well: [https://www.bleepingcomputer.com/news/microsoft/how-to-bypass-the-windows-11-tpm-20-requirement/](https://www.bleepingcomputer.com/news/microsoft/how-to-bypass-the-windows-11-tpm-20-requirement/)
I'm aware this for Installing and bypassing TPM but it should still work for your friend's lockout.
He worked his way though this.

When it didn't work, he called Asus, and they told him that is not the issue.  Asus assured him that it was entirely a Microsoft Update, and that they were aware of the problem, and working on a solution.

I was listening to this conversation while he was on speaker-phone.  

He said "How long is this solution going to take?  I can't use my computer in the mean time."
They replied with "Well, you can use Windows."  He replied "Yeah, but I don't want to use Windows.  That's why I was running Ubuntu."
The man on the phone paused briefly, then said "We only support our Windows on our hardware.  IF you want to use Ubuntu, you'll have to troubleshoot that yourself."

He quickly replied with "Oh, so because you only support Windows, you are going to lock my computer to using only Windows?"

Another long pause...  "You don't *have* to use your computer until this is resolved *sir.*  We'll email you to let you know when we have a solution."

He just hung-up.  We just stared at each other "slack-jawed" for about a minute. 

> **1fallen said:**
> Remember he's going to blame you, for listening to me, if things goes sideways...:lolflag:
LOL!  I immediately thought that!  Like he was going to blame me for this whole thing!  Seeing as how I was the one that got him interested in Ubuntu.

Fortunately, he saw that this was entirely from Microsoft, and not Ubuntu at all.  He's been making comments like "How insecure is Microsoft, that they have to take control of your PC so that you can't use other OS's?" and "How many people has this happened to, and they don't even know it?"

---

### Post by #&amp;thj^% on 2022-06-23
Sounds like the normal reply, and easy out.....
**Note to Self: Do Not update windows for a spell. ;)**
EDIT: I can always find a challenge and accept it>>>>now I'm going to update my Windows Drive just to see. :P

---

### Post by #&amp;thj^% on 2022-06-23
That was easy, I just rolled back these two updates on my end.
(KB890830)
(KB5014668)
I'm back on linux, FTR there is NO dual boot here, two different Drives

---

### Post by Shibblet on 2022-06-24
Next Day Update:

Asus called him back, and told him that because he has a "Microsoft Pluton Processor" in his new computer, it will be locked to Windows only.  They are "not" creating a solution for this problem, as it falls outside their "support."

I looked into "Pluton" Processor, and found this:
[https://www.microsoft.com/security/blog/2020/11/17/meet-the-microsoft-pluton-processor-the-security-chip-designed-for-the-future-of-windows-pcs/]("https://www.microsoft.com/security/blog/2020/11/17/meet-the-microsoft-pluton-processor-the-security-chip-designed-for-the-future-of-windows-pcs/")

This may be a problem for Linux users.  You may no longer be able to buy whatever you want, and run Linux on it...

---

### Post by #&amp;thj^% on 2022-06-24
> **Shibblet said:**
> Next Day Update:

Asus called him back, and told him that because he has a "Microsoft Pluton Processor" in his new computer, it will be locked to Windows only.  They are "not" creating a solution for this problem, as it falls outside their "support."

I looked into "Pluton" Processor, and found this:
[https://www.microsoft.com/security/blog/2020/11/17/meet-the-microsoft-pluton-processor-the-security-chip-designed-for-the-future-of-windows-pcs/]("https://www.microsoft.com/security/blog/2020/11/17/meet-the-microsoft-pluton-processor-the-security-chip-designed-for-the-future-of-windows-pcs/")

This may be a problem for Linux users.  You may no longer be able to buy whatever you want, and run Linux on it...

Thanks for the link and this: Buyer Beware for Linux.
Microsoft is hardening right down to the real hardware it's ran on.
Makes sense if you think of this from a MS point of view.

---

### Post by Shibblet on 2022-06-24
> **1fallen said:**
> Thanks for the link and this: Buyer Beware for Linux.
Microsoft is hardening right down to the real hardware it's ran on.
Makes sense if you think of this from a MS point of view.

So, this seemed to arise from a Dual-Boot situation.  There are two SSD's in this PC, along with a regular HDD for storage purposes.
Windows 10/11 was installed on the primary SSD, and Ubuntu 22.04 was installed on the secondary.  Grub was used to choose which OS to boot into.

This happened after a boot into Windows, and an update.

Now, if a user was only using Windows, they probably wouldn't notice anything happened.

My primary concern, at this point, is the purchase of a New PC.  If SecureBoot and TPM are already locked down when you buy it, you may not be able to use Linux.

My secondary concern is manufacturers like StarLabs (are they still around), System76, and SlimBook...  They are Linux supporters... however, would this Pluton Processor force the computer to use Windows when it was purchased for the purposes of running Linux.  I mean, it sound dystopian to say "Dust off your Raspberry PI folks!  That's all you're gonna get!"

---

### Post by grahammechanical on 2022-06-26
> attackers have begun to innovate ways to attack it, particularly  in situations where an attacker can steal or temporarily [gain physical access to a PC]("https://pulsesecurity.co.nz/articles/TPM-sniffing").

The  owner of the machine certainly has physical access to the machine. Is  Microsoft including the owner as an attacker? Possibly. It is certainly  true that the security of the internet has been compromised by  owner/users running security weak versions of Windows and out of support  versions of Windows. Who is responsible for selling security vulnerable  computer operating systems? No prizes for pointing the finger in the  right direction.

I can see some advantage to businesses from this  development. But the owner/user should still be asked for informed  consent (authentication) before making this change. 

The StarLabs  Systems web site is still active. I nearly purchased one of their  laptops a few months ago but the model I chose was out of stock and I  need a new machine quickly so I purchased from Entroware. Both these  companies are UK based.

Regards

P.S. StarLabs are now offering laptops with Ubuntu 22.04 pre-installed. So, they are keeping up to date.

---

### Post by issh on 2022-06-26
This is bad news, eh? I thought maybe someone could have injected keys into the TPM chip using MOKUTIL, but this is a new monster here. I'm sure there will be people who buy a device and think they're going to just be able to install another OS onto it, but they'll realize they can't.

---

### Post by grahammechanical on 2022-06-27
My new laptop came with Ubuntu 20.04 pre-installed. The TPM is enabled and so is the SGX (Software Guard Extensions). These things in themselves do not prevent an OEM from installing Linux distributions.

This thread was started in reference to a Ubuntu user who found that he could not load Ubuntu after experiencing a Windows update. I understand that this often happens after Windows updates. I also understand that there are fixes that can be tried. I do not know if any of these fixes have been tried. I am yet to be convinced that the problem is caused by the Windows update making changes to the Pluton processor. After all, nothing stopped Ubuntu being installed in the first place.

Lenovo say this in regard to their machines with the AMD Ryzen 6000 series processors:

> AMD integrated Microsoft's Pluton design into its Ryzen 6000 chips,  which were just introduced at CES. AMD said its goal is to bring better  security to Windows PCs, and users can disable Pluton on machines that  follow AMD's reference firmware.

"AMD respects user choice and, as is typical with many other security  technologies, we provide the ability for a user to enable or disable  Pluton based on their preferences in our reference BIOS," an AMD  spokeswoman told *The Register*.


Pluton does not restrict Linux installation, and is a security component for Windows deployments, the spokeswoman added.

 "AMD Ryzen 6000 Series processors support Linux. AMD has closely  collaborated with Canonical (Ubuntu) and Red Hat to certify and optimize  OEM designs with their operating systems," she said.


[https://www.theregister.com/2022/01/20/microsoft_amd_pluton_lenovo/](https://www.theregister.com/2022/01/20/microsoft_amd_pluton_lenovo/)

Who knows what will happen in the future? But it seems to give reassurance regarding machines with Linux pre-installed. I am not so confident with machines that have Windows pre-installed. If Microsoft wants to block dual booting or running an OS from a USB memory stick then I cannot see manufacturers like Lenovo denying Microsoft demands.

This is information about Dell's position on Pluton:

[https://www.techradar.com/news/sorry-microsoft-dell-isnt-bothered-about-the-pluton-security-chip](https://www.techradar.com/news/sorry-microsoft-dell-isnt-bothered-about-the-pluton-security-chip)

> Dell has followed Lenovo in saying it won't be using [Microsoft&#8217;s Pluton technology (opens in new tab)]("https://www.techradar.com/news/microsofts-new-security-chip-will-not-lock-devices-to-windows-11-as-feared") to secure its products.

But as Intel hasn&#8217;t implemented it in its 12th-Gen Core processors (Alder Lake), Dell won&#8217;t be using it.




The  same things seem to be going on at Lenovo, at least partially, as it&#8217;s  new ThinkPad devices will also be powered by Intel&#8217;s chips. Those that  run on the AMD Ryzen 6000, however, will include Pluton, but it will be  disabled by default. Lenovo also has devices powered by Qualcomm&#8217;s  Snapdragon 8cx Gen3 chip, which will include Pluton.




Besides Lenovo, the other major laptop manufacturer, HP, is yet to confirm its stance on the Pluton technology.


Regards

---

### Post by #&amp;thj^% on 2022-06-27
After talking with a few Developers (Non Microsoft) they told me this only chip was made and and pressed for Microsoft only, they went as far to say that the  generic Pluton processor will not be locked to just Windows, except if your unlucky enough to get one with this criteria.
Meet the "Microsoft Pluton" processor &#8211; The security chip designed for the future of Windows PCs. Ah Rubbish just Rubbish
I don't think Microsoft gives the owner of the said chip enough credit, or the ability to think or make choices, so they will do it for you.
To me this says Linux has them a bit worried, and rightfully so. 
> Enabled or disabled

[B]PC makers have the option to ship their new Windows 11 PCs with Pluton either enabled or disabled though end users will also be able to reverse this decision if they want to.
[/B]
Microsoft's Pluton design was integrated into AMD's latest Ryzen 6000 (opens in new tab) chips but users will be able to disable the security chip on machines that follow the chipmaker's reference firmware. This can be done in the company's reference BIOS.

The Register also learned from a Lenovo spokesperson that Pluton will be disabled by default on the company's new Z13, Z16, T14, T16, T14s, P16s and X13 ThinkPads (opens in new tab) that feature Ryzen 6000-series processors. However, users will be able to enable Pluton themselves.

---

### Post by Shibblet on 2022-06-27
> **grahammechanical said:**
> The  owner of the machine certainly has physical access to the machine. Is  Microsoft including the owner as an attacker?
Well, if the owner is attempting to put a different OS on the machine, that could be viewed as an "attack" on the Microsoft OS.

> **grahammechanical said:**
> I can see some advantage to businesses from this  development. But the owner/user should still be asked for informed  consent (authentication) before making this change.
I wouldn't care if they did this with their own Microsoft Products...  It's no different than the iOS or MacOS license that says it's only "allowed" to be run on authentic Apple Products...  But, Microsoft is getting Chip and MoBo manufacturers to include these "Microsoft Only" options (Secure Boot, TPM, Pluton) as a STANDARD.  Will there be Manufacturers out there that will have alternatives?  And, if so, how good of a product will the alternative be?  

Asus may put out about 10 different Motherboards per year...  Maybe one of them, you know, the low-end, non-gamer, crap-tastic motherboard will come without TPM and Secure Boot... you know, for Linux users, because they don't really need good hardware, right?

Pardon me for being a bit overdramatic, but this reminds me of:

[ATTACH=CONFIG]290656[/ATTACH]

---

### Post by Shibblet on 2022-07-06
Well... there is an update to this story.

Apparently the hardware manufacturer was able to send him a "flash utility" that runs in Windows.  This utility would allow him to flash his bios back to factory defaults, and remove the "Windows" components.  

However, they told him specifically that he needs to choose one OS or another.  No dual booting.  in other words: Pick one, Windows or Ubuntu.  Because, if Microsoft does this again (and changes the way it works), the flash utility "may" not be able to fix it.

---

### Post by #&amp;thj^% on 2022-07-06
OMG I now love even more being Windows & Gates Free. ;)

---

### Post by agentl074 on 2022-07-19
I will never buy a computer with Microsoft's Pluton -- which only affects AMD's mobile processor line (at the present time). As far as I know, their desktop processors are fine. This is all very strange -- since AMD is a Canonical partner.

I believe -- as others have mentioned -- that so long as you only use Ubuntu (instead of Windows), you should be fine. As for games, I have found the latest online games to be fully supported with Ubuntu's Linux Kernel 5.15 LTS and Mesa 22 -- and even outperforming Windows by a significant margin (Asus Vivobook with AMD 5500U).

---

### Post by Shibblet on 2022-07-19
> **agentl074 said:**
> I will never buy a computer with Microsoft's Pluton -- which only affects AMD's mobile processor line (at the present time). As far as I know, their desktop processors are fine. This is all very strange -- since AMD is a Canonical partner.

I agree with you.  My concern is that this may become a standard, with no ability to stay away from it.

> **agentl074 said:**
> I believe -- as others have mentioned -- that so long as you only use Ubuntu (instead of Windows), you should be fine. As for games, I have found the latest online games to be fully supported with Ubuntu's Linux Kernel 5.15 LTS and Mesa 22 -- and even outperforming Windows by a significant margin (Asus Vivobook with AMD 5500U).

Yeah, this whole thread started because I dual boot...  If Microsoft has done this to other computers, chances are the owner would not even notice, as their computer would only be booting into Windows...
Regardless, it's happening, and be careful!  ;)

---

### Post by kurt18947 on 2022-07-19
Is this sort of behavior something the EU would be interested in? I can see enterprise IT being just fine with this behavior but if there's no way to disable this once the machine is removed from inventory it would make the refurbished ex-corporate market less attractive. Maybe there'll be more interest in [coreboot.]("https://www.coreboot.org/") Or some sort of utility to reverse or over ride the Microsoft crap. I imagine Microsoft will wait to see how much pushback there is. If there is significant pushback it'll be something like 
>  Oh gee, we're sorry we had no intention of removing consumer choice. We will issue a patch reversing this unintended behavior forthwith. or some crap like that.

---

### Post by agentl074 on 2022-07-19
> **Shibblet said:**
> I agree with you.  My concern is that this may become a standard, with no ability to stay away from it.



Yeah, this whole thread started because I dual boot...  If Microsoft has done this to other computers, chances are the owner would not even notice, as their computer would only be booting into Windows...
Regardless, it's happening, and be careful!  ;)


Excellent points... and this obviously an area of concern for many of us who are classified as 'enthusiasts'. I remember back in the day when microzoft was charged with antitrust violations in the US -- and won on appeal later on -- thereby ending the powerful enforcement of antitrust laws. This should worry a lot of people, but it doesn't.... 

[https://corporatefinanceinstitute.com/resources/knowledge/strategy/microsoft-antitrust-case/](https://corporatefinanceinstitute.com/resources/knowledge/strategy/microsoft-antitrust-case/)

---

### Post by arraybolt3 on 2022-08-07
Enable the 3rd Party UEFI Secure Boot CA. That should get him back up and running.

edit: Just realized that you already found a solution. But for anyone else in this thread who's scared of Microsoft killing the ability to run Linux, just look around in the BIOS for the 3rd Party UEFI Secure Boot CA switch. That should hopefully fix the problem (it's what got Ubuntu running on one of those Pluton-ified ThinkPads for the Phronix author the other day, [https://www.phoronix.com/review/rembrandt-linux-boot](https://www.phoronix.com/review/rembrandt-linux-boot)).

---

### Post by agentl074 on 2022-08-07
> **arraybolt3 said:**
> Enable the 3rd Party UEFI Secure Boot CA. That should get him back up and running.

edit: Just realized that you already found a solution. But for anyone else in this thread who's scared of Microsoft killing the ability to run Linux, just look around in the BIOS for the 3rd Party UEFI Secure Boot CA switch. That should hopefully fix the problem (it's what got Ubuntu running on one of those Pluton-ified ThinkPads for the Phronix author the other day, [https://www.phoronix.com/review/rembrandt-linux-boot](https://www.phoronix.com/review/rembrandt-linux-boot)).

Thank you :)

---

