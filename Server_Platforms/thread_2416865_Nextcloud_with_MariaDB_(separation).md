---
title: "Nextcloud with MariaDB (separation)"
date: 2019-04-16
forum: Server Platforms
---

### Post by aljames2 on 2019-04-16
I’ve read its best to separate the two onto separate servers.  Is this for security reasons?  What if the only application using the DB is Nextcloud should they still be on separate servers?

---

### Post by TheFu on 2019-04-17
> **aljames2 said:**
> I&#8217;ve read its best to separate the two onto separate servers.  Is this for security reasons?  What if the only application using the DB is Nextcloud should they still be on separate servers?

What is best depends on the size of your deployment and number of concurrent users and how you are deploying.  There are rules of thumb for when a separate, physical, DB server is best but no exact _you must use another server system_ mandate.

A properly secured server is secure whether the webapp and DB runs on the same machine or not.  If they are on the same machine, then the DBMS should only listen on the localhost interface.  If they are on different machines, then the DBMS should only allow traffic FROM the webapp servers and nowhere else by using the firewall for inbound and outbound connections.

I'm not confident enough to believe I can actually secure a php webapp, so I don't allow it to be available on the internet.  To access nextcloud, I require a full VPN or ssh-SOCKs proxy be used to get onto the LAN first.  But different networks will have different needs for security.  If I put a nextcloud instance onto some cloudy service, my security stance would be completely different.  Actually, I wouldn't know where to begin, since I don't believe there is any security when you put sensitive data on someone elses disks, on someone elses computer, at the end of someone elses network.  But that's me.  I have issues with data being outside my control.  My common sense doesn't allow me to get passed those issues.


IMHO.

---

### Post by aljames2 on 2019-04-30
What I’m looking to do is have a separate Nextcloud bare metal server box looking at a data folder on my separate LVM + EXT4 storage server.  I’m assuming all the nextcloud dependencies (apache2, PHP, mariadb, etc.) would live on the nextcloud box?

---

### Post by TheFu on 2019-04-30
> **aljames2 said:**
> What I’m looking to do is have a separate Nextcloud bare metal server box looking at a data folder on my separate LVM + EXT4 storage server.  I’m assuming all the nextcloud dependencies (apache2, PHP, mariadb, etc.) would live on the nextcloud box?

Nextcloud has network storage or you can keep the access to the network storage completely separate and setup NFS outside any nextcloud knowledge.  That's how I do it.  In general, I don't trust nextcloud with write access to files I keep elsewhere, but I'm happy for it to have read-only access limited to specific people.  A read-only NFS mount, controlled on the NFS-server, is how I handle this mistrust.

---

