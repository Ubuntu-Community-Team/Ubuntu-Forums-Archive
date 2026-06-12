---
title: "How to lock my server?"
date: 2008-03-01
forum: Server Platforms
---

### Post by JimTDI on 2008-03-01
When I boot my Ubuntu 6.06LTS server, it comes up to a login prompt.  At that point everything I need to be running is, my FTP server, Apache, etc...

But... anybody can walk by and <Ctrl> + <Alt> + <Del> reboot it.

How can I lockout the keyboard, and prevent this?

Do I need to login first, and then somehow lock the keyboard?

Thanks!

---

### Post by PilotJLR on 2008-03-01
Nah, all you need to do is edit /etc/inittab.
Check out the details here:
[http://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/security-ctrlaltdel.html](http://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/security-ctrlaltdel.html)

---

### Post by .nedberg on 2008-03-01
Or you could just disconnect the keyboard, mouse and monitor and lock the computer away.

If you need to setup things then use ssh (and vnc if you want a GUI). I keep my servers in the attic.

---

### Post by JimTDI on 2008-03-23
> **PilotJLR said:**
> Nah, all you need to do is edit /etc/inittab.
Check out the details here:
[http://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/security-ctrlaltdel.html](http://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/security-ctrlaltdel.html)

Thank you!  I'll take a look at doing that.  Appreciate your help!

---

### Post by JimTDI on 2008-03-23
> **.nedberg said:**
> Or you could just disconnect the keyboard, mouse and monitor and lock the computer away.

If you need to setup things then use ssh (and vnc if you want a GUI). I keep my servers in the attic.

Thanks!  It's too bad my attic gets so hot in the summer, and cold in the winter.  Although the cold might be OK, the heat would kill my server.  But I surely do like that idea!

---

