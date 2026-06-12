---
title: "Need help on migrating from an online server to Ubuntu server"
date: 2012-08-29
forum: Server Platforms
---

### Post by WakeUpWolfgang on 2012-08-29
I have a website using an online hosting service. They just raised their rates and I want to host it on my own Ubuntu server. I am having difficulty trying to figure out how. Any help will be much appreciated. 

I am plaining on using Ubuntu server 12.04.01 32 bit

---

### Post by LHammonds on 2012-08-29
You're not giving us a whole lot to go on.  Ubuntu Server?  That is an operating system.  Not a web server.

If you are looking to emulate the same environment your web site lives on today, you need to find out what exactly your host is running and what your web site is requiring.  Are they running Apache?  Which version?  Are you making use of a database?  MySQL? What version? So on and so on.

It is rarely a simple task to spin up a Linux server, setup a web service, copy over your web files and be up-and-running.  There are many facets to consider besides just getting a server to mimic the features of an online hosting company.

Once you jump through all the technical hurdles of getting a domain to point to your server (dynamic or static IP) and then map through your router/firewall, you will also be facing automated attacks against your server on a daily basis.  Your server needs to have its security locked down as tight as possible and just enough to let your web site do its job.

You will also need to maintain patches on the server and setup automated and semi-automated backups of your data/server in case your hard drive fails, server burns up or house catches fire.

LHammonds

---

### Post by SeijiSensei on 2012-08-31
Start by reading the relevant sections of the [Ubuntu Server Guide]("https://help.ubuntu.com/12.04/serverguide/index.html").

---

