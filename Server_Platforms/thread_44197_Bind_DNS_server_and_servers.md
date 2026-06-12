---
title: "Bind DNS server and servers?"
date: 2005-06-24
forum: Server Platforms
---

### Post by D4_B34M on 2005-06-24
What I've heard is that making your own DNS what connects to others can provide you a domain name.

So I installed Bind DNS to try out, but I have no idea how to get it to connect and find other DNS servers to work on worldwide and not only on my local area.
I have read some "howto's".. Well actually many of them, but still, I have no idea.

So if someone can clear this a bit for me and tell what is the easiest way to make this acually works (if its possible even..).

P.S. I use webmin to control it (just so fast and easy).
Thank you in advance :)

---

### Post by LordHunter317 on 2005-06-24
If you want to have your own domain, you don't need to run a DNS server, nor should you unless you exactly no what you're doing.

---

### Post by D4_B34M on 2005-06-26
Well, can I then harm something if I run DNS server?

And to know how it works, I have to try it.

---

### Post by LordHunter317 on 2005-06-26
[QUOTE=D4_B34M]Well, can I then harm something if I run DNS server?[/quote]Yeah, you can completely break your Internet access, if you screw it up.  DNS is fundamental to the running of the Internet.

> And to know how it works, I have to try it.Start with the DNS-HOWTO on tldp.org.  Read the whole thing first before even attempting anything.  Make sure you understand it before attempting anything.  Ask questions if you don't understand something.

---

