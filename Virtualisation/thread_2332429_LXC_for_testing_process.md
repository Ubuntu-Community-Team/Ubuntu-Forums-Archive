---
title: "LXC for testing process"
date: 2016-07-31
forum: Virtualisation
---

### Post by dmytro2 on 2016-07-31
Hi Everyone,

I'm working on a project which is a web application development encompassing  web-site (html), RESTful web server, database, etc.
I want to establish testing using LXC, to let testers simply start several containers with pre-deployed parts of web app and verify test cases.

For every new web-app version a bunch of LXC containers will be created each with particular pre-installed software (like DB server or application server).
Then pieces of web-app will be copied to the rootfs'es of corresponding containers.

What I want to know is whether above can be considered as a good approach and what shortcomings it might result into. 
I will appreciate any comments, suggestions or recommendations. If anyone knows of similar usage of LXC please kindly share your experience.

Thanks in advance)

---

### Post by MAFoElffen on 2016-08-01
Moved to Virtualization section for better exposure.

---

