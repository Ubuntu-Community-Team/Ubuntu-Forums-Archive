---
title: "Problems with jailroot sftp and write permissions"
date: 2011-02-22
forum: Server Platforms
---

### Post by scangirl on 2011-02-22
Hi, I have a problem between a jail root (so a group of users can access through sftp to Apache directory (var/www) an not get out of this directory.

1. I have the group 'sftponly', I need to access / var / www for sftp (read only)

2. On the other hand I need that user www-data (Apache) is the owner or at least have write permissions in the same directory (/ var / www)

The problem comes when the two needs together, as from what I read, to do jailroot in a directory is necessary for the owner is root and any other user has write permissions on it.

If along the jailroot with write permissions then attempt to connect to the client via sftp throws me the following error:

"Error: Server unexpectedly closed network connection"

Permissions system User/group/Others doensn't work to me, so I tried it with ACL, but I have the same problem when I grant write permissions to the apache user.

Does anyone know how can I do for the user www-data can have write permission in the Apache directory and be able to create a user or group of users who are "locked"in this directory to enter sftp?

Thanks a lot!!

P.S.: I am using Ubuntu Server 10.04 LTS

---

### Post by mciverza on 2011-02-22
/var would need to be "world readable" i.e. readable by any user. Permissions from 'ls -lh' would be rwxr-xr-x
and /var/www should be rwxr-x--- or rwxr-xr-x 
the user that owns /var/www should be www-data 
and the group that owns it should be sftponly

that way  'ls -lhd   /var/www'  will output something like
drwxr-xr-x 2     www-data     sftponly     4.0K     2011-02-03 15:49     /var/www
the important bit is the first 3 columns:
drwxr-xr-x   www-data  sftponly

when members of the sftponly group log in, they will be able to read the contents of /var/www 
but the web server which runs as user www-data will be able to write to it.

---

### Post by scangirl on 2011-02-23
Hi mciverza, thanks for your reply!

I'm afraid that I have already tested with this privileges 
rwx r-x --x for /var directory
and 
rwx -xr --x for /var/www
and chown www-data:sftponly

But, when I connect to the server via filezilla, I have the same error:
    Network error: Software caused connection abort

But the problem still the same: the problem dissappear when I give the ownership directory to root and returns when I do chown for www-data.

I have this in my sshd_config to jailroot:

Subsystem       sftp    internal-sftp

Match Group sftponly
        ChrootDirectory /var/www
        ForceCommand internal-sftp
        AllowTcpForwarding no
        X11Forwarding no

Any other ideas?

Thanks a lot.

---

### Post by rudelgurke on 2011-02-23
And what is the problem doing - for your DocRoot:

/var/www as root:sftponly 660

And adding "www-data" to the sftponly group ?

---

### Post by scangirl on 2011-02-28
Hi rudelgurke, and thanks for your reply.

The problem is that write permissions are incompatible with chroot. (Throws the "Error: Server unexpectedly closed network connection" error)

I found a possible solution in another post [http://ubuntuforums.org/showthread.php?t=1664531](http://ubuntuforums.org/showthread.php?t=1664531) but I have Internet in my server and external access to it, and I think this solution is insecure...

Any other solution, please?

Thanks a lot.

---

### Post by scangirl on 2011-03-03
Solved!!

I finally succeeded, for example, for var/www, we have to do chroot to /var (to avoid conflict with write permissions for users other than root) as beams on the base directory, in this case, var. With this the user can enter sftp var directory and therefore to www, then you can lock the other directories with ACLs, and then I put the user in a group with the apache user to write in www.

I hope this is helpful for someone.

---

