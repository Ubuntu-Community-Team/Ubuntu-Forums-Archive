---
title: "Where can I find port names for iptables?"
date: 2010-06-04
forum: Server Platforms
---

### Post by leesiulung on 2010-06-04
I noticed you can use names for ports like ssh, instead of the actual port number in iptables, but I can't find a list of what they are? Anyone know?

I tried man pages and google, but none yields any result. Are they common or something?

---

### Post by Bachstelze on 2010-06-04
/etc/services

---

### Post by benderisgreat on 2010-06-04
iptables grabs it from /etc/services

---

### Post by leesiulung on 2010-06-04
Thanks guys!

---

