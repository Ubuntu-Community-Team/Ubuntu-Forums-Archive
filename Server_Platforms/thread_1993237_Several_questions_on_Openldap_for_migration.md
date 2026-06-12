---
title: "Several questions on Openldap for migration"
date: 2012-06-01
forum: Server Platforms
---

### Post by paco699 on 2012-06-01
Hello everybody,

First of all, sorry in advance for my approximate English.

I have several questions. Questions for which I did not find answer until today, despite one very large number of reading of docs, faqs, tickets etc. (I did not necessarily read everything, internet is so vast).

Presentation:
I have to migrate all the servers of the company, from ubuntu 10.04.3lts (package openldap 2.4.21) to ubuntu 12.04lts (package openldap 2.4.28).

Configuration:
Configuration of openldap, identical on all the servers (Masters and Slaves), configuration of dynamic type (with cn=config ), with reference ldap Masters in the config of slaves ; syncrepl (N-Way) Multi-Master mode.
All servers are VMs on kvm.


Questions:
Questions according to several scenarios:
- there are problems of synchronization between 2 Masters, if the one is in 2.4.21 and the other one in 2.4.28?
- there are problems of synchronization between 2 servers, if 1 Master is in 2.4.21 and 1/severals Slave(s) in 2.4.28?
- there are problems of synchronization between 2 servers, if 1 Master is in 2.4.28 and 1/several Slaves in 2.4.21?
- I want to do an update of part of the slaves servers. What it is better to use?: acl or in syscrepl? Which is the most flexible?

MDB backend:
- can one use now the backend-mdb new in "production mode" with openldap 2.4.28? Is it with good/enough stability? Or do I have to stay with the backend-hdb and migrate towards backend-mdb later?
- Is it pisible to migrate from backend-hdb towards backend-mdb for server in production, in the future? 

Tcmalloc:
- I placed tcmalloc in this file '/etc/init.d/slapd' as this "LD_PRELOAD=/usr/lib/libtcmalloc_minimal.so.0". Is it good? Is it the good place/file?
- where can I find track of its load (of tcmalloc)? How can I see the functioning of tcmalloc? In what file of log? The LSOF command no give nothing.
- it is indicated in the site "[http://code.google.com/.../google-perftools-1.8.3/README]("http://code.google.com/r/heybrowny-higmysql/source/browse/google-perftools-1.8.3/README?r=bf85e419619834120ab33c6358b6d16e833ee2ae&spec=svnadce3f5e52fd66eb901bb4e4287e28f7202a5599")" > "TCMALLOC_DEBUG=<level> -- the higher level, the more messages malloc emits". It is indicated that more the number increase and more tcmalloc verbose. But it is not indicated/informed has what corresponds the numeros (levels) of log and until how much?
-to use "TCMALLOC_DEBUG", I have to use "LD_PRELOAD=/usr/lib/libtcmalloc_minimal_debug.so.0" or keep "LD_PRELOAD=/usr/lib/libtcmalloc_minimal.so.0"?

Backups and restore:
-the opinions diverge. Indeed, to make a backup/restore, slapadd command is enough with the file created with slapcat? Or i need to integrate (with slapadd) at first the config file (cn=config file) and then the acl config file  and then the data of the users that were created at the first installation of openldap 2.4.21?

So, I installed and configured openldap in 2005 on a debian for the needs of a company but today many things changed and difficult to find itself there.

Thank you in advance for taking time and your answers.

Francois

---

### Post by highlandsun on 2012-10-09
backup/restore: slapcat/slapadd are the only tools needed for the job. "slapcat -n0" will backup the configuration. "slapadd -n0" will load a config.

back-mdb had a few small issues in 2.4.28. 2.4.33 is about to come out, it's looking quite stable there.

There are no major issues with mixing 2.4.xx releases for syncrepl, but it's best to upgrade everything to the latest code as soon as practical.

---

