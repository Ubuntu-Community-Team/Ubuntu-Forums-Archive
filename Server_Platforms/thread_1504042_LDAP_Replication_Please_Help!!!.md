---
title: "LDAP Replication Please Help!!!"
date: 2010-06-07
forum: Server Platforms
---

### Post by BrettFace on 2010-06-07
I have successfully installed Openldap and am able to authenticate to it, but I can not get the replication server operating correctly. I have followed all of the steps in doing so from this guide, [https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html#openldap-server-installation](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html#openldap-server-installation), but there are a few things i don't understand. when creating the consumer_sync.ldif file on the consumer server it says to replace ldap01.example.com to your server's hostname. would this be the provider or consumer? My porvider is [email]ldap@tech.local[/email] and my consumer is [email]ldap-backup@tech.local[/email].... so what one are they refurring to with the ldap01? And is there a way to push, or sync the two server manually? How do I know if they are backing up properly? How do I test? The information on the site is good but lacking for us less experienced. Any help would be very appreciated.

---

### Post by radarstreet on 2011-04-10
Did you ever find a solution to this problem? I am trying to do the same thing and have ran into this obstacle as well.

---

