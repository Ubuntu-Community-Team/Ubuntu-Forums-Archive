---
title: "Sun Ultra 10 Creator Xorg problems."
date: 2006-10-28
forum: Sun Sparc Users
---

### Post by chris_andrew on 2006-10-28
Hi,

I have just managed to install Edgy on my Ultra 10.  First time I've managed to get Ubuntu on here, due to problems booting with the Creator card installed.

I used a work around, and now have a booting system.

Unfortunately, Xorg keeps erroring.

I did a normal install, no DNS/ LAMP server selected.  I then installed the Xorg and xubuntu-desktop packages.  That worked.

When I tried to startx, I get a similar problem to this:

Fatal Server Error:
xf86MapPciMem: Could not mmap PCI memory [then some address] (inappropriate ioctl device)

Has anybody else seen this, or can anyone help.  I really want to get the desktop working.

Many thanks,

Chris.

---

### Post by Delta_Farce on 2006-10-29
Is your creator card being found on the right PCI address?

Your xorg.conf should list an address for the PCI device, which you can check using the lspci command I think. 

Hope this helps, and sorry if it doesn't.

Cheers,

Mark

---

### Post by netztier on 2006-10-30
> **Delta_Farce said:**
> Is your creator card being found on the right PCI address?

Your xorg.conf should list an address for the PCI device, which you can check using the lspci command I think. 


To the best of my knowledge, Creators only ever came in UPA versions, never as PCI. If the card in question is PCI, it  probably is a PGX32 or PGX64 and based on either ATI or Permedia chips.

regards

Marc

---

### Post by chris_andrew on 2006-10-30
Hi,

The PCI card is ATI (Rage, I think).  

Thanks for the comments.  I did lspci and dpkg-reconfigure xserver-xorg, and the PCI addresses were the same.

Still no luck :-(.

Thanks,

Chris.

---

### Post by netztier on 2006-10-31
> **chris_andrew said:**
> Hi,

The PCI card is ATI (Rage, I think).  

Thanks for the comments.  I did lspci and dpkg-reconfigure xserver-xorg, and the PCI addresses were the same.

Still no luck :-(.

Thanks,

Chris.

Chris

If this card is PCI, it can't be a Creator. Is it a PGX32 with the Permedia2? I think there was another thread here recently with someone trying to get that one to run in an Enterprise 250, and I don't think it was successful either. Do you actually need two screens, or is the onboard adapter so bad that it's unusable?

regards

Marc

---

### Post by chris_andrew on 2006-10-31
Hi,

I don't need two screens.  I just thought that as I have a better graphics card, it would be great to use it.  I could go back to using the internal card, I guess.

Cheers,

Chris.

---

