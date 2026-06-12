---
title: "[SOLVED] telnet localhost without port failed"
date: 2008-03-04
forum: Server Platforms
---

### Post by yanny on 2008-03-04
Is it normal that it fails when I type: 

```

telnet localhost

```

Because when I type telnet localhost 25 I can connect to localhost.localdomain.

---

### Post by charles_s45 on 2008-03-04
Yes, that is normal. port 25 is used for email (SMTP). Telnet uses port 23. You must have telnetd running if you want to be able to telnet to your machine.

---

### Post by Oldsoldier2003 on 2008-03-04
> **charles_s45 said:**
> Yes, that is normal. port 25 is used for email (SMTP). Telnet uses port 23. You must have telnetd running if you want to be able to telnet to your machine.

To the OP:
Telnet is bad, use SSH instead. Telnet sends passwords in clear text.

---

### Post by yanny on 2008-03-04
Ok, thanks! 

So telnet to localhost is not neccessary at all?

---

### Post by Oldsoldier2003 on 2008-03-04
> **yanny said:**
> Ok, thanks! 

So telnet to localhost is not neccessary at all?
I don't see why you would want to open a telnet session to the local host when you could just open a terminal, so yes i would say telnet isn't needed, nor would SSH be needed unless you wanted to remotely access that machine from another.

---

