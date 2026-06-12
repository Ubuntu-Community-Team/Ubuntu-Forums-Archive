---
title: "OpenLDAP &amp; Samba Integration"
date: 2013-01-08
forum: Server Platforms
---

### Post by OmegaHarvest on 2013-01-08
Hey

I'm currently in the process of setting up a test network with some core services for authentication. I've got OpenLDAP working perfectly now and am currently working my way through the following guide to integrate Samba: [https://help.ubuntu.com/12.04/serverguide/samba-ldap.html](https://help.ubuntu.com/12.04/serverguide/samba-ldap.html)

I've reached the 'Adding Samba LDAP objects' section and have since found an acknowledged bug that the configure.pl is missing from the smbldap-tools package. From what I can see this script simply generates some conf files.

I just wondered if anyone else has had this issue before, and how they have got round it. Are these even essential if I have already loaded the schema and can add the samba-related attributes to user accounts?

Although I have found the 12.04 documentation excellent for getting me setup, some of it implies former knowledge and a noob like me struggles easily ;). 

If anyone has any tips I'd be very grateful.

Thanks

---

### Post by IJselflearner on 2013-02-20
Hi,
 
I had the same issue as you had but somehow managed to solved it.
We're you not able to execute smbldap-populate?
What I did was to locate the file smbldap.conf.gz in /usr/share/doc/smbldap-tools/, copy the file to /etc/smbldap-tools/ then unzip it. You can now configure smbldap.conf and smbldap_bind according to your environment. -hope this help. kindly reply if this helped.
 
But right now my problem is I can't add existing LDAP user and new user to my samba server. I'm partly missing some additional configurations.
 
It somehow took so long to gather ideas in this forum, no one somehow bother to share their ideas. We are experiencing limited support from others who may have had the proper configuration.
 
 
Self Learner
-IJ-

---

### Post by ranger12 on 2013-02-20
I have a question, what tool did you use to try and add a Samba user to ldap?

---

### Post by IJselflearner on 2013-02-21
Hi Ranger12,
 
Thanks for the reply.
 
I'm completely new to Ubuntu Server. I just explore and try some configuration to setup a server.
 
I have no idea on the tool to use to add Samba user to LDAP. Should I configure something more to execute adding Samba user to LDAP? sorry, i am really new. 
 
I followed this  guide [https://help.ubuntu.com/12.10/serverguide/samba-ldap.html](https://help.ubuntu.com/12.10/serverguide/samba-ldap.html) til adding an existing LDAP user to my new LDAP-backed Samba, where i got stuck. This was included in the guide "*The smbpasswd utility can do this as well (your host will need to be able to see (enumerate) those users via NSS; install and configure either libnss-ldapd or libnss-ldap)*" but I have no idea how to configure this.
 
Hope you can enlighten me with this.
 
Thank you!
 
-IJ-

---

