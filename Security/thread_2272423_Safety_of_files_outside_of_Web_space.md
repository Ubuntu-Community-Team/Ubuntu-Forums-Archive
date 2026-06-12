---
title: "Safety of files outside of Web space"
date: 2015-04-06
forum: Security
---

### Post by Frank P on 2015-04-06
Ubuntu 14.04LTS server, Apache2.4, MySQL, PHP, NAT router, ufw on all pcs

I know there's no such thing as a 100% secure server but are the directories/files outside of the web space /var/www/html and sub directories, still relatively secure if the web server is hacked? Do Apache aliases into outside directories compromise the security. Other PCs on the LAN?

Can anyone recommend some reading on the subject - not a security "how to" but mainly concepts

Thanks

Frank P

---

### Post by tgalati4 on 2015-04-06
Yes, the files outside of the apache's root directory are generally safe if only the content of the site has been defaced.  However, it is possible to have an infected PHP or other script file that could do further damage.  That will take close examination of all of the files in the apache root directory tree.  Pointing to outside directories with symbolic links should keep permissions and access control the same as the apache process, but again, it may not be 100%.

There are lots of resources on the web, just do a search and start reading.  Security concepts can be found as well, but most are How-to's since that is what most folks want right-away.  

Security can be broken down and explored a few ways:

Overall linux security model:  [https://www.linux.com/learn/docs/727873-overview-of-linux-kernel-security-features/](https://www.linux.com/learn/docs/727873-overview-of-linux-kernel-security-features/)

and  [http://linuxaria.com/article/an-introduction-to-security-models-in-linux](http://linuxaria.com/article/an-introduction-to-security-models-in-linux)

And for your Use Case, LAMP stack security precautions:  [http://security.stackexchange.com/questions/53752/what-needs-to-be-focused-on-when-hardening-a-lamp-stack](http://security.stackexchange.com/questions/53752/what-needs-to-be-focused-on-when-hardening-a-lamp-stack)

and [http://security.stackexchange.com/questions/9948/how-to-secure-a-dedicated-linux-server-running-a-lamp-stack-for-commercial-e-com](http://security.stackexchange.com/questions/9948/how-to-secure-a-dedicated-linux-server-running-a-lamp-stack-for-commercial-e-com)

How was the original web server compromised?

---

### Post by Frank P on 2015-04-06
Thanks for the links - I'll check them out. The web server hasn't been compromised - yet! It's a personal hobby site on my own LAN. I'm just trying to make sure it won't be compromised if I open it up to the outside.

Thanks

Frank P

---

### Post by tgalati4 on 2015-04-06
It's best to think of security in layers.  The more layers you provide, the more secure your server will be.  It requires a lot of reading and testing, but there are enough tutorials on the web to get you started.

---

### Post by SeijiSensei on 2015-04-07
Assuming this is a standard installation where the Apache server runs as the "www-data" user, you want to limit the places where that user can write files.  If there is a PHP application that needs write privileges, you should pay close attention to enabling only the minimal permissions www-data needs and limiting its access to a specific directory outside the web tree.

---

### Post by Frank P on 2015-04-17
Thanks to all for replies
Frank P

---

