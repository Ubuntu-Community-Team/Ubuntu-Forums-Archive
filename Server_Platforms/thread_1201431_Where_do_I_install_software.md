---
title: "Where do I install software?"
date: 2009-07-01
forum: Server Platforms
---

### Post by MarioFromBelgium on 2009-07-01
Hi,

I'm building my perfect home/development server.

One goal will be to develop a web-app: using coldfusion as application-server. (I know that Coldfusion is not garanteed on UBUNTU but for know I need Coldfusion and UBUNTU)

My problem is not how to install Coldfusion but where!
My question is more general (but I use the Coldfusion install to explain)
The tutorials on how to install Coldfusion don't say where I would best install it.
I' mean when you can use apt-get everything is taken care for you. But in this case (and probably others will come) I have to run the bin-file from the directory where I want to install the soft.

I was thinking to create a dir /etc/coldfusion and in build Coldfusion in that directory.

Would that be the best/most logical thing to do?
Is this the way I should proceed when installing soft that is not in apt-get?

Mario

---

### Post by Kareeser on 2009-07-01
/opt


[http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)

:)

---

### Post by scorp123 on 2009-07-01
> **kareeser said:**
> /opt 

+1 !!

---

### Post by scorp123 on 2009-07-01
> **MarioFromBelgium said:**
>  /etc/coldfusion  /etc is for config files. ):P

---

