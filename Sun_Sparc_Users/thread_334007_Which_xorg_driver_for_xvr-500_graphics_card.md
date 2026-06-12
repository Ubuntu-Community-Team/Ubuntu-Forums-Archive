---
title: "Which xorg driver for xvr-500 graphics card?"
date: 2007-01-08
forum: Sun Sparc Users
---

### Post by Basurero on 2007-01-08
Hi, I've succesfully installed Ubuntu server for SPARC on my Blade 2000 but I still haven't been able to configure Xorg. The sunffb driver does not respond ("device not found" error) and I haven't found any useful information for this video card.
  Has anyone had success configuring it? If so, which driver should I use?

  Thanks in advance,

  Lucas 'Basurero' Vieites

---

### Post by netztier on 2007-01-08
> **Basurero said:**
> Hi, I've succesfully installed Ubuntu server for SPARC on my Blade 2000 but I still haven't been able to configure Xorg. The sunffb driver does not respond ("device not found" error) and I haven't found any useful information for this video card.
  Has anyone had success configuring it? If so, which driver should I use?


**sunffb** won't be the right choice for XVR cards. Is that an UPA or a PCI card? does **lspci** give any meaningful output?

If the card is based on a Permedia Chip by 3Dlabs, the glint driver might work. 

However, when reading this [Blog Entry]("http://blogs.sun.com/alanc/entry/xorg_for_solaris_sparc"), things don't look that good...

best regards

Marc

---

### Post by Basurero on 2007-01-08
Hi, lspci shows this:
```

0000:00:01.0 Display controller: 3DLabs Sun XVR-500 Graphics Accelerator (rev 01)
        Subsystem: 3DLabs: Unknown device 1024
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 7568512
        Memory at 000007fd02000000 (32-bit, prefetchable) [size=32M]
        Memory at 000007fd00140000 (32-bit, non-prefetchable) [size=128K]
        Memory at 000007fd01000000 (32-bit, prefetchable) [size=16M]
        Expansion ROM at 0000000000110000 [disabled] [size=64K]
        Capabilities: [68] Power Management version 1

```

and I've already tried the glint driver to no avail.
I think I'll be asking for advice on the sun forums, maybe someone over there has more luck or experience.

  Thanks very much,
   cheers

---

### Post by torches on 2007-01-13
I would be also interested in the outcome of your search. I have an XVR-1200 on a SB2500.

---

### Post by torches on 2007-09-03
Anyone knows what does this mean  
>>> Graphics


      pm3fb: Preliminary 2.4 to 2.6 port (commit)

      New framebuffer driver (vt8623fb) for VIA VT8623 (commit)
 
      Hecuba framebuffer driver (commit)
    
      arkfb: new framebuffer driver for ARK Logic cards (commit)

      atmel_lcdfb: AT91/AT32 LCD Controller framebuffer driver (commit)

 >>>      Add Sun XVR-500 framebuffer driver. (commit) and Sun XVR-2500 framebuffer driver. (commit)

It is in the following page : 
[http://kernelnewbies.org/LinuxChanges](http://kernelnewbies.org/LinuxChanges)

Also in a [http://ubuntuforums.org/archive/index.php/t-531146.html](http://ubuntuforums.org/archive/index.php/t-531146.html)  has a reference to similar information

---

### Post by clarkritz on 2008-04-02
I also have a problem with the xvr-500 video card in a Sun Blade 1500.  I can get Ubuntu 7.10 to install on the SPARC system.  I can install ubuntu-desktop, but I can't configure xorg.

Now, I've also seen this recent "new kernel features" with the xvr-500 framebuffer.  I can't really add any new information to this thread.  I can speculate that there is a way to get X to send things through the kernel framebuffer exclusively.

I don't really know what I'm talking about (or what the frame buffer even is); just hoping I'll kick start someone else's thinking.

---

