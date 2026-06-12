---
title: "Firewalling ipv4 and ipv6"
date: 2009-12-25
forum: Security
---

### Post by memilanuk on 2009-12-25
Since it appears that some server daemons fire up listening for both ipv4 and ipv6 traffic... will the same firewalling rules in iptables block/filter both ipv4 & ipv6?

TIA,

Monte

---

### Post by bodhi.zazen on 2009-12-26
iptables does not filter ipv6, you need to use ip6tables.

Try it yourself

```
sudo ufw enable

# With this command you will see a long list of rules =)
sudo iptables -L -v

# But look at ip6tables, all traffic is allowed
sudo ip6tables -L -v
```

ipv6 is not in wide spread use

So when you notice servers are listening on ipv6, are you configured to receive ipv6 traffic ?

[http://showmyip6.com/](http://showmyip6.com/)

You can configure many servers to bind them to a specific ip address =)

At any rate, many people somply block all ipv6 traffic (default deny).

See : [http://linuxreviews.org/features/ipv6/iptables/](http://linuxreviews.org/features/ipv6/iptables/)

---

### Post by memilanuk on 2009-12-26
Well... its not like I *want* IPv6, but it seems to be enabled by default for at least dnsmasq (compiled in) and ntpd...

See [this thread]("http://ubuntuforums.org/showthread.php?t=1363837") and the netstat output in [this one]("http://ubuntuforums.org/showthread.php?t=1363895").

---

