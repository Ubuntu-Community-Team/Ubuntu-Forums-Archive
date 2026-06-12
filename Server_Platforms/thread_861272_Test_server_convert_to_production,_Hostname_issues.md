---
title: "Test server convert to production, Hostname issues"
date: 2008-07-16
forum: Server Platforms
---

### Post by quietas on 2008-07-16
Howdy folks quick question probably.

I've got an old server about to be replaced by a newer server. The old one is mail.domain.com, the new one was being tested on a test subdomain as mail.test.domain.com.

I changed /etc/hosts and /etc/hostname to reflect the cnage on the new server and also glanced through bind, resolv, and network settings to check for changes needed. When I log in I see the old name, but if I ping mail.domain.com it resolves to itself as it should. 

Any idea why I see the old name at the log in? It seems cosmetic, but where to I change it?

---

### Post by danfluidmind on 2008-07-16
My first thought is that you need to use the "hostname" command while the machine is running. I'm pretty sure the /etc/hostname file is only read at boot time. DNS is resolving correctly because you've changed /etc/hosts. So type the following, then log out and back in and see what it does:

   hostname mail

Cheers
--Dan

---

