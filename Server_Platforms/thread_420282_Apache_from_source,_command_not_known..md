---
title: "Apache from source, command not known."
date: 2007-04-23
forum: Server Platforms
---

### Post by peRosine on 2007-04-23
I installed Apache from source and everything works fine except for one thing. When I want to use some apache commands like:

```
apache2-ssl-certificate
a2enmod <something>
```

I get the "command not found" error. How can I enable this commands in my shell?

Thanks in advance.

---

### Post by yeehawjared on 2007-04-23
for generating the ssl certificate under feisty:

```

sudo apt-get install ssl-cert

mkdir /etc/apache2/ssl

/usr/sbin/make-ssl-cert /usr/share/ssl-cert/ssleay.cnf /etc/apache2/ssl/apache.pem
```

---

### Post by jtc on 2007-04-23
a2enmod, etc are Debian/Ubuntu specific solutions. You get those when you install apache2 using your packagemanager. They depend on the way your apache configuration is split up.

---

### Post by peRosine on 2007-04-24
And is it possible to get them when compiling from source?

---

### Post by jtc on 2007-04-24
Well, somehow I'm sure it is possible, but since it depends on a diffrent structure on your apache configuration I doubt it's trivial. If you install apache2 using apt-get and take a look at /etc/apache2 I'm sure things will be clearer :-)

---

