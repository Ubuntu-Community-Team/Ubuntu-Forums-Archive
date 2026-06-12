---
title: "change curl listening port"
date: 2009-09-04
forum: Server Platforms
---

### Post by JustTCO on 2009-09-04
Hi,

I install the dfGallery 2.0 on a standalone webserver on port 80 and worked well. I changed just to test from port 80 to port 8080 and curl extension crashed. So can anyone help me change the cURL port from 80 to 8080??

---

### Post by Vegan on 2009-09-04
you need to make changes with apache2

```
cd /etc/apache2
```

```
sudo nano httpd.conf
```

and then you can change the listen port to or add one if there is none:

```
listen 8080
```

---

### Post by JustTCO on 2009-09-05
That changes i allready made but that is not what i ask for. the changes are not in the httpd.conf but in ports.conf file.

I had to change the sites-available/default as well so virtual addresses see the port 8080.

My problem is if i install curl over port 80 it work fine, if i change the apache to port 8080 curl dont work anymore. So how can i change curl to work with port 8080?:confused:

---

