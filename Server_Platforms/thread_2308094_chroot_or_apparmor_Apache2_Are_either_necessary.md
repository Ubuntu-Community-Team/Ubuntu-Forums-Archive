---
title: "chroot or apparmor Apache2??? Are either necessary?"
date: 2015-12-30
forum: Server Platforms
---

### Post by mroussin51 on 2015-12-30
Greetings,

I am learning Ubuntu Server 14.04 LTS. I noticed that BIND is being monitored/protected by Apparmor and Apache2 is not. Is it necessary to chroot or apparmor Apache? I have looked at a couple of dated Tutorials on the matter. Please give some recommendations with some recommended reading. I searched Google and found very little. Also, I did a search in the Forum as well. Digitalocean has a guide for employing apparmor with NGINX but nothing related to Apache2. There is an Apache module for apparmor but I don't have a clue how to utilize it.

[https://www.digitalocean.com/community/tutorials/how-to-create-an-apparmor-profile-for-nginx-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-create-an-apparmor-profile-for-nginx-on-ubuntu-14-04)

Should we be concerned with security measures involving Apache2 or is it just paranoia.

Thanks for taking the time to look at this.

Best regards,

Mike

---

### Post by TheFu on 2015-12-31
> **mroussin51 said:**
> Should we be concerned with security measures involving Apache2 or is it just paranoia.

You should ALWAYS be paranoid.  BIND has a long history of being hacked. In my 20+ yrs running Linux/Unix systems, I've been hacked twice. Once was thru BIND - though it was BINDv8 and a long time ago.

Setting up chroot and apparmor for BIND is relatively simple. The scope of BIND is fairly limited and it usually only touches a few, specific, file system locations. Very easy to chroot.  

OTOH, apache can touch pretty much anywhere on the file system depending on requirements. There could be a DBMS, php, python, perl, java, proxy, reverse-proxy, load balancer or 500 other addons for apache. In short, it is hard to make a generic chroot or a generic apparmor setup for apache. You'll need to do it yourself if that is part of the mitigation strategy deemed to be important.

For apparmor, there are many guides and I found a few good youtube videos explaining how to put it into monitor mode to build the settings. Then take those settings an apply them to the running processes. Any access outside those pre-approved file system areas would be blocked. This can be a nice-to-have or a terrible maintenance headache, since we commonly add more websites to our web servers.

Sadly, there is no "Enable Security" checkbox for these things. A layered approach has been found to be the best defense. Allow only traffic required from external addresses. Limit access to admin panels and other ports just from those addresses which require it (not the entire internet). Perhaps a reverse-proxy that restricts traffic requests to those which fit the application would be another layer worth adding?  It all comes down to your risks and the level of mitigation required.  We put a static copy of our website on a separate server, since 98% of our traffic is people browsing. They don't need to connect to the "edit" version of the site until some transaction is started. Trying to hack a read-only website isn't easy (especially when the files are read-only on the server file storage). ;)

With great power comes great responsibility. Your team is responsible to provide enough security for the services offered. What is enough? Only the crackers know.

Being paranoid is smart. "They" are out to get all of us, especially if we are easy marks.

---

### Post by SeijiSensei on 2015-12-31
You might consider [mod_security]("https://www.linode.com/docs/websites/apache-tips-and-tricks/modsecurity-on-apache") as an alternative.

---

