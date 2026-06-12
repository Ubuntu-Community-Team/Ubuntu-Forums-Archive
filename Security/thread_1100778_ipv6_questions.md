---
title: "ipv6 questions"
date: 2009-03-19
forum: Security
---

### Post by lovinglinux on 2009-03-19
1 - How do I know if my ISP provides ipv6?

2 - I have no iptables rules for ipv6. Should I disable ipv6 to be safe?

3 - Does any router works with ipv6? I have a Linksys WRT54G with original firmware

---

### Post by lemming465 on 2009-03-21
> How do I know if my ISP provides ipv6?
Visit their main support page and see if the mention it, do a web search for the ISP name and IPv6, call their tech support.  If it was the USA, they probably don't; I have no idea about Brasil.

> I have no iptables rules for ipv6. Should I disable ipv6 to be safe?
It wouldn't hurt.  First security rule for configuring systems to be safe is to minimize the stuff you are running.

> Does any router works with ipv6? 
No, most older ones don't.  The magic keywork is "DOCSIS 3.0" support; that has IPv6, I believe.  With your linksys you might be able to flash it with 3rd party Linux firmware (e.g. dd-wrt), but the real issue is going to be your DSL or Cable modem at the ISP uplink, not your wireless router.

---

### Post by lovinglinux on 2009-03-21
Thanks.

---

### Post by ninjapirate89 on 2009-03-21
What are the benefits of switching to ipv6?

---

### Post by lemming465 on 2009-03-22
Basically none, which is why things are so slow to move off IPv4.  The problem is that we're running out of IPv4 addresses, with the address apocalypse currently scheduled for 2011 or so.  If we haven't deploy a whole lot more IPv6 by then, new internet users will be a world of hurt.  Notably 2/3 of India and China, and anyone with a new smartphone.  US users, who are squatting on 50% of the worlds address space with 5% of the population, due to having invented the Internet, are particularly oblivious.

---

