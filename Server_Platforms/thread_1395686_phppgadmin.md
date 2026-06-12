---
title: "phppgadmin"
date: 2010-02-01
forum: Server Platforms
---

### Post by Drenriza on 2010-02-01
Im trying to run phppgadmin, on postgresql 8.3 and apache2.

Ive done

sudo -u postgres psql postgres
\password postgres
new password: xxxxxxx
re-type password: xxxxxxx
(dont know if this is 100% correct)

/etc/postgresql/8.3/main/pg_hba.conf
host all all x.x.x.x/xx trust (work)
host all all x.x.x.x/xx trust (home)

vim /etc/postgresql/8.3/main/postgresql.conf
listen_addresses='*'

/etc/init.d/postgresql restart

iptables -A INPUT -p tcp -s 0/0 --sport 1024:65535 -d 10.10.29.50  --dport 5432 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp -s 10.10.29.50 --sport 5432 -d 0/0 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT

Then i write
[http://ip-address/phppgadmin](http://ip-address/phppgadmin),
403 error You don't have permission to access /phppgadmin on this server.
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.10 with Suhosin-Patch Server at ip-adresse Port 80

how do i gain permission.


EDIT1.
got a friends help, needed to edit
sudo vim /etc/apache2/sites-enabled/phppgadmin

EDIT2.
The password for postgres (the postgressql default user) does not work when i want to gain access to the server through phppgadmin. Is this common?

EDIT3.
$ sudo -u postgres createuser -D -A -P mynewuser
$ sudo -u postgres createdb -O mynewuser mydatabase 
Solved EDIT2.

---

