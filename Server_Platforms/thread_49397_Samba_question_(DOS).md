---
title: "Samba question (DOS)"
date: 2005-07-16
forum: Server Platforms
---

### Post by kirsche on 2005-07-16
Hello,

I know, it might not be the best forum for my question, but... 

I've got a Ubuntu server with samba running. everything works fine, but I have an annoying problem when I access the shares from DOS (PC-DOS or MS-DOS).

I map the drive, can see the files, copy, move everything, but if I try to run an executable (say ghost.exe), I get an error: "Bad command or file name"
I have to rename the file in order to execute it -> ren ghost.exe GHOST.EXE
Before I switched to Ubuntu, I used RedHat / Fedora - no problem.

Did anybody came accross this problem?
Thanks

---

### Post by alastair on 2005-07-16
This would appear to be something related to the way filename case is interpreted.

If I recall, there is at least one option, perhaps more, in the samba config file related to this - perhaps a tweak on this/these?

/etc/samba/smb.conf

and see the smb.conf man pages (samba-doc - /usr/share/doc/samba-doc/htmldocs/).

---

### Post by kirsche on 2005-07-18
Hi, 

I checked the man smb.conf (5):

case sensitive = yes/no/auto

    controls whether filenames are case sensitive. If they aren't, Samba must do a filename search and match on passed names. The default setting of auto allows clients that support case sensitive filenames (Linux CIFSVFS and smbclient 3.0.5 and above currently) to tell the Samba server on a per-packet basis that they wish to access the file system in a case-sensitive manner (to support UNIX case sensitive semantics). No Windows or DOS system supports case-sensitive filename so setting this option to auto is that same as setting it to no for them. Default auto.

I can successful rename the file in question, I just can't execute it before I rnemaed it...

---

