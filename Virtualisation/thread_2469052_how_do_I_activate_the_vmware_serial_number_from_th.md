---
title: "how do I activate the vmware serial number from the terminal ?"
date: 2021-11-18
forum: Virtualisation
---

### Post by etneulfa on 2021-11-18
Hello, I would like to know how I can run vmware from the terminal in root mode and adding the serial number , thanks

---

### Post by MAFoElffen on 2021-11-18
Go to terminal and enter
```

sudo vmware

```
If it says not found, then enter the path_to before it... If you have gksudo installed, you could use gksu instead of sudo... Running Workstation as root is not recommend, unless you are diagnosing if you have a permissions problem...

In Workstation, go to Help > Enter License Key... Enter the serial number.

---

