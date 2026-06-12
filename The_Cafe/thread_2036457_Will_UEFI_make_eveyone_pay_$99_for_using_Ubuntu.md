---
title: "Will UEFI make eveyone pay $99 for using Ubuntu?"
date: 2012-08-01
forum: The Cafe
---

### Post by c2tarun on 2012-08-01
Hi friends,

I read this article today, 
[http://www.wired.com/wiredenterprise/2012/06/microsoft-windows8-secure-boot/](http://www.wired.com/wiredenterprise/2012/06/microsoft-windows8-secure-boot/)
Does this mean that anyone who want to use Linux (ubuntu/red-hat) have to pay $99 to someone?

---

### Post by ahallubuntu on 2012-08-01
No, it means that Canonical (the organization that distributes Ubuntu) has to pay it one time to sign their boot loader.  They don't pay $99 for each person downloading Ubuntu; they pay it ONCE.

---

### Post by c2tarun on 2012-08-01
> **ahallubuntu said:**
> No, it means that Canonical (the organization that distributes Ubuntu) has to pay it one time to sign their boot loader.  They don't pay $99 for each person downloading Ubuntu; they pay it ONCE.

ohh.. :)

---

### Post by mörgæs on 2012-08-02
It's still a problem. After some time when people are getting used to the fee it can easily be changed to per-installation. It surprises me that Torvalds does not comment on that.

Moved to the cafe as it is not a support request.

---

### Post by madjr on 2012-08-02
this is why is time to switch to linux friendly hardware vendors/preinstalled options.

[http://www.omgubuntu.co.uk/category/hardware-2/](http://www.omgubuntu.co.uk/category/hardware-2/)

---

### Post by ranger1021994 on 2012-08-02
Microsoft behaves like a bully

---

### Post by mamamia88 on 2012-08-02
how is secure boot even legal?

---

### Post by drawkcab on 2012-08-02
Where are the lawyers?

---

### Post by KiwiNZ on 2012-08-02
There are ways to work with this or work around this. It just takes a small amount of research.

---

### Post by omiazad on 2012-08-02
Awesome News!!!

---

### Post by vasa1 on 2012-08-02
Won't this be an issue only for those who buy computers with Win 8 pre-installed?

---

### Post by Elfy on 2012-08-02
> **vasa1 said:**
> Won't this be an issue only for those who buy computers with Win 8 pre-installed?

Not necessarily.

Looking to buy a new machine myself - people I use have barebones etc, the one I was looking at has UEFI enabled, I'd imagine most if not all will eventually.

A quick call to them told me it was easy to disable and that if I did have any problems a call to their tech dept would walk me through it.

---

### Post by effenberg0x0 on 2012-08-02
I know this is supposed to be top-notch security, etc. But, really: it feels like MS vs. Linux. Every kid in the word will feel compelled to hack it. How long will it take for it to be completely destroyed? IMO, it will turn out to be another embarrassment for MS and OEMs.

Regards,
Effenberg

---

### Post by Paqman on 2012-08-02
> **mamamia88 said:**
> how is secure boot even legal?

Why would it be illegal?

---

### Post by c2tarun on 2012-08-02
BTW why do we even need UEFI? What is wrong with BIOS? and What kind of security they are going to add in UEFI?

---

### Post by Paqman on 2012-08-02
> **c2tarun said:**
> BTW why do we even need UEFI? What is wrong with BIOS? and What kind of security they are going to add in UEFI?

BIOS is really, really outdated and doesn't support modern hardware. The only reason we're still able to use it is that individual vendors have hacked and extended it way beyond what it was originally capable of doing. That's not a sensible or sustainable model, and we should have switched to (U)EFI years and years ago.

---

### Post by vasa1 on 2012-08-02
> **Elfy said:**
> Not necessarily.

Looking to buy a new machine myself - people I use have barebones etc, the one I was looking at has UEFI enabled, I'd imagine most if not all will eventually.

A quick call to them told me it was easy to disable and that if I did have any problems a call to their tech dept would walk me through it.

Aren't there two issues? One is the presence of UEFI instead of BIOS. The other is the secure boot aspect.

If one buys a computer with UEFI but no Win8 on it, will there be the problem of needing a key?

---

### Post by Grenage on 2012-08-02
Indeed; IIRC, it was only supposed to be a temporary solution.

---

### Post by vasa1 on 2012-08-02
Just curious, but is this UEFI thing baked into the motherboard? If yes, then who can upgrade from Win7? Only those who already have a PC with UEFI?

---

### Post by mörgæs on 2012-08-02
> **Elfy said:**
> 
Looking to buy a new machine myself - people I use have barebones etc, the one I was looking at has UEFI enabled, I'd imagine most if not all will eventually.

A quick call to them told me it was easy to disable and that if I did have any problems a call to their tech dept would walk me through it.

Was that for ARM's or x86? As of now, most restrictions are focusing on ARM.

---

### Post by Primefalcon on 2012-08-02
hell with this.... my pre-built systems will be vendors like system76 from now on.....

---

### Post by drmrgd on 2012-08-02
I would imagine that if it becomes too restrictive or monopolative (not sure that's a word, but I kind of like it anyway!), MS will get sued to fix it.  I mean, they're still getting pounded over Internet Explorer, which as much as I dislike IE, I think that was a silly and frivolous lawsuit.

Either way, there will be workarounds and ways to do it.  It's just a change people will get used to.

---

### Post by ssam on 2012-08-02
you might to read this, which explains the situation well.
[http://mjg59.dreamwidth.org/12368.html](http://mjg59.dreamwidth.org/12368.html)

the distros basically have 3 choices.
1) tell users to go into the BIOS and disable security options
2) tell users to go into the BIOS and add the distro key
3) create a key and signing infrastructure, and convince all the manufactures to install it by default
4) buy a key that is signed by a key that is already guaranteed to be installed

