---
title: "pure-FTPd issue"
date: 2011-05-25
forum: Server Platforms
---

### Post by cybernet on 2011-05-25
this are the instructions
```
For example, with pure-ftpd you could add the port range 30000:35000 to TCP_IN
and add the following line to /etc/pure-ftpd.conf and then restart pure-ftpd:
PassivePortRange	30000 35000
```

since /etc/pure-ftpd.conf doesn't exists how can i make the change :(

---

### Post by Lars Noodén on 2011-05-25
If you are only looking for a quick and secure way to transfer files, then you'll want to look at SFTP instead of FTP.  It's time to retire FTP because it is inherently insecure and difficult to set up.

You can be up and running with [SFTP within 5 minutes](http://ubuntuforums.org/showthread.php?p=9065471).

---

### Post by cybernet on 2011-05-25
realy thanks for advice, but i'm already using sftp from openssh
i only need to setup this because of csf:-\"

---

### Post by lykwydchykyn on 2011-05-25
I haven't used the latest version of pure-ftpd before, but if I understand what I'm looking at under /etc, here's what you probably need to do:

 - Create the file /etc/pure-ftpd/conf/PassivePortRange
 - Edit that file and put "30000 35000" (without quotes) in it.
 - restart the pure-ftpd service


It appears that instead of using a conf file, the new version puts conf directives in files named after the directive under the /etc/pure-ftpd/conf directory.  Weird behavior, but there it is.

---

### Post by Lars Noodén on 2011-05-26
> **cybernet said:**
> ...
i only need to setup this because of csf:-\"

What is csf?

---

### Post by cybernet on 2011-05-31
> **lykwydchykyn said:**
> I haven't used the latest version of pure-ftpd before, but if I understand what I'm looking at under /etc, here's what you probably need to do:

 - Create the file /etc/pure-ftpd/conf/PassivePortRange
 - Edit that file and put "30000 35000" (without quotes) in it.
 - restart the pure-ftpd service


It appears that instead of using a conf file, the new version puts conf directives in files named after the directive under the /etc/pure-ftpd/conf directory.  Weird behavior, but there it is.

thanks a lot :D
csf stands for ConfigServer Security & Firewall
[http://www.configserver.com/cp/csf.html](http://www.configserver.com/cp/csf.html)

---

