---
title: "Ubuntu Email Server Question"
date: 2010-11-23
forum: Server Platforms
---

### Post by zxkelxz on 2010-11-23
Our main DNS(ours.com) resolves to a windows 2008 server box. What I want to do is have a secondary box with Ubuntu to receive sent emails(our@our.com). The problem my brain cannot get around is the DNS resolves to the windows server 2008 box(which host the website as well), how can we allow the email (ours@ours.com) to go to the Ubuntu email server even though the DNS name resolves to the windows server?

There is a method to our madness, we need the Windows Server but just Don't want it hosting our mail.

---

### Post by samosamo on 2010-11-23
Add an MX record for the host

---

