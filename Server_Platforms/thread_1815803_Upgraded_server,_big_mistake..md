---
title: "Upgraded server, big mistake."
date: 2011-07-31
forum: Server Platforms
---

### Post by jose.parejo on 2011-07-31
Hello,

I started an Ubuntu server running on 10.10, and I was very pleased with it. I got what I wanted to do in less than two days while on Windoze it was taking me 6 months and I was still failing. I had to install the GUI so I could get a Vbox running on Windoze and host my magicJack. I upgraded the server to 11.04 and I'm very disappointed with it. The server is now extremely slow on the GUI and over SSH. I can barely get anything done. If I restart it, it'll work fine for a few minutes, but then, when it goes idle, it gets extremely slow until I log in again. Right now, it's not idle, but it's painfully slow. Can anyone please help me? I want to avoid reinstalling at all cost.

Thanks in advanced,
Jose.

---

### Post by Wim Sturkenboom on 2011-08-01
Try to check with *top* which processes are eating CPU time and RAM. Take it from there.

And why the heck did you upgrade? Would it offer you anything extra (that you really needed) over 10.10? If it ain't broken, don't fix it; 10.10 is supported till april 2012 so there is no need to upgrade if it does what it is supposed to do.

---

### Post by jose.parejo on 2011-08-01
> **Wim Sturkenboom said:**
> Try to check with *top* which processes are eating CPU time and RAM. Take it from there.

And why the heck did you upgrade? Would it offer you anything extra (that you really needed) over 10.10? If it ain't broken, don't fix it; 10.10 is supported till april 2012 so there is no need to upgrade if it does what it is supposed to do.
Thanks. I'll try that. I really really did not mean to upgrade. I really like 10.10... I have it on my desktop

**UPDATE**
While I wait on results, is there anything like cpulimit but for RAM?

---

### Post by Entilza on 2011-08-01
use #top and sort by M.

How much ram do you have?

---

### Post by jose.parejo on 2011-08-01
> **Entilza said:**
> use #top and sort by M.

How much ram do you have?
I have about 1GB. OK, I left the server alone last night, and now there's no way for me to access it

---

### Post by jose.parejo on 2011-08-02
OK, so I think I found the problem. The server seems fine until the VM starts. Could it be that I have to re-install Vbox?

---

