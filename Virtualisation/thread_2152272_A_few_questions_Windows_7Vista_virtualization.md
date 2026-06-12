---
title: "A few questions Windows 7/Vista virtualization"
date: 2013-06-07
forum: Virtualisation
---

### Post by Coder88 on 2013-06-07
I'd like to consider setting up a virtualized Windows 7 (or Vista) on an ArtistX (ubuntu) 32-bit system I recently set up on a hard drive (Windows 7 on a different drive; dual boot). 

Question: **Should I buy another copy of Windows 7 OEM for the virtualization, because otherwise I assume Microsoft will have a fit if it 'sees' my original Win7 (on my other drive) being installed on a different 'computer' (virtualized) in addition to being on my other drive (non-virtualized)?** I also have a legal copy of Vista (though I hate Vista), that I could use. 

The main reason I have a dual boot system at this point is I need Windows for doing high end music composition using expensive instrument sample libraries that I have (Symphobia, East West Quantum Leap symphonic orchestra, etc-- simply not available for linux) and the software (Sibelius 7, Cubase) that uses those instrument libraries. My hope would be to get the music composition running in a virtualized Windows environment. Buying a second copy of Windows 7 for $99 or so would well be worth it if I could accomplish this.

I have installed virtualbox many times on my Windows 7 system, and have installed virtualized linux distros on my windows system, so I feel pretty fluent in using virtualbox, that is not the issue here.

---

### Post by 2F4U on 2013-06-07
> Question: **Should I buy another copy of Windows 7 OEM for the  virtualization, because otherwise I assume Microsoft will have a fit if  it 'sees' my original Win7 (on my other drive) being installed on a  different 'computer' (virtualized) in addition to being on my other  drive (non-virtualized)?** I also have a legal copy of Vista (though I hate Vista), that I could use. 


I am no lawyer but my understanding is that you have to buy a second copy of Windows 7 or use the existing copy of Windows Vista. Reason is that Windows recognizes the hardware it is installed on and therefore would complain when installed in the VM since it is already installed on different hardware. As far as I understand Microsoft licensing terms, it is illegal to install one copy on both physical and virtual hardware.

---

### Post by dragonfly41 on 2013-06-07
This thread might shed more light on this topic ..

[http://superuser.com/questions/25678/how-does-windows-7-licensing-work-for-running-the-os-as-virtual-machines](http://superuser.com/questions/25678/how-does-windows-7-licensing-work-for-running-the-os-as-virtual-machines)

---

### Post by Coder88 on 2013-06-07
> **dragonfly41 said:**
> This thread might shed more light on this topic ..

[http://superuser.com/questions/25678/how-does-windows-7-licensing-work-for-running-the-os-as-virtual-machines](http://superuser.com/questions/25678/how-does-windows-7-licensing-work-for-running-the-os-as-virtual-machines)

Sounds like I would need to purchase ($100) another copy of Windows for the virtualbox install on a linux host.  I might give my Windows Vista DVD a go then as a virtual OS, much as I do not care for Vista; but as a guest virtualised OS Vista might suffice for at least testing how well a virtual Windows works for some Windows software I need to run and at this point would have to reboot into Windows 7 to run (Sibelius 7, Cubase, and the sample instrument libraries that work with such software, like Symphobia and EWQL Symphonic Orchestra).  If a virtualized Windows 7 or Vista could run native Windows app nicely inside of a linux host, that could be really nice, lessen dual booting.

---

### Post by Coder88 on 2013-06-07
Can't find my VISTA disc, i might have tossed it that is how much i thought of Vista. But I did just now find my Windows XP disc, so I might install Windows XP as a virtual guest OS, nothing to lose; trick might be finding the SP3 service pack, but I would think that would be somewhere online on a torrent or something (just the SP, I legally own Windows XP).

---

### Post by dragonfly41 on 2013-06-07
SP3 is here ..

[http://technet.microsoft.com/en-us/windows/windows-xp-service-pack-3.aspx](http://technet.microsoft.com/en-us/windows/windows-xp-service-pack-3.aspx)

---

