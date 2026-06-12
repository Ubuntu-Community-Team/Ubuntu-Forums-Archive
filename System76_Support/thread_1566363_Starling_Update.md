---
title: "Starling Update"
date: 2010-09-02
forum: System76 Support
---

### Post by THNDRRR on 2010-09-02
Sorry if this was already covered.  I didn't see it anywhere.

Are you guys still working on a 4 GB version of the Starling ?

Getting ready to purchase and wanted to hold out until I knew for sure.
:popcorn:


Thanks guys

---

### Post by jml on 2010-09-02
I'm sure one of the System 76 reps can answer this more difinitively than I can, but from what I have read, Ubuntu's netbook optimized OS, (the one S76 installs on the Starling,) is only available in 32 bit format. A 32 bit OS cannot address 4 gig's of RAM.  I think it tops out somewhere in the neighborhood of 3.8 gig.  So theoretically, you would not be able to utilize all of the ram you are paying for.  By the way, I believe that is why many bargan basement laptops come with only 3 gig's of RAM, they are usually loaded with a 32 bit OS.

Joe

---

### Post by Skaperen on 2010-09-02
> **jml said:**
> I'm sure one of the System 76 reps can answer this more difinitively than I can, but from what I have read, Ubuntu's netbook optimized OS, (the one S76 installs on the Starling,) is only available in 32 bit format. A 32 bit OS cannot address 4 gig's of RAM.  I think it tops out somewhere in the neighborhood of 3.8 gig.  So theoretically, you would not be able to utilize all of the ram you are paying for.  By the way, I believe that is why many bargan basement laptops come with only 3 gig's of RAM, they are usually loaded with a 32 bit OS.

Joe
In general, a 32-bit OS with PAE or PSE-36 support can go up to around 64GB in a PAE or PSE-36 equipped CPU.  PAE and PSE-36 have been around for years.  Linux has supported it since 2.3.23.  The kernel cannot access all of RAM virtually at the same time.  Processes are still limited to less than 4GB, maybe even as low as 1GB, depending on how the memory access model is configured.  Also, the CPUs used by netbooks may not have PAE support and the kernels built for netbook distributions may not have PAE support.  PSE-36 is no longer used.  I don't know if Linux ever supported PSE-36.

My home server has been running a 32-bit kernel on an older Slackware with 8GB of memory (with the memory hole area moved up to just above the 8GB address line, so I get to use all of my RAM) for the past 3 years.

64-bit is still the preferred way to go if you can do it, for any memory size above 2GB (or even 1GB in some cases).  If you can't, PAE is the solution to get above 4GB.  if you need larger virtual memory space, you need 64-bit (long mode).

Read more at [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

### Post by msrinath80 on 2010-09-02
> **Skaperen said:**
> In general, a 32-bit OS with PAE or PSE-36 support can go up to around 64GB in a PAE or PSE-36 equipped CPU.  PAE and PSE-36 have been around for years.  Linux has supported it since 2.3.23.  The kernel cannot access all of RAM virtually at the same time.  Processes are still limited to less than 4GB, maybe even as low as 1GB, depending on how the memory access model is configured.  Also, the CPUs used by netbooks may not have PAE support and the kernels built for netbook distributions may not have PAE support.  PSE-36 is no longer used.  I don't know if Linux ever supported PSE-36.

My home server has been running a 32-bit kernel on an older Slackware with 8GB of memory (with the memory hole area moved up to just above the 8GB address line, so I get to use all of my RAM) for the past 3 years.

64-bit is still the preferred way to go if you can do it, for any memory size above 2GB (or even 1GB in some cases).  If you can't, PAE is the solution to get above 4GB.  if you need larger virtual memory space, you need 64-bit (long mode).

Read more at [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

+1 My System76 Lemur (lemu1) runs a 32 bit Debian squeeze kernel. No problems seeing all the 4 gigs. The plus side is that I get no problems with flash player or other software that requires quirks before it can be used in 64 bit mode.

---

### Post by jbelmonte on 2010-09-03
From a Tweet from System76 on July 19, 2010:

> 640GB hd stress test in the new Starling Netbook completed successfully. Having trouble with 4 GB of ram. Possibly a chipset limitation.

This may be why there is not a 4GB option for the Starling, but someone from System76 will have to confirm.

---

### Post by isantop on 2010-09-03
jbelmote has it right %100. We'll have to wait for a new chipset to use RAM larger that 2 GB.

---

