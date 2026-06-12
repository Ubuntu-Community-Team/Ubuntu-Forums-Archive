---
title: "I want Apache2, NOT Apache!"
date: 2007-07-15
forum: Server Platforms
---

### Post by Ek0nomik on 2007-07-15
When I install Apache 1.3.34 (the software titled, "apache" in the repository), I can load localhost fine on the local machine and I can load the site fine with an internal IP from another computer.

If I uninstall Apache 1.3.34, and install Apache2 instead, I can no longer access localhost on the local machine or from another external machine.  I get a page not found error.

I want to use the newer version of apache, not the older one.  Why will only the older version work?

I'd appreciate any help you can offer!

---

### Post by Koybe on 2007-07-15
Make sure apache2 is started :

```
sudo /etc/init.d/apache2 start
```

Maybe you can remove any configuration files related to apache1 -> remove /etc/apache.

Check your pc is correctly listening on port 80 :
```
netstat -atn
```

---

### Post by Ek0nomik on 2007-07-15
I did run the start command to get the process running, but oddly enough that didn't fix it.

So, I changed the NO_START entry in /etc/default/apache2 to 0, and rebooted, and it suddenly worked.

Thanks for the advice though.  I also did delete my old apache folder in /etc, just to clean things up a bit.  :)

---

### Post by Koybe on 2007-07-15
Ok i didn't get it. It must be that it detects you apache1 installed and protect from having port 80 enabled 2 times ;)

---

### Post by unixhead on 2007-07-15
Why do you need Apache 2 if you hardly to configure Apache 1.x to work? Newer versions are not guaranteed to be better and for newcomer they both are the same in most cases.

If would be easier to help here if you show us your .conf file for Apache 2.

---

### Post by Ek0nomik on 2007-07-16
> **unixhead said:**
> Why do you need Apache 2 if you hardly to configure Apache 1.x to work? Newer versions are not guaranteed to be better and for newcomer they both are the same in most cases.

If would be easier to help here if you show us your .conf file for Apache 2.

It was the version of the software I wanted.  I'm not asking why you install every piece of software on your computer.

Somehow installing Apache1 and PHP4 really screwed up the pathway to Apache2.  PHP5 wouldn't get recognized by Apache2, even after complete removals of the software.

I wanted to install the server edition anyways, so I went ahead and did that.

---

