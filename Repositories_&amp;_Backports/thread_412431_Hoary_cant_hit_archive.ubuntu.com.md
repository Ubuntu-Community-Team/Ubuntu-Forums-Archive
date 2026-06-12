---
title: "Hoary cant hit archive.ubuntu.com"
date: 2007-04-18
forum: Repositories &amp; Backports
---

### Post by siyisoy on 2007-04-18
Hi 
I cant install programs from archive.ubuntu.com repo.
The other standart repos are hit by hoary except this one.
I get this:
Could not connect to archive.ubuntu.com:80 (91.189.88.31), connection timed out [IP: 91.189.88.31 80]

---

### Post by siyisoy on 2007-04-18
Any replies?

---

### Post by viciouslime on 2007-04-18
They seem to be working for me. As are the gb mirrors, but seriously, hoary?! Maybe it's time for an upgrade...

---

### Post by AusIV4 on 2007-04-18
You're using Hoary Hedgehog? Considering Breezy is no longer officially supported as of last week, and Hoary hasn't been supported since October, I'm surprised you still get any repo's for Hoary.

I agree with viciousslime, it's time to consider an upgrade.

---

### Post by siyisoy on 2007-04-18
I use it as a gateway and nfs server machine. It is an old P2400 machine with 8GB hdd and 192MB ram. Will it be convenient to upgrade?

BTW: I realised that when i stop the firewall it can hit this repo. It seems to be weird to me.

---

### Post by siyisoy on 2007-04-19
I have observed that when I try to hit this repo firewall blocks a connection from 91.189.89.6 with service Sun RPC portmap. May this be the problem?

---

### Post by dmizer on 2007-04-19
for something simple like an nfs file server that has no connection to the world ... i wouldn't worry about having a hoary machine still in use.  but you indicated you're using it as a gateway, and trying to connect to repos ... so yeah, an upgrade is way over due.

this doesn't really address your problem directly, but you shouldn't be relying on packages in hoary repos anyway because they are not maintained.

---

