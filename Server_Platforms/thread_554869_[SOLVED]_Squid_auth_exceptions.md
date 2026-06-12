---
title: "[SOLVED] Squid auth exceptions"
date: 2007-09-19
forum: Server Platforms
---

### Post by xyrer on 2007-09-19
Hi, I have squid already installed on ubuntu server, the authentication works flwlessly, but too much...
What I would like is to have a couple exceptions in the auth process, I need some computers to go tru the proxy without authenticating themselves so they can use a software to connect to a vpn, the software has no option for proxy and there is no hope of asking for it.

Basically, here's what I have in squid.conf:

acl noauth src 192.168.0.9/255.255.255.255
acl nivel1 proxy_auth REQUIRED
acl all src 192.168.0.0/255.255.0.0

http_access allow noauth
http_access allow nivel1


but it keeps asking for authentication to the 192.168.0.9
I assumed that would be the way to make the acl as there is zero documentation about this case.

Maybe someone knows why this is not working, my boss is giving opensource a chance and I don't want to make it look as useless.

---

### Post by xyrer on 2007-09-27
Anyone, Please?

I read somewhere about recognizing the programs requests and allowing them, any ideas about this?
How do i check on that?

---

