---
title: "Bonobo P5 NOT compatible with 11.10!"
date: 2011-10-29
forum: System76 Support
---

### Post by CaptSaltyJack on 2011-10-29
I had a problem with the LightDM greeter not coming up, and the System76 driver not running. The latter issue seems to have randomly fixed itself. The LightDM not coming up due to the nvidia kernel not being loaded yet is a known issue. The workaround is to edit /etc/init/lightdm.conf and add 'sleep 2' before 'exec lightdm'. Hacky, but it works.

---

### Post by CaptSaltyJack on 2011-10-31
.

---

