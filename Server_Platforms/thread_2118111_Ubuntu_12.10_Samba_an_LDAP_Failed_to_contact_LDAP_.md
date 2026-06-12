---
title: "Ubuntu 12.10 Samba an LDAP: Failed to contact LDAP server."
date: 2013-02-20
forum: Server Platforms
---

### Post by IJselflearner on 2013-02-20
Hi Linux Professionals,

I'm a new member here and I am also new to Ubuntu Linux.

I'm trying to set up a Domain Controller in Ubuntu Server 12.10. I have successfuly followed the setup guide for Network Authentication in Ubuntu Server Guide, already configured OpenLDAP ([[COLOR=#444444]https://help.ubuntu.com/12.10/server...ap-server.html[/COLOR]]("https://help.ubuntu.com/12.10/serverguide/openldap-server.html")) and **[COLOR=#dd4814]Samba[/COLOR]** and **[COLOR=#dd4814]LDAP[/COLOR]** ([[COLOR=#444444]https://help.ubuntu.com/12.10/server...amba-ldap.html[/COLOR]]("https://help.ubuntu.com/12.10/serverguide/samba-ldap.html")) so far but got stuck along the **[COLOR=#dd4814]Samba[/COLOR]** Configuration, while including an existing **[COLOR=#dd4814]LDAP[/COLOR]** user:

~$ sudo smbpasswd -a user1

got this response -->

Failed to issue the startTLS instruction: Can't contact **[COLOR=#dd4814]LDAP[/COLOR]** server
New SMB password:
Retype new SMB password:
Failed to issue the startTLS instruction: Can't contact **[COLOR=#dd4814]LDAP[/COLOR]** server

I got no idea as to where I may have not configured or needed to configure.

Any idea or advice will be highly appreciated. also, if there was previous thread posted regarding this problem, kindly redirect me.

Thank you so much in advance. Hope you can help me with this.


Fr: Ubuntu Newbie. :smile:

---

### Post by luvshines on 2013-02-24
> **IJselflearner said:**
> 
Failed to issue the startTLS instruction: Can't contact LDAP server
New SMB password:
Retype new SMB password:
Failed to issue the startTLS instruction: Can't contact LDAP server


Looks like it's failing with TLS stuff. Maybe you haven't configured the TLS on the ldap server.
No problem, just try switching off TLS with 'ldap ssl = no' in /etc/samba/smb.conf and restart the samba service

---

