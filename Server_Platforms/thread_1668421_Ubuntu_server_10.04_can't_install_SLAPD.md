---
title: "Ubuntu server 10.04 can't install SLAPD"
date: 2011-01-16
forum: Server Platforms
---

### Post by thesti on 2011-01-16
Hello,

I use Ubuntu server 10.04
I try to install slapd, but i get the following error

```

libldap-2.4-2 (= 2.4.21-0buntu5.2) but 2.4.21-0ubuntu5.3 is to be installed
E: Broken packages

```

And also, when I try to install some other packages such as nagios, squid, .. I get the some list of errors. One of the error say something like


```
Failed to fetch http://id.archive.ubuntu.com/ubuntu/pool/main/n/nagios-plugins/nagios-plugins-standard_1.14.14-1ubuntu1_i386.deb  Temporary failure resolving 'id.archive.ubuntu.com'
```

What to do? Should I edit /etc/apt/source.list to point to other repo site? Where?


Thank you

---

### Post by Calimo on 2011-01-16
Hi,

Have you tried to do a```
sudo apt-get update
```to refresh your repositories? What is the output? Are there errors linked to id.archive.ubuntu.com? 

If so, you may want to find another mirror; you can find a list there: [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by thesti on 2011-01-17
oh, my bad. It is actually my eth0 interface that is not up. 
After upping my eth0, and do apt-get update. The installation process went smoothly.

Thank you

---

