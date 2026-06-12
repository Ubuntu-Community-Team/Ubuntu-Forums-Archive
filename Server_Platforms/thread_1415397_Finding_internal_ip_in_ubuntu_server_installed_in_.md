---
title: "Finding internal ip in ubuntu server installed in virtualbox."
date: 2010-02-24
forum: Server Platforms
---

### Post by bolla3 on 2010-02-24
Hi! 

I have installed ubuntu server in virtual box. Everything works smooth. But when setting it up with my dyndns free domain and forwarding the ports in my router I cant seem to find my internal ip. i have tried ifconfig but dont really understand, which of them is the internal ip :( I dont even know if it works like that.

---

### Post by joberly on 2010-02-24
ifconfig will indeed show your localhost's internal network IP address.

Post the output of it here.

On another note, make sure you have virtualbox networking configured properly, and set to bridged mode.

---

### Post by bolla3 on 2010-02-24
Thank you! Setting it in bridged mode was all i needed. *feels stupid*

---

