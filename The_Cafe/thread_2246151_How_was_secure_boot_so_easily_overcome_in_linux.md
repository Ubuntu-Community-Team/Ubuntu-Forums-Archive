---
title: "How was secure boot so easily overcome in linux?"
date: 2014-09-28
forum: The Cafe
---

### Post by user1397 on 2014-09-28
I remember everyone freaking out when it was announced that all Windows 8 pre-installed computers would come with the secure boot feature which made it practically impossible to install another OS alongside it.  I didn't really follow through with what happened in the months or years afterwards, and now ubuntu installs on my Windows 8.1 EFI GUID hard drive just like it would on legacy systems.

What did I miss?

(Just curious :))

---

### Post by pqwoerituytrueiwoq on 2014-09-28
i think signed images are in use for it
recently i had the *joy* of working with a win8 system, i could not even access the bios or boot anything but the internal hdd
i removed the hdd and powered it up to get into the bios and disable the super fast boot feature that makes it skip the bios access as well as secure boot so i could boot my usb install disk
my task was to upgrade them to a ssd and get windows 8.1 on them for a single application
they were inexpensive (200-250) tiny asus netbooks/notebooks

---

### Post by Habitual on 2014-09-29
> **pqwoerituytrueiwoq said:**
> i removed the hdd and powered it up to get into the biosOld tricks are still the best tricks. :)

---

### Post by Maverick Meerkat on 2014-09-30
I goofed up and tried to install 14.04 in a second hard drive without unplugging the original drive.
I was very careful NOT to overwrite the primary drive during the install, but it bricked my boot loader on my main drive.
Thanks to the kind and knowledgeable folks on these forums, I was spared having to tell my wife I hosed our new computer.
That scared the heck out of me and I became a lot more gun shy about installing.

I now have 3 systems running 14.04, so I didn't completely bail out.

Rick

---

### Post by buzzingrobot on 2014-09-30
It wasn't all that "easily overcome". On the other hand, Secure Boot was not really the all-conquering threat many made it out to be. Trying to prevent boot time malware is a good idea. Microsoft's implementation is inconvenient for non-MS platforms because they have the market strength to induce hardware OEM's to build systems that cater to Microsoft's specific interests. It would have been "nice" if MS had lobbied the industry to adopt some kind of universal approach, but that's an unrealistic expectation. (Would also have required someone to step  forward as the source and custodian of all the necessary keys and, at the time, no one seemed willing to do that.)

---

### Post by Lars Noodén on 2014-09-30
Rather than standing up, it was just a matter of getting Microsoft's permission to allow Ubuntu to boot on the restricted hardware:

> 
1. Microsoft signs Canonical's 'shim' 1st stage bootloader with their 'Microsoft Corporation UEFI CA'. When the system boots and Secure Boot is enabled, firmware verifies that this 1st stage bootloader (from the 'shim-signed' package) is signed with a key in DB (in this case 'Microsoft Corporation UEFI CA')

2. The second stage bootloader (grub-efi-amd64-signed) is signed with Canonical's 'Canonical Ltd. Secure Boot Signing' key. The shim 1st stage bootloader verifies that the 2nd stage grub2 bootloader is properly signed.

3. The 2nd stage grub2 bootloader boots an Ubuntu kernel (as of 2012/11, if the kernel (linux-signed) is signed with the 'Canonical Ltd. Secure Boot Signing' key, then grub2 will boot the kernel which will in turn apply quirks and call ExitBootServices. If the kernel is unsigned, grub2 will call ExitBootServices before booting the unsigned kernel) 