fedora and ubuntu both went with 4. i expect smaller distros will choose 1 or 2.

---

### Post by mips on 2012-08-02
They are already working on it, I would not worry to much about it. See links below.

[http://ubuntuforums.org/showthread.php?t=2028529](http://ubuntuforums.org/showthread.php?t=2028529)
[http://www.pcworld.com/businesscenter/article/259368/linux_developers_step_up_to_the_secure_boot_challenge.html](http://www.pcworld.com/businesscenter/article/259368/linux_developers_step_up_to_the_secure_boot_challenge.html)
[http://sourceforge.net/apps/mediawiki/tianocore/index.php?title=Welcome](http://sourceforge.net/apps/mediawiki/tianocore/index.php?title=Welcome)

---

### Post by madjr on 2012-08-02
> **Paqman said:**
> BIOS is really, really outdated and doesn't support modern hardware. The only reason we're still able to use it is that individual vendors have hacked and extended it way beyond what it was originally capable of doing. That's not a sensible or sustainable model, and we should have switched to (U)EFI years and years ago.

Well am glad we didnt switch to (U)EFI years and years ago, as it would just had been another headache for new non technical/experienced users trying to install linux. And wouldn't mind this gets postponed (or at least not fully adopted) for some more years.


> **ssam said:**
> you might to read this, which explains the situation well.
[http://mjg59.dreamwidth.org/12368.html](http://mjg59.dreamwidth.org/12368.html)

the distros basically have 3 choices.
1) tell users to go into the BIOS and disable security options
2) tell users to go into the BIOS and add the distro key
3) create a key and signing infrastructure, and convince all the manufactures to install it by default
4) buy a key that is signed by a key that is already guaranteed to be installed

fedora and ubuntu both went with 4. i expect smaller distros will choose 1 or 2.

If distros are based on ubuntu or fedora, do they automatically get #4 ?

and what about if you install using Wubi, do you still need keys and stuff?

---

### Post by Paqman on 2012-08-02
> **madjr said:**
> Well am glad we didnt switch to (U)EFI years and years ago, as it would just had been another headache for new non technical/experienced users trying to install linux. And wouldn't mind this gets postponed (or at least not fully adopted) for some more years.

Switching to UEFI doesn't automatically mean using Secure Boot, that's just a speedhump that Microsoft has thrown in our way recently. Macs have been using it for years, and there are currently PCs/mobos available with UEFI and no secure boot. Linux has officially supported EFI for yonks.

