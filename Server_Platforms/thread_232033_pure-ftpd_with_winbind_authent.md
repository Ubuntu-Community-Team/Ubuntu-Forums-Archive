---
title: "pure-ftpd with winbind authent"
date: 2006-08-08
forum: Server Platforms
---

### Post by mynameisjohn on 2006-08-08
hi all.

i installed pure-ftpd the other day and (having finally discovered how the config works - linking files to command arguments) i want to set it up to allow windows passwords to authenticate with it, but not allow local unix user accounts.

my samba setup is fully operational, i can login to my ubuntu server using windows passwords if i want, and can see a full list of domain users etc.

my config works through k-meleon but i'm not 100% confident of my pam file and was hoping someone could cast an objective eye over it. :D

anyway, here's the file (it is rather short)

/etc/pam.d/pure-ftpd

```
auth    requisite       pam_winbind.so
account requisite       pam_winbind.so

# standard
##auth    required        pam_shells.so
##account required        pam_unix.so
session required        pam_unix.so

```

any advice greatly appreciated.

thx

mnij

---

