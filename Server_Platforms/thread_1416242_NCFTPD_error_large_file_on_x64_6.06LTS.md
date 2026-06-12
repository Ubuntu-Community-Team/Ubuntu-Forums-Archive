---
title: "NCFTPD error large file on x64 6.06LTS"
date: 2010-02-25
forum: Server Platforms
---

### Post by prodsacnetworking on 2010-02-25
Hi, I'm unable to download large files from ftp. 

The ftp server is: NCFTPD.

My server is: 
[SIZE="1"]
Version:
istributor ID:	Ubuntu
Description:	Ubuntu 6.06.2 LTS
Release:	6.06
Codename:	dapper
Linux morpheus 2.6.15-55-amd64-server #1 SMP Tue Dec 1 18:31:51 UTC 2009 x86_64 GNU/Linux[/SIZE]

when I download, it gives an 131 error unknown.

I tried the same file on a 32 b server, same version of all except 32 instead of x64.

any ideas?

---

### Post by prodsacnetworking on 2010-03-11
it's an known problem with the x64 version.

add: 

sendfile-io=no

in the general.cf

---

