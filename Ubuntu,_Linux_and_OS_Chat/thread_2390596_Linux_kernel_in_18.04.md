---
title: "Linux kernel in 18.04"
date: 2018-04-30
forum: Ubuntu, Linux and OS Chat
---

### Post by rattskjelke on 2018-04-30
I don't understand something.
Ubuntu 18.04 ships with Linux kernel version 4.15.
Last week I read that the Linux kernel maintainers ended support (EOL) for 4.15 and recommended moving to 4.16.
Does this mean that 18.04 will get 4.16 soon or will Ubuntu maintain 4.15 themselves?

---

### Post by deadflowr on 2018-04-30
> Does this mean that 18.04 will get 4.16 soon or will Ubuntu maintain 4.15 themselves?

The Ubuntu kernel team will maintain the 4.15 kernel themselves.

---

### Post by Claus7 on 2018-04-30
Helo,

> **deadflowr said:**
> The Ubuntu kernel team will maintain the 4.15 kernel themselves.

yet this means that 4.15 will remain for the entire life of 18.04? I guess that soon enough there will be an update for 4.16. No? 

Regards!

---

### Post by monkeybrain20122 on 2018-04-30
> **Claus7 said:**
> Helo,



yet this means that 4.15 will remain for the entire life of 18.04? I guess that soon enough there will be an update for 4.16. No? 

Regards!

If you enable HWE for LTS, otherwise probably no.

---

### Post by Claus7 on 2018-04-30
Hello,

> **monkeybrain20122 said:**
> If you enable HWE for LTS, otherwise probably no.

yup! And a graphical info about this quotation:
[https://wiki.ubuntu.com/Kernel/Support](https://wiki.ubuntu.com/Kernel/Support)

which about 18.04 is:
ga (general availability) = 4.15 for entire life
hwe (hardware enablement kernel) - >= 4.15

Regards!

---

### Post by grahammechanical on 2018-05-04
This chart might give some clarity. Or may be not.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Look for the chart: 18.04.x kernel support. Ubuntu is at version 18.04.0 with Linux kernel version 4.15 and this kernel will be supported by Ubuntu for the 5 years of the 18.04 support period. To keep up with the release of newer Linux kernels Ubuntu has what are called point releases. This is the Ubuntu point release schedule. As you can see much is still to be decided. And this includes what kernel will released with Ubuntu 18.04.2 and onwards.

[https://wiki.ubuntu.com/BionicBeaver/ReleaseSchedule](https://wiki.ubuntu.com/BionicBeaver/ReleaseSchedule)

If I remember correctly, we will be prompted to upgrade to the newer Hardware Enablement Stack which will bring a newer kernel. Or we can choose to stay on kernel 4.15. Ubuntu ISO images for download will come with upgraded kernels which will keep Ubuntu up to date with newer hardware.

For comparison, here is the 16.04 release schedule. You can see the dates of the point releases which will be a guide for how things will be done with 18.04.

[https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule](https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule)

Regards.

---

