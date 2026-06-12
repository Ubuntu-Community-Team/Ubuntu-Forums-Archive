---
title: "Webhosting - PHP5 upgrade for wordpress"
date: 2011-11-29
forum: Server Platforms
---

### Post by MezzUK on 2011-11-29
Hi all,

I have recently been handed our webhosting server to manage after my collegue, who set everything up, moved to another company. I have a rather limited understanding of Linux systems and sofar have been fine, creating new users, mysql dbs and other bits related to setting up space for others to upload content for their sites to.

I have received a request to setup a Wordpress site for a customer and had everything setup until I loaded the wp-config page and was greeted with a message stating that
"Your server is running PHP version 5.1.6 but WordPress 3.2.1 requires at least 5.2.4."

The server was setup a rather long time ago and has been left for the most part as things were working fine. The Linux version is 2.6.17-12-server (rather outdated to say the least but it has been fine sofar).

I have been trying to update the PHP version, following a number of tutorials and threads, to part success although something I have done has now caused another one of our sites (running and older version of Wordpress) to display the :

"Your PHP installation appears to be missing the MySQL extension which is required by WordPress."

I have again followed a number of tutorials etc to try and alleviate this issue so that at least our current sites are back up and running. I briefly managed to get this back earlier but when I continued to solve the php version issue the problem cropped up again and I am not sure what exactly fixed it.

I would appreciate any help that can be offered, or if there is any extra information that I can provide please let me know. Unfortunately I've been rather thrown in at the deep end on this one.

---

### Post by SeijiSensei on 2011-11-29
> **MezzUK said:**
> "Your PHP installation appears to be missing the MySQL extension which is required by WordPress."

If you're running Ubuntu, you need to install the php5-mysql package.  On RedHat/CentOS, it's called php-mysql.

---

### Post by MezzUK on 2011-11-29
Thanks for the reply, unfortunately I'm already running the newest version (according to the apt-get install results). I am assuming that the sources.list info is out of date. It is ubuntu that I am running on.

---

### Post by armandoroggio on 2012-09-05
MezzUK, I had a similar experience. Turned out that I needed to update PHP5.

sudo apt-get install php5

You might try this.

---

### Post by Cheesemill on 2012-09-05
What version of Ubuntu are you running?

Can you post the outputs of:
```
uname -a
cat /etc/lsb_release
```

---

### Post by nothingspecial on 2012-09-05
Old thread.

Closed.

---

