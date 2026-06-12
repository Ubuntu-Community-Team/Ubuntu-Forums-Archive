---
title: "Samba 3.2.xx or lower on Ubuntu 10.04"
date: 2010-03-03
forum: Server Platforms
---

### Post by Ares545 on 2010-03-03
Hi all,

I need to set up ssh/sftp/network shares all authenticating with AD. I want to use likewise to do the auth, but to mount the network shares I need to use an older version of samba so it can connect with likewise.

How can I go about installing an older version of samba onto this new distro of the OS?

I've tried installing the lenny and etch versions but I always get an error during install just saying that samba errored.

Any help please?

---

### Post by ICEB3AR on 2010-03-03
You could download the source of your prefered Samba Version: 
[http://www.samba.org/samba/ftp/]("http://www.samba.org/samba/ftp/")

and Compile it by your own:
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/compiling.html]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/compiling.html")

---

### Post by Ares545 on 2010-03-04
I followed the directions and after everything was complied and installed, the /usr/local/samba/sbin folder is empty...

Help?

---

### Post by ICEB3AR on 2010-03-05
Have there been any errors on install/compilation?

---

### Post by Ares545 on 2010-03-06
Didn't see any... just a couple warnings.

---

