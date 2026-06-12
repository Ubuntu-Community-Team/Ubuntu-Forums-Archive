---
title: "Share one folder as NFS3 and NFS4"
date: 2010-09-22
forum: Server Platforms
---

### Post by J&#7885;hn on 2010-09-22
Hi All.

Before I go prodding about on this server does anyone have any experience of sharing a single folder over NFS3 (for compatibility) and NFS4 (for newer clients)??

---

### Post by arrrghhh on 2010-09-22
Can you run both servers at the same time...?  That would be my question, since NFS is now kernel-supported...

---

### Post by the_original_billq on 2010-09-22
The kernel-based nfsd supports NFS versions 2, 3, and 4 by default.  One export is all you need, regardless of the NFS version you want available.

The NFS client dictates which version will be used for the mount.

The examples provided in /etc/exports under 10.04 are a bit misleading.  The gss/krb5i is a deprecated syntax.  Please read the exports man page to see the full syntax of the file.  The secure mount methods are only supported under NFSv4, which is why they are segregated in the examples found in /etc/exports. Using secure mounts is not a requirement of NFSv4, however, so the examples for NFSv2 or 3 will also work for 4.

See also the man pages for mount and nfsd, which is where I found the answers above... :-)

-Bill

---

### Post by arrrghhh on 2010-09-22
Ah, thanks for clearing that up.  Should've checked the man page myself obviously... That also makes a lot of sense, and is a very good decision made by the devs!

---

### Post by J&#7885;hn on 2010-09-27
Thanks for clarifying that, Bill. I didn't know it was handled by the client. That will make migration much easier!

---

