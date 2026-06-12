---
title: "Jumpy scroll wheel"
date: 2012-01-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dirtylobster on 2012-01-26
I just installed 12.04 and I'm experiencing some weirdness with the mouse. My computer is an Asus U36SD laptop.

When I scroll up and down using the scrollwheel (Logitech VX Nano) the page/list randomly jumps up/down if I move the mouse simultaneously. If I'm holding the mouse in the air while scrolling the page/list scrolls fine.

Two-finger scrolling is also buggy but not in the same way. It takes a huge leap when I start scrolling but after that it works fine.

The problem is system-wide.

What could be the cause of these problems and how can I fix it?

---

### Post by TerryNewton on 2012-01-26
> **dirtylobster said:**
> When I scroll up and down using the scrollwheel (Logitech VX Nano) the page/list randomly jumps up/down if I move the mouse simultaneously. If I'm holding the mouse in the air while scrolling the page/list scrolls fine.

The same thing happens under VirtualBox (4.1.8) after the X11 update. If the mouse pointer is held completely still then scrolling works OK, otherwise it jumps randomly. Some kind of driver thing as disabling the "mouse integration" makes scrolling work OK.

---

### Post by dirtylobster on 2012-01-28
Hmm, it's been really weird the last few days. The problem comes and goes without any apparent connection to what I've been doing.

---

### Post by kaldor on 2012-01-28
Confirmed here. Yesterday this happened a few times but haven't had it since. Unsure what triggers it.

---

### Post by dirtylobster on 2012-02-01
Didn't have any problems for a few days but now, right after starting Wine the scrolling is all jumpy again.

---

### Post by Kow on 2012-02-01
I'm running Ubuntu 12.04 64-bit in a Virtualbox 4.1.8 environment, host being Win 7 64-bit with a dual monitor setup. After scrolling three times, and on the fourth time, the scroll jumps back to where I was before I started scrolling. If I scroll three times, wait a couple seconds, the "counter" resets and I can scroll in the same direction another three times.

I do have the guest additions installed, and I do not recall having this issue in any of the other VBox O/S' I have installed (Linux Mint 12 64-bit, Win XP, Ubuntu 10.04 64-bit). My guess is this is a xorg "issue" which can be corrected with a xorg config quirk. I'm just not sure where to begin with it. It appears that xorg uses evdev to catch all mouse pointers, and there is a quirk file for specific mouse types. These quirks do not seem to apply to the virtualbox pointer. Perhaps this has to do with the "Timeout" value set in the generic evdev "pointer catchall", maybe...

---

### Post by effenberg0x0 on 2012-02-01
+1
Same behavior on VirtualBox, VMWare-Player and default install, since yesterday. It's happens also on Unity 5 or 5.2, so it must be something else.
Looking for clues...

Regards,
Effenberg

---

