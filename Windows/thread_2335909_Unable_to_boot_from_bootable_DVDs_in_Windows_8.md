---
title: "Unable to boot from bootable DVDs in Windows 8"
date: 2016-09-02
forum: Windows
---

### Post by tech291083 on 2016-09-02
Hi Friends,

I have this 2/3 years old Lenovo Z580 laptop with Windows 8 (not 8.1, Single language, 64-bit) and I want to boot a bootable CD/DVD such as Ubuntu 16.04 LTS Desktop 32/64 bit, Fedora etc and if possible install them alone (remove Windows 8 completely) or install them alongside it, but I am not able to boot from CD/DVD, not even Windows 8 DVD is booting. 

I went to Settings > Change PC Settings > General > Advanced Startup > Restart Now.

Then I chose Troubleshoot > Advanced Options > UEFI Firmware Settings > Restart.

Then I got to Boot Menu, where I chose my DVD Drive and pressed enter, but instead of booting from the Ubuntu DVD, PC booted normally into Windows 8.

But I tried something else, this time I I went to Settings > Change PC Settings > General > Advanced Startup > Restart Now.

Then I chose Use a device > ATAPI CD MATSHITA DVD-RAM UJ8D1.

but again instead of booting from the Ubuntu DVD, PC booted normally into Windows 8.

Can you please help? Thanks a lot.

---

### Post by coldraven on 2016-09-03
Make sure that Windows is really shutting down and not going into suspend. In the BIOS it might be called "Quick Boot" or something similar, disable it.
Can you check the CD in another machine to make sue that is is actually bootable?

---

### Post by tech291083 on 2016-09-03
> **coldraven said:**
> 
Make sure that Windows is really shutting down and not going into suspend. In the BIOS it might be called "Quick Boot" or something similar, disable it.


You may be 100% right, but I am not able to get into BIOS, let alone disable it.

> 
Can you check the CD in another machine to make sue that is is actually bootable?


Oh yes, all the CDs are very much bootable on other pcs and laptops.

Thanks a lot for the help so far, but I need more of the same.

---

### Post by pfeiffep on 2016-09-03
**I am not able to get into BIOS, let alone disable it.**

From the user manual ...
Novo button When the computer is off, press this button to start the
Lenovo Recovery system or the BIOS setup utility, or to
enter the boot menu.

---

### Post by tech291083 on 2016-09-03
There is a small special purpose button next to the regular power button on my Lenovo laptop called the Novo button, if one presses that button, he has the chance to get into BIOS as shown in the attached images. But whenever I try that I am asked to provide a password. And after 3 failed attempts there is a message called "system locked".

Below is the normal Novo button,

[https://lnv.i.lithium.com/t5/image/serverpage/image-id/8477iCC2A990BAFF1E587?v=v2](https://lnv.i.lithium.com/t5/image/serverpage/image-id/8477iCC2A990BAFF1E587?v=v2)

Pressing the Novo button gives these options as shown in the images listed below,

[URL="http://i.stack.imgur.com/5Lbwd.png"]http://i.stack.imgur.com/5Lbwd.png
[/URL]
Thanks.

---

### Post by pfeiffep on 2016-09-03
Apparently you or a previous owner set a bios password, or the default is still in place. I can't help

---

### Post by tech291083 on 2016-09-04
> **pfeiffep said:**
> Apparently you or a previous owner set a bios password, or the default is still in place. I can't help

I do not remember setting a password at all, previous owner was myself only. I appreciate your effort to help me. Thanks.

---

### Post by tech291083 on 2016-09-04
> **pfeiffep said:**
> **I am not able to get into BIOS, let alone disable it.**

From the user manual ...
Novo button When the computer is off, press this button to start the
Lenovo Recovery system or the BIOS setup utility, or to
enter the boot menu.

Oh yes, I know this from the user manual, thanks.

---

