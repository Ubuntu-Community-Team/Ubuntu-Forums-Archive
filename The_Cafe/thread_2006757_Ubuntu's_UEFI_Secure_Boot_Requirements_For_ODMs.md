---
title: "Ubuntu's UEFI Secure Boot Requirements For ODMs"
date: 2012-06-19
forum: The Cafe
---

### Post by newbie2 on 2012-06-19
[QUOTE="Swapnil Bhartiya"]Does that mean you will have the same restrictions on a Ubuntu pre-installed machines as you will have on a Windows machine? Does it mean you won't be able to boot any other OS of your choice on a Ubuntu PC?[/QUOTE]
[http://www.muktware.com/3709/ubuntus-uefi-secure-boot-requirements-odms](http://www.muktware.com/3709/ubuntus-uefi-secure-boot-requirements-odms)
[http://mjg59.dreamwidth.org/13713.html](http://mjg59.dreamwidth.org/13713.html)
:rolleyes:

---

### Post by MadmanRB on 2012-06-19
Another reason why secure boot sucks I suppose

---

### Post by Bandit on 2012-06-19
> **MadmanRB said:**
> Another reason why RESTRICTED boot sucks I suppose

Fixed :D

---

### Post by Dr. C on 2012-06-19
The key difference is on computers with ARM processors where Canonical is mandating the abilitiy of the owner of the computer to 
1) Disable secure boot
2) Install their own keys or those of a trusted (by the owner of the computer) third party in a custom secure boot environment.

Microsoft has specifically mandated lockdown of computers with ARM processors to prevent the owner of the computer from doing 1 and 2 above. This is a huge difference.

---

### Post by jwbrase on 2012-06-20
The article says: > In a nutshell, the requirements for secure boot are:
The system must have an Ubuntu key preinstalled in each of KEK and db
It must be possible to disable secure boot
It must be possible for the end user to reconfigure keys

It's basically the same set of requirements as Microsoft have, except with an Ubuntu key instead of a Microsoft one.

But I have *never* heard anything said about Microsoft requiring that the user be able to reconfigure keys on Win8/x86, as the above implies.

Can anyone confirm whether MS does in fact require this?

The user being able to reconfigure keys is the critical factor here, so if Microsoft *is* in fact requiring that for Win8/x86, then everything's fine and we should shut up and leave Microsoft and Canonical alone about secure boot: They're both providing the ability for the user to determine what software will and won't boot, and every article talking about secure boot on the x86 is FUD. (We still ought to get on MS's case about Win8/ARM though).

If Microsoft is *not* requiring that the user be able to reconfigure keys for Win8/x86 machines, then this quip from the article is a flat-out falsehood: > That is, a certified Ubuntu system may be more locked down than a certified Windows 8 system.

If Microsoft isn't requiring key reconfigurability and Canonical is, then being Ubuntu certified makes a greater guarantee of not-locked-down-ness than being Win8 certified does.

Remember, Secure Boot is a good thing, and actually does make systems more secure, *as long as the owner of the machine is in full control of the Secure Boot policy*. It only becomes a vulnerability when the owner does not have full control. Whether the system is by default configured to only boot Win8 or only boot Ubuntu doesn't matter. What matters is that the user can change the defaults without disabling secure boot entirely.

---

### Post by MadmanRB on 2012-06-20
> **jwbrase said:**
> The article says: 


Remember, Secure Boot is a good thing

No, it isnt, its just another wqay for Microsoft to lock down computers to use windows only limiting the option to use alternate OS's.
The only good it does is for microsofts wallet.

---

### Post by azangru on 2012-06-20
> That is, a certified Ubuntu system may be more locked down than a certified Windows 8 system. 
*Why* exactly is Ubuntu doing this at all? I can understand Microsoft being a d-ck - but for Ubuntu to act in this way - ? What's the purpose?

---

### Post by AllRadioisDead on 2012-06-20
> **azangru said:**
> *Why* exactly is Ubuntu doing this at all? I can understand Microsoft being a d-ck - but for Ubuntu to act in this way - ? What's the purpose?

Microsoft and Canonical are both companies in business to make a profit.

---

