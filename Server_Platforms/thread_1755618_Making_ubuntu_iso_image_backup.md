---
title: "Making ubuntu iso image backup"
date: 2011-05-11
forum: Server Platforms
---

### Post by andriu1 on 2011-05-11
Hello all,

     Here we have some ubuntu servers installed on physical systems, and now we'd like to try virtualize them to vmware machines, and we need some help for it.

     The machines are in production environment, so, the best situation would be to make the iso image with the systems running, something similar to make a hot backup, but in this case, of all the system.

     Another detail is that we've not installed X, so, we must execute the command or aplication, if it exists, on command line.

Could anyone help us?

Thanks in advance

Regards,
Andres

---

### Post by Lars Noodén on 2011-05-11
[mkisofs](http://linux.die.net/man/8/mkisofs) is the name of the program to use to make ISO images.

---

### Post by The Real Dave on 2011-05-11
[Remastersys]("http://geekconnection.org/remastersys/") is what you're looking for, but I'm unsure whether it's GUI only tbh. It'll do exactly what you're looking for though.

---

### Post by andriu1 on 2011-05-12
Thank you very much. I'll try

Regards,
Andres

---

### Post by samosamo on 2011-05-12
Don't reinvent the wheel, just google "converting physical to vmware" or something

---

