---
title: "How can I turn on pc without the &quot;drive&quot; external"
date: 2016-05-12
forum: Server Platforms
---

### Post by sed_faster on 2016-05-12
Hello everyone,

I don't know if I am in right place but will we go...
I have the pc with the ubuntu server, for I learn about that, but I think! If I want which this pc turn on a specially time of the day how can I do this? Imagine, the pc turn on at the seven o'clock (am) and turn off after 25 minutes. When 10 o'clock evening the pc turn on and repeat the behaviour! This is possible only which the pc or I will be create a little "drive" (component linked on the pc) to turn on and turn off?

If can't make the first option, which consist the pc management all process, I thought use a raspberry pi to server as the drive! Imagine, this raspberry pi, through the networking turn on the pc. But I don't know how configure this! This option I should set on bios or in the Linux?

Thanks

---

### Post by houstonbofh on 2016-05-15
Truning on a PC is not an OS thing, but a hardware thing.  You can set a "wakeup time" in the BIOS if you want to do this only once a day.  Otherwise, enable "Wake On LAN" (WOL) in the BIOS and use another computer to send a wol magic packet to wake the computer.

---

