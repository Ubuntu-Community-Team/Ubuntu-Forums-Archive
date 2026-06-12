---
title: "enable both tcp and udp on iptables?"
date: 2008-08-21
forum: Security
---

### Post by firsttimeuser on 2008-08-21
Hi guys, can someone give me a quick answer how can I enable both TCP and UDP protocol in iptables command? looks like it won't take tcp|udp or IP option, thanks

example command:

iptables -A INPUT -s 1.2.3.4 -p tcp|udp --dport 5999:6020 -j ACCEPT

---

### Post by brian_p on 2008-08-21
> **firsttimeuser said:**
> Hi guys, can someone give me a quick answer how can I enable both TCP and UDP protocol in iptables command? looks like it won't take tcp|udp or IP option, thanks

example command:

iptables -A INPUT -s 1.2.3.4 -p tcp|udp --dport 5999:6020 -j ACCEPT

You need two rules: one for each protocol.

```
man iptables
```

and the -p option.

---

### Post by firsttimeuser on 2008-08-21
i checked the manpage, according to it, I should be able to use ! to invert the argument, as this

-p ! icmp

but this command does not work on my box....

---

### Post by brian_p on 2008-08-21
> **firsttimeuser said:**
> i checked the manpage, according to it, I should be able to use ! to invert the argument, as this

-p ! icmp

but this command does not work on my box....

Pass on this. I'd agree with your interpretation. I wonder how you would fare with

```
-p tcp,udp

```

---

### Post by The Cog on 2008-08-22
I#m pretty sure the normal approach would be:
> iptables -A INPUT -s 1.2.3.4 -p tcp --dport 5999:6020 -j ACCEPT
iptables -A INPUT -s 1.2.3.4 -p udp --dport 5999:6020 -j ACCEPT


---

### Post by paulojjs on 2008-08-22
> **firsttimeuser said:**
> i checked the manpage, according to it, I should be able to use ! to invert the argument, as this

-p ! icmp

Please keep in mind that !icmp is not the same as tcp+udp, there are other protocols beside those 3 (check /etc/protocols).

---

