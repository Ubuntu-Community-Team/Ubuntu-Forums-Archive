---
title: "Win7 x64 host, Karmic x64 guest - no sound input"
date: 2010-04-07
forum: Virtualisation
---

### Post by Xianath on 2010-04-07
I've searched far and wide but it doesn't look like many people are using Linux guests on Windows hosts, let alone where sound input is involved. This is however my setup and I'd like to get it working. Everything else (mostly) works, including sound output. Anyone with a success story getting sound input to work? Is it even possible?

Thanks,
Peter

---

### Post by TheFu on 2010-04-07
I ran VirtualBox (not OSE) with both a 32 and 64bit Vista and Win7 host. Sound worked under it for all the *nix* clients that I can recall with little issue. I don't really recall any issue except when the host sound would fail, it would obviously not work in a client too.

I ran xubuntu 8.0.4 full screen for over a year and got to the point where I forgot it was running in a VM. It was my day-to-day OS.  I did find that I needed to reboot the host OS weekly or it would lock up (not BSOD), just lock up.  In Dec, I moved to xubuntu 9.10 as my daily use VM. Still no sound issues. It sorta just worked. Nothing special needed.  I think I always selected the "SB16" setting for emulation, but I honestly don't recall.

---

### Post by Xianath on 2010-04-07
Thanks TheFu. Does sound working for you also include sound input? I haven't had any luck with SB16 BTW, but I'll give it another go.

---

