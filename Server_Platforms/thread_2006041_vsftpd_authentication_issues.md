---
title: "vsftpd authentication issues"
date: 2012-06-18
forum: Server Platforms
---

### Post by gigaSproule on 2012-06-18
I've followed the guides in the Ubuntu help, but I cannot connect using my local user. I think there is a mistake in the help, in that it doesn't say to uncomment the local_enable=YES, which I have done

So to clarify, I can connect with anonymous and ftp, but I cannot connect with my user account. Does anyone have any idea what the problem could be?

EDIT: Managed to get more info - "500 OOPS: 421 Service not available, remote server has closed connection"
That message appears after entering the password.

---

### Post by gigaSproule on 2012-06-23
Does nobody have an answer? I'm connecting to the server fine via SSH and SMB, but not FTP (or at least through Filezilla).

Changed the protocol to SFTP and it seems to have worked. It's always the simple things...

---

