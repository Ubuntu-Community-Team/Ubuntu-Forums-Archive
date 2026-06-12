---
title: "Samba and Windows user passwords"
date: 2008-09-25
forum: Server Platforms
---

### Post by kamaji792 on 2008-09-25
Hi all,

Currently I set the samba user passwords on my Ubuntu box and then manually synchronize them on the Windows boxes.

What do I need to so that I do not have to keep the passwords synchronised manually?

Thanks in advance

---

### Post by bab1 on 2008-09-25
It sounds like you want to go to a domain type of environment.  You can either use Samba as a PDC (NT4 style) with winbind or join a AD domain.  Either way you get 2 things.  A centralized system of managing users...and a lot more complexity in the setup.  :-)

---

