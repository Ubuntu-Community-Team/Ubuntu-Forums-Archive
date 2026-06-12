---
title: "Joining Ubuntu 15.04 to a Server 2012 domain"
date: 2015-08-12
forum: Server Platforms
---

### Post by don39 on 2015-08-12
Hi Guys,

Im trying to join ESXi\Ubuntu 64bit to a domain using PBIS
I've been using the instructions on this page:
[http://gamblisfx.com/how-to-join-ubuntu-15-04-to-a-windows-domain-using-pbis-open/](http://gamblisfx.com/how-to-join-ubuntu-15-04-to-a-windows-domain-using-pbis-open/)

The package installs go ok, but when I try running [COLOR=#666666][FONT=arial]sudo domainjoin-cli –disable ssh join gamblisfx.co.id administrator[/FONT][/COLOR] or in my case:
 *sudo domainjoin-cli -disable ssh join Server.home.local administrator *(I've tried with and without the servername Server)

Anything I've tried results in the domainjoin-cli --help info being displayed.

I am able to ping the server, but Im not sure how it would recognise the domain.

Any suggestions on where Im going wrong?
Is there a better way to join Ubuntu to the domain?

---

### Post by howefield on 2015-08-12
Thread moved to the "*Server Platforms*" forum.

---

