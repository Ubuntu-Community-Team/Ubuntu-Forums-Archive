---
title: "new webserver - use edgy or dapper?"
date: 2006-12-19
forum: Server Platforms
---

### Post by at0mic on 2006-12-19
Hi,

If i were to build a new webserver for long term use, should i use dapper with LTS or edgy with the latest kernel and updates to software ? What exactly does LTS reflect and what exactly does the shortfalls of using edgy entail? Does using edgy have a shorter life on how long the repository database is kept updated?

---

### Post by nocturn on 2006-12-19
I'd recommend Dapper.

It will have 5 years of support on the server.
Edgy will have 18 months of security updates, BUT, you cannot skip releases, so when Edgy retires, you have to upgrade to Edgy+1 then to +2 etc.

I think there will be an upgrade path from Dapper to the next LTS.

---

### Post by az on 2006-12-19
You probably don't want the most cutting-edge LAMP stack running your server.  Use the simple-and-boring Dapper.

That being said, Dapper was released with apache2, mysql5 and php5 - which is pretty up-to-date.

Unless there is a specific web application that you want to run that requires something in Edgy, there is no reason to use Edgy as a web server.  Dapper will outlast Edgy in terms of support (security updates and bug fixes) and is better built for stability than Edgy.  I don't think there is that much difference in Edgy than in Dapper otherwise.

---

### Post by at0mic on 2006-12-22
Ok. so im sold on dapper.

Is there any known exploits for a LAMP server that only has port 80 accessible? Do i need an AV software installed? i dont think i do but i imagine this is highly debatable.

---

### Post by MrHorus on 2006-12-22
> **at0mic said:**
> Is there any known exploits for a LAMP server that only has port 80 accessible?


Of course - you will be vulnerable to any exploits that affect Apache since this is the underlying webserver.

Unfortunatly you have little choice but to suck it up and deal with it - it's part and parcel of running a publically accessable web server.

Make sure you have all the latest updates installed and regularly download and install any new ones, design rebust firewall rules and check your log files regularly.

The IDS of your choice might be worth investigating as well.

Also, if you only have port 80 open, how do you plan on connecting to the box for maintanance and administrative tasks?

---

### Post by technodigifreak on 2006-12-22
> **at0mic said:**
> Ok. so im sold on dapper.

Is there any known exploits for a LAMP server that only has port 80 accessible? Do i need an AV software installed? i dont think i do but i imagine this is highly debatable.

Unless you are running a public fileserver, you shouldn't need AV.

check apache.org for current known exploits, they usually stay on top of the latest issues.

---

### Post by at0mic on 2006-12-22
thnx guys.

port 80 is the only external acecss. i plan to run an internal ip restricted ftp backend using glftpd + ssh.

im also slightly considering running an LDAP service that is internal ip block restricted on it as well but with the box exposed to the world i dunno.

---

### Post by at0mic on 2006-12-22
thnx guys.

port 80 is the only external acecss. i plan to run an internal ip restricted ftp backend using glftpd + ssh.

im also slightly considering running an openLDAP service on it as well that is internal ip/port restricted.  but with the box exposed to the world i dunno. not recommended im thinking due to the personal infos that would be stored locally should port 80 and the box be comprimised somehow.

---

