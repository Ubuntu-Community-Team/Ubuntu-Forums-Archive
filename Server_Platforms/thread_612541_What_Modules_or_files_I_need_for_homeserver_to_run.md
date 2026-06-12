---
title: "What Modules or files I need for homeserver to run own business e-commerce site"
date: 2007-11-14
forum: Server Platforms
---

### Post by kustomjs on 2007-11-14
Hey Guys
I need to know what kind of scripts or modules I would need to install on my home server to run my own small business e-commerce site and the shopping cart i am going to use is Oscommerce. your help would be really good Thanks Tim

---

### Post by adza on 2007-11-14
you will need a LAMP stack (Linux, Apache2, Mysql, PHP) you can install these from the repositories no probs... remember to do the apt-get install <package> --build-dependancies (i think that's it) to ensure tha tthe required dependencies are installed for each package... Also, for production environments, remember you should really do all the DB admin from the command line as tools like phpmysqladmin, while excellent in a dev environment, are not as secure as they could be and shouldn't be used on PRD machines (i do all the DB admin in DEV, then use phpmysqladmin to generate the sql script required and then run that in the PRD environment to build the DB, users etc etc). Anyway, have fun and good luck!

---

### Post by kustomjs on 2007-11-14
ok now since I am going to be dealing with credit cards and personal information what can I do make my server more secure to do this?

---

### Post by twistedtwig on 2007-11-14
I presume you would need to set up SSL or https (not 100% sure how or differences and stuff like that)... I am sure some people could point you in the right direction.. (interested my self as I would like to know how to do it but never really looked into it).

---

