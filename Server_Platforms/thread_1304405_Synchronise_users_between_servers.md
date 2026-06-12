---
title: "Synchronise users between servers"
date: 2009-10-29
forum: Server Platforms
---

### Post by bluntknife on 2009-10-29
Hi,

I've created a 2 node Active/Passive Ubuntu server cluster using Heartbeat and DRBD to mirror the data disks.
I'm hosting a web service on the active server that hosts websites and virtual servers.
The problem is, when a new website or virtual server is created a new local user is created (and can be viewed in the /etc/passwd /etc/shadow files).  Now, when the web service fails and the passive node becomes the active node the websites that were created on the previously active node aren't available.  This is becuase the users that were created in association with the new websites do not exist on the newly active node. (I hpoe this is clear!!!)

To solve this problem I need to 'merge' not overwrite the user information between the servers.  I don't think RSYNC is the right tool for the job because I believe it would overwrite the files.

Is it possible to resolve this issue?

Many thanks in advance.

---

### Post by bluntknife on 2009-10-30
Sorry to bump - nobody has had this requirement before?

---

### Post by samosamo on 2009-10-31
I don't get it. Why don't you use a directory service like OpenLDAP?

---

### Post by bluntknife on 2009-10-31
> **samosamo said:**
> I don't get it. Why don't you use a directory service like OpenLDAP?

The web service I'm using is virtualmin / webmin / usermin and I'm not sure whether if they will create a local user or utilise openldap.
I've not used openldap before. When the ubuntu server is configured to use it does it stop creating local users and groups?  Virtualmin automatically creates local users and groups when you setup a new domain or virtual server.

Regards.

---

### Post by capscrew on 2009-10-31
> **bluntknife said:**
> The web service I'm using is virtualmin / webmin / usermin and I'm not sure whether if they will create a local user or utilise openldap.
And therein lies the problem.  Webmin has it's downsides.  It alters some fundamental aspects of Debian/Ubuntu.> 

I've not used openldap before. When the ubuntu server is configured to use it does it stop creating local users and groups?  Virtualmin automatically creates local users and groups when you setup a new domain or virtual server.

Regards.
OpenLDAP is pretty raw for most users (e.g. lots of manual configuration).  No, it does not stop you from manually creating local users, and this is probably what you should be doing; creating local users on both hosts. 

When you create a local user, the user is assigned a UID and a GID.  If you are careful you can match the login/pass with the UID/GID on both hosts.  

I do this for a small network I manage.  There are only 4 users with no centralized management.  The users also have information stored at a centralized file server.  It works exactly like a domain except I have to match all the user IDS on all the hosts myself.

I use the CLI tools (adduser or useradd) to create the users and match the UID/GID's, so I would have no specific methods or advice when using webmin.

---

