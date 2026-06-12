---
title: "Oidentd problems, please help"
date: 2005-09-06
forum: Server Platforms
---

### Post by TheDemon on 2005-09-06
I'm troubled because i've reinstall ubuntu hoary on my server box probobly three times now for various resons. In the "past" oidentd has worked fine, now it does not, everything is setup correctly, port forwarding, configuration, it's all been checked, and port 113 is respondin, but no ident. Also, I just install oidentd on my friend's box which i administrate for him, and it works fine (he's behind 2 routers).
I was wondering if anyone has experianced this problem and knows what may be doing this. On my friend's box i used the apt package, and on my server, i've tried the apt package and manually installing, neither work.

Thanks in advance for any help,
-TheDemon-

---

### Post by TheDanMan on 2005-09-06
dpkg-reconfigure oidentd

---

### Post by TheDemon on 2005-09-06
i already tried that, i'm not new to the debian/ubuntu field :)

..and if you couldn't tell, it does nothing

---

### Post by Velox Letum on 2005-09-06
Is it being run as a inetd/xinetd process or a daemon?

---

### Post by TheDemon on 2005-09-08
intit.d/daemon (also it says it can't be used with inetd so...it's not)

---

### Post by TheDemon on 2005-09-08
i found out the problem, my dlink router detects ident request as SYN Packet floods, pos.

---

