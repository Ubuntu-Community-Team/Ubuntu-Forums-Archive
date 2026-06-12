---
title: "LAMP installation without terminal"
date: 2012-06-25
forum: Server Platforms
---

### Post by emrahustun on 2012-06-25
Hi,

I searched but couldn't find anything about LAMP installation with GUI.

I am packaging my application to .deb package. I need to add LAMP server to dependencies.

Is there a way to install LAMP with my default configuration during .deb package installation without terminal?

Thank you very much.

---

### Post by irv on 2012-06-25
Go here for a list of packages needed for LAMP, and if you don't want to install them from a terminal use the package manager.
[http://en.wikipedia.org/wiki/List_of_Apache%E2%80%93MySQL%E2%80%93PHP_packages]("http://en.wikipedia.org/wiki/List_of_Apache%E2%80%93MySQL%E2%80%93PHP_packages")
I found the OP not very clear on what you want to do.
EDIT: Are you really still using version 7.10?

---

### Post by emrahustun on 2012-06-25
Thank you.

Actually I'm tring to install LAMP with my .deb package background. User will not see LAMP installation steps and will not configure it.

---

### Post by irv on 2012-06-25
> **emrahustun said:**
> Thank you.

Actually I'm tring to install LAMP with my .deb package background. User will not see LAMP installation steps and will not configure it.

There are a few things that need to be configured while they are installed, like MySQL and Apache.

---

### Post by spynappels on 2012-06-25
You just need to be careful as well, as installing services which, if not managed correctly, could open the server to attack and compromise should not be installed without the user's knowledge or input unless your install includes some script which locks it down completely and makes the user aware of their responsibility to keep it secure through security updates etc.

---

