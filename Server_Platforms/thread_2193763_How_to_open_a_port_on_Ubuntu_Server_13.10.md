---
title: "How to open a port on Ubuntu Server 13.10"
date: 2013-12-14
forum: Server Platforms
---

### Post by keymoo on 2013-12-14
I want to open port 8333, how do I do it? I tried this to list the rules, but nothing is there, so a bit confused. I normally use CentOS, so I'm a bit lost.
```

# iptables -L INPUT --line-numbers
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination

```

---

### Post by CharlesA on 2013-12-14
```
iptables -A INPUT -p tcp --dport 8333 -j ACCEPT
```

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

With that being said, it doesn't look like you have any firewall rules in place to block access to that port.

---

### Post by Ubi_one_2014 on 2014-02-15
> **CharlesA said:**
> ```
iptables -A INPUT -p tcp --dport 8333 -j ACCEPT
```

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

With that being said, it doesn't look like you have any firewall rules in place to block access to that port.

so i did  iptables -A INPUT -p tcp --dport 21 -j [ enter]
followd by service proftpd restart [ enter]

question:
is this permanent?
i mean, i have my pc virtually allway's on, and want to sync to the nas using a schedule

so after a reboot everything must work as before.

---

### Post by CharlesA on 2014-02-15
Unless you have a script that applies iptables rules after a reboot, the changes are only temporary.

---

### Post by SeijiSensei on 2014-02-16
> **CharlesA said:**
> Unless you have a script that applies iptables rules after a reboot, the changes are only temporary.

If you don't know where to put this script, I recommend placing it in /usr/local/sbin and executing it from /etc/rc.local with a line like

```
/usr/local/sbin/myfirewall
```

Make sure myfirewall is executable by the root user.

---

### Post by CharlesA on 2014-02-16
Good idea.

I have mine set up in /etc/interfaces/if-preup.d/ and call it from the /etc/networking/interfaces file.

---

