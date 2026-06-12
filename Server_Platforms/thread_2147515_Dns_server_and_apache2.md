---
title: "Dns server and apache2"
date: 2013-05-22
forum: Server Platforms
---

### Post by mirceabondar on 2013-05-22
At this time i used bind9 and apache 2 on the same server. It is poosible to move apache2 and document root to another server (one for dns and other for webserver)? and how do this?

---

### Post by termvrl on 2013-05-22
By default, apache will operate on the “*/var/www*” folder. If you mean this "document", yes you can copy it to another server. 
i use winSCP program as my laptop run win OS.

---

### Post by mirceabondar on 2013-05-22
My dns server have 192.168.1.2 and apache have 192.168.1.3. How to modify dns server to work with apache where apache is installed in another server

---

### Post by SeijiSensei on 2013-05-22
Point the A record for the website in the DNS to 192.168.1.3.

---

