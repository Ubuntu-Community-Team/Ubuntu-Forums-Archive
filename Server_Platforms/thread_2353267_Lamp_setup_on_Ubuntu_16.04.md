---
title: "Lamp setup on Ubuntu 16.04"
date: 2017-02-20
forum: Server Platforms
---

### Post by fernandoch on 2017-02-20
Hello,

I have a question about my LAMP setup.

Would you disable mpm_event and enable mpm_prefork? Is that a good idea?

Thanks

---

### Post by gordintoronto on 2017-02-20
A more specific message subject would help you get an answer.  Eg: "mpm_prefork?"

Since I have no idea what mpm_prefork is, I have no answer to your question.

---

### Post by fernandoch on 2017-02-20
According to this guide

[https://www.linode.com/docs/websites/lamp/install-lamp-on-ubuntu-16-04](https://www.linode.com/docs/websites/lamp/install-lamp-on-ubuntu-16-04)

They recommend this

The default multi-processing module (MPM) for Apache is the event module but by default PHP uses the prefork module.

Then this

sudo a2dismod mpm_event
sudo a2enmod mpm_prefork

Is that a good idea?

---

### Post by igdfpm on 2017-02-21
Why would it not be a good idea? Apache uses one model **by default** (*ie others are available that may be preferable for reasons such as compatibility with other parts of the system*) and PHP uses the other... turning off what you are not using is a very good idea for a whole host of reasons - resource usage, fault reduction, security etc

---

### Post by fernandoch on 2017-02-21
> **igdfpm said:**
> Why would it not be a good idea? Apache uses one model **by default** (*ie others are available that may be preferable for reasons such as compatibility with other parts of the system*) and PHP uses the other... turning off what you are not using is a very good idea for a whole host of reasons - resource usage, fault reduction, security etc

Why the default is not mpm_prefork then?

---

