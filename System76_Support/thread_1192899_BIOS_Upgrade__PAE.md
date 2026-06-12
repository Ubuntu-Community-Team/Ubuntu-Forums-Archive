---
title: "BIOS Upgrade / PAE?"
date: 2009-06-20
forum: System76 Support
---

### Post by Rowan187 on 2009-06-20
Alright, so I'm still rocking my Pangolin Value (PanV2), and decided to finally upgrade from 2gb RAM to 4gb RAM. When I put in the RAM, i was running Windows 7 32bit, which said i had 4 GB ram, but only 2.87gb was usable, I expected this to happen, so I decided to install the 64bit OS. When I installed the 64bit version of Windows 7, my RAM said 4gb found, 2.87 gb usable.

I figured maybe Ubuntu 9.04 64bit would be different, but then checked the SysInfo in my BIOS and it said "Max memory: 2897mb" or something like that, meaning my motherboard/bios itself perhaps doesn't even allow more. This saddens me :(

I read a lot about a kind of hack/workaround/feature called PAE (Physical Address Extension), but haven't really figured out how to do it yet

So my main question is does anyone know how I'd be able to get more RAM for my OS/Bios and such?

My bios says

Z96FM Bios
Version: 0301
Date: 05/14/07

Perhaps there's an upgrade to the bios to support 4gb RAM? I dunno, I'm kind of sad that I spent money on getting only 0.87 GB more ram :'(

Any help/ideas?

---

### Post by Rowan187 on 2009-06-26
Damn :(

---

### Post by rumblered on 2009-06-26
I would think if a 64-bit system supports PAE, then it would also support native 64-bit access to > 3 GB of RAM. PAE was a hack to get more memory on a 32-bit system or OS.

Though I heard memtest86+ uses PAE, so you could use that as a quick and simple test to see if setting up PAE will get you anything.

---

### Post by Rowan187 on 2009-06-26
> **rumblered said:**
> I would think if a 64-bit system supports PAE, then it would also support native 64-bit access to > 3 GB of RAM. PAE was a hack to get more memory on a 32-bit system or OS.

Though I heard memtest86+ uses PAE, so you could use that as a quick and simple test to see if setting up PAE will get you anything.

I'll give that a try, but seeing the limit in my BIOS kind of makes me worry. Perhaps I need to do a search on my exact motherboard to see if anyone has come up with anything. I figured I'd ask System76 first before I did anything stupid. Can't afford to buy a new laptop at the moment (or any time soon)

---

### Post by thomasaaron on 2009-06-29
I'm not aware of a BIOS update that extends the PanV2's ability to recognize more RAM.

---

