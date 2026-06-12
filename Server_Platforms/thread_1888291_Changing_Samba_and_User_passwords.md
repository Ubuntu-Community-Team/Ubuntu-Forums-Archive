---
title: "Changing Samba and User passwords"
date: 2011-11-29
forum: Server Platforms
---

### Post by edmundjc on 2011-11-29
I have an 11.10 server built in a VM with the purpose of having a quickly deploy-able LAMP server.  All passwords are generic, and are intended to be changed upon deployment.  The /var/www folder is being shared to a 'webdev' user (so named in both the system users and the samba users), but when I go to change the passwords, I lose sharing access.  I've changed both the user password (first) and the samba user password (second) to the same thing, and seem to get no access.

Is there something I am missing?  I am guessing that maybe samba does not know the new user password, and therefore cannot gain access to the folder.

The smb.conf file looks like this:
[COLOR=Blue]workgroup = default
security = user
username map = /etc/samba/smbusers

...
[www]
comment = Apache shared Samba folder
path = var/www
browsable = yes
writeable = yes
write list = webdev
read only = no
valid users = webdev
create mask = 0777[/COLOR]

And I have an smbusers identifying 'webdev' as 'webdev'


Any help would be fantastic.  Also, I am sure some of this may need clarifying.

Thanks!
-Jer

edit: The offending log entry:
[2011/11/29 00:30:43.438429,  1] smbd/service.c:678(make_connection_snum)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED

---

### Post by edmundjc on 2011-11-29
Ok, so apparently, I have appropriate access from another computer that I haven't tried yet.  It looks like the issue is either cached credentials on my Windows machines or perhaps they are blocked by the server for too many failed attempts? (does Samba do that?)  If so, how would I clear that?  I've cleared the creds. on the Windows machines, but still no access.

---

