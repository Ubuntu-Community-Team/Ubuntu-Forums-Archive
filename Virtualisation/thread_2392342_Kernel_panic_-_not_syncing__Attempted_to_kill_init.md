---
title: "Kernel panic - not syncing:  Attempted to kill init!"
date: 2018-05-20
forum: Virtualisation
---

### Post by andy.r2 on 2018-05-20
Hi!

I'm running 16.04 in a Virtual box, and have been for a good while.  I now get a 
```
Kernel panic - not syncing:  Attempted to kill init!
```

 during boot up, and no further progress.  

during GRUB loading, I can select advanced options, and see 
Linus 4.4.0-124-generic is the latest version that gives the above error, as does 4.4.0-1240generic in recovery mode.
I also have 4.4.0-81-generic which I can select and this boots successfully.  

Having loaded this version, I've attempted an apt-get update, apt-get upgrade.  This completes successfully, but I get the same Kernel panic error on re-boot to the default version.

so, how do I repair the latest version, so that the default version loads successfully?

---

### Post by howefield on 2018-05-20
Thread moved to the more appropriate "*Virtualisation*" forum.

---

### Post by cruzer001 on 2018-05-20
The newer kernels do not play well with older versions of vBox.  What version are you running?

---

### Post by andy.r2 on 2018-05-21
It's up to date... version 5.2.12r122591

---

### Post by cruzer001 on 2018-05-21
I have been hit in the pass with kernel panic and the only thing that has worked for me is a reinstall.  There are lots of suggestions out there

[https://www.google.com/search?client=ubuntu&hs=A5m&channel=fs&ei=VMACW6j7J4XEjwOswZrgDg&q=virtualbox+kernel+panic+not+syncing+attempted+to+kill+init&oq=virtualKernel+panic+-+not+syncing%3A+Attempted+to+kill+init&gs_l=psy-ab.1.0.0i7i30k1j0i7i10i30k1j0i7i30k1l2j0i8i7i30k1l3j0i7i5i30k1l3.115613.121940.0.128311.9.8.1.0.0.0.134.966.0j8.8.0....0...1.1.64.psy-ab..0.9.970...0i13k1j0i8i13i30k1j0i8i13i10i30k1.0.HzLRv7FICEw](https://www.google.com/search?client=ubuntu&hs=A5m&channel=fs&ei=VMACW6j7J4XEjwOswZrgDg&q=virtualbox+kernel+panic+not+syncing+attempted+to+kill+init&oq=virtualKernel+panic+-+not+syncing%3A+Attempted+to+kill+init&gs_l=psy-ab.1.0.0i7i30k1j0i7i10i30k1j0i7i30k1l2j0i8i7i30k1l3j0i7i5i30k1l3.115613.121940.0.128311.9.8.1.0.0.0.134.966.0j8.8.0....0...1.1.64.psy-ab..0.9.970...0i13k1j0i8i13i30k1j0i8i13i10i30k1.0.HzLRv7FICEw)

but no one answer to this.

If it was me, I think I would give HWE a shot and just reinstall if that didn't work.  I wouldn't invest a lot of time in it, but that's me, maybe you wish to pursue it.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

