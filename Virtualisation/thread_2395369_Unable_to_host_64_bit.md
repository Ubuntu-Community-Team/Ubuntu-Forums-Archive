---
title: "Unable to host 64 bit"
date: 2018-06-30
forum: Virtualisation
---

### Post by frrobert on 2018-06-30
I am currently running Ubuntu 16.04 64 bit
I have installed Virtual box Version 5.2.12 r122591 (Qt5.6.1) 64 bit.
I have changed my bios to support virtualization.
The only option I have is to host 32 bit Guest OSs

Is there another setting I am unaware of that I also need to change?

Thanks

---

### Post by Hund on 2018-06-30
By "changed my bios to support virtualization" you mean you enabled VT-x?

---

### Post by frrobert on 2018-07-01
In my Bios I  checked 2 boxes.
The first said enable Intel Virtualization Technology
The second said enable Intel VT for Direct I/O

---

### Post by frrobert on 2018-07-01
Long story short, I was able to update my bios and the issue is solved.

---

