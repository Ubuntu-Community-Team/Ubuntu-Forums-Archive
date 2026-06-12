---
title: "Opened Outgoing ports"
date: 2010-06-01
forum: Security
---

### Post by oshirowanen on 2010-06-01
I read somewhere (forgot where) that by default ubuntu has all incoming ports closed and all outgoing ports open.

Is it possible for me to close all outgoing ports except the ones I need?

---

### Post by suseendran.rengabashyam on 2010-06-01
Hi,

UFW is the default firewall in Ubuntu, you can refer the UFW community wiki for more details

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Hope this helps.

---

### Post by bodhi.zazen on 2010-06-01
> **oshirowanen said:**
> I read somewhere (forgot where) that by default ubuntu has all incoming ports closed and all outgoing ports open.

Is it possible for me to close all outgoing ports except the ones I need?

You can do this with iptables or UFW.

    [http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

---

