---
title: "proftpd, permission denied, uid and permissions okay"
date: 2008-08-05
forum: Server Platforms
---

### Post by altonbr on 2008-08-05
With proftpd enabled, I've had ftp users using my server for quite some time.

Users are added via 'adduser', they are chrooted into their home and their public directory is in /public_html/ using 'mount --bind'.

However, I'm having a problem with a user.

They have the same uid as the folder and files contained and the user is getting permissions denied errors when trying to upload a file.

I checked this with 'id <username>'

Using SSH/SFTP works fine though.

What could be going wrong?

---

### Post by altonbr on 2008-08-06
Anyone?

Could it be permissions at a lower level are blocking the user from editing his files?

I can't tell.

---

### Post by RealPSL on 2008-08-06
That is a possibility but you seem to have ruled this out already by saying that ssh/sftp works. proftpd could also be the source of the restriction by denying uploads but it is impossible to tell without seeing your configuration.

---