> 
and what about if you install using Wubi, do you still need keys and stuff?

Since Wubi uses NTLDR, it would presumably be ok. Good question though.

---

### Post by Eddie Wilson on 2012-08-02
> **Primefalcon said:**
> hell with this.... my pre-built systems will be vendors like system76 from now on.....

The most that they'll be able to do is turn it off for you. Everyone is making more of a problem with this than what is really is. Canonical and Redhat have already figured out there will be no serious problems. All the secure boot is for the Windows 8 certification logo. It MUST be setup where it can be disabled. OEM's can still install Windows 8 without the certification but they wouldn't get the OEM price package for Windows 8. UEFI is needed and secure boot is much ado about nothing.

---

### Post by Lucradia on 2012-08-03
Buy a Crosshair V Formula. It has UEFI, but allows Linux out of the box. ASUS is more open-source friendly from what I hear. (Routers use DD-WRT.)

---

### Post by drmrgd on 2012-08-03
> **Lucradia said:**
> Buy a Crosshair V Formula. It has UEFI, but allows Linux out of the box. ASUS is more open-source friendly from what I hear. (Routers use DD-WRT.)

I guess that depends on who you talk to at the company.  As I was trying to figure out how to configure my new ASUS mobo with UEFI, I did the usual barrage of Google searching.  On more than one occasion I came across a post on a forum saying that the user called ASUS customer support to get help and they just said, "sorry we don't support Linux."

---

### Post by ssam on 2012-08-03
> **madjr said:**
> 
If distros are based on ubuntu or fedora, do they automatically get #4 ?


if they use the ubuntu/fedora bootloader and kernel then i guess it would work.

I imagine ubuntu and fedora will not want to sign kernels and boot loaders built by anyone else, as they would take the blame if there was anything bad in them.

not all distros feel to strongly about being super easy to install. I imagine gentoo will be happy to just give instructions for how to create your own key, load it into UEFI and sign your own kernels. This could allow you to make a super secure server that will only run software that you have signed personally.

---

### Post by Lucradia on 2012-08-03
> **drmrgd said:**
> I guess that depends on who you talk to at the company.  As I was trying to figure out how to configure my new ASUS mobo with UEFI, I did the usual barrage of Google searching.  On more than one occasion I came across a post on a forum saying that the user called ASUS customer support to get help and they just said, "sorry we don't support Linux."

My Crosshair V Formula came with a huge manual. Always a good idea to read it. As for updating the graphic on the BIOS, you **have** to have Windows for that. You also **have to have** windows for updating the BIOS too.

---

### Post by SeijiSensei on 2012-08-03
Can anyone tell me how all this will work with virtual machines?  Will a virtualized Win8 on Linux talk to the UEFI controller at boot?  Or will VMs emulate the security component of UEFI or simply ignore all this stuff entirely?

---

### Post by Paqman on 2012-08-03
> **SeijiSensei said:**
> Can anyone tell me how all this will work with virtual machines?  Will a virtualized Win8 on Linux talk to the UEFI controller at boot?  Or will VMs emulate the security component of UEFI or simply ignore all this stuff entirely?

I don't see any reason why a VM would have to implement secure boot. They may offer it as a feature, but they're not locked into it to get a good licencing deal from Microsoft like the OEMs are.

---

### Post by drmrgd on 2012-08-03
> **Lucradia said:**
> My Crosshair V Formula came with a huge manual. Always a good idea to read it. As for updating the graphic on the BIOS, you **have** to have Windows for that. You also **have to have** windows for updating the BIOS too.

