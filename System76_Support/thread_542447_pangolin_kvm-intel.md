---
title: "pangolin kvm-intel?"
date: 2007-09-03
forum: System76 Support
---

### Post by dantrevino on 2007-09-03
Are the virtualization extensions enabled on the pangolin bios?  In other words, can I load kvm-intel successfully?

Some other laptops have this disabled, and no way to enable it in the bios.


TIA,
dan

---

### Post by thomasaaron on 2007-09-04
There is nothing obvious in the BIOS for enabling virtualization.

---

### Post by dantrevino on 2007-09-04
> **thomasaaron said:**
> There is nothing obvious in the BIOS for enabling virtualization.

Can you test loading the kvm module?

```
sudo modprobe kvm-intel
```


This would only work on the core 2 duo laptops, not the celerons.  If the extensions are not enabled you'll see a "Operation not supported" error.

tia,
dan

---

### Post by thomasaaron on 2007-09-04
I'm currently testing VT capabilities on all of our laptops. I'll post my findings here when I'm done.

---

### Post by dantrevino on 2007-09-14
> **thomasaaron said:**
> I'm currently testing VT capabilities on all of our laptops. I'll post my findings here when I'm done.


Any updates?

---

### Post by dantrevino on 2007-09-19
bump

---

### Post by thomasaaron on 2007-09-19
I used the XEN live cd to test.

It appears that Virtualization is enabled on the Darter but not on the Pangolin.

I could not get the CD to boot on the Serval. I've got instructions for testing on a serval by installing XEN on Ubuntu, but
I don't currently have a Serval in the shop to test on, but when I get one in, I will.

---

### Post by Zxaos on 2007-09-19
So would we be looking at a BIOS update for Pangolins with core 2 duos?

---

### Post by thomasaaron on 2007-09-19
I'm not sure. I haven't gotten that far.
I'll keep you updated.

---

### Post by Zxaos on 2007-12-26
I've had no problems running kvm-intel on my panv3 (but it's got a core2 duo, not a celeron)

---

