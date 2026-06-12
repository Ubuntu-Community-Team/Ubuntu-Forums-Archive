---
title: "OTRS 2 on Ubuntu 8.04 server"
date: 2008-06-05
forum: Server Platforms
---

### Post by ncozzolino on 2008-06-05
I've been trying to install OTRS 2.2.7 from source and the respository on Ubuntu 8.04 server.  Neither is successful.  From the respository the install creates the DB with no problem then fails with error:

chmod: cannot access '/etc/otrs/fetchmailrc' : No such file or directory
dpkg: error processing otrs2 (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
otrs2
E: Sub-processes /usr/bin/dpkg returned an error code (1)

I've searched google extensively for issues with OTRS, Ubuntu, Debian, etc and haven't found a solution.  Does OTRS 2 work on Ubuntu 8.04?  Any suggestions would be greatly appreciated.  

Thanks!

Nick

---

### Post by gtdaqua on 2008-06-05
I stumbled across OTRS 2 and had similar problems getting it set up in Ubuntu 8.04 and eventually moved to Debian etch and worked without any problems. 

Debian is usually considered as a more stable OS. However, this should not affect OTRS 2 installation anyway. I just had to move to debian to get this installed.

But then again, I moved to OCS-ng and GLPI - by far, the best IT asset/inventory management solution clubbed with internal Helpdesk System in the industry. Unlike Altiris or MS System Center, the OCS-ng is extremely fast and extremely easy to roll out. Give it a try - its Open Source and definitely worthwile. 

Both are installed on my Debian server and currently administering over 250+ desktops located in different cities and on different domains!

[OCS Inventory]("http://www.ocsinventory-ng.org/")

[GLPI]("http://glpi-project.org/?lang=en")

---

### Post by BringR on 2008-06-20
I've got the same damn prob using jeos 8.04 in a VMWare::confused:

```
This module does not exist!
dpkg: Fehler beim Bearbeiten von otrs2 (--configure):
 Unterprozess post-installation script gab den Fehlerwert 1 zurÃ¼ck
Fehler traten auf beim Bearbeiten von:
 otrs2
E: Sub-process /usr/bin/dpkg returned an error code (1)
bringr@coglin:~$ dpkg: Fehler beim Bearbeiten von otrs2 (--configure):
-bash: syntax error near unexpected token `('
```

s.o. who knows a solution?

thx BringR

---

### Post by gtdaqua on 2008-06-20
jeOS is a bare-minimum OS from Ubuntu optimized to host Virtual Environments. Check your repositories first. otrs2 is included in Ubuntu 64-bit Hardy Server

```

$ sudo apt-get install otrs2
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  apache2 apache2-mpm-worker apache2-utils apache2.2-common dbconfig-common
  libalgorithm-diff-perl libapr1 libaprutil1 libauthen-sasl-perl
  libconvert-binhex-perl libcrypt-passwdmd5-perl libdate-pcalc-perl
  libdbi-perl libdigest-hmac-perl libdigest-sha1-perl libemail-valid-perl
  libfile-temp-perl libio-stringy-perl libmailtools-perl libmime-perl
  libmime-tools-perl libnet-daemon-perl libnet-dns-perl libnet-domain-tld-perl
  libnet-ip-perl libpcre3 libplrpc-perl libpq5 libtext-diff-perl
Suggested packages:
  apache2-doc virtual-mysql-client mysql-client postgresql-client
  libgssapi-perl dbishell libcompress-zlib-perl libnet-ldap-perl otrs2-doc-en
  otrs2-doc-de
Recommended packages:
  aspell ispell libapache2-mod-perl2 libdbd-pg-perl libdbd-mysql-perl
  libgd-graph-perl libgd-text-perl postgresql-8.2 mysql-server
The following NEW packages will be installed:
  apache2 apache2-mpm-worker apache2-utils apache2.2-common dbconfig-common
  libalgorithm-diff-perl libapr1 libaprutil1 libauthen-sasl-perl
  libconvert-binhex-perl libcrypt-passwdmd5-perl libdate-pcalc-perl
  libdbi-perl libdigest-hmac-perl libdigest-sha1-perl libemail-valid-perl
  libfile-temp-perl libio-stringy-perl libmailtools-perl libmime-perl
  libmime-tools-perl libnet-daemon-perl libnet-dns-perl libnet-domain-tld-perl
  libnet-ip-perl libpcre3 libplrpc-perl libpq5 libtext-diff-perl otrs2
0 upgraded, 30 newly installed, 0 to remove and 2 not upgraded.
Need to get 6098kB of archives.
After this operation, 26.7MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

So, check your "apt" repositories.

---

### Post by klcant on 2008-08-22
I am getting the same errors as Nick.  Did you ever have any luck finding a solution?

Thanks,
Kevin

---

### Post by promodus on 2008-08-22
Depending on your situation, maybe try GLPI ? I found OTRS hideous.

---

### Post by klcant on 2008-09-11
> **promodus said:**
> Depending on your situation, maybe try GLPI ? I found OTRS hideous.

Promodus - My main need is for trouble ticket tracking.  How does GLPI stack-up against OTRS for that?

---

### Post by n0manarmy on 2008-10-08
I found the answer to my problem, which looks to be your problem as well here

[https://bugs.launchpad.net/ubuntu/+source/otrs2/+bug/226444](https://bugs.launchpad.net/ubuntu/+source/otrs2/+bug/226444)

Try 'sudo apt-get install libapache2-mod-perl2-dev' before 'sudo apt-get install otrs2'

So the installation process works fine...

---

