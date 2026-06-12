---
title: "Multiple localhost sites in apache2?"
date: 2006-02-06
forum: Server Platforms
---

### Post by OneSeventeen on 2006-02-06
I have an ubuntu workstation that I do all my major web application development on, then I move it to my ubuntu server.  Now I want to work on more than one major app at a time, and each has their own sub-domain.

Is it possible to setup more than one localhost account?

Such as rerouting a certain URL to localhost, or adding subdomains to localhost?  such as foo.localhost or localhost.foo?

---

### Post by ::DoGG:: on 2006-02-06
Maybe Virtual Hosts are the thing You are looking for ?

[http://httpd.apache.org/docs/1.3/vhosts/](http://httpd.apache.org/docs/1.3/vhosts/)

---

### Post by OneSeventeen on 2006-02-06
My ubuntu webserver has roughly 7 server names and 2 IP addresses, so I am very comfortable with virtual hosts, but what I can't figure out is how to do the same thing for local websites.

The goal is to have a copy of the main webserver with all of its virtual hosts, but allow me to go to each one individually on my local machine without having an internet connection.

For some reason the ServerName foo.localhost doesn't seem to work.

---

### Post by LordHunter317 on 2006-02-06
You can do name-based virtual hosting on the localhost, but you need to add the hostname entries to  /etc/hosts for it to work.

---

### Post by OneSeventeen on 2006-02-06
[QUOTE=LordHunter317]You can do name-based virtual hosting on the localhost, but you need to add the hostname entries to  /etc/hosts for it to work.[/QUOTE]
**Exactly** what I was looking for!  Thanks!

---

