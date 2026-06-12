---
title: "apply security updates alone, ubuntu server"
date: 2010-08-14
forum: Security
---

### Post by ldweeks on 2010-08-14
I'm new to server admin, so my question is based on what may be a bad assumption. With a server, my assumption is "if it ain't broke, don't fix it". In other words, I'm not really interested in upgrading the software to the latest and greatest if I already have stuff working on the server.

However, the one place where I DO want to constantly have upgrades is for security patches. How do I apply security updates to Ubuntu Server... and ONLY security updates?

Thanks!

---

### Post by Bachstelze on 2010-08-14
Comment out the "-updates" lines in your sources.list, and leave only the "-security" ones uncommented.

---

### Post by CharlesA on 2010-08-14
> **Bachstelze said:**
> Comment out the "-updates" lines in your sources.list, and leave only the "-security" ones uncommented.

This would work.

You could also just set it to install security updates automatically when you installed it or by configuring it per this page: [https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

---

