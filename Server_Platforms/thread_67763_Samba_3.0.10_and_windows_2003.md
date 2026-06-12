---
title: "Samba 3.0.10 and windows 2003"
date: 2005-09-21
forum: Server Platforms
---

### Post by nobodii on 2005-09-21
Dear all,

I have Ubuntu Hoary as server, and did a apt-get install samba for the samba server.

The samba version appeared to be 3.0.10-Ubuntu.

However, when I tried to access the samba shared from a M$ Server 2003, I have these errors in the samba log:

[2005/09/21 16:33:10, 0] lib/util_sock.c:read_socket_data(384)
  read_socket_data: recv failure for 4. Error = Connection reset by peer

From the windows, this is the error:
\\servername is not accessible.  You might not have permission to use this
network resource.  Contact the administrator of this server to find out if
you have access permissions.  The request is not supported. 

Access from M$ Windows XP is fine.

Any advice? Thanks in advance!

Best regards,
KS

---

### Post by sattard on 2006-01-03
I have the same problem. 
Anyone got a solution for this problem?

Sebastian

---

### Post by grendelkhan on 2006-01-03
what do you have the sercurity set to?  if it's user, make sure you have created users to access the samba shares.

---

### Post by LordHunter317 on 2006-01-03
[QUOTE=grendelkhan]what do you have the sercurity set to?  if it's user, make sure you have created users to access the samba shares.[/QUOTE]If it's .NET 2003 with SP1, you'll just have to upgrade Samba.

---

