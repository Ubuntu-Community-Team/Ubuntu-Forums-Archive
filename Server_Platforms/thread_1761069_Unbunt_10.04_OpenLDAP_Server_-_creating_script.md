---
title: "Unbunt 10.04 OpenLDAP Server - creating script"
date: 2011-05-17
forum: Server Platforms
---

### Post by robertomason on 2011-05-17
I'm working on a script, creating an OpenLdap server. I'm using Ubuntu Documentation from Ubuntu 10.04 OpenLdap. In building the script I've followed step by step the instructions. When it comes to the ACL portion, I run the following as described in the documentation

These scripts were taken and modified from albanianwizard.org

[http://albanianwizard.org/ubuntu-10-0-4-lucid-lynx-ldap-configuration-the-working-how-to.albanianwizard0](http://albanianwizard.org/ubuntu-10-0-4-lucid-lynx-ldap-configuration-the-working-how-to.albanianwizard0)

ldap_bind: Server is unwilling to perform (53)
    additional info: unauthenticated bind (DN with no password) disallowed

Admittedly, I have little knowledge of LDAP. I'm trying to create a script that I can share with community. 
I'm including two scripts

1.  	[create-rmasonfamily-info.sh]("http://ubuntuforums.org/attachment.php?attachmentid=192482&stc=1&d=1305668104")
   be aware, it does an apt-get install, and then does the configuration. You have to define early on the your domain, $dc1 and $dc2

2. 	[remove_ldap.sh]("http://ubuntuforums.org/attachment.php?attachmentid=192483&stc=1&d=1305668494")
 remove ldap and all configuration files, and reinstalls openLdap

---

