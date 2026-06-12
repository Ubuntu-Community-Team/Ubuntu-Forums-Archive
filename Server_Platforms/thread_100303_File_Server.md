---
title: "File Server"
date: 2005-12-07
forum: Server Platforms
---

### Post by nocturn on 2005-12-07
I would like to set up a fileserver again... but I'm in a dilemma as how to go about it.

I used to have NFS with automount, and it works well but lacks any kind of security.

I already have a server, it is running OpenLDAP for user accounts and MIT kerberos for authentication (pam_krb5), I have SSO set up this way for Cyrus (SASL).

What I would really like is to have a FileShare system that uses the same framework.  

- Can I use Samba3 for this (it supports MS Kerberos)?
- What about NFSv4 on Breezy (support kerberos)?

Are there other alternatives?

---

### Post by nocturn on 2005-12-13
*bump*

---

### Post by Glut on 2005-12-13
You can use your PAM authentication and account management with NFS. So you don't necessarily need a version of NFS with authentication builtin, simply tunneling nfs will work fine with your setup.

You could use NFS v4, I have no experience with it so am not the best to ask in depth questions about it. 
There other more secure alternatives, though:
Linux enhanced SMB: [http://uranus.it.swin.edu.au/~jn/linux/smbfs/](http://uranus.it.swin.edu.au/~jn/linux/smbfs/)
OpenAFS: [http://www.openafs.org/](http://www.openafs.org/) which I'm told is difficult to setup.

My personal preference is to tunnel NFS over SSL, using an ssh tunneling tool such as OpenVPN or (at a very desperate pinch) stunnel or even ssh itself. [http://www.math.ualberta.ca/imaging/snfs/](http://www.math.ualberta.ca/imaging/snfs/)

---

