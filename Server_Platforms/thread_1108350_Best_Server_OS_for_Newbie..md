---
title: "Best Server OS for Newbie."
date: 2009-03-27
forum: Server Platforms
---

### Post by avacomputers on 2009-03-27
I am new to Linux, I am currently using Ubuntu 8.10 on my desktop and would like to setup a webserver. What would you recommend for a Linux newbie.

Thanks.

---

### Post by cariboo on 2009-03-27
If you are a new user, but not afraid of the command line, install the server version, but there is no gui installed. For you I think the best way to go would be to install the LAMP stack on your desktop, that way you still have a gui to fall back on. To install Lamp go to System-->Adminstration-->Synaptic-->Package Manage-->Edit-->Mark Packages by Task, select LAMP and click apply.

Jim

---

### Post by neilevan814 on 2009-03-28
I would also take a little guidance from a how to...like this one...it helped me immensely:

[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by hyper_ch on 2009-03-28
best thing is to do a cli-only install and then try to get things manually work. If you know how apache, mysql, php, postfix (or other mtas) etc. work, then you can switch to a toollike webmin.

Rationale: If you know how to manage the individual daemons (installation/configuration/troubleshooting) then you won't face problems if webmin (or a gui) fails to start properly ;)

---

