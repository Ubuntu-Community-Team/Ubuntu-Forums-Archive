---
title: "Ultra 10 and ATI card problem"
date: 2006-09-11
forum: Sun Sparc Users
---

### Post by chris_andrew on 2006-09-11
Hi, all.

I have an Ultra 10 with an ATI card (Creator), and also have another (built in?) card listed in dmesg.

I get the feeling from the forums that ATI and Ultra 10 do not like Xorg.  This seems to be the reason why I can't get past "Booting Linux...." on several distros.

I have filed a bug for this.  Does anybody know whether a fix is being worked on, or how I might be able to use the internal Sun card, on my Ultra?  I would really like to install Ubuntu, but it fails every time.

Seems a shame not to be able to use the Creator card.  The other option is to use it with Debian Sarge (XFree86, not Xorg), but this distro is starting to feel a little old (although stable).

BTW, I may have a PCI video card spare, maybe this would work?

Any thoughts?

Thanks,

Chris.

---

### Post by amo-ej1 on 2006-09-11
Try to phsyically remove the creator card, this should result in the onboard card to be detected used. This solved issues with creator cards on sun blade 100's, perhaps it'll work on you ultra 10 too.

---

### Post by netztier on 2006-09-12
> **chris_andrew said:**
> Hi, all.
I have an Ultra 10 with an ATI card (Creator), and also have another (built in?) card listed in dmesg.


Are you sure that the Creator Card is ATI based? If I remember correctly, the GPU chips on the all Creator cards were "Sun only", and they use the **sunffb** driver module in X.org.

The onboard chips in the U5 and U10 are ATI based, however. From ATIs archives: [ATI RAGE™ PRO TURBO chip selected for Sun Microsystems' new Ultra 5 and Ultra 10 motherboard graphics]("http://www.ati.com/companyinfo/press/1998/4150.html"). In X.org, they use the **ati** driver module.

Have you already tried pulling the Creator Card out and giving Ubuntu installation another try, while only the onboard ATI graphics card is active?

regards

Marc

---

### Post by chris_andrew on 2006-09-12
Marc,

Removing the card is tonight's mission.  I will report the outcome.

Cheers,

Chris.

---

### Post by chris_andrew on 2006-09-15
Ripped the Creator out and using internal video device.  At least the install runs, now.  Question is, how do I get OpenPROM to use my PCI video card that i've added, instead of the built-in one?

Thanks,

Chris.

---

### Post by netztier on 2006-09-15
> **chris_andrew said:**
> Ripped the Creator out and using internal video device.  At least the install runs, now.  Question is, how do I get OpenPROM to use my PCI video card that i've added, instead of the built-in one?


What kind of card is that? If it's in the UPA slot (which is behind the PCI riser board) it most probably is a Sun card, and if i remember correctly, you're not going to see it in lspci.

I fear that hardware support for non-Sun cards is somewhat limited...

Can you make out a model number on the card? Here's the list of U10 supported video cards from sun's website:

```

370-4072 [F]  SunVideo Plus 
370-2256 [F]  PGX 8-Bit Color Frame Buffer,  also 370-3753
501-4789 [F]  Creator Series 3 (FFB2+)
501-5690 [F]  Creator3D Series 3 (FFB2+), also 501-4788
501-5484 [F]  Elite3D-m3, also 501-4860 
540-3902 [F]  Elite3D-m6, also 540-3623
370-3753 [F]  PGX32 8/24-Bit Color Frame Buffer 
501-5690 [F]  Creator3D Series 3 (FFB2+), also 501-4788
501-4789 [F]  Creator Series 3 (FFB2+) 
501-5574 [F]  Elite3D-m3 Series 2 Accelerator 
540-4313 [F]  Elite3D-m6 Series 2 Accelerator 
370-4362 [F]  PGX64 8/24-Bit Color Frame Buffer

```

You say that the installation runs now (hey, congrats! :-) )... Once done, try to put the creator card back in and switch over to "sunffb" as the X.org driver, if ubuntu boots.

regards

Marc

---

### Post by chris_andrew on 2006-09-15
Hi,

The card is a PCI one.

dmesg shows the following card:

atyfb 3D Rage Pro (Mach64)

but I suspect this is the built-in one, not my PCI card.

Hopefully will be able to find the make/ model when the installation is complete.

Many thanks,

Chris.

---

