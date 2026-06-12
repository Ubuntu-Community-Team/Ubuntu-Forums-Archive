---
title: "vsftpd - users that have no /home directory?"
date: 2011-06-23
forum: Server Platforms
---

### Post by Jose Catre-Vandis on 2011-06-23
Hi

I have vsftpd running on my server, opened up for local users.

When I set up samba on the server I added two users to enable them to access the samba shares on the server.

1. If either of these users try to login into the ftp server they are refused, because they don't have a home directory. Do they have to have one for vsftpd?

2. How do you set up a user list (if you can)for vsftpd that doesn't rely on system users? (I found that you could add a file for users, but this only gave user names and not passwords, so am guessing this was a restrictive list on system users?)

3. How do you restrict directories in vsftpd (I don't mean the /home directory only). Seems everything on the server is available? I have a partition at /media/data - this is all i want to be sharing via ftp.

Thanks

---

### Post by craigcrawford114 on 2011-06-23
I would recommend pure-ftpd instead. I found it the easiest to setup.

You can easily create virtual users and have them run under the ftpuser:ftpgroup.

---

