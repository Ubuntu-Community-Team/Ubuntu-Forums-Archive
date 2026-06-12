---
title: "Submitting forms don't load next page."
date: 2010-08-25
forum: Server Platforms
---

### Post by Jon914 on 2010-08-25
I'm running into a very strange issue that affects all web apps on my server. This happened after a reboot.

Basically, I can fill out a form, submit it, and then the next page will never load, or it will load after several minutes. To reiterate, this affects every web app on this server, and many of my users are noticing it.

I've already tried restarting Apache and doing a repair of MySQL tables as a friend suggested, but I'm out of idea and find this problem to be pretty hard to Google up.

Any ideas? I can provide server details upon request, but it's a basic LAMP stack running Ubuntu 9.x on a Linode.

---

### Post by Jon914 on 2010-08-25
Solved. It was caused by an edit to the etc/hosts file where I was attempting to fix a broken sudo command by adding 127.0.0.1 [boxnamehere], which fixed that issue but caused the reported issue to happen.

---

