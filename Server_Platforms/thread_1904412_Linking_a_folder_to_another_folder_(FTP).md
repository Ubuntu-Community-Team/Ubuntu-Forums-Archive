---
title: "Linking a folder to another folder (FTP)"
date: 2012-01-04
forum: Server Platforms
---

### Post by kembar4 on 2012-01-04
Hey guys,

I'm using VSFTP and jailed my users into a certain directory under their home.

Example: /home/$user/downloads

What should i do, if i want to add an additional folder under the /downloads folder that links them to an external folder on another drive?

---

### Post by kembar4 on 2012-01-04
Anyone?

---

### Post by dazman19 on 2012-01-05
I think if you have chrooted jailed it, then its jailed.

you will have to undo the chroot on that folder. create the link, and put the security back for everything else accordingly.

Im no expert but chroot is generally a really tight way of securing files.

---

### Post by kembar4 on 2012-01-05
> **dazman19 said:**
> I think if you have chrooted jailed it, then its jailed.

you will have to undo the chroot on that folder. create the link, and put the security back for everything else accordingly.

Im no expert but chroot is generally a really tight way of securing files.


Would there be any alternative then?

I don't want users to be brought in directly to their home folders upon logging in the ftp.

I want them to stay in /home/user/application/userfolder

Then i want to link a folder from /home/admin/application/files to /home/user/application/userfolder/linktofilesfolder

---

