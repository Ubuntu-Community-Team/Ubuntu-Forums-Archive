---
title: "Why there is no update of ClamAV in the Ubuntu repositories?"
date: 2006-09-06
forum: Server Platforms
---

### Post by aixo on 2006-09-06
Hi!

On 8 August a serious update of ClamAV was published: denial of service on corrupted UPX-packed executables. As ClamAV is widely used on mail gateways to protect MS Windows machines behind the gateways from their mail receiving users, this update is quiet important. Also, ClamAV is used for such protection on FTP and file (Samba) servers.

The other distros I kwow quiet well have integrated the update in short time, adressing the needs of administration of such servers - especially without the obligation to look for it anywhere else and without the risk of incompatibilities of dependencies.

But after almost one month, there is no such update in the Ubuntu repositories. Please correct me if I am wrong, but I understood that Ubuntu wants to place the server version of Drapper Drake LTS as an serious alternative to the professional "big" distributions. If so, why isn't there any update of ClamAV?

With best regards, Frank

---

### Post by jimwillsher on 2006-09-13
(First posting got deleted!)

Yes I agree. I could go and download the clamav sources and compile them - but isn't this totally against the ethos of Ubuntu?

---

### Post by asmpro on 2006-10-19
I have already contacted Debian maintainer of original package (Maintainer: Stephen Gran <sgran@debian.org>), which assured me he has nothing to do with the debian package.

In the meantime another serious security flaw has been found in clamav package, so I would like to ask Ubuntu maintainer of this package to update it.

If this is the wrong place to ask, please let me know :)

---

### Post by boz on 2006-11-06
Has there been any progress on this important update?  I'm still using Dapper so if it's out for Edgy are there plans to port it to Dapper as well?  If not, I'm going to download the source code and install it myself.  I'm personally not afraid of getting any viruses myself, but I connect to a Windows network regularly and I don't want to spread any I may accidently come across.

---

