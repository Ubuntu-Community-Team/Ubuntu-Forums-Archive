---
title: "UFW doesn't work"
date: 2008-07-01
forum: Security
---

### Post by erioll on 2008-07-01
Hi everyone!
I'm new to Linux and I'm trying to set up ufw in my pc but it doesn't seem to work since i tried to block all traffic using "ufw default deny" and i still can send and receive mails and browse the internet! I even tried "ufw deny from any to any" but it doesn't block anything...
How can i fix this?

---

### Post by cdenley on 2008-07-01
I don't think UFW can be used to filter outgoing traffic or established connections. Normally desktop users are only concerned with incoming traffic they did not initiate. If you want better control of traffic filtering, you can use iptables directly.
```

man iptables

```
```

sudo iptables -P INPUT DROP
sudo iptables -P OUTPUT DROP

```

---

