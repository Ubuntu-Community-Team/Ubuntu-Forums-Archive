---
title: "How to decrease ThreadStackSize"
date: 2010-02-05
forum: Server Platforms
---

### Post by zereshk on 2010-02-05
Desparate to reduce RAM usage of my tiny VPS running Ubuntu 9.04 and Apache2.2.11,  [here]("http://ubuntuforums.org/On%20Linux,%20each%20child%20process%20will%20use%208MB%20of%20memory%20by%20default.%20This%20is%20probably%20unnecessary.%20You%20can%20decrease%20the%20overall%20memory%20used%20by%20Apache%20by%20setting%20ThreadStackSize") I saw that 

> On Linux, each child process will use 8MB of memory by default. This is
probably unnecessary. You can decrease the overall memory used by Apache by
setting ThreadStackSize used by Apache by setting ThreadStackSize to 1MB in So I tried to give the suggestion a try. But when I append

> ThreadStackSize 1000000in my /etc/apache2/httpd.conf <IfModule mpm_prefork_module> directive, and restarted apache, it failed with this message:

> Invalid command 'ThreadStackSize', perhaps misspelled or defined by a module not included in the server configuration
So I[ figured out]("http://httpd.apache.org/docs/2.1/mod/mpm_common.html") that  the relevant modules  are neither enabled nor available on apache2. Now I am wondering whether there is a way to decrease the ThreadStackSize without the need to compile apache from source? If not, what should I do?
Thanks

---

### Post by Bachstelze on 2010-02-05
Which MPM are you using? If you are using a non-threaded MPM like prefork, it obviously makes no sense to define the thread stack size.

In order to do that, you'll need to install a threaded MPM like worker:

```
sudo apt-get install apache2-mpm-worker
```

However, this will break PHP, as PHP requires a non-threaded MPM (prefork or itk).

---

