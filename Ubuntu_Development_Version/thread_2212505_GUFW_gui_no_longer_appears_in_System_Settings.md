---
title: "GUFW gui no longer appears in System Settings"
date: 2014-03-21
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2014-03-21
Just noticed this:

[https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/1295783](https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/1295783)

Anyone care to confirm :)

---

### Post by Dreamer Fithp Apprentice on 2014-03-21
Dunno, but if it turns out to be a persistent problem, ufw is EXTREMELY easy to manage from a terminal.

---

### Post by mc4man on 2014-03-21
> **kansasnoob said:**
> Just noticed this:

[https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/1295783](https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/1295783)

Anyone care to confirm :)
The proposed change to the .desktop fixes this in an ubuntu (unity) session, as far as any other session don't know as I don't & won't have any other session installed

---

### Post by craig10x on 2014-03-22
It still comes up in the dash, though...just type gufw and you will see it...But i am not seeing it in systems settings...

---

### Post by kansasnoob on 2014-03-22
> **mc4man said:**
> The proposed change to the .desktop fixes this in an ubuntu (unity) session, as far as any other session don't know as I don't & won't have any other session installed

Thanks, I have a little time this PM but where do I find "gufw.desktop.in" :confused:

---

### Post by Mateusz Stachowski on 2014-03-22
You have to edit this file:

```
sudo nano /usr/share/applications/gufw.desktop
```

Of course you can use different text editor than nano.

Also the branch which resolves this bug is already [merged]("https://code.launchpad.net/~robert-ancell/gui-ufw/unity-control-center/+merge/206320") in gufw trunk so soon it will land in Trusty.

---

