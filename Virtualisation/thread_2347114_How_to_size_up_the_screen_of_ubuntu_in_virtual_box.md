---
title: "How to size up the screen of ubuntu in virtual box?"
date: 2016-12-21
forum: Virtualisation
---

### Post by lukemone on 2016-12-21
I set up a virtualbox using the latest ubuntu version (LTS) and everything on the screen is pretty small. How do I size it up?

Virtualbox version: 5.1.12

My OS: Windows 10

Ubuntu version: Ubuntu desktop 16.04.1 LTS

Thanks in advance

-Luke

---

### Post by ajgreeny on 2016-12-21
You probably need to use the guest additions, which are available by using the **Devices -> Add Guest Additions iso** you will then need to run the **VBoxLinux.run** script in a root terminal which I always do with command ```
sudo -i
```

Give that a try and if it does not work come back again.

---

