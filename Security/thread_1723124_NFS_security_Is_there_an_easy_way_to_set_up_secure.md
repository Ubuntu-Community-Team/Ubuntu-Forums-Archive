---
title: "NFS security: Is there an easy way to set up secure NFS/filesharing?"
date: 2011-04-06
forum: Security
---

### Post by KIAaze on 2011-04-06
Hi,

NFS is vulnerable when the client cannot be trusted since the user can use su USER to access the data of any user.
Is there a way to prevent this?

I read about the all_squash and root_squash options, but none of them seem to really allow for a secure network share with multiple users and untrusted clients.

So the only really secure options seem to be SMB/CIFS, SSHFS and "NFS over SSH".
What is the most secure considering clients cannot be trusted and you don't want users to access the data of other users? (And it should of course be possible for the clients to mount the user's home directory located on the server on login)

I think this is an important problem to solve for companies&co to finally start using GNU/Linux servers instead of Windows servers. Or do the Windows filesharing systems have the same security issues (i.e. users can gain full access to all files on the server)?

Stuff I found:
NFS:
[http://www.troubleshooters.com/linux/nfs.htm](http://www.troubleshooters.com/linux/nfs.htm)
[http://tldp.org/HOWTO/NFS-HOWTO/security.html](http://tldp.org/HOWTO/NFS-HOWTO/security.html)
SSHFS:
[http://fuse.sourceforge.net/sshfs.html](http://fuse.sourceforge.net/sshfs.html)
NFS over SSH
[http://www.math.ualberta.ca/imaging/snfs/](http://www.math.ualberta.ca/imaging/snfs/)
[http://www.crufty.net/Products/sNFS.html](http://www.crufty.net/Products/sNFS.html)
Debian request for packaging of it: [http://www.mail-archive.com/debian-wnpp@lists.debian.org/msg33759.html](http://www.mail-archive.com/debian-wnpp@lists.debian.org/msg33759.html)

---

### Post by bodhi.zazen on 2011-04-06
kerberos =)

---

### Post by KIAaze on 2011-04-06
Ah, thanks! :)

I looked up some info about kerberos and it seems to be what I was looking for.
But does it really fully protect against legitimate users with full root access on their clients? i.e. are there any permission checks after the authentication?

Links:
Kerberos+NFS: [https://help.ubuntu.com/community/NFSv4Howto#NFSv4%20with%20Kerberos](https://help.ubuntu.com/community/NFSv4Howto#NFSv4%20with%20Kerberos)
Kerberos+Samba: [https://help.ubuntu.com/community/Samba/Kerberos](https://help.ubuntu.com/community/Samba/Kerberos)

---

### Post by bodhi.zazen on 2011-04-07
The only things that I know of that can fully restrict the root user are

encryption
apparmor/selinux

---

