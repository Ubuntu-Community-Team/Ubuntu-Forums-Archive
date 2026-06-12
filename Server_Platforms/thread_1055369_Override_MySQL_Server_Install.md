---
title: "Override MySQL Server Install?"
date: 2009-01-30
forum: Server Platforms
---

### Post by Geek42 on 2009-01-30
I am building a set of systems that all use a central MySQL server or it's replication servers. These MySQL systems do not run any other service of note, and that's fine, they are working perfectly and adding remote users works great.

The problem I am experiencing is with the package management on the other servers. Many packages require me to install the mysql-server package on the server in order for me to install the tool itself(examples include mediawiki and rsyslog-mysql). Since these systems are often running in a virtual(OpenVZ in this case, but it's not the issue), I have limited space I want to give them, and even installing mysql-server is a waste of space and time and could add things to the system that will give me problems later.

Assume that each of these is a clean install of a minimal-server setup of Ubuntu 8.10 server(it's actually less then that, a debootstrap that has almost nothing running). So any package I want to install will have a bunch of dependencies to install and I don't want to figure out each one.

So, with a package that thinks it needs a database installed locally, is there a process I can follow to allow me to install the application and not have it install mysql-server and it's dependencies on the system? I can deal with setting it up to do the remote database, and already have for a number of the items I've used, but the ones that I have had not problem with have been ones I installed from source(PowerDNS, MediaWiki is currently from source, but I would prefer to use the package).

Any suggestions?

---

### Post by JamesMcT on 2011-01-13
Just a bump.  I'm experiencing this exact same problem.  I do not want mysql-server installed on this box, instead I want to use an existing remote server.

Is there a way to let apt know that I don't want this package and don't care?

---

### Post by Robert Kelly on 2011-01-22
This works:
sudo apt-get --no-install-recommends install mediawiki

---

