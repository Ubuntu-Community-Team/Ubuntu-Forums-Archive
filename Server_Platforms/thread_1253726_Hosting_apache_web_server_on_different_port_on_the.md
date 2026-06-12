---
title: "Hosting apache web server on different port on the internet"
date: 2009-08-30
forum: Server Platforms
---

### Post by Cero44 on 2009-08-30
I am trying to build a web server on my home box just for testing purposes. I've setup LAMP correctly and it worked well under localhost. But I want this to be visible on the internet (again for testing purposes), and to listen on a port other than 80. Is it possible to do this, and if so how?

I have port 40001 forwarded to the box. I have added "Listen *:40001" in my ports.conf and changed the virtualhost to listen on 40001 as well with "<VirtualHost *:40001>" in the enabled-sites conf for the site. And when I try to access my site locally or outside my network, I get a failed to connect error.

---

### Post by Bachstelze on 2009-08-30
You need to append the port number to the address, separated by a colon. For example: [http://123.45.67.89:40001](http://123.45.67.89:40001)

---

### Post by Cero44 on 2009-08-30
Thanks, that worked. Is there any way to make it work without specifying the port? Without using port 80?

The problem is port 80 is being used by something else on my network so I need to use another port for this web server. So just for convenience if I can access it without specifying the port I would like to implement this change.

---

### Post by bear24rw on 2009-08-30
i also run apache on different port and would like to know if its possible with godaddy to set it to always use a different port.. i dont know if its possible, anyone know?

---

### Post by Bachstelze on 2009-08-30
It is normally not possible (i.e. without someone to do the redirection for you). I know No-IP has a service for that, but don't jnow about godaddy.

---

