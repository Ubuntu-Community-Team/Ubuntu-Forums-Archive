---
title: "Error Ubuntu install on VMware fusion"
date: 2014-01-07
forum: Virtualisation
---

### Post by carl.pearce on 2014-01-07
Hi all,

Sorry my first post is for help, I successfully installed Ubuntu on my vmware fusion on mac, but at the commandline I get the below error and the cursur freezes.

[COLOR=#405A04][ 233.209703] hub 2-2:2:1.0: hub_port_status failed (err = -110)
[ 233.209703] hub 2-2:2:1.0: connect-debounce failed, port 1 disabled

cheers[/COLOR]

---

### Post by Bucky Ball on 2014-01-07
*Thread moved to **Virtualisation**.*

---

### Post by carl.pearce on 2014-01-08
No one know?

---

### Post by Bucky Ball on 2014-01-08
Doesn't look like it. Have you also posted this on Mac forums as you are using Mac software on a Mac computer? You might have more luck.

I can also move this to the ***Apple Users*** section if you'd like.

---

### Post by ZippyUbu on 2014-01-08
> [COLOR=#405A04][ 233.209703] hub 2-2:2:1.0: hub_port_status failed (err = -110)
[ 233.209703] hub 2-2:2:1.0: connect-debounce failed, port 1 disabled[/COLOR]

Hi - What version of Ubuntu are you running? What version of Fusion? Were you able to install VMware Tools? What USB devices have you connected through to the virtual machine (besides your mouse) Have a look through the output of ```
dmesg | grep -i usb
```[COLOR=#405A04]
[/COLOR]

---

### Post by zircon_34 on 2014-01-08
I also had issues installing Ubuntu using an outdated version of Fusion. This already happened to me when installing Mountain Lion. If you use OSX Mavericks you may have to upgrade to Fusion v.6.

---

