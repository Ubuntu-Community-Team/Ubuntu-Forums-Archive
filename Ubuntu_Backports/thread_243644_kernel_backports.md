---
title: "kernel backports"
date: 2006-08-25
forum: Ubuntu Backports
---

### Post by andrius on 2006-08-25
Hi folk, it might be not easy to do, but it would be very attractive for server admins/developers to have more kernel backports. For example - fedora always includes newest stable kernel into updates for FC4, though there is almost ready FC6. New kernels sometimes increse perfomance and drivers support dramatically and would be really nice easily to get that from backports still keeping track/supporting security for them. I think ubuntu could do even better than fedora and include -rcX kernels.

Thank you

---

### Post by Klaidas on 2006-08-28
The idea seems nice, just don't know if it would be impossible as of now :-k

---

### Post by tribaal on 2006-08-28
Isn't that what the "backports" repositories are for?

Check your /etc/apt/sources.list file, if I remember correctly there are commented backport repos, you can just uncomment them if you like, then as usual "sudo apt-get update && sudo apt-get upgrade"...

Hope this helps

- trib'

---

