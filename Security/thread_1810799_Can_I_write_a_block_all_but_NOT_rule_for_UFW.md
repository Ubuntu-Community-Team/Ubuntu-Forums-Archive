---
title: "Can I write a block all but NOT rule for UFW?"
date: 2011-07-23
forum: Security
---

### Post by nrundy on 2011-07-23
For example, can I write something to the effect: block all outbound UDP connections over port 53 except those going to IP 123.456.789. Or stated another way: Block outbound to port 53/udp NOT going to ip address 123.454.678

Is it possible to do this? How would I write the argument?

---

### Post by uRock on 2011-07-23
Try that which is in my screenies.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=198198&stc=1&d=1311459610[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=198199&stc=1&d=1311459610[/IMG]

---

### Post by bodhi.zazen on 2011-07-23
> **nrundy said:**
> For example, can I write something to the effect: block all outbound UDP connections over port 53 except those going to IP 123.456.789. Or stated another way: Block outbound to port 53/udp NOT going to ip address 123.454.678

Is it possible to do this? How would I write the argument?

With iptables? Assuming your outbound policy is set to allow traffic ...

```
iptables -A OUTPUT -p udp ! -d 123.454.687 -j DROP
```

That rules drops all outbound packets to udp port 53 not going to the ipaddress. If you policy is to DROP, just skip the ! ;)

---

### Post by nrundy on 2011-07-24
Thanks guys!

---

