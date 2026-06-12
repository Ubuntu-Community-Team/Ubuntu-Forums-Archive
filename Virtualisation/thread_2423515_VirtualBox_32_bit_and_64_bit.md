---
title: "VirtualBox 32 bit and 64 bit"
date: 2019-07-24
forum: Virtualisation
---

### Post by jim Kane on 2019-07-24
Am I correct in thinking that the guest OS must be the same architecture 32-bit or 64-bit as the host OS 
i need to run a 32 bit windows XP as the guest os

---

### Post by TheFu on 2019-07-24
No.  
64-bit hostOS can run any supported guest.
32-bit hostOS can only run 32-bit guests unless there is VT-x CPU support.  You can check this in the virtual box manual.  It is fairly good. [https://www.virtualbox.org/manual/](https://www.virtualbox.org/manual/)
[https://askubuntu.com/questions/475653/does-virtualbox-run-64-bit-guests-on-a-32-bit-host](https://askubuntu.com/questions/475653/does-virtualbox-run-64-bit-guests-on-a-32-bit-host)

---

### Post by jim Kane on 2019-07-25
Thanks
 I had  have misread the notes on the  VirtualBox web page

---

