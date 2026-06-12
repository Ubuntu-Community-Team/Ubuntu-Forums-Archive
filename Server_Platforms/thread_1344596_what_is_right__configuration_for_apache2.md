---
title: "what is right  configuration for apache2"
date: 2009-12-03
forum: Server Platforms
---

### Post by tapas_mishra on 2009-12-03
I want to know what are the best practises as far as apache2 is concerned to host your sites.
Some one who have used if they can point out to the entries in httpd.conf or apache2.conf
right now I am having apache2 running but users do not have write permission to /var/www
so no one is able to make any changes in the sites there

---

### Post by madverb on 2009-12-03
What are you planning on using the websites for?

---

### Post by tapas_mishra on 2009-12-03
Server support tool sort of applications like controling a Virtual Machine etc

---

### Post by M!K3_$ on 2009-12-03
> **tapas_mishra said:**
> right now I am having apache2 running but users do not have write permission to /var/www
so no one is able to make any changes in the sites there

As far as that goes. only give users write access to directories that they absolutely need write access for. Also, in your application that is letting users write to said directory, only allow them to write certain things(filter by file type or file size), this will stop them from uploading nasty scripts or flooding out your hard drive.

---

### Post by tapas_mishra on 2009-12-04
> **M!K3_$ said:**
> As far as that goes. only give users write access to directories that they absolutely need write access for. 
For this I have given them the home directories where they can host the sites and and make what ever changes they wish to do in their code.

---

