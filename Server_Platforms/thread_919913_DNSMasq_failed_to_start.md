---
title: "DNSMasq failed to start"
date: 2008-09-14
forum: Server Platforms
---

### Post by PinkFloyd102489 on 2008-09-14
I installed DNSMasq and added localhost to the listen-address in the conf file. However, when I try to start it, I get this:

```

brandon@ubuntu-server:~$ sudo /etc/init.d/dnsmasq start
 * Starting DNS forwarder and DHCP server dnsmasq
dnsmasq: failed to create listening socket: Address already in use
 * failed
                                                             [fail]

```


Anyone have an idea why?

---

### Post by PinkFloyd102489 on 2008-09-14
I figured out that I had to kill the "named" process but how to I uninstall it or prevent it from starting?

---

### Post by Pronco on 2010-05-28
The simple solution is to add the bind-interfaces option to the DNSmasq configuration.

---

