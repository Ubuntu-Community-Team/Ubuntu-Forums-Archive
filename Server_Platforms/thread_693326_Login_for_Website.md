---
title: "Login for Website"
date: 2008-02-10
forum: Server Platforms
---

### Post by Holmes89 on 2008-02-10
I am learning more and more about Ubuntu server and am ready to move onto the next step. Since this is a home based server I want to limit the people who can connect to my website in order to protect my bandwidth. So I want to add some sort of login system to prevent a bunch of people connecting to the server. So I would like to have login names and passwords for people to connect. How would I go about doing this? I have no idea where to start.

---

### Post by faulkes on 2008-02-10
The simplest and least complicated (with a grain of salt) would be to setup basic authentication under httpd (apache2).

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

See section 19 on setting up a password protected directory.

Faulkes

---

### Post by Holmes89 on 2008-02-10
Will this allow me to create unique accounts for people?

---

### Post by faulkes on 2008-02-10
Yes.

---