### Post by azangru on 2012-06-20
> **AllRadioisDead said:**
> Microsoft and Canonical are both companies in business to make a profit.

Yes, but their positions on the market are entirely different, so their tactics should be different as well. Since Microsoft controls most of the desktop market, it makes sense for them to prevent installation of other OSes. They are a giant, they can *afford* to upset the users. Canonical, on the other hand, is still barely visible on the market, very few systems come with Ubuntu preinstalled, so what exactly are those machines they want to put restrictions on? And why aggravate their still so small user base?

Not that I would be upset if I get a nice Ubuntu machine that wouldn't allow me to easily boot another OS on it - I wouldn't want to do it anyhow. But I still fail to see the reasoning behind this restriction.

---

### Post by Linuxratty on 2012-06-20
> **MadmanRB said:**
> .
The only good it does is for microsofts wallet.

 And when all is said and done,that's it in a nutshell..Same for Ubuntu.
I've said for years we would eventually have 3 independent computers out there.One for Windows,one  for Apple and one for Linux. For once,I was right!
:o

---

### Post by Dr. C on 2012-06-20
> **jwbrase said:**
> ...

Can anyone confirm whether MS does in fact require this?

...


Yes on page 122 of [http://download.microsoft.com/download/A/D/F/ADF5BEDE-C0FB-4CC0-A3E1-B38093F50BA1/windows8-hardware-cert-requirements-system.pdf]("http://download.microsoft.com/download/A/D/F/ADF5BEDE-C0FB-4CC0-A3E1-B38093F50BA1/windows8-hardware-cert-requirements-system.pdf")

[QUOTE=Microsoft]...

17. MANDATORY. On non-ARM systems, the platform MUST implement the ability for a physically present user to select between two Secure Boot modes in firmware setup: "Custom" and "Standard". Custom Mode allows for more flexibility as specified in the following:
a) It shall be possible for a physically present user to use the Custom Mode firmware setup option to modify the contents of the Secure Boot signature databases and the PK. This may be implemented by simply providing the option to clear all Secure Boot databases (PK, KEK, db, dbx) which will put the system into setup mode.
b) If the user ends up deleting the PK then, upon exiting the Custom Mode firmware setup, the system will be operating in Setup Mode with SecureBoot turned off.
c) The firmware setup shall indicate if Secure Boot is turned on, and if it is operated in Standard or Custom Mode. The firmware setup must provide an option to return from Custom to Standard Mode which restores the factory defaults.

On an ARM system, it is forbidden to enable Custom Mode. Only Standard Mode may be enabled.


...
[/QUOTE]

---

### Post by Bandit on 2012-06-20
As long as its optional in the BIOS to have it or not, I dont care, I dont run windows.. If its locked in then I will loose my temper and start waving red flags while shouting German!

---

