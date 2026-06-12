---
title: "do you recommend turning the linux firewall on?"
date: 2022-04-30
forum: Security
---

### Post by ronjjjg8885 on 2022-04-30
why?

---

### Post by kc1di on 2022-04-30
Yes turn it on.  The defaults setting will work for most people.

---

### Post by ronjjjg8885 on 2022-04-30
it isn't on by default or it is?

---

### Post by CharlesA on 2022-04-30
What version of Ubuntu are you trying to check the firewall status with?

UFW should be installed by default, but I know there is a move away from iptables (which is what ufw controls) to nftables.

With that said, I'm still using iptables on Debian 11, mostly because ansible doesn't handle nftables yet.

---

### Post by ronjjjg8885 on 2022-05-01
Ubuntu 22.04 LTS 64bit

---

### Post by TheFu on 2022-05-01
22.04 changed the add nftables (instead of iptables).  Beware.  Read the release notes.

Yes, I enable the firewall, because it is smarter than most router firewalls and will block a number of undesirable callback connections that many popular websites/trackers abuse. After you enable the firewall, look at the logs. You'll see plenty of blocked attempts that get to the computer going passed the router's firewall.

Tricking most home router firewalls to accept packets that they didn't actually request isn't really hard. It is actually sad that we've settled for good enough, though the really smart websites know how to blow right through them.  Enterprise firewalls don't get tricked in this way.

---

### Post by ronjjjg8885 on 2022-05-04
thanks

---

