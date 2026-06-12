---
title: "Port Changing in Apache"
date: 2007-04-29
forum: Server Platforms
---

### Post by laforge on 2007-04-29
Hello, I just got a server installed using the guide [here]("http://ubuntuforums.org/showthread.php?t=419530&highlight=LAMP+web+server").  The only problem is that my service provider does not allow me to use port 80 for outgoing transfers, so I need to change it to port 81.  I am not too familier with the linux file system and where everything goes, so if anyone could direct me to what file I need to edit and where to find it so that I can change the port from 80 to 81 that would be really helpful.

Also I wanted to know if there is a way to open Screem so that I can save files into the www directory without doing "sudo screem" into terminal.

Thanks for any help in advance.

---

### Post by d.j.schroeder on 2007-04-29
for apache2 it is /etc/apache2/ports.conf

You can just add/change one of the Listen directives to the port you want to use.

---

