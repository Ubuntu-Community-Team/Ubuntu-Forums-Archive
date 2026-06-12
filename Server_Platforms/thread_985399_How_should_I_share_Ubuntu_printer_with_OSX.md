---
title: "How should I share Ubuntu printer with OSX?"
date: 2008-11-17
forum: Server Platforms
---

### Post by saaz on 2008-11-17
I have a printer attached to my Hardy server which I'd like to share with my Mac Book running Leopard. I realize there's a number of ways to do this but I'm wondering if there's a preferred method by anyone? Samba? IPP?

---

### Post by Philio on 2008-11-17
Cups does it quite easily, it works fine with Windows/Linux so one would assume it would work fine with MacOS as well. It's easier to setup than Samba too.

---

### Post by cariboo on 2008-11-17
Samba is pretty easy also, just make sure it is using cups to share the printers. It should be easier to share with OSX, as it supports a lot more file systems than WIndows.

Jim

---

