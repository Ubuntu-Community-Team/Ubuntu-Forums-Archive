---
title: "Login Title"
date: 2007-01-10
forum: Server Platforms
---

### Post by yeoheric on 2007-01-10
Hi,

Just installed Ubuntu 6.06.1 Server Edition, my first foray using Ubuntu as a server. When I login I get the message:

[I]Linux snoopy 2.6.15-26-server #1 SMP Fri Sep 8 21:00:37 UTC 2006 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.[/I]

Now, that does not actually inspire trust from my boss. Is there a way I can remove that statement or replace it somehow?

Please help. 

Thanks

Eric

---

### Post by nsleiman on 2007-01-10
maybe in the /etc/motd ?

---

### Post by yeoheric on 2007-01-10
Thanks, that did the trick.

---

### Post by PetePete on 2007-01-10
but it might come back when you restart. 

if it does theres a file in /etc/init.d which re-creates MOTD on reboot. can't remember the exact location but you'll be able to find it with using grep and searching for motd

---

