---
title: "Mature motherboard supporting virtualization, any recommendation?"
date: 2008-06-15
forum: Virtualisation
---

### Post by jmn42 on 2008-06-15
Is there any recent list with motherboards that both plays well with Ubuntu AND has bios support to activate virtualization for the CPU?

I tried my luck with the Ubuntu HW compatibility WIKI but at least the ones I checked up (downloaded vendors manual + browsed BIOS updates) showed no signs  of support. I mainly checked ASUS, and there it appeared to be support only on newer boards, which instead suffered problems with drivers not in the standard distribution yet.

I'm about to buy a new CPU+motherboard to get hardware support for virtualization. Nothing fancy. Just something that works so I can learn how to use Xen or KVM. Thus I really prefer something mature = cheap + simple Ubuntu install.

If there is no good list, you may have success stories to share?
I have an AMD x2 bias, but just a very small bias.

---

### Post by calraith on 2008-06-16
I can tell you that some NForce boards are prone to have problems with APIC.  This is because there was a bug in the ACPI tables published in the reference BIOS back in the NForce2 days, which manufacturers have been recycling generation after generation (even though no NVidia reference BIOS since then has contained the bug).  I kept bugging Gigabyte over and over until they finally sent me a fixed BIOS for my GA-M57SLI-S4.  They also fixed hardware virtualization for me.  As a note of interest, you might find [http://ubuntuforums.org/showthread.php?t=430801](http://ubuntuforums.org/showthread.php?t=430801) entertaining / informative / whatever.

---

### Post by jmn42 on 2008-07-03
I went for the Gigabyte GA-M57SLI-S4 since it was fairly mature by now, and they had documented in a BIOS release that virtualization indeed was added.

It appears to work. There was an option in BIOS, Virtualization bit is reported and KVM accepts it. I still have some issues installing win2k, but that's after the windows reboot so it obviosly runs.

As for ACPI it might be solved. I just clicked on the shutdown (in Hardy Heron) icon and it went off OK without issues. I remember big trouble with ACPI and shutdown with Gutsy on my fairly old Dell before it worked smooth.
I'm not sure if its the new MB or the new Ubuntu that solved this though.

---

