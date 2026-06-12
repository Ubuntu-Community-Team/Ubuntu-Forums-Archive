---
title: "Suspend/Resume Intel Z68 Sandy Bridge"
date: 2012-02-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by fjgaude on 2012-02-29
On my Z68 Intel chipset motherboard, ASRock Model 68M-ITX/HT, with i5-2405S CPU, latest UEFI BIOS, computer goes into **Suspend** but does not **Resume**. Have tried many different settings without success. Booting is not an issue.

Any ideas, workarounds, anyone? Thank you!

---

### Post by bupe on 2012-02-29
I have the same issue with a Gigabyte Z68 so this seems to be chipset specific. I'll post logs tomorrow.

---

### Post by bupe on 2012-02-29
I kept reading and found this:

 [http://blog.le-vert.net/?p=24](http://blog.le-vert.net/?p=24)

Looks promising, I will try this tomorrow and report back.

---

### Post by fjgaude on 2012-02-29
Well, I don't know... there is no "AE_NOT_FOUND" in my **dmesg** log.

```
[    0.580983] i2c-core: driver [aat2870] using legacy suspend method
[    0.580984] i2c-core: driver [aat2870] using legacy resume method
```

Can't say what this means. I'm interested in seeing what you get from your dmesg log.

---

### Post by bupe on 2012-03-01
Well it seems I'm lucky, this is what I got from 

```
dmesg | grep AE_NOT_FOUND
```:

> [    0.292836]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d

I just finished installing the 3.2.1 kernel from deb package - unfortunately it did not contain the fix, so I will do the following:

1. Install the latest stable 3.2.9 kernel from source and see how that works. Since I will be using source I will attempt to add the fix from the article.
2. If the above is not good enough I will have a look at the 3.3rc5 kernel - according to the article 3.3 should contain the fix by default.

---

### Post by fjgaude on 2012-03-01
I'll be waiting to hear how you do... I guess my BIOS is somewhat different. We'll see what happens as time goes by.

Please do keep us informed.

---

### Post by Tweak42 on 2012-03-02
I just did an in place upgraded today for my desktop from 11.10 to 12.04 beta1 and my suspend resume works ok.  
Hardware: Asus P8Z68-V, i5-2500k cpu, Nvidia Geforce GTX-480 w/ 295.20 drivers

---

### Post by fjgaude on 2012-03-02
> **Tweak42 said:**
> I just did an in place upgraded today for my desktop from 11.10 to 12.04 beta1 and my suspend resume works ok.  
Hardware: Asus P8Z68-V, i5-2500k cpu, Nvidia Geforce GTX-480 w/ 295.20 drivers

Wow, I just did a suspend/resume and it worked... wonder if it is fixed for sure? We'll see, eh?

###

I spoke too soon. When I suspended for a longer time than at first, the machine wouldn't resume. Just as it was before the Beta came out. So...

---

### Post by bupe on 2012-03-03
I just did a fresh install of 12.04 Beta 1 - I got stuck while trying to compile the 3.2.9 and 3.3-rc5 kernels. I can confirm that suspend/resume works for me as well! :-) However I'm still getting the error message AE_NOT_FOUND...

---

### Post by MacUntu on 2012-03-03
Asus P8Z68-V, Intel Core i5-2500K with Intel HD Graphics 3000, never had resume issues.

---

### Post by fjgaude on 2012-03-03
> **bupe said:**
> I just did a fresh install of 12.04 Beta 1 - I got stuck while trying to compile the 3.2.9 and 3.3-rc5 kernels. I can confirm that suspend/resume works for me as well! :-) However I'm still getting the error message AE_NOT_FOUND...

Yes, yes! The 3.3-rc5 kernel caused yours to work? I guess I'll have to give that kernel a try.

---

### Post by fjgaude on 2012-03-03
> **MacUntu said:**
> Asus P8Z68-V, Intel Core i5-2500K with Intel HD Graphics 3000, never had resume issues.

Now this is interesting... wonder what gives. The issue must be something other than the ACPI 5.0 situation.

Now to remember how to install new kernels from .deb files. <smile>

###

Okay, with the 3.3-rc5 kernel I'm good to go, suspend/resume. (from the change log of rc1 I can see where they fixed the resume issue)

MacUntu, could you tell us what kernel you are using? Thanks!

---

### Post by fjgaude on 2012-03-03
Well, the new kernel requires later versions of gcc to get VMware Player to work... so I guess I'm back to waiting for the repositories to update the kernel to 3.3 or later and that could take months. So I'm back to not using suspend/resume.

---

