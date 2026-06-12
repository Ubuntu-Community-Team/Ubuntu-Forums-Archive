---
title: "Apache + tomcat my way"
date: 2007-02-06
forum: Server Platforms
---

### Post by rogier.de.groot on 2007-02-06
Hi all, I need some help setting up a newly installed Edgy server.
I want: apache2 + php5 & tomcat 5.5 & connect them with the command:
ProxyPass /bliep ajp://localhost:8009/bliep
I don't want to use JkMount because it won't let me do something like:
ProxyPass /foo/bar ajp://localhost:8009/helloworld
I've got the apache2+php5 part down, but the rest is giving me headaches.
There doesn't seem to be a mod_proxy_ajp package in the repos, and installing tomcat5.5 has some weirdness too - it installs useless examples - but I can't delete them from the manager webapp for some reason. Probably permissions, but so far I've failed to correct them.
This setup probably isn't rare, but Google won't find me no hints! So I turn to you all for help.
BTW, I want this to work without tomcat being directly accessible to anyone, only the apps / urls I want to expose via apache.

---

### Post by rogier.de.groot on 2007-02-06
P.S.
If it's possible, and/or less hassle, ProxyPass'ing http instead of ajp would also be fine.
That is, if I can get away with something like
ProxyPass /bliep [http://localhost:8180/bliep](http://localhost:8180/bliep)
on a SSL site, which might just cause some problems.

---

### Post by rogier.de.groot on 2007-02-08
Ok, so after digging around a little, I figure I need apache 2.2 - which isn't in the repositories. So, I'll build it from source, or get it from an external repo. Anyone out there know a repo that has apache 2.2?
If I build it from source, I'd like to make it into a bunch of packages and put them online for everybody to use - but I don't know how to do that. Could someone please enlighten me?

---

