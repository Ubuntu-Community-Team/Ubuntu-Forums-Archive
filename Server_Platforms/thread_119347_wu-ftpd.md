---
title: "wu-ftpd"
date: 2006-01-19
forum: Server Platforms
---

### Post by ebmar on 2006-01-19
I've installed wu-ftpd on my server.
The users have ALL rights.

They can browse and delete whatever they want.

How can i add some security?

I want them only to read whats in their homefolder.

and also with ssh.

It's a webserver so they don't need much permissions.

They also have all permissions to mysql..


Someone very nice person here who can help me?

---

### Post by mvaniersel on 2006-01-19
If you give them SSH accounts, they'll automatically have SFTP accounts and then you don't need a separate FTP server.

---

### Post by ebmar on 2006-01-20
It worked with sftp, but they still have permissions to read other folders.

---

