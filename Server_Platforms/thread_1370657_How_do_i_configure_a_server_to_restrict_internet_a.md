---
title: "How do i configure a server to restrict internet access?"
date: 2010-01-02
forum: Server Platforms
---

### Post by Grey08 on 2010-01-02
Hi

I've been searched for the related topic, but i couldn't found any of them. Basically, i want to set up a server to restrict internet access for other computer (windows box), but allow internet connection for kaspersky to download its database.

[IMG]http://edwardchia.dyndns.org/upload/ubuntu_1.gif[/IMG]

Here are some questions:
1. Do i need two network card at the server box?
2. There are 8 computers but only 2 are allowed all internet connection, 6 of the rest are not allowed, all windows box can accept connection to download database from kaspersky.
3. Is it Iptables the best, easiest way to configure?

Could you people help me on this? Thanks

Best regards
Grey08

---

### Post by Iowan on 2010-01-02
Dunno if you're looking for [Squid]("https://help.ubuntu.com/8.10/serverguide/C/squid.html") proxy server...

---

### Post by mike_yung on 2010-01-02
I agree.  When you get Squid setup configure the LANs on the 192.168.0.3 & ...4 to use 192.168.0.2 as their proxy server.  This can do what you want while speeding up the Kaspersky updates.

---

### Post by Grey08 on 2010-01-03
Thanks Iowan & Mike_yung

But do i need two network card at the server box?

---

### Post by mike_yung on 2010-01-03
> **Grey08 said:**
> Thanks Iowan & Mike_yung

But do i need two network card at the server box?


No, the single nic topology in your well done diagram is perfectly valid just as it is.

---

