---
title: "Problems with firebird server installation"
date: 2008-06-16
forum: Server Platforms
---

### Post by amester on 2008-06-16
Hi,

I just wanted to install Firebird server on an Ubuntu 8.04 machine. I installed it with this command:

sudo apt-get install firebird2.0-super

Everything seemed to be OK. So I typed:

sudo dpkg-reconfigure firebird2.0-super

and I enabled the server and set the SYSDBA password. After it I saw the following message:

* Firebird 2.0 server manager not running.
* Starting Firebird 2.0 server manager...

And nothing happens. I have waited about 1-2 minutes but still nothing.

Can anyone help?

(The above happend on another computer too, but strangly I could install firebird on a third one)


Attila Mesterhazy

---

### Post by mariuz on 2008-07-30
check the log file and also check if /var/run/firebird/2.0 is created when you start it 
see this related bug 
[https://bugs.launchpad.net/ubuntu/+source/firebird2.0/+bug/135582](https://bugs.launchpad.net/ubuntu/+source/firebird2.0/+bug/135582)


also is better to use firebird2.1 

[https://help.ubuntu.com/community/Firebird2.1](https://help.ubuntu.com/community/Firebird2.1)

---

