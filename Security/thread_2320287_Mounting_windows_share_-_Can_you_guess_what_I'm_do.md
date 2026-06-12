---
title: "Mounting windows share - Can you guess what I'm doing wrong?"
date: 2016-04-12
forum: Security
---

### Post by biosboy4 on 2016-04-12
mount -t cifs //10.10.31.10/Astra\ Bessemer /media/ark/destinationfolder -o credentials=/etc/smb-credentials

returns: for more details see mount(8)

Pretty much any version of this command tells me the same thing. What am I doing wrong?

---

### Post by TheFu on 2016-04-12
a) I always put options before the source and targets.  That is shown in the mount manpage.
b) I always quote funny file/directory names. Yes, the escape SHOULD work, but ... 
c) I NEVER allow spaces in directory or file names.  It just isn't worth this hassle.
d) mount is a restricted command - if you aren't using **sudo** before it, it will not work.
e) almost all Unix commands have either debug or verbosity settings. mount does. At a -v before the options to get more detailed output.  Many commands allow multiple -vvvv to get more verbose output. This is a general knowledge thing for all Unix commands.

For cifs mounts, I use these options: [FONT=Courier New]cifs,rw,iocharset=utf8,file_mode=0666,dir_mode=0777,credentials=/etc/samba/winsrv.credentials[/FONT] with the credentials file root.root and 600 permissions.  Since I use autofs, there isn't a copy/paste method to show the exact mount command. Sorry.  

If the source storage machine isn't Windows, please consider using NFS.  NFS storage feels like native Unix storage and it is faster than Samba.  NFS v4 can be much more secure than any CIFS storage too, with Kerberos server-to-server authentication.

---