I'm not sure how this is relevant to what I said.  I'm not (and wasn't) trying up grade the BIOS graphic.  Also, I have the X79 Sabertooth board, which doesn't even require a hard drive, monitor, or keyboard to update the BIOS Firmware (just need the board, a USB flash drive, and power):

[http://event.asus.com/2012/mb/USB_BIOS_Flashback_GUIDE/](http://event.asus.com/2012/mb/USB_BIOS_Flashback_GUIDE/)

---

### Post by mips on 2012-08-03
> **SeijiSensei said:**
> Can anyone tell me how all this will work with virtual machines?  Will a virtualized Win8 on Linux talk to the UEFI controller at boot?  Or will VMs emulate the security component of UEFI or simply ignore all this stuff entirely?

Why? Virtual hard drives are just that, virtual.

---

### Post by pqwoerituytrueiwoq on 2012-08-03
> **drawkcab said:**
> Where are the lawyers?
collecting funds from Microsoft

secure boot can be turned off in the BIOS

---

### Post by matt_symes on 2012-08-03
> You also **have to have** windows for updating the BIOS too.

Gigabyte boards with Q-flash also do not need windows to update the BIOS (UEFI).  They just need a drive (pen, solid or rotatory) formatted using FATx.

I know because i have flashed a BIOS on a Gigbyte board just today.

---

### Post by Paulgirardin on 2012-08-03
> **effenberg0x0 said:**
> I know this is supposed to be top-notch security, etc. But, really: it feels like MS vs. Linux. Every kid in the word will feel compelled to hack it. How long will it take for it to be completely destroyed? IMO, it will turn out to be another embarrassment for MS and OEMs.

Regards,
Effenberg

My guess is about 3 days prior to the first Secure Boot system being released.

---

### Post by Lucradia on 2012-08-03
> **drmrgd said:**
> I'm not sure how this is relevant to what I said.  I'm not (and wasn't) trying up grade the BIOS graphic.  Also, I have the X79 Sabertooth board, which doesn't even require a hard drive, monitor, or keyboard to update the BIOS Firmware (just need the board, a USB flash drive, and power):

[http://event.asus.com/2012/mb/USB_BIOS_Flashback_GUIDE/](http://event.asus.com/2012/mb/USB_BIOS_Flashback_GUIDE/)

My board is not listed on step 3. So yes, ***[SIZE="4"]I[/SIZE]*** have to. There is a button with that marking, but no "BIOS" under it. It also is green-colored, not blue, and resets the BIOS cache, and defaults all the settings, it's not near any of my USB connections though. Only White USB thing is the ROG Connect USB slot, which is meant for hooking up to a tablet or something to look at your motherboard's status.

> **matt_symes said:**
> Gigabyte boards with Q-flash also do not need windows to update the BIOS (UEFI).  They just need a drive (pen, solid or rotatory) formatted using FATx.

I know because i have flashed a BIOS on a Gigbyte board just today.

See above.

---

### Post by Paulgirardin on 2012-08-03
> **madjr said:**
> Well am glad we didnt switch to (U)EFI years and years ago, as it would just had been another headache for new non technical/experienced users trying to install linux. And wouldn't mind this gets postponed (or at least not fully adopted) for some more years.




If distros are based on ubuntu or fedora, do they automatically get #4 ?

and what about if you install using Wubi, do you still need keys and stuff?
UEFI isn't a problem - I built a mythbox 7 months ago with an ASUS mb with UEFI.There was no problem loading Mythbuntu 11.10 on it.

---

### Post by matt_symes on 2012-08-03
> See above.

I was not disagreeing about your specific situation.

I was, however, stating that not all UEFI BIOS updates require windows.

---

### Post by SeijiSensei on 2012-08-03
> **Paqman said:**
> I don't see any reason why a VM would have to implement secure boot. They may offer it as a feature, but they're not locked into it to get a good licencing deal from Microsoft like the OEMs are.

Maybe I need to read more deeply into UEFI, but I thought a UEFI-compliant operating system won't boot unless the BIOS includes a known certificate?  Otherwise what's the point?  

So I'll ask the question in a slightly different way.  Will Win8 boot in a VM if the virtualized BIOS isn't signed with a certificate recognizable by Windows?

---

### Post by mjg59 on 2012-08-05
> **SeijiSensei said:**
> Maybe I need to read more deeply into UEFI, but I thought a UEFI-compliant operating system won't boot unless the BIOS includes a known certificate?  Otherwise what's the point?  

So I'll ask the question in a slightly different way.  Will Win8 boot in a VM if the virtualized BIOS isn't signed with a certificate recognizable by Windows?

Yes. Secure boot (if enabled) stops operating systems from booting if they're not signed with a trusted certificate. It does not permit operating systems to refuse to boot.

---

