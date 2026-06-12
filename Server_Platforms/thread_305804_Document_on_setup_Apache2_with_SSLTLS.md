---
title: "Document on setup Apache2 with SSL/TLS"
date: 2006-11-23
forum: Server Platforms
---

### Post by satimis on 2006-11-23
Hi folks,

Ubuntu-6.06.1-LAMP-server-amd64
Apache2
SSL

I'm installing/config a web/apache2 server for experiment/testing and encountering difficulty on googling document.  Either the document found is out off day or not for Ubuntu.

I found following document;
Apache 2 with SSL/TLS: Step-by-Step, Part 1
[http://www.securityfocus.com/infocus/1818](http://www.securityfocus.com/infocus/1818)

Apache 2 with SSL/TLS: Step-by-Step, Part 2
[http://www.securityfocus.com/infocus/1820](http://www.securityfocus.com/infocus/1820)

Please advise whether they are document for setup SSL/TLS on Apache2?  If NO please advise can I find  the relevant document?  TIA.


B.R.
satimis

---

### Post by MJN on 2006-11-24
I would personally recommend [http://www.vanemery.com/Linux/Apache/apache-SSL.html](http://www.vanemery.com/Linux/Apache/apache-SSL.html)
 
Nice and simple, well explained and, above all, it works!
 
(It may mention Red Hat rather a lot but that's not a problem... and in Step 4 you need to be editing /etc/apache2/sites-available/default rather than httpd.conf, and you can ignore Step 6 onwards if you're not yet interested in authenticating clients)
 
Mathew

---

### Post by satimis on 2006-11-24
Hi Mathew,

Tks for your advice and URL

How to check whether mod_ssl and ssl/openssl have been installed.  What are the names of the packages

TIA


B.R.
satimis

Edit:
$ sudo apt-cache search mod_ssl
Password:
libapache-mod-ssl-doc - Documentation for Apache module mod_ssl
$ sudo apt-cache showpkg mod_ssl
W: Unable to locate package mod_ssl
$ sudo apt-cache policy mod_ssl
W: Unable to locate package mod_ssl

---

### Post by MJN on 2006-11-24
mod_ssl is an Apache module and hence 'installed' with **sudo a2enmod ssl**.
 
For openssl, just install it with your package manager if not already - try running **sudo openssl** as I imagine it's already there.
 
Mathew

---

### Post by satimis on 2006-11-24
Hi Mathew,

I got them.

$ sudo openssl
Password:
OpenSSL> exit

$ sudo a2enmod ssl```

This module is already enabled!
```

$ lsmod | grep ssl
No printout

$ sudo apt-cache showpkg openssl```

Package: openssl
Versions:
0.9.8a-7ubuntu0.3(/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-amd64_Packages)(/var/lib/dpkg/status)
0.9.8a-7build1(/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_main_binary-amd64_Packages)

Reverse Depends:
  sendmail-bin,openssl
  libssl0.9.7,openssl 0.9.6-2
  apache-ssl,openssl
  mutt,openssl
  libssl0.9.8,openssl 0.9.6-2
  dovecot-common,openssl
  courier-ssl,openssl
  courier-pop-ssl,openssl
  courier-imap-ssl,openssl
  apache2-threaded-dev,openssl
  apache2-prefork-dev,openssl
  apache2-common,openssl
  dovecot-common,openssl
  wl-beta,openssl
  wl,openssl
  w3-el-e21,openssl
  uw-imapd,openssl
  ultrapossum-tls,openssl
  tunneldigger,openssl
  tinyca,openssl 0.9.7e
  thy,openssl
  telnetd-ssl,openssl 0.9.2b
  sympa,openssl 0.9.5a
  stunnel4,openssl
  stunnel,openssl
  stone,openssl
  sslwrap,openssl
  sisu,openssl
  sendmail-bin,openssl
  pyca,openssl 0.9.6
  pyca,openssl 0.9.7
  pkcipe,openssl
  partimage-server,openssl
  openswan,openssl
  lighttpd,openssl
  libssl0.9.7,openssl 0.9.6-2
  libpam-mount,openssl
  libmultisync-plugin-syncml,openssl
  libapache-mod-ssl,openssl
  kvpnc,openssl
  ipopd,openssl
  httping,openssl
  ftpd-ssl,openssl 0.9.2b
  etpan-ng,openssl
  ejabberd,openssl
  education-main-server,openssl
  dsniff,openssl
  debian-edu-config,openssl
  cipe-source,openssl
  carpaltunnel,openssl
  bincimap,openssl
  apache-ssl,openssl
  aolserver4-nsopenssl,openssl 0.9.6
  ssl-cert,openssl
  schooltool,openssl
  schoolbell,openssl
  nessusd,openssl
  mutt,openssl
  libssl0.9.8,openssl 0.9.6-2
  gnus,openssl
  dovecot-common,openssl
  courier-ssl,openssl
  courier-pop-ssl,openssl
  courier-imap-ssl,openssl
  ca-certificates,openssl
  apache2-threaded-dev,openssl
  apache2-prefork-dev,openssl
  apache2-common,openssl
Dependencies:
0.9.8a-7ubuntu0.3 - libc6 (2 2.3.4-1) libssl0.9.8 (2 0.9.8a-1) zlib1g (2 1:1.2.1) ca-certificates (0 (null)) ssleay (3 0.9.2b)
0.9.8a-7build1 - libc6 (2 2.3.4-1) libssl0.9.8 (2 0.9.8a-1) zlib1g (2 1:1.2.1) ca-certificates (0 (null)) ssleay (3 0.9.2b)
Provides:
0.9.8a-7ubuntu0.3 -
0.9.8a-7build1 -
Reverse Provides:

```

Tks


B.R.
satimis

---

### Post by MJN on 2006-11-24
Great - now get securing! :)

---

### Post by satimis on 2006-11-25
Hi Mathew,

On 
Step 2: Make a key and a certificate for the web server:
[http://www.vanemery.com/Linux/Apache/apache-SSL.html](http://www.vanemery.com/Linux/Apache/apache-SSL.html)

encountered following problem;

# cp mars-server.crt /etc/httpd/conf/ssl.crt```

cp: cannot create regular file `/etc/httpd/conf/ssl.crt': No such file or directory
```

# cp mars-server.key /etc/httpd/conf/ssl.key```

cp: cannot create regular file `/etc/httpd/conf/ssl.key': No such file or directory
```

# cp my-ca.crt /etc/httpd/conf/ssl.crt```

cp: cannot create regular file `/etc/httpd/conf/ssl.crt': No such file or directory

```

Whether I need to run;
mkdir -p /etc/httpd/conf/ssl.crt
mkdir -p /etc/httpd/conf/ssl.key

TIA


B.R.
satimis

---

### Post by MJN on 2006-11-25
SUbstitute **apache2** for **httpd** in those paths and you'll be set...

I'm not sure if there's a **conf** either - I've got **ssl** on mine - so you might need to create a conf or ssl directory yourself.

It doesn't really matter where you put the keys (within reason) - just as long as you reference them correctly in the config later on.

Mathew

---

### Post by satimis on 2006-11-25
Hi Mathew,

> SUbstitute **apache2** for **httpd** in those paths and you'll be set...

I tried it before.

$ ls -l /etc/apache2/ | grep conf```

-rw-r--r-- 1 root root 12728 2006-11-14 19:07 apache2.conf
-rw-r--r-- 1 root root 12728 2006-11-22 18:30 apache2.conf.original
-rw-r--r-- 1 root root  7534 2006-11-09 20:24 apache2_conf.txt
drwxr-xr-x 2 root root  4096 2006-11-22 18:25 conf.d
-rw-r--r-- 1 root root   367 2006-11-25 17:31 httpd.conf
-rw-r--r-- 1 root root   268 2006-11-14 19:11 httpd.conf.original
-rw-r--r-- 1 root root    45 2006-11-23 23:07 ports.conf
-rw-r--r-- 1 root root    10 2006-11-09 20:07 ports.conf.original
```

$ ls -l /etc/apache2/conf.d/```

total 8
-rw-r--r-- 1 root root 619 2006-07-27 02:01 apache2-doc
-rw-r--r-- 1 root root  24 2006-10-17 12:38 charset
```

No conf directory there.

Either I have to create
$ sudo mkdir -p /etc/apache2/conf/ssl.crt
$ sudo mkdir -p /etc/apache2/conf/ssl.key

Or to creat
$ sudo mkdir -p /etc/httpd/conf/ssl.crt
$ sudo mkdir -p /etc/httpd/conf/ssl.key

Which way will be more suitable?

Others noted with tks.


B.R.
satimis

---

### Post by MJN on 2006-11-25
The first (apache2) - it's the 'new' location for Apache config files (on Debian-based systems). I'd still use **ssl** instead of conf though and just keep your keys/certs in there (it's clear to you then what's in there) - anything else that might require seperate files would likely use it's own directory (conf.d is more for directives as opposed to files).

Mathew

---

