---
title: "File sharing b/w linux guest and linux host (VMWare)"
date: 2008-12-25
forum: Virtualisation
---

### Post by davidbilla on 2008-12-25
How do I enable file sharing b/w linux guest and linux host in VMWare?

Host: Ubuntu 8.04

Guests: Fedora 10, Sabayon 3.4, Puppy 4.

---

### Post by Dedoimedo on 2008-12-25
Hello,

You can use Samba.

Please see here, under sharing:
[http://www.dedoimedo.com/computers/linux_commands.html](http://www.dedoimedo.com/computers/linux_commands.html)

And see here, pages 4 & 5:
[http://www.dedoimedo.com/computers/install_pclinuxos.html](http://www.dedoimedo.com/computers/install_pclinuxos.html)

Not exactly what you want, but the basic principles are the same.
Use Samba, define uses, define shares and off you go!

Cheers,
Dedoimedo

---

### Post by bodhi.zazen on 2008-12-26
+1 on Samba. IMO Samba is easy to set up and will work on most any OS and any virtualization platform.

Alternates include NFS, SSHFS, FTP, and to some extent http.

---

### Post by davidbilla on 2008-12-26
Thanks! I'll try it out this evening and let you know!

---

