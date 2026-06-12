---
title: "server problem"
date: 2006-12-17
forum: Server Platforms
---

### Post by fpois on 2006-12-17
Hi all,

At the moment I've got 2 computers running ubuntu (both 6.06 server-edition), one behind my office router and one behind my home router, both have ssh and portforwarding setup. Now the funny thing is that I can ssh to either of them from any 3rd-party site, but i can't ssh to each other. In other words, if I'm currently in my home network I can't ssh to my office server, while if i do it from another place it's doable; and if I'm currently in my office network I can't ssh to my home server, while if i do this from another place it's doable also (so if i ssh first to a 3rd party place, then originate the ssh login from there, it's doable, for either cases, just not direct connection to and from each other.)

I hope I didn't confuse you too much. I currently guessing it could be something wrong with my firewall or port-forwarding setting, but if 3rd-party can login these shouldn't be a problem??

I understand that this may well be a non-ubuntu question, since the OS doesn't appear to be where my problem is, but I really have no idea where to begin finding a solution, so please bare with me.

---

### Post by Iowan on 2006-12-18
Mostly, this'll give your thread a bump...
Are you using standard SSH port?  (Wondering if port forwarding might be causing issues - although it should interfere w/ SSH to a 3rd party place - if that were the case).

---

### Post by fpois on 2006-12-19
> **Iowan said:**
> Mostly, this'll give your thread a bump...
Are you using standard SSH port?  (Wondering if port forwarding might be causing issues - although it should interfere w/ SSH to a 3rd party place - if that were the case).

Thanks for the bump at least.
Yes I am using standard SSH port 22.

---

