---
title: "Using non-root account to serve"
date: 2006-07-09
forum: Server Platforms
---

### Post by tgoose on 2006-07-09
I'm trying to set up Ubuntu Server 6.06 to use for a home network, running (at least) lighttpd, gnump3d, ftp and opendchub. Unfortunately I can't work out how to allow remote computers access to the daemons.

So far I've installed lighttpd and gnump3d. lighttpd will serve only to localhost; using my network IP lynx says "Alert!: Unable to connect to remote host." gnump3d will not serve any music unless the user is set to "root". I tried running lighttpd as root to test if it would work in this configuration, but it wouldn't allow me to, which I suppose is a good thing security wise but that means I don't know how to test if non-root accounts are the specific problem.

I read that by default, all ports on Ubuntu Server are closed, but opened when applications need them, but presumably they're not actually opening in the way they should - that said I'm rather guessing it's my fault than Ubuntu's!

I've looked into using iptables to allow access, but every guide I've read seems to talk of using the computer as a router/firewall, which is not what I'm doing at all. Moreover, iptables -L says only three things with "(policy ACCEPT)" beside them, which makes me think that it's not the thing stopping everything.

Anyway, the gist of what I'm saying is, how do I allow remote traffic to access these things on my Ubuntu Server?

Thanks.

edit: since torrentflux seems to require an apache server, I'll be using that rather than lighttpd; I just hope I have more luck setting it up than on Fedora Core!

edit again: and I reinstalled with the LAMP option and apache works fine. So far, so good.

final edit: I think I've found the problem, and the title of this post (and much of the content) is no longer relevant, but I don't seem to be able to delete it or change the title, so I've started another one.

---

