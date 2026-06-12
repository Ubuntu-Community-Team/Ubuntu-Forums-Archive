---
title: "MySQL issues"
date: 2010-12-23
forum: Server Platforms
---

### Post by cisbrane on 2010-12-23
I'm having a lot of trouble with MySQL on 10.04 for some reason...

I have tried to reinstall serveral times, and the server just has issues starting up or shutting down.

I have done:

apt-get --purge remove mysql-server
reboot
apt-get install mysql-server

when things are getting setup it says:

start: Job failed to start


sudo service mysql status
mysql stop/waiting


service mysql start
start: Job failed to start

NOTE: i run all this from a root shell by doing sudo su -.

I can't get this thing to startup at all which is really strange.
Some of my other trouble was that it would just hang when stopping or starting forever, and I found a bug for this, but it said it was fixed, but mine doesn't seem to be.

any ideas?

---

### Post by cisbrane on 2010-12-23
I guess I will be answering my own issue:

It turned out purge removing the server was not enough.
These additional steps were taken to ensure everything mysql related was gone, and then when I reinstalled it seemed to work fine.

sudo apt-get --purge remove mysql-server
sudo apt-get --purge remove mysql-client
sudo apt-get --purge autoremove

reboot

sudo apt-get install mysql-server

---

