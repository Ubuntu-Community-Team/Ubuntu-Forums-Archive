---
title: "Apache Sub-Domains"
date: 2006-02-17
forum: Server Platforms
---

### Post by JustRandomName on 2006-02-17
How do I configure apache to use sub-domains?

To be more clear:

If I have three projects stored on my hard-drive like so:

/home/user/dev/project1
/home/user/dev/project2
/home/user/dev/project3

Instead of using sub-dirs to access the projects (e.g. [http://localhost/project1](http://localhost/project1) etc) how would I use subdomains like:

[http://project1.localhost](http://project1.localhost)
[http://project2.localhost](http://project2.localhost)
[http://project3.localhost](http://project3.localhost)
[http://webmail.localhost](http://webmail.localhost)
etc etc

I am not bothered about the outside world being able to view the sites (it is just dev stuff).

How would one go about this? I think it is something to do with the <VirtualHost *> in the httpd.conf file, but I am by no stretch of the imagination a apache admin.

Cheers

---

### Post by JustRandomName on 2006-02-17
Ignore me, I found this wiki entry:

[https://wiki.ubuntu.com/LocalhostSubdomain](https://wiki.ubuntu.com/LocalhostSubdomain)

Could of sworn I searched the wiki and forums though...

Sorry for wasting your time

---

### Post by dk_pa on 2006-02-17
> Sorry for wasting your time

Bah!  Not a waste, you are simply making it easier for the next person with the same question to find! :)

---

