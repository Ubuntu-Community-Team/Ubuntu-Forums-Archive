---
title: "pam question on [success=2] pam_unix.so"
date: 2009-02-18
forum: Security
---

### Post by bagpussnz on 2009-02-18
Hi,
I have a number of users with broken authentication (e.g. ssh just returns a connection closed, who cannot run su -auth failed and cannot change their passwords)  (they are all running intrepid).

I know it is caused by a ubuntu update (but I haven't been able to track down which one - but have listed the only ones it can be at the end of this. I know this because these updates were applied on a working machine - mine - and it was broken afterward).

After investigation, the following changes fix their problems...
/etc/pam.d/common-account
Change: 
account	[success=**1** new_authtok_reqd=done default=ignore] pam_unix.so
To: 
account	[success=**3** new_authtok_reqd=done default=ignore] pam_unix.so

/etc/pam.d/common-auth
Change:
auth	[success=**1** default=ignore]	pam_unix.so nullok_secure
To: 
auth	[success=**2** default=ignore]	pam_unix.so nullok_secure

/etc/pam.d/common-password
Change:
password	[success=**1** default=ignore]	pam_unix.so obscure sha512
To:
password	[success=**2** default=ignore]	pam_unix.so obscure sha512

**My question is: what do the _success=_ values mean? and why does it break authentication?**

The list of updates that could have caused this are...

libck-connector0 (0.2.10-1ubuntu10)

consolekit (0.2.10-1ubuntu10)

dpkg-dev (1.14.20ubuntu6.1)

libgvfscommon0 (1.0.2-0ubuntu2)

gvfs (1.0.2-0ubuntu2)

gvfs-backends (1.0.2-0ubuntu2)

gvfs-bin (1.0.2-0ubuntu2)

gvfs-fuse (1.0.2-0ubuntu2)

hal-info (20090128-0ubuntu1~intrepid2)

kde-icons-oxygen (4:4.1.4-0ubuntu1~intrepid1)

kdelibs5-data (4:4.1.4-0ubuntu1~intrepid1)

kdebase-runtime-data-common (4:4.1.4-0ubuntu1~intrepid1)

kdebase-runtime-data (4:4.1.4-0ubuntu1~intrepid1)

libpam-ck-connector (0.2.10-1ubuntu10)

libpq5 (8.3.6-0ubuntu8.10)

libxine1-bin (1.1.15-0ubuntu3.1intrepid1)

libxine1-misc-plugins (1.1.15-0ubuntu3.1intrepid1)

libxine1-ffmpeg (1.1.15-0ubuntu3.1intrepid1)

libxine1-plugins (1.1.15-0ubuntu3.1intrepid1)

libxine1-x (1.1.15-0ubuntu3.1intrepid1)

libxine1-console (1.1.15-0ubuntu3.1intrepid1)

libxine1 (1.1.15-0ubuntu3.1intrepid1)

rhythmbox (0.11.6svn20081008-0ubuntu4.3)

sudo (1.6.9p17-1ubuntu2.1)

kdelibs-bin (4:4.1.4-0ubuntu1~intrepid1)

kdelibs5 (4:4.1.4-0ubuntu1~intrepid1)

kdebase-runtime-bin-kde4 (4:4.1.4-0ubuntu1~intrepid1)

kdebase-runtime (4:4.1.4-0ubuntu1~intrepid1)

khelpcenter4 (4:4.1.4-0ubuntu1~intrepid1)

kmix (4:4.1.4-0ubuntu1~intrepid1)

ksnapshot (4:4.1.4-0ubuntu1~intrepid1)

python-kde4 (4:4.1.4-0ubuntu1~intrepid1)

Regards,
Ian.

---

### Post by jaraco on 2011-06-07
I have this question too. Where is this apparently newer syntax documented?

---

### Post by islandlinux on 2011-08-21
When set to 2 it means skip the next 2 rules.

---

