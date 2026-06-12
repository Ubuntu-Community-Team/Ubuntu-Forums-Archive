---
title: "Samba and LDAP"
date: 2008-08-22
forum: Server Platforms
---

### Post by whitemts on 2008-08-22
Hello,
I just configured a Ubuntu x64 server.  I have Samba installed and I have shared out a directory on a RAID 5 12TB drive.  I can connect to the share via a Windows Vista machine on my network by using the Samba user I setup.  I would now like to install LDAP configured with my Windows 2003 Active Directory servers.  I tried following a couple of docs I found online and it is somewhat of a nightmare.  Can anyone offer any advice?

I need to share out my 12TB Share to a group of users authenticating against AD.

Thank you for any help,

---

### Post by bab1 on 2008-08-22
Indeed, reading the doc's will give you a headache.  :-)  But you have to do it to understand.  I would make the Ubuntu host a member server in the AD domain.  The users should be able to use AD for authentication.  I believe you will need to understand "winbind".  This will allow the Samba username/passwords to be stored in AD.  See the official Samba site for the official documentation and a great white paper with the title "Samba 3 by example".

---

### Post by whitemts on 2008-08-25
Thank you for the help, I basically wish I was never born at this point!

---

