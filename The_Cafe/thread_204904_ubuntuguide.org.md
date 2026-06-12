---
title: "ubuntuguide.org"
date: 2006-06-27
forum: The Cafe
---

### Post by ashrack on 2006-06-27
I would like an explanation of this:
[http://ubuntuguide.org/wiki/Dapper#Samba_Server](http://ubuntuguide.org/wiki/Dapper#Samba_Server)

Notice it says to install SAMBA and also SMBFS but looking over the SAMBA package in SYNAPTIC it already installs the package SMBFS:
> samba - LanManager-like file and printer server for Unix.
 samba-common - Samba common files used by both the server and the client.
 smbclient - LanManager-like simple client for Unix.
 swat - Samba Web Administration Tool
 samba-doc - Samba documentation.
 samba-doc-pdf - Samba documentation in PDF format.
 smbfs - Mount and umount commands for the smbfs (kernels 2.2.x and above).
 libpam-smbpass - pluggable authentication module for SMB/CIFS password database
 libsmbclient - Shared library that allows applications to talk to SMB/CIFS servers
 libsmbclient-dev - libsmbclient shared libraries
 winbind: Service to resolve user and group information from Windows NT servers
 python2.4-samba: Python bindings that allow access to various aspects of Samba
So why does it say to install both of them?

---

### Post by nixternal on 2006-06-27
at one point you may have to install both. it could have been added in as a dependency since that article was written. or it could be that the article has a typo. you could contact the owners of that site and ask them also. good luck!!!

---

### Post by woedend on 2006-06-27
whats the question exactly?
The last time I used dapper samba did not need smbfs....I was fighting with mounting a remote HD for a while before I realized that I needed smbfs installed.  If its now a dependency its a new thing.

---

### Post by ashrack on 2006-06-28
Its not a dependecy. Since after U install SAMBA U can still install SMBFS. 
But apperantly theres no need for it, since CIFS works great on my setup with only SAMBA installed

---

### Post by woedend on 2006-06-28
ah, i see.
smbfs is indeed not needed, unless you want to mount a remote HD using smbfs.  This was important to me because all of the good audio players(xmms,bmp,audacious..etc) don't support the samba protocol so won't play from a remote location using samba.  I had to use smbfs to mount it as a folder and play from there.  I think it should just come with samba, I really don't see a point in this separation.

---

### Post by ashrack on 2006-07-09
found another usage for SMBFS! Without it installed theres no man pages for cifs!!!

---