From [https://wiki.ubuntu.com/SecurityTeam/SecureBoot](https://wiki.ubuntu.com/SecurityTeam/SecureBoot)

See also [https://lists.ubuntu.com/archives/ubuntu-devel/2012-June/035445.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-June/035445.html)

---

### Post by user1397 on 2014-09-30
> **Lars Noodén said:**
> Rather than standing up, it was just a matter of getting Microsoft's permission to allow Ubuntu to boot on the restricted hardware:



From [https://wiki.ubuntu.com/SecurityTeam/SecureBoot](https://wiki.ubuntu.com/SecurityTeam/SecureBoot)

See also [https://lists.ubuntu.com/archives/ubuntu-devel/2012-June/035445.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-June/035445.html)so if that's true, then how does installing other distros work?  I don't think most of them have the pull that Canonical has to make a deal with Microsoft like that...  Or am I not understanding something correctly?

---

### Post by buzzingrobot on 2014-09-30
> **ubuntuman001 said:**
> so if that's true, then how does installing other distros work?  I don't think most of them have the pull that Canonical has to make a deal with Microsoft like that...  Or am I not understanding something correctly?

I think it wasn't so much a matter of "pull" but going to a website, jumping through the hoops there, paying $99 (seems to go to Verisign), and get the MS key to sign as many first stage bootloaders as you wanted. 

Red Hat's Matthew Garrett had some good posts about their approach to Secure Boot at his blog: [http://mjg59.dreamwidth.org/](http://mjg59.dreamwidth.org/).

---

### Post by grahammechanical on 2014-09-30
To reiterate the previous comment that dealing with secure boot was not easy, just watch this video of a talk about UEFI and secure boot by Matthew Garret who did a lot of work on this when he was working for Redhat.

[http://www.youtube.com/watch?v=V2aq5M3Q76U](http://www.youtube.com/watch?v=V2aq5M3Q76U)

For the Ubuntu solution

[http://blog.canonical.com/2012/06/22/an-update-on-ubuntu-and-secure-boot/](http://blog.canonical.com/2012/06/22/an-update-on-ubuntu-and-secure-boot/)

[http://blog.canonical.com/2012/09/20/quetzal-is-taking-flight-update-on-ubuntu-secure-boot-plans/](http://blog.canonical.com/2012/09/20/quetzal-is-taking-flight-update-on-ubuntu-secure-boot-plans/)

Regards

---

### Post by Bucky Ball on 2014-09-30
> **Maverick Meerkat said:**
> I goofed up and tried to install 14.04 in a second hard drive without unplugging the original drive.
I was very careful NOT to overwrite the primary drive during the install, but it bricked my boot loader on my main drive.
Thanks to the kind and knowledgeable folks on these forums, I was spared having to tell my wife I hosed our new computer.
That scared the heck out of me and I became a lot more gun shy about installing.



You're a brave man, Rick, and more strength to you! I can see the beads of sweat when that happened ... ;)

Always remember, [BOOT REPAIR ]("https://help.ubuntu.com/community/Boot-Repair")is your friend ...

---

### Post by Lars Noodén on 2014-10-01
> **ubuntuman001 said:**
> so if that's true, then how does installing other distros work?  I don't think most of them have the pull that Canonical has to make a deal with Microsoft like that...  Or am I not understanding something correctly?

It's not a matter of pull, Microsoft *wants* to be the gatekeeper of what can boot on any given hardware.  The shim mentioned did take a lot of skill and work, see the links from buzzingrobot and grahammechanical, but I'm not sure the goal was admirable.  Some consider the advantages to have been overstated especially in regards to security.   The alternate name is "restricted boot" and you will also find relevant material under that term.  

About the other distros, one way is to just turn off "secure" boot which seems to be the way most do it.  But for some firmware that means adding a firmware password, which risks getting lost or forgotten and that would be rather bad.  Red Hat and [Fedora](https://fedoraproject.org/wiki/Secureboot) use the same shim as Ubuntu, but point it at Grub2.   Gentoo [does not officially](http://wiki.gentoo.org/wiki/UEFI_Gentoo_Quick_Install_Guide) support UEFI, the superset of 'secure' boot.  [Slackware](http://www.slackware.com/releasenotes/14.1.php) does not support 'secure' boot either, but a user could still do the leg work with keys, etc. theirself.  And [Debian](http://forums.debian.net/viewtopic.php?f=19&t=91432), at least as recently as wheezy, does not support it either.  And skimming various forums, it looks like jessie is frozen out too.  FreeBSD is/was also looking at using Matthew Garrett's shim loader.

---

### Post by buzzingrobot on 2014-10-01
> **Lars Noodén said:**
> It's not a matter of pull, Microsoft *wants* to be the gatekeeper of what can boot on any given hardware.

I agree with that, but think it's to-be-expected behavior. I.e., why would MS not do that?  And, why would vendors whose existence depends on Microsoft not go along?

 The consumer tech market gravitates to dominance by a very few vendors.  Customers and users are happy with that because they do not want to be forced to choose from a myriad of products that may or may not work with each other. More to the point, they typically lack the expertise and interest to make those kind of choice.  And won't be acquiring it.  We won't be seeing that kind of choice in the consumer tech market any more than we will see it in the auto or aircraft industries.

---

### Post by user1397 on 2014-10-06
Thanks for all the replies guys.  I understand the situation better now.

---

### Post by Roasted on 2014-10-07
> **buzzingrobot said:**
> I think it wasn't so much a matter of "pull" but going to a website, jumping through the hoops there, paying $99 (seems to go to Verisign), and get the MS key to sign as many first stage bootloaders as you wanted. 

Red Hat's Matthew Garrett had some good posts about their approach to Secure Boot at his blog: [http://mjg59.dreamwidth.org/](http://mjg59.dreamwidth.org/).

I have a potentially dumb question. The signed key with the 99 dollar price tag... is that a one time thing? I mean, is that to say all Canonical had to do was pay Microsoft 99 bucks for a key that would allow millions of Ubuntu systems to be installed on UEFI systems?

On one hand, I still want to flip some tables over that nonsense. But on the other, if it's a matter of 99 bucks to work around the issue altogether for countless users... one of those pick your battles wisely type things.

---

### Post by buzzingrobot on 2014-10-07
[QUOTE=Roasted;13137687].... The signed key with the 99 dollar price tag... is that a one time /QUOTE]

I believe so.

---

### Post by kurja on 2014-10-09
I haven't really read up about secure boot, could someone summarize just how is it supposed to benefit the user? Because it sounds to me like some drm-ish nonsense that only manages to annoy people without actually benefiting anyone at all.

---

### Post by buzzingrobot on 2014-10-09
> **kurja said:**
> I haven't really read up about secure boot, could someone summarize just how is it supposed to benefit the user? Because it sounds to me like some drm-ish nonsense that only manages to annoy people without actually benefiting anyone at all.

Systems can be vulnerable to attacks that load during the startup process. UEFI -- think of it as the successor to the ages-old BIOS approach -- allows PC firmware to determine if the signatures of the software executed during the boot -- drivers, the OS, etc. -- are valid. If they are, the firmware hands off control to the OS. (Whether a system has a BIOS or uses UEFI, both are in control of a machine as it boots, and then turn over control to the OS.)

Microsoft developed an implementation of this feature for use in Windows 8, calling it Secure Boot (with the uppercase letters.  Hardware vendors, dependent on selling into the Windows market, included the feature in new hardware intended to Windows 8. 

One effect, of course, is that other operating systems would be flagged as invalid unless  they obtained a key and were signed.

System very often (usually?) have an option to disable Secure Boot and revert to "Legacy Boot".

---

### Post by Linuxratty on 2014-10-10
So I'm correct in presuming that this will be sop on *all *computers that have Windows on them from now till the end of time,correct?

---

### Post by buzzingrobot on 2014-10-10
> **Linuxratty said:**
> So I'm correct in presuming that this will be sop on *all *computers that have Windows on them from now till the end of time,correct?

It's safe to say it will be in PC's that vendors want to sell with pre-installed Windows. The salient point is the need for vendors to sell boxes with preinstalled Windows. 

Note that 'Secure Boot' and UEFI are different things, and that Windows 8/8.1 will install and run per normal on a machine set to 'Legacy Mode'.

---

### Post by oldfred on 2014-10-10
[http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

The only major Boot virus was actually Sony creating DRM for its music. 
Microsoft has had major marketing issues with virus, so what better to market a system with "Secure Boot" even though that has nothing to do with almost all of the virus issues.

Even more security changes?

   Some UEFI also have TPM 
[http://technet.microsoft.com/en-us/windows/dn168169.aspx](http://technet.microsoft.com/en-us/windows/dn168169.aspx)
UEFI secure boot doesn't have anything to do with a TPM.
[https://www.ibm.com/developerworks/community/blogs/smartersecurity/entry/uefi_secure_boot_and_the_tpm20?lang=en](https://www.ibm.com/developerworks/community/blogs/smartersecurity/entry/uefi_secure_boot_and_the_tpm20?lang=en)
Microsoft has announced that from January 1, 2015 all computers will have to be equipped with a TPM 2.0 module in order to pass Windows 8.1 hardware certification.
[https://en.wikipedia.org/wiki/Trusted_Platform_Module](https://en.wikipedia.org/wiki/Trusted_Platform_Module)

---

