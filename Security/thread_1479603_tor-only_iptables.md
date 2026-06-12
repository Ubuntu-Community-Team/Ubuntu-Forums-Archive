---
title: "tor-only iptables"
date: 2010-05-10
forum: Security
---

### Post by directedition on 2010-05-10
I'm looking to force a system to network using only tor, and I want the firewall to block all activity that isn't from tor. How would I go about this? I would imagine I could add rules to to only allow traffic on common tor ports, but that includes port 80, which I definitely don't want the user to be able to communicate on.

---

### Post by cdenley on 2010-05-11
```

sudo iptables -P INPUT DROP
sudo iptables -A INPUT -s 127.0.0.1 -d 127.0.0.1 -j ACCEPT
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -P OUTPUT DROP
sudo iptables -A OUTPUT -s 127.0.0.1 -d 127.0.0.1 -j ACCEPT
sudo iptables -A OUTPUT -m owner --uid-owner debian-tor -j ACCEPT

```

---

### Post by directedition on 2010-05-11
Thanks! I guess the line being based on the user I'll have to lose, since tor is started by the user with Vidalia, but the rest should work alright.

---

### Post by cdenley on 2010-05-11
> **directedition said:**
> Thanks! I guess the line being based on the user I'll have to lose, since tor is started by the user with Vidalia, but the rest should work alright.

If tor isn't being run as a separate user, then that will not work.
```

sudo netstat -tlnp

```

---

### Post by Agent ME on 2010-05-12
There's a way to make it so a program is run under your user, but as a different group, which you can set iptables to let through. How you do this though I forget. Might be able to use a sticky bit or such but can't remember.

---

