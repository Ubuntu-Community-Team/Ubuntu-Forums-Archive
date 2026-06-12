---
title: "no SATA drive found on random boots"
date: 2009-12-15
forum: System76 Support
---

### Post by in0giro on 2009-12-15
ahoy all,

  i recently purchased a new System76 Darter Ultra.  so far i have very happy with the system, especially as this is the first computer that i have used on which everything works right out of the box with GNU/Linux :)  kudos system76.

  there is however a small problem, which i believe is either the hard drive (HD) or BIOS:  when booting (after a restart or shutdown+cold start) the BIOS sometimes freezes during initialization, looking for the HD on the first SATA port (right after listing the video adapter, before listing the HD info).  it does sound as if the HD is not spinning at all.  if left long enough, the BIOS eventually gives up and the computer attempts to start without the HD, defaulting to PXE net boot which also fails.  so far, holding down the power button for a few seconds and restarting results in the system booting up normally.  however, one can see that so far the computer is not reliably starting nor restarting.

  does this sound like a hard drive, BIOS, or motherboard issue?  i figured it may be a BIOS issue, since i think it is an EFI enabled BIOS.  however, i have the default settings and it still occurs.  i will keep searching for this problem (and have contacted support ... at .. system...76), but wanted to know if anyone had anything similar.

  thanks in advance.

peace.

---

### Post by thomasaaron on 2009-12-16
If I haven't answered your email already, I will. 

But you might try removing your battery and ac adapter and re-seating your hard drive.

---

### Post by in0giro on 2009-12-16
ahoy Tom,

  thanks for the post.  i have not yet received your reply to my support email, though perhaps the forum is better since others are able to use our results.

  i did try re-seating the drive and still no luck.  seems to mostly occur on cold starts, not restarts.  however, it has been happening on both.

  is there a BIOS update to try?  or perhaps some BIOS setting?  i noticed in the advanced config the OS is set to Vista by default.  not sure if this makes a difference or not.

peace.

---

### Post by thomasaaron on 2009-12-17
Sorry, I've gotten deluged with emails. I do see yours, and I'll answer it.

If this was BIOS related, we'd be seeing it across the board. I think a replacement HD is the way to go, and I'll provide further details in my email.

---

