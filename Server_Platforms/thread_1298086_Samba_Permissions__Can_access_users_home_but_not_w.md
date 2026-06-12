---
title: "Samba Permissions:  Can access users home but not write to the share directories?"
date: 2009-10-22
forum: Server Platforms
---

### Post by photoman355 on 2009-10-22
Hi 

I'm tearing my hair out trying to figure out what's going wrong.  

Am setting up samba with webmin for the 1st time and have been following the webmin wiki instructions.  My setup allows me to access the home directory of the logged on windows user and read/write files.  However my problem is that I can navigate to the share directories I setup via webmin but cannot write to them.  I can only guess that my permissions are incorrect.

My setup:  OS Ubuntu Server 8.04LTS

Users and groups have been setup in the System>Users & Groups module, each with their own manually assigned home directory.  Groups have been setup with no password and other than that everything uses default settings.

Samba has been setup to automatically sync with unix users and as stated was setup following the webmin wiki.  Windows Network settings seem to work and security has been set to User Level.  Authentication has been set to use encrypted passwords.  File Share Defaults are set as default.

Each share has been set to writeable but other than that I am using the default settings for both Security & Access Control and File Permissions.

Can anyone help?

---

### Post by photoman355 on 2009-10-22
Woo hoo, cracked it.  Good old Knightwise came to the rescue again.  

I'd been messing around with the unix users so changed them back and followed his post on setting up samba with webmn.  Worked like a charm.

[http://www.knightwise.com/content/view/301/9/](http://www.knightwise.com/content/view/301/9/)

---

