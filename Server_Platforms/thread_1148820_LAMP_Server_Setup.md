---
title: "LAMP Server Setup"
date: 2009-05-04
forum: Server Platforms
---

### Post by UbuFreak on 2009-05-04
Im new to the forums. Been an Ubuntu user for almost a year now.
Im currently trying to set up my LAMP Server on Kubuntu 9.04. 
I've used "sudo tasksel" and I've successfully installed it. But at the moment I'm unsure of how to invoke the server I've installed. I want to do that so I can use it for testing while I'm doing my PHP tutorial.

Any help would be really nice.

(Thanks much bluefrog, but I knew that. Im editing it to make it clearer)

---

### Post by bluefrog on 2009-05-04
sudo tasksel

---

### Post by Iowan on 2009-05-04
When I set up my LAMP server, it powered up ready for action.  [This]("https://help.ubuntu.com/community/ApacheMySQLPHP") help page was useful.

---

### Post by cariboo on 2009-05-05
If the LAMP server is installed correctly, everything is setup and ready to go, just add your pages to /var/www.

---

### Post by Iowan on 2009-05-05
By default /var/www is owned by root - so you'll need to "sudo" your files in... or move the DocumentRoot somewhere more convenient (details mentioned in the provided link).

---

### Post by UbuFreak on 2009-05-06
Thanks Alot Iowan. :)

---

### Post by UbuFreak on 2009-05-06
Thanks alot cariboo :)

---

