---
title: "Dropping firestarter ?"
date: 2009-12-20
forum: Security
---

### Post by oygle on 2009-12-20
Hi,

I have been using Ubuntu 9.04 (all updates applied) for quite a while, and want to drop firestarter, as it has been giving me a lot of pain, and I'd rather drop it, and just use iptables.

What changes do I need to do please ?  I have read a few how-to's on iptables, but find them difficult. I simply want to open a few ports only, like htp/80, smtp, pop3, https,etc

Thanks,

Oygle

---

### Post by bodhi.zazen on 2009-12-20
First, to remove firestarter, you need to use the purge option or it leaves conflicting config files:

```
sudo apt-get purge firestarter
```

As a step towards firestarter, you may wish to look at ufw. The syntax of UFW is fairly easy to learn, and the syntax of iptables is similar.

Take a look at these links :

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

Just take it slow, give yourself a few hours if you need, and it will click.

If you get stuck or have problems understanding a specific part of those pages, feel free to ask.

---

### Post by oygle on 2009-12-20
Okay thanks for those links. I will probably use UFW, it looks less complicated than iptables. That said, I can no doubt 'flush' iptables, list the standard rules that exist after a flush, then add one 'rule' via UFW, and then list iptables, and see what it has done.

Thanks,

Oygle

---

