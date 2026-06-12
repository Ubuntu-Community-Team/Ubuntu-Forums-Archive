---
title: "Xming with putty"
date: 2013-06-20
forum: Virtualisation
---

### Post by umaDik on 2013-06-20
Hi,

I was connecting to a ubuntu server using xming and putty. I have installed ubuntu desktop in remote machine. But suddenly when I tried once, I could not get the desktop and error is as follows,

[FONT=arial]X: user not authorized to run the x server, aborting.[/FONT]
[FONT=arial]No protocol specified.[/FONT]
[FONT=arial]No protocol specified.[/FONT]
[FONT=arial]xint: giving up[/FONT]
[FONT=arial]xint: unable to connect to x server: Resource temporarily unavailable.[/FONT]
[FONT=arial]xint: server error.

What am I supposed to do?

Regards[/FONT]

---

### Post by SlugSlug on 2013-06-20
what command are you running? Also check X forwarding is enabled in /etc/ssh/sshd.conf

can you issue 

xeyes

---

### Post by umaDik on 2013-06-28
Hi,

I was able to find out the issue later. I have disabled IPV6 and it was the problem. I againg fix it and now it's working again. Thanks for your reply.

Regards..

---

