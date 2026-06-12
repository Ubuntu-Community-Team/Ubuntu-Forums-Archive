---
title: "Firewall with OpenVZ"
date: 2009-10-29
forum: Server Platforms
---

### Post by ChromoX on 2009-10-29
I am in the process of setting up a OpenVZ based VPS, and I was wondering if there was a fix for using UFW on OpenVZ?(Currently it just fails on ufw-init), or if there was another tool like ufw that I could use to configure iptables without having to deal with iptables.

Thanks.

---

### Post by ChromoX on 2009-11-09
Anyone have any ideas?

---

### Post by smautf on 2009-11-19
I also get the ufw on OpenVZ init error.

I've since used [Shorewall]("http://www.shorewall.net/") on a Hardy OpenVZ based VPS with some success. Even got rudimentary port knocking through Shorewall just to try it!

---

### Post by bodhi.zazen on 2010-05-12
> **ChromoX said:**
> I am in the process of setting up a OpenVZ based VPS, and I was wondering if there was a fix for using UFW on OpenVZ?(Currently it just fails on ufw-init), or if there was another tool like ufw that I could use to configure iptables without having to deal with iptables.

Thanks.

This is an old thread, but for anyone who comes across this via google. search see :

[http://blog.bodhizazen.net/uncategorized/how-to-use-ufw-in-openvz-templates/](http://blog.bodhizazen.net/uncategorized/how-to-use-ufw-in-openvz-templates/)

---

