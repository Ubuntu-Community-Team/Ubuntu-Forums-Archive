---
title: "How to change font size on terminal"
date: 2015-04-24
forum: Server Platforms
---

### Post by satimis on 2015-04-24
Hi all,

Ubuntu 14.04 server

Please advise how to increase the font size?

Edit /etc/default/console-setup

Try 
FONTFACE="Terminus"
FONTSIZE="24x12" / "24"

and reboot without effect.

Thanks

Regards
satimis

---

### Post by slickymaster on 2015-04-24
What about```
sudo dpkg-reconfigure console-setup
```It would guide you through the steps to choose a font and font-size.

---

### Post by satimis on 2015-04-24
> **slickymaster said:**
> What about```
sudo dpkg-reconfigure console-setup
```It would guide you through the steps to choose a font and font-size.
Hi,

Thanks for your advice which is what I need.

satimis

---

### Post by slickymaster on 2015-04-24
You're welcome.

Just one other thing, the new settings will be effective after reboot. To apply immediately, just run ```
setupcon
```

---

### Post by satimis on 2015-04-25
> **slickymaster said:**
> You're welcome.

Just one other thing, the new settings will be effective after reboot. To apply immediately, just run ```
setupcon
```

Thanks

Regards
satimis

---

