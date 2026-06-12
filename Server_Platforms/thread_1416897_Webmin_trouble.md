---
title: "Webmin trouble"
date: 2010-02-26
forum: Server Platforms
---

### Post by espressobeanie on 2010-02-26
Hi,

I'm having trouble with Webmin. I got it up and running. However, I was changing the 'listen on port' to something other than port# 10000. I made sure ufw was open to the tcp requests on my new webmin port only. UDP has been disabled. I type in my browser my ip address with the new port, and I get 'problem loading page' now. How can I see the tcp port webmin is set from a terminal on the host computer? Do I goto a webmin folder and change a .conf file?

I'm running ubuntu server by the way.

---

### Post by cdenley on 2010-02-26
I'm not familiar with webmin, but this should list all your listening TCP processes.
```

sudo netsat -tlnp

```

---

### Post by espressobeanie on 2010-02-26
Hmm. Thanks. The port is open and it's correctly configured on ufw.

---

### Post by joberly on 2010-02-26
The previous command shows this:

tcp  0  0 0.0.0.0:10000    0.0.0.0:*               LISTEN      27191/perl

With 10000 set as the new port? Just clarifying the change was committed.

---

### Post by espressobeanie on 2010-02-26
I was able to get it working now. Thanks. That netstat command gave me the right port.

[SOLVED]

---

