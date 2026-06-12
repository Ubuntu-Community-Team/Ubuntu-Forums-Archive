---
title: "Access local Apache server on Ubuntu from within VirtualBox Windows install?"
date: 2008-05-29
forum: Virtualisation
---

### Post by khughitt on 2008-05-29
Hi,

I just set-up VirtualBox for the first time, and was able to install Windows XP and get on the net without a hitch. One thing that would be really useful to be able to do, however, would be to access a local development server (Apache2) I have running on the HOST machine (Ubuntu 8.04), from *within* the windows box. E.g. Be able to open up IE and go to "http://localhost" and have my dev server root page loaded.

Is this possible? I imagine I could share the root web folder and then set up Apache on windows, using the same directory, but this just doesn't seem like the best idea.

Anyone have any suggestions?


Thanks!

---

### Post by bradmkjr on 2008-05-29
[http://192.168.0.101/](http://192.168.0.101/) ? why not use the ip address of the server?

---

### Post by khughitt on 2008-05-30
> **bradmkjr said:**
> [http://192.168.0.101/](http://192.168.0.101/) ? why not use the ip address of the server?

I didn't think of that at all. That worked perfectly :)

Thanks brad!

---

