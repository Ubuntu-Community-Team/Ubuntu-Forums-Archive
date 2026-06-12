---
title: "apache2-ssl-certificate: command not found"
date: 2007-12-02
forum: Server Platforms
---

### Post by mitjab on 2007-12-02
when i try
sudo apache2-ssl-certificate -days 365
i get
apache2-ssl-certificate: command not found

i search in forum but no working solution found. Everyone said that this is bug. Howto fix it?

EDIT:
is ok if i use instead:

openssl req -new -newkey rsa:2048 -keyout key.pem -x509 \
-set_serial 1000 -days 365 -out cert.pem

---

### Post by MJN on 2007-12-02
On 6.06? It's on mine:

[B] $ ls -l /usr/sbin/apache2-ssl-certificate
-rwxr-xr-x 1 root root 910 2007-08-16 23:29 /usr/sbin/apache2-ssl-certificate[/B]

..or is the bug that the command is there but it doesn't work?

Mathew

---

### Post by mitjab on 2007-12-02
mitjab@server:$ ls -l /usr/sbin/apache2-ssl-certificate
ls: /usr/sbin/apache2-ssl-certificate: No such file or directory


i do not have this, what i must install that this will work?

thx

---

### Post by MJN on 2007-12-03
It comes from the apache2-common package which presumably you have got.

You are running 6.06 like your profile says aren't you?

Mathew

---

### Post by nowhere@cox.net on 2008-01-02
I am having the same problem. I am running Gutsy server, Apache is installed and I have been using/developing with it no problem. I have the a2enmod program in /usr/sbin but apache2-ssl-certificate is nowhere to be found on my system.

What's up?

Thanks,
Eric

---

### Post by MJN on 2008-01-02
It's missing from Feisty onwards - see [https://launchpad.net/ubuntu/+source/apache2/+bug/77675](https://launchpad.net/ubuntu/+source/apache2/+bug/77675) for some discussion/workarounds (in particular the extraction of the two files from the Edgy release, manual SSL creation and/or the use of make-ssl-cert).

Mathew

---

