---
title: "Disable Auto Assemble RAID on Boot"
date: 2012-09-19
forum: Server Platforms
---

### Post by RoboSK on 2012-09-19
Hi, is possible disable auto assemble raid on boot? - "need" this manually...

Thanks

---

### Post by rubylaser on 2012-09-20
The easiest way is to move it's udev rule and reboot.
```
mv /lib/udev/rules.d/64-md-raid.rules /root/
```
This will move it your your /root/ path so that you can always restored it later if you'd like.
```
reboot
```

Any arrays in your system will need to be assembled manually at that point.  I can't think of a case where this would be useful, can you explain why you need this functionality?

---

### Post by RoboSK on 2012-09-21
thanks **rubylaser** - this works - and it is my old ArchLinux way :)

---

### Post by rubylaser on 2012-09-21
No problem :)  Do you mind explaining why you need this behavior, I'm interested.

---

### Post by RoboSK on 2012-09-23
/me use HDD in external case and if i dont connect ok all cables then i maybe create problem - now have script to check if is connected all hdd and if is then assemble raid and mount...

"safe" :)

edit: RAID 5 with 5xHDD - i dont need extra shocks

---

