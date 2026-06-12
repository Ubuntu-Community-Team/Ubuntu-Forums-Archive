---
title: "VSFTPD and Apache Setup Question"
date: 2008-04-20
forum: Server Platforms
---

### Post by darwin2kx on 2008-04-20
I am working with the LAMP stack that comes with the server. I also have installed vsftpd, and am trying to get a specific configuration working. Been through about a dozen or so different and unhelpful tutorials.

I would like to have multiple system accounts able to login through to the FTP, and have access to the same www directory ( /var/www ). I would like the setup to be so any files uploaded are owned by www-data, since I can add all the users that need access to the www-data group. I think that covers everything. Does anyone have a config that would work for this purpose?

---

### Post by ikonia on 2008-04-21
all you need is to auth against /etc/passwd which as I recall is the default option in vsftpd.

put any users you want to have write access in the www-data group, then make sure the directory is writeable by the www-data group.

Job done.

---

### Post by darwin2kx on 2008-04-21
I have modded the directory to be owned by www-data user/group. My user account is a member of the same group. 


vsftpd.conf

listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=077

chown_uploads=YES
chown_username=www-data

#nopriv_user=ftpsecure


And yet, I still get a 550 Create directory operation failed

What else do I need?

---

