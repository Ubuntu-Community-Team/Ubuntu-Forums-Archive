---
title: "lucid on amazon EC2: The following Linux command line was extracted from /etc/default"
date: 2010-12-06
forum: Server Platforms
---

### Post by MuschPusch on 2010-12-06
Hey, 

when running apt-get upgrade today i got a strange blue-screen:

The following Linux command line was extracted from /etc/default/grub or the `kopt' parameter in GRUB Legacy's menu.lst.  Please verify that it is correct, and modify it if necessary

Linux command line: 

and an empty line... What to do? 

regards Volkan

---

### Post by MuschPusch on 2010-12-06
Ok i just created a snapshot of the image and tried what happened. You don't need grub on amazons ec2. So just hit enter and go on without configuring grub...

---

