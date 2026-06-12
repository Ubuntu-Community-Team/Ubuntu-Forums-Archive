---
title: "apache running as root?"
date: 2007-02-12
forum: Server Platforms
---

### Post by PetePete on 2007-02-12
ok so I was checking what was running on my system , then noticed this.

```

pete@linux-server:~$ ps -aux | grep apache
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
root      3363  0.0  0.8   4636  2064 ?        S    20:45   0:00 /usr/sbin/apache
www-data  3364  0.0  0.3   4636   888 ?        S    20:45   0:00 /usr/sbin/apache
www-data  3365  0.0  0.3   4636   888 ?        S    20:45   0:00 /usr/sbin/apache
www-data  3367  0.0  0.3   4636   888 ?        S    20:45   0:00 /usr/sbin/apache
www-data  3368  0.0  0.3   4636   888 ?        S    20:45   0:00 /usr/sbin/apache
www-data  3369  0.0  0.3   4636   888 ?        S    20:45   0:00 /usr/sbin/apache

```

it appears that one instance of apache is running under the root username??!!!

is this normal? at first i thought it was cos i started it from becoming root, so then restarted the server and it still came up with one instance of apache running root ?

---

### Post by phiphedog on 2007-02-12
If the Port specified in the configuration file is the default of 80 (or any other port below 1024), then it is necessary to have root privileges in order to start Apache, so that it can bind to this privileged port. 
Once the server has started and completed a few preliminary activities such as opening its log files, it will launch several child processes which do the work of listening for and answering requests from clients. The main httpd process continues to run as the root user, but the child processes run as a less privileged user. This is controlled by Apache's process creation directives.

---

### Post by PetePete on 2007-02-12
ahhh ok!

makes sense i suppose :P

thanks

---

