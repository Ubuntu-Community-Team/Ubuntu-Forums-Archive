---
title: "Using Snort Flexible Response"
date: 2008-04-09
forum: Security Discussions
---

### Post by davinci0212 on 2008-04-09
Hopefully this is a quick question and easy to answer. I am running Ubuntu 7.10 desktop. I've installed Snort 2.7.0 with apt. I am trying to use a "resp" option in the local.rules file, but I am receiving the error:

*"snort: unrecognized option '--enable-flexresp' . *

My command for launching Snort is: 

```
sudo snort -i eth0 -l /var/log/snort -c /etc/snort/snort.conf
```

Does anyone know how I can get the "resp" option to work in a rule? I am trying to use it for tearing down a connection. I read that you have to compile Snort in flexible mode in order to use the resp options. Is there an easier way of doing so with apt? Am I messing up with my command for Snort? :)

Thanks!

---

### Post by lintoolman on 2008-04-10
The package version probably doesn't have flexresp compiled in.

Uninstall the snort packages then, download the source code from snort and compile with the proper flag, which I'm fairly certain is "--enable-flexresp."

 I used the following tutorial with no problems:

[http://www.howtoforge.com/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10-updated](http://www.howtoforge.com/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10-updated)

On a side note, I was never able to get the Ubuntu snort packages to run after install. It didn't like the fact the mysql server was running on another host, so the configuration script died.  I'm a big fan compiling my own security software anyway, so that was no big deal.






---

### Post by davinci0212 on 2008-04-10
Thank you! I tried that URL last night and complied from source using ```
./configure -enable-flexresp
```.

---

