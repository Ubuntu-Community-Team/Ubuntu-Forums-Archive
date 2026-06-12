---
title: "Some firewall ports were detected as being closed"
date: 2010-11-12
forum: Security
---

### Post by dogdo on 2010-11-12
What does this mean? What are the security implications of closed ports?

---

### Post by The Cog on 2010-11-12
I have no idea what it means. What is the context - who said that to you?

> What are the security implications of closed ports?You can't connect to them - they're closed. So they're quite secure.

---

### Post by dogdo on 2010-11-12
> **The Cog said:**
> I have no idea what it means. What is the context - who said that to you?

You can't connect to them - they're closed. So they're quite secure.

I just ran a test on shields up website-in any case ive just set the firewall to default deny all incoming-now all ports are stealth again.

---

### Post by CharlesA on 2010-11-12
Closed and stealth mean the same thing security-wise - the ports aren't accepting connections.

---

### Post by Velnias on 2010-11-12
[http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject)


"Conclusion
DROP offers no effective barrier to hostile forces but can dramatically slow down applications run by legitimate users. DROP should not normally be used."

---

### Post by CharlesA on 2010-11-12
I haven't noticed any major problems with running drop instead or reject from inside the LAN. 

See here: [http://serverfault.com/questions/157375/iptables-reject-vs-drop](http://serverfault.com/questions/157375/iptables-reject-vs-drop)

---

