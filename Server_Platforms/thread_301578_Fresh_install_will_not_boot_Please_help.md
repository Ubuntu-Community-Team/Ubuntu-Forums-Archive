---
title: "Fresh install will not boot Please help"
date: 2006-11-17
forum: Server Platforms
---

### Post by luvdemheels on 2006-11-17
I get the following when it tries to boot:

MP-BIOS bug: 8254 timer not connected to IO-APIC
iop0: device already claimed
iop0: DMA / IO allocation for I2O controller failed
Alert! /dev/i20/hda1 does not exist dropping to a shell

The install went great until it finished and tried to boot. I have an adaptec 3200S raid controller with a raid 5. Thanks for any help.

---

### Post by RicochetPeter on 2006-11-23
OK, this issue is related to [a known bug/problem](https://launchpad.net/distros/ubuntu/+bug/52956). The installer seems to be using i2o_block, which might be the only i2o driver in the single processor kernel. After installation, upon booting the SMP kernel, which has dpt_i2o AND i2o_block, the dpt driver is laoded first and doesn't find any devices at /dev/i2o/..., so the boot process stops.

A workaround is to edit the kernel line (and/or /etc/fstab) and exchange /dev/i2o/hda by /dev/sda, f.e.

I posted a question in the bug two days, but I must confess it's not actually the right place to do. So here's my question to the ubuntu folks:

Is there a way to make the boot process NOT load dpt_i2o, but only i2o_block? I read something about "blacklisting", but am not quite sure what that means...

btw, I only tested in Dapper, but this problem seems to persist in Edgy, which I will find out during my lunch break :)

---

### Post by RicochetPeter on 2006-11-23
OK, confirmed in Edgy, same problem. So, the question remains: how do I prevent dpt_i2o from being loaded at boot time?

---

### Post by RicochetPeter on 2006-12-01
Hi again folks,

I've noticed that hardware questions like I have them don't seem to get much input here.... does anyone know of a place where poeple discuss things like these in more detail?

My other thread about fibre channel device detection ([http://ubuntuforums.org/showthread.php?t=279712](http://ubuntuforums.org/showthread.php?t=279712)) also received no input at all... :???:

---

