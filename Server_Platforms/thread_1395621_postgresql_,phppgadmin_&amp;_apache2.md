---
title: "postgresql ,phppgadmin &amp; apache2"
date: 2010-02-01
forum: Server Platforms
---

### Post by Drenriza on 2010-02-01
I have an remote server running, with postgresql 8.3.9, phppgadmin 4.1.3-0.1 and apache2. I have never used either programs before, and im having trouble figuring out how to start phppgadmin. i have tryed [http://ip-address/phppgadmin](http://ip-address/phppgadmin) but that says

Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.10 with Suhosin-Patch Server at ip-address Port 80

Anyone who can help me out?
Thanks on advance:D

---

### Post by Drenriza on 2010-02-01
when ido su - postgres on my server it ask for a password, but i have not defined any password. So does it have some kind of default password?

---

### Post by Drenriza on 2010-02-01
I think i have changed the password for the postgre user. Using
sudo -u postgres psql postgres
\password postgres
new password: xxxxxxx
re-type password: xxxxxxx

then i connected using sudo su - postgres (password) and now iam
postgres@cristianserver:~$

(su - postgres did not work for some reason)

---

### Post by Drenriza on 2010-02-01
Im trying to edit a file to allow remote control of the server.

sudo chmod 777 /var/lib/pgsql/data/pg_hba.conf ( i wanted to do this to get rights to edit the file, as i did not have my default)
then it asks for
[sudo] password for postgres:
i enter the password i defined and it says
Sorry, try again.
???????????????? Something ive missed?

what i wanted to do in /var/lib/pgsql/data/pg_hba.conf was adding a line
host all all x.x.x.x/24 trust (work network)
host all all x.x.x.x/xx trust (my home network)

So hopefully i would be able to remotely connect to the sql server.

---

