---
title: "Apache Install Messed Up?"
date: 2007-01-25
forum: Server Platforms
---

### Post by hammonjj on 2007-01-25
So I was trying to figure out why virtual hosting isn't working on my computer and I noticed in the apache documentation to try this command:

 /usr/local/apache2/bin/httpd -S

After searching my hard drive I found no such directory nor did I find httpd.  

Did I do something wrong when I installed Apache?

I used:

sudo apt-get install apache2

Should I have installed one of the other packages, like apache2-common?

Thanks
James

---

### Post by kidders on 2007-01-25
Hi there,

> **hammonjj said:**
> So I was trying to figure out why virtual hosting isn't working on my computerWhat happens? Could you post the relevant bits of your apache configuration?

> **hammonjj said:**
> /usr/local/apache2/bin/httpd -S"httpd" is the name of the web server binary on many distros, and many Linux-like OSs. On Ubuntu, you probably want /usr/sbin/apache2.

> **hammonjj said:**
> Did I do something wrong when I installed Apache?No... Looks like you did fine. :-)

---

