---
title: "Installing IMQ on ubuntu dapper (Mastershaper tutorial?)"
date: 2006-08-21
forum: Server Platforms
---

### Post by Bogaurd on 2006-08-21
Hi,
I'm looking to install mastershaper on my ubuntu dapper drake setup, however, I need IMQ setup first.

I saw there was a thread about mastershaper, but it didnt say very much, though someone mentioned the possibility of a tutorial.

If anyone has a tutorial on installing mastershaper on ubuntu, patching the badger kernel to work with IMQ, or would be able to send me a libipt_IMQ.so that would work on 2.6.15-26-server, or could write such a tutorial, this would be really appreciated :D

Thanks in advance! :)

---

### Post by Bogaurd on 2006-08-22
OK,
I managed to recompile my kernel with IMQ support, which took ages day on the P3 550 that runs my ubuntu install! I've loaded the IMQ module via modconf.

I've tried to recompile iptables to work wit IMQ, but am having no luck. Can anyone please please help? I really want to get mastershaper working :(

# iptables -t mangle -A MYFILTER -j IMQ
iptables v1.3.3: Couldn't load target `IMQ':/lib/iptables/libipt_IMQ.so: cannot open shared object file: No such file or directory

:(

---

### Post by Bogaurd on 2006-08-24
Bump? Anybody? :(

---

### Post by Mithrilhall on 2006-08-31
I'm currently running MasterShaper on Kubuntu 6.06. What seems to be the problem you're having?

---

### Post by Bogaurd on 2006-09-10
I havent tried to install mastershaper itself yet - but for the setup that I have, i need IMQ setup on my box. Did you setup IMQ on your box? If so, could you tell me how? I've tried recompiling the kernel and iptables... all to no avail :(

---

### Post by WesleyWex on 2006-09-24
I also can't find a way to learn how to compile the kernel to install IMQ on ubuntu anywhere on the web, and seems that here nobody wants to help...

---

### Post by Mithrilhall on 2006-10-24
What's your setup?

Did you get anywhere with this?

---

