---
title: "proftpd server configuration"
date: 2008-03-31
forum: Server Platforms
---

### Post by Drezard on 2008-03-31
I'm trying to set up a proftpd ftp server so that I can upload and download files directly to my webservers public file (var/www). How do I do this in the configuration file of proftpd?

Daniel

---

### Post by dmizer on 2008-03-31
there is a proftpd howto in my sig that you should take a look at.

however, i suggest you look into using ssh instead of ftp for remote access and file transfer to your server, primarily because ssh is encrypted and secure.

---

