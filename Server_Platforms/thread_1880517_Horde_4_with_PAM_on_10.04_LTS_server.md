---
title: "Horde 4 with PAM on 10.04 LTS server"
date: 2011-11-13
forum: Server Platforms
---

### Post by madods on 2011-11-13
Hi,

I'm trying to install version 4 of Horde Groupware Webmail Edition on Ubuntu Server 10.04 LTS.

The Horde test script reports:

"PAM Support: No
The PAM extension is required to allow PAM authentication to be used."

I have the php5-auth-pam 0.4-10ubuntu1 module installed.

I've tried installing the PECL pam module, but I get this error:

"configure: error: install the the PAM library or use --with-pam=DIR to specify the location."

From my Googling it seems that the php5-auth-pam 0.4-10ubuntu1 module may be the problem, but I can't find what to do about it. I can uninstall it OK, but what do I replace it with, and how?

---

### Post by yunosh on 2011-11-13
PECL is the correct way, but to build it, you need the libpam0g-dev package.

---

