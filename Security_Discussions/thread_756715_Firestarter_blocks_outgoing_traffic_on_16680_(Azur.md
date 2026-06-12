---
title: "Firestarter blocks outgoing traffic on 16680 (Azureus)"
date: 2008-04-16
forum: Security Discussions
---

### Post by bajun on 2008-04-16
Since I've started to use Azureus, my Firestarter shows that outgoing UDP traffic (port 16680) is blocked. As I understand this is a normal behavior of the Azureus. Or maybe not? The outgoing policy is blacklist based and totally clear, therefore all outgoing traffic should be accepted, but the log periodically shows, as example:
```
Blocked: Port - 16680, Source - My IP, Target - Some IP, Length - 167, Protocol - UDP
```
How to understand this discrepancy between policy and events?
How can I make, that this traffic has been accepted.
Thank you.

---

### Post by Tews on 2008-04-16
Enter the following ....

```
sudo ufw enable
```

```
sudo ufw allow 16680/udp
```

You should see all sorts of green smiley faces now .. :lolflag:

Hardy Heron uses Uncomplicated Firewall and it is now much easier to deal with iptables than it was with Firestarter ... Have Fun!

---

### Post by bajun on 2008-04-16
Hm, right, ufw is very simple. Everything works.
Faces run around and become gradually green. :)

---