### Post by jwbrase on 2012-06-21
> **Dr. C said:**
> Yes on page 122 of [http://download.microsoft.com/download/A/D/F/ADF5BEDE-C0FB-4CC0-A3E1-B38093F50BA1/windows8-hardware-cert-requirements-system.pdf]("http://download.microsoft.com/download/A/D/F/ADF5BEDE-C0FB-4CC0-A3E1-B38093F50BA1/windows8-hardware-cert-requirements-system.pdf")

Thanks. That clears things up a bunch.

---

### Post by jwbrase on 2012-06-21
> **MadmanRB said:**
> No, it isnt, its just another wqay for Microsoft to lock down computers to use windows only limiting the option to use alternate OS's.
The only good it does is for microsofts wallet.

For Win8/Arm, that's true, because MS controls what keys the firmware will accept, so they control what will boot or not, and can lock out competing OS's. But for Win8/x86 or Ubuntu, it's not. The user controls which keys will be accepted, so the user controls what will boot, and Microsoft or Canonical cannot prevent competing operating systems from being used. Even if they only require the inclusion of a key for their OS from manufacturers, the user can always add a key for whatever OS they want to run, including code they have written themselves. 

Secure boot is good for whoever has the authority to approve / disapprove keys. If the user has that authority, secure boot is a good thing. 

> **azangru said:**
> *Why* exactly is Ubuntu doing this at all? I can understand Microsoft being a d-ck - but for Ubuntu to act in this way - ? What's the purpose?

See above: Secure boot is good for whoever controls what keys will be accepted. Canonical is requiring that the user have that control on any hardware that comes with Ubuntu pre-installed. So they aren't being d-ck's at all. The problem with MS is that they're requiring that the user *not* have that control on ARM.

---

### Post by AllRadioisDead on 2012-06-21
> **azangru said:**
> Yes, but their positions on the market are entirely different, so their tactics should be different as well. Since Microsoft controls most of the desktop market, it makes sense for them to prevent installation of other OSes. They are a giant, they can *afford* to upset the users. Canonical, on the other hand, is still barely visible on the market, very few systems come with Ubuntu preinstalled, so what exactly are those machines they want to put restrictions on? And why aggravate their still so small user base?

Not that I would be upset if I get a nice Ubuntu machine that wouldn't allow me to easily boot another OS on it - I wouldn't want to do it anyhow. But I still fail to see the reasoning behind this restriction.

So, you wouldn't get upset if you bought an Ubuntu laptop that was locked down, but you would if it was a Windows laptop?

---

### Post by forcecore on 2012-06-21
Just wipe secure rom and replace casual rom without keys, no encryption can stand against force flash or physical chip replacement.

Now hardware experts please explain why this cannot be done, if this had done then there would be all phones unlocked too that has bootloader locked but currently none.

---

### Post by bobman321123 on 2012-06-21
> **forcecore said:**
> no encryption can stand against force flash or physical chip replacement.
 
Not necessarily true. If the computer were to develop an encrypted AI capable of defending its self, it would be able to stand against a force flash. :P

---

### Post by newbie2 on 2012-06-21
[QUOTE="Steven J. Vaughan-Nichols"]Shuttleworth wishes he has a better answer, but at this point he doesn’t. He continued, “Secure Boot retains flaws in its design that will ultimately mandate that Microsoft’s key is on every PC (because of core UEFI driver signing). That, and the inability of Secure Boot to support multiple signatures on critical elements means that options are limited but we continue to seek a better result.”

That better solution, Canonical commercial engineering director Victor Tuson Palau suggested last year, would include: “systems manufacturers including a mechanism for configuring your own list of approved software. This will allow you to run Windows 8 and Linux at the same time in your PC with Secure Boot “ON”. This should also include you being able to try new software from a USB stick or DVD.”

Palau added, “With the ability for users to configure Secure Boot, it will become harder for non-techie users to install, or even try, any other operating system besides the one that was loaded on the PC when you bought it. For this reason, we recommend that PCs include a User Interface to easily enable or disable Secure Boot.”

I think anyone who’s serious about Linux desktop agreement would agree on these points. Linux developers would be better off co-ordinating their efforts to get ODMs and OEMs to work together on an open UEFI Secure Boot solution, such as the Linux Foundation proposed last year, than in bickering with each other. In the end, if we squabble among ourselves over the best ways to address Microsoft’s attempt to lock Linux out of the desktop instead of working on a unified response to UEFI Secure Boot the only real winner will be Microsoft.[/QUOTE]
> Related Stories:

Linus Torvalds on Windows 8, UEFI, and Fedora

Microsoft to lock out other operating systems from Windows 8 ARM PCs & devices

Why is Microsoft locking out all other OSes from Windows 8 ARM PCs & devices?

Linux Foundation proposes to use UEFI to make PCs secure and free

Microsoft to stop Linux, older Windows, from running on Windows 8 PCs
[http://www.zdnet.com/blog/open-source/shuttleworth-on-ubuntu-linux-fedora-and-the-uefi-problem/11270](http://www.zdnet.com/blog/open-source/shuttleworth-on-ubuntu-linux-fedora-and-the-uefi-problem/11270)

---

### Post by mips on 2012-06-21
I'm sure someone will hack it and publish a workaround.

Anyone with a interest in linux that endorses this I have no respect for.

---

### Post by azangru on 2012-06-21
> **AllRadioisDead said:**
> So, you wouldn't get upset if you bought an Ubuntu laptop that was locked down, but you would if it was a Windows laptop?

Precisely. Now if I buy a laptop, I am practically *forced* to get a Windows machine, but I don't need Windows. So any restriction to wipe out Windows and install Linux will affect me directly. If, on the other hand I buy an Ubuntu machine (which are practically nonexistent where I live), I wouldn't want to change Ubuntu for anything. So while the secure boot thing on Windows computers *affects me personally*, secure boot on Ubuntu laptops doesn't. That's what I meant.

But in principle, of course, any restriction is bad.

---

### Post by Dr. C on 2012-06-21
> **forcecore said:**
> Just wipe secure rom and replace casual rom without keys, no encryption can stand against force flash or physical chip replacement.

Now hardware experts please explain why this cannot be done, if this had done then there would be all phones unlocked too that has bootloader locked but currently none.

There are provisions in the Microsoft specification above against this for example om page 133

[QUOTE=Microsoft] MANDATORY. The platform shall maintain and enforce a policy with regards to signature authorities for firmware and pre-Operating System components; the policy (and hence the set of authorities) shall be possible to update. The update must happen either as a result of actions by a physically present authorized user or by providing a policy update signed by an existing authority authorized for this task. On ARM platforms, the physical presence alone is not sufficient. Signature authority (db or KEK) updates must be authenticated on ARM platforms.[/QUOTE]

On an ARM system the firmware signatures have to be trusted by Microsoft. So no installing user customized firmware such as the UEFI equivalent of a "Free Bios" on these systems. Yes one can mod the motherboard and replace chips as is the case with game consols; however this activity is illegal in some countries such as the United States thanks to the lobbying efforts of organizations such as the MPAA. Unlike the case of x86/AMD64 for Operating Systems I have not found a requirement that it be possible to change the firmware to a user customized firmware such as the UEFI equivalent of a "Free Bios" on these systems either. So again even on an x86/AMD64 it would be illegal in certain countries to mod the system in order to install custom firmware.

---

### Post by newbie2 on 2012-06-23
> Canonical explains decision to ditch GRUB 2 on UEFI systems
[http://www.extremetech.com/computing/131628-canonical-explains-decision-to-ditch-grub-2-on-uefi-systems](http://www.extremetech.com/computing/131628-canonical-explains-decision-to-ditch-grub-2-on-uefi-systems)

[http://blog.canonical.com/2012/06/22/an-update-on-ubuntu-and-secure-boot/](http://blog.canonical.com/2012/06/22/an-update-on-ubuntu-and-secure-boot/)

[http://www.muktware.com/3735/how-ubuntu-will-deal-uefi-secure-boot](http://www.muktware.com/3735/how-ubuntu-will-deal-uefi-secure-boot)

[http://www.h-online.com/open/news/item/Canonical-details-Ubuntu-UEFI-Secure-Boot-plans-1624444.html](http://www.h-online.com/open/news/item/Canonical-details-Ubuntu-UEFI-Secure-Boot-plans-1624444.html)

[http://www.pcadvisor.co.uk/news/software/3365792/windows-8-secure-boot-two-linux-distros-respond/](http://www.pcadvisor.co.uk/news/software/3365792/windows-8-secure-boot-two-linux-distros-respond/)

[http://www.itworld.com/it-managementstrategy/282069/canonical-details-plans-deal-uefi-secure-boot](http://www.itworld.com/it-managementstrategy/282069/canonical-details-plans-deal-uefi-secure-boot)

---

### Post by Dr. C on 2012-06-23
> **newbie2 said:**
> [http://www.extremetech.com/computing/131628-canonical-explains-decision-to-ditch-grub-2-on-uefi-systems](http://www.extremetech.com/computing/131628-canonical-explains-decision-to-ditch-grub-2-on-uefi-systems)

[http://blog.canonical.com/2012/06/22/an-update-on-ubuntu-and-secure-boot/](http://blog.canonical.com/2012/06/22/an-update-on-ubuntu-and-secure-boot/)

[http://www.muktware.com/3735/how-ubuntu-will-deal-uefi-secure-boot](http://www.muktware.com/3735/how-ubuntu-will-deal-uefi-secure-boot)

[http://www.h-online.com/open/news/item/Canonical-details-Ubuntu-UEFI-Secure-Boot-plans-1624444.html](http://www.h-online.com/open/news/item/Canonical-details-Ubuntu-UEFI-Secure-Boot-plans-1624444.html)

[http://www.pcadvisor.co.uk/news/software/3365792/windows-8-secure-boot-two-linux-distros-respond/](http://www.pcadvisor.co.uk/news/software/3365792/windows-8-secure-boot-two-linux-distros-respond/)

[http://www.itworld.com/it-managementstrategy/282069/canonical-details-plans-deal-uefi-secure-boot](http://www.itworld.com/it-managementstrategy/282069/canonical-details-plans-deal-uefi-secure-boot)

Thanks for the information. This is very helpful. I have included some more links:

[https://lists.ubuntu.com/archives/ubuntu-devel/2012-June/035387.html]("https://lists.ubuntu.com/archives/ubuntu-devel/2012-June/035387.html")

This is a comment by Mark Shuttleworth. It is very gratifying to see that the seriousness of this situation is being addressed at the highest levels of Canonical
> **Mark Shuttleworth]
We've been working to provide an alternative to the Microsoft key, so that the entire free software ecosystem is not dependent on Microsoft's goodwill for access to modern PC hardware. We originally flagged the UEFI / SecureBoot transition as a major problem for free software, we lead the efforts to shape the specification in a more industry-friendly way, and we're pressing OEM partners for options that will be more broadly acceptable than Red Hat's approach.

SecureBoot retains flaws in its design that will ultimately mandate that Microsoft's key is on every PC (because of core UEFI driver signing). That, and the inability of SecureBoot to support multiple signatures on critical elements means that options are limited but we continue to seek a better result.

Mark [/QUOTE]

The second link is also from the ubuntu-devel mailing list [https://lists.ubuntu.com/archives/ubuntu-devel/2012-June/035445.html]("https://lists.ubuntu.com/archives/ubuntu-devel/2012-June/035445.html")

What is being proposed here is to not use GRUB 2 on systems with secure boot enabled and instead use amodified version of Intel's efilinux loader. This avoids the legal implications and risks of  GPL v3 code in the locked boot loader said:**
> 

...

Kernel signing
==============

We believe that the intention of secure boot is to protect against
malicious use or modification of pre-boot code, before the
ExitBootServices UEFI service is invoked.  Currently, this call is
performed by the boot loader, before the kernel is executed.

Therefore, we will only be requiring authentication of boot loader
binaries.  Ubuntu will not require signed kernel images or kernel
modules.

...



The implications of this are profound. All I can say is that this is an excellent solution for Free Software in an otherwise very difficult situation.

---

### Post by mips on 2012-06-23
> **Dr. C said:**
> 
The implications of this are profound. All I can say is that this is an excellent solution for Free Software in an otherwise very difficult situation.

If I'm not mistaken someone has already done a hack wrt secure boot allowing Win8 to boot without hassles.

---

### Post by Bandit on 2012-06-23
I am happy to see Canonical is addressing this huge concern. But I will still be astonished if SB isnt optional in the BIOS for the user. Even more so on retail hardware.

---

### Post by Carborundum on 2012-06-23
> **Bandit said:**
> I am happy to see Canonical is addressing this huge concern. But I will still be astonished if SB isnt optional in the BIOS for the user. Even more so on retail hardware.
I don't think BIOS even supports SecureBoot.

---

### Post by mips on 2012-06-23
> **Carborundum said:**
> I don't think BIOS even supports SecureBoot.

As far as know you are correct.

---

### Post by Bandit on 2012-06-23
> **Carborundum said:**
> I don't think BIOS even supports SecureBoot.

hmm.. I thought it was some mess they was trowing into the BIOS.. I guess I should read up on the hardware specs instead of looking up fishing stuff. :D

EDIT:
Ahh see were I got confused. ASUS is calling the mess a "UEFI BIOS" or "UEFI enabled BIOS" on one of the [new motherboards I was considering.]("http://www.asus.com/Motherboards/Intel_Socket_1155/Maximus_V_GENE/#specifications")

[Wikipedia cleared it up though.]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface")

Gosh I hope my new hardware I picked out doesnt give me any troubles.

---

### Post by KiwiNZ on 2012-06-23
I still believe there is too much FUD being peddled about this tempest in a beverage receptical

---

### Post by Dr. C on 2012-06-23
> **mips said:**
> If I'm not mistaken someone has already done a hack wrt secure boot allowing Win8 to boot without hassles.

Yes, but the beauty of Canonical's approach is that is does not involve "anti-circumvention" and its legal consequences in countries with repressive copyright laws. 

> **Bandit said:**
> I am happy to see Canonical is addressing this huge concern. But I will still be astonished if SB isnt optional in the BIOS for the user. Even more so on retail hardware.

It will not be the case for Windows 8 on ARM hardware anymore than it is the case now for an iPad, a PS3 or an Xbox.

---

### Post by MadmanRB on 2012-06-23
> **KiwiNZ said:**
> I still believe there is too much FUD being peddled about this tempest in a beverage receptical

Right we should thank Microsoft for locking us out of our hardware, the nice wonderful people they are and how well they like having competitors.

---

### Post by KBD47 on 2012-06-23
Secure Boot will mean I will not be doing what I did today, hand my brother 2 Linux CD's so that he can try them out on his computer. Fast forward a bit into the future, I hand him a couple of Linux CD's and tell him: "Oh, and by the way, turn the Secure Boot on your laptop off before you try those CD's."
  I won't give people CD's and tell them to turn off Secure Boot on their machines, even if they know how. MS knows that Secure Boot means fewer Linux users. Does anyone really believe Windows can be made  secure?
  As for Ubuntu, I will be amazed if they ever get on much hardware. I hope they do, but not holding my breath :-)

---

### Post by Dr. C on 2012-06-24
> **KBD47 said:**
> Secure Boot will mean I will not be doing what I did today, hand my brother 2 Linux CD's so that he can try them out on his computer. Fast forward a bit into the future, I hand him a couple of Linux CD's and tell him: "Oh, and by the way, turn the Secure Boot on your laptop off before you try those CD's."
  I won't give people CD's and tell them to turn off Secure Boot on their machines, even if they know how. MS knows that Secure Boot means fewer Linux users. Does anyone really believe Windows can be made  secure?
  As for Ubuntu, I will be amazed if they ever get on much hardware. I hope they do, but not holding my breath :-)

The whole point of the very important work of Canonical and Red Hat is that you will be able to continue to do what you are doing now in spite of the efforts by Microsoft to prevent you. It is also why it is very important for this community to remain very vigilant and not simply dismiss what is a very serious threat to Free Software as "FUD".

---

### Post by Dr. C on 2012-07-05
The FSF's response to the UEFI Secure Boot Requirements. [http://www.fsf.org/campaigns/secure-boot-vs-restricted-boot/whitepaper-web]("http://www.fsf.org/campaigns/secure-boot-vs-restricted-boot/whitepaper-web")

It glosses over one very critical issue namely that in the Ubuntu case the signed bootloader does not require signed kernel images while in the Fedora case signed kernel images are mandatory. So while technicaly the following is true[QUOTE=FSF] ... Ubuntu has chosen a path which explicitly allows Restricted Boot. ...[/QUOTE] the practical reality is that by allowing the loading of unsigned kernel images Canonical's approach in fact allows the loading of any modified GNU/Linux distribution on a "Restricted Boot" computer using the Ubuntu bootloader.

---

### Post by newbie2 on 2012-08-03
> There is still another way though: **Use open hardware with open source software.** This is the path Cathy Malmrose, CEO of the Linux PC vendor ZaReason would like to see followed.

As Malmrose said "With UEFI's Secure Boot around the corner, we are hoping to raise awareness that Linux distributors don't need to sign with Microsoft [or use their secure boot]. Computers that are rooted with open bootloader are available. That's what we ship." True, "UEFI's Secure Boot is implemented at OEM (original equipment manufacturer) level, all new PCs purchased (with the intent of loading your favorite distro) will have Secure Boot."

Malmrose isn't happy with disabling it or using Fedora or Ubuntu's methods. "Yes, you can disable it. But 'disabling' something that's 'secure' makes you bad." She also fears that in the long run, "the keystroke(s) needed to get Linux to run on machines post-2012 will be simple at first, becoming increasingly complex at a non-shocking rate. It's a monumental shift at OEM level." Malmrose fears that this will make desktop Linux "too difficult to new users, [and this will cause] slow death by suffocation" for Linux.
[http://news.idg.no/cw/art.cfm?id=4DCE37F8-BFD8-ADDA-EFE06EB7A0997DE4](http://news.idg.no/cw/art.cfm?id=4DCE37F8-BFD8-ADDA-EFE06EB7A0997DE4)
:roll:

---

### Post by newbie2 on 2012-08-29
> A year ago, Linux lovers were worrying that Secure Boot was going to somehow give Linux the boot, but now it looks like there’s a brand-new twist to the story. **It could be used to keep Microsoft’s software from running on a computer.**

To date, nobody has pulled off this technically tricky feat. In fact, most people will have to wait for Windows 8 to ship before they can even give it a try. But Red Hat Developer Matthew Garrett has been working with the Secure Boot standards-makers, and he recently described how users can replace the Microsoft cryptographic keys that ship with Windows 8 with their own keys and then sign any software that they want so it can run on their machine.
[http://www.wired.com/wiredenterprise/2012/08/secure-boot/](http://www.wired.com/wiredenterprise/2012/08/secure-boot/)
:p

---

### Post by vexorian on 2012-08-29
The only way Secure boot would count as a good thing and a security measure rather than a "limit the user of choice" measure would be if:

- It was disabled by the fault.
- User could enable it manually and choose whatever key he wants for the restricted boot.

Else it is just monopolistic BS.

---

### Post by BigCityCat on 2012-08-29
Just wanted to say that when I first found Linux it was complicated to me to install it. At least in my mind because I wasn't familiar but the website that introduced the idea gave complete and easy to understand directions. I was able to accomplish the install and now, well it's easy. Point is, experienced users will be fine and I am sure there will be easy to use instructions for persistent curious new users. I don't think this changes anything. It will be old hat before you know it.

---

### Post by Erik1984 on 2012-08-29
> **BigCityCat said:**
> Just wanted to say that when I first found Linux it was complicated to me to install it. At least in my mind because I wasn't familiar but the website that introduced the idea gave complete and easy to understand directions. I was able to accomplish the install and now, well it's easy. Point is, experienced users will be fine and I am sure there will be easy to use instructions for persistent curious new users. I don't think this changes anything. It will be old hat before you know it.

I'm not sure. Before the instruction was: "insert the Ubuntu cd" now you first have to give a counter-intuitive advise: disable secure boot. Newbies might think: So I have to make my PC less secure to install the 'secure' operating system Linux?

---

### Post by BigCityCat on 2012-08-29
> **Euroman said:**
> I'm not sure. Before the instruction was: "insert the Ubuntu cd" now you first have to give a counter-intuitive advise: disable secure boot. Newbies might think: So I have to make my PC less secure to install the 'secure' operating system Linux?

Kind of but I'm not sure the installer would install along side. when I started you had to use the windows shrink function to set some un allocated space so you could use the largest continuous space. Or I was just doing it wrong lol can't remember. Yeh I wouldn't call it disabling secure boot. I would call it removing Microsoft's impediment to using a more secure os.

---

### Post by BigCityCat on 2012-08-29
Anyway Windows 8 is terrible. I am a Linux user that has a windows os on his computer. In the future if they make it that difficult. I just won't use it all.

---

### Post by Bandit on 2012-08-29
I figure Win7 wil be the next WinXP and everyone will skip WinH8 if anyway possible like most did with Vista. Yea many will get it, some will even like it. But most that do get it will be becuase it came with there system. I just will not be one of those.

I will however shake the hand of the first person that can demonstrate to me how the heck one can multitask on Win8.

I dont run much on my PC at work, but I do run Solidworks 2012, Outlook, Excel, and Explorer routinely. Plus what ever else I may have to run. Thats not a lot programs at all, mind you SW is a resource hog in a half. But Win8 cant do just those 4! So how is it suposed to survive in an office enviroment.

----------------------------\\

Now kinda getting back on track. Purchased a new Mobo today with UEFI bios on it. Doesnt say anything about secure boot feature. I may be wrong though, its a ASUS P8Z77-V Pro.

---

