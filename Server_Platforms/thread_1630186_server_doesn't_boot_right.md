---
title: "server doesn't boot right"
date: 2010-11-24
forum: Server Platforms
---

### Post by lexthoonen on 2010-11-24
Hi, 

my server is not booting right and i'm in troubles now...

it's a 6.06 ubuntu server (don't ask) and it's been working fine. In fact, it hasn't been rebooted for quite some months, but today it hung and I had to reboot it.

It's at fasthosts.co.uk, and I've got some 'vkm' (java) remote control for it. 

Rebooting didn't 'start' the server as it should, as no sites were accessible. None of the services were accessible, not ssh, not ftp etc etc

with the vkm remote controle i could see what was going on, I get a console and see the server as if it's local.

The last thing it does when starting up, is showing that it's started Postfix [ok] and then nothing.

If I hit enter then, I can login. Internally, it then seems all fine and services are up and running.

However, it can't ping outside or see external websites. From outside, nothing can see the server either.

My questions:
How do I find out what the server is supposed to be doing after loading Postfix, as that's where the problem might be?

What could cause this communication problem?

Iptables is empty at this stage, no rules

If I type: ping [http://www.google.com](http://www.google.com) it says: unknown host [http://www.google.com](http://www.google.com)

It's unable to resolve anything outside. Looks like a DNS issue then, doesn't it?

netstat -nr gives empty result.

If I type ifconfig, i get this at inet6 addr: 

inet6 addr: ::1/128 Scope:Host

as if something's missing, no?

Does anybody have an idea what I should do next? Thanks!

---

### Post by lexthoonen on 2010-11-24
And then there's this:

ifup -a

 * if-up.d/mountnfs[eth0]: waiting for interface eth0:0 before doing NFS mount:SIOCSIFFLAGS: Cannot assign requested address

---

### Post by lexthoonen on 2010-11-25
Ok, it's solved.

I had to restart networking services (/etc/init.d/networking restart).

Well solved, I don't know why this doesn't happen at startup yet, but at least the server is up and running now.

---

