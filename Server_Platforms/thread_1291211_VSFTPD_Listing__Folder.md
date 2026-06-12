---
title: "VSFTPD Listing / Folder"
date: 2009-10-14
forum: Server Platforms
---

### Post by Johnsie on 2009-10-14
Hi,
    I'm trying to set up vsftpd to restrict users so that they can only see their home directory. I want every Ubuntu user on the system to to be restricted this way.

My problem is that one user account is working fine for this, but another account is showing the entire file system starting from the / folder and everything below that instead of taking them to the users /home/user folder


Can anyone help me with this?

Thanks.

---

### Post by Lars Noodén on 2009-10-14
FTP is designed, in the context of today's network, where it can only be safely used for read-only, without login or passwords.  

If you want secure connections, then the package OpenSSH-server is the one to use and the protocol SFTP (not FTPS or FTP).  The task you describe comes up often enough.  See step 6 in [SFTP on Ubuntu and Debian in 9 easy steps ](http://blog.markvdb.be/2009/01/sftp-on-ubuntu-and-debian-in-9-easy.html")
[INDENT]
[FONT="Courier New"]Match group sftponly
ChrootDirectory /home/%u
X11Forwarding no
AllowTcpForwarding no
ForceCommand internal-sftp[/FONT]
[/INDENT]

For the example above, you'll need a user group called 'sftponly' and those who shall have their access restricted to their home folder be members of that group.

---

