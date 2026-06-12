---
title: "[SOLVED] 8.04.1 Hardy can't resolve during apt-get update"
date: 2008-07-25
forum: Server Platforms
---

### Post by cravenc on 2008-07-25
Hello,

I'm running 8.04.1 server for my church.  After installing the OS I tried to run apt-get update, but it couldn't resolve addresses for the update.  I did some research and modified /etc/hosts to say:

127.0.0.1         localhost
127.0.1.1         Abacus
192.168.1.150     Abacus

at the top.
Then it worked. However, when I moved it to the church the same problem occurred.  The box is using a static IP and I set it up correctly because I can SSH into it remotely.  I'm going to try changing the DNS server address in the resolve.conf and under /etc/network/interfaces since it is currently using Roadrunner's DNS and it's on Windstream DSL now.

Has anyone else had this problem?
Thank you.

I changed DNS servers.  No cigar.

---

### Post by cravenc on 2008-07-25
Did some more research: I'm a fool!  

I edited etc/resolve.conf instead of etc/resolv.conf.

Simply by replacing the Roadrunner DNS with Windstream DNS caused it to work.

---

