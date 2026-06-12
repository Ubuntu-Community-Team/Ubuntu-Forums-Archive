---
title: "Problem with files of a configuration the apache2"
date: 2008-04-22
forum: Server Platforms
---

### Post by alexash on 2008-04-22
I have removed a folder "/etc/apache2". After reinstallation the folder has appeared again, but files of a configuration were not established. How to be:?: What to do? :)

---

### Post by bluefrog on 2008-04-23
What did you reinstalled? apache2 package?

If you want the conf files you should try to reinstall the "real" apache2 package not only the meta package.

example

sudo apt-get install --reinstall $(dpkg -l apache2-mpm-* | grep ii | awk '{print $2}')

James Dupin

---

### Post by alexash on 2008-04-23
> **bluefrog said:**
> What did you reinstalled? apache2 package?

If you want the conf files you should try to reinstall the "real" apache2 package not only the meta package.

example

sudo apt-get install --reinstall $(dpkg -l apache2-mpm-* | grep ii | awk '{print $2}')

James Dupin

All the same there is a following mistake >>>
+++++++++++++++++
apache2: Could not open configuration file /etc/apache2/apache2.conf: No such file or directory
[fail] invoke-rc.d: initscript apache2, action "start" failed.
+++++++++++++++++

---

### Post by bluefrog on 2008-04-23
ah indeed removing /etc/apache2 folder is not a good thing. I reproduced what you did and had the same problem.

So to solve it, I removed everything related to apache2 and installed it again.

sudo apt-get remove --purge $(dpkg -l apache* | grep ii | awk '{print $2}') && sudo apt-get install apache2

James Dupin

---

### Post by alexash on 2008-04-23
> **bluefrog said:**
> ah indeed removing /etc/apache2 folder is not a good thing. I reproduced what you did and had the same problem.

So to solve it, I removed everything related to apache2 and installed it again.

sudo apt-get remove --purge $(dpkg -l apache* | grep ii | awk '{print $2}') && sudo apt-get install apache2

James Dupin

Thanks, James! The service was started, but as well as earlier, before removal of the catalogue, with a mistake:

 * Starting web server apache2                                                                                                                               apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

---

### Post by bluefrog on 2008-04-23
this is not a real problem. it will work anyway.

you could give your computer a FQDN to solve that (so when you do hostname -d it gives you your TLD)

example

cat /etc/hosts
127.0.0.1  localhost.local localhost your-machine-name

James Dupin

---

### Post by alexash on 2008-04-23
Apache2 works. Has left a configuration by default.

---

