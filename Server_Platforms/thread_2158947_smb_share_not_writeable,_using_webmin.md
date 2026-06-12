---
title: "smb share not writeable, using webmin"
date: 2013-07-01
forum: Server Platforms
---

### Post by jamurphy on 2013-07-01
I have a ubuntu server (servera) with a share created by webmin (\\servera\mv).  It is not read-only.

I have a lubuntu client (clientb) with webmin installed - and I'm trying to create a mount (permanent) pointing to the server share.

When I create it using default permission settings, files that I create from clientb (using 'touch' for instance) end up having -rw-r----- and directories that I create end up with drwxr-x---.  Does anyone know why I can't get it to create files with -rw-rw---- and directories with drwxrwx---?

When I try changing the **File permissions** setting in webmin from 'default' to 0660 or 660, I get the following error:
 [h=3]Failed to save mount : '0660' is not a valid octal file mode[/h]or 
[h=3]Failed to save mount : Remount failed :
WARNING: CIFS mount option 'fmask' is deprecated. Use 'file_mode' instead.WARNING: 'file_mode' not expressed in octal.mount error(22): Invalid argumentRefer to the mount.cifs(8) manual page (e.g. man mount.cifs)[/h]Thanks,
Jay

---

### Post by volkswagner on 2013-07-02
Do you get the same result when creating files via file browser from <network> as you do when using touch?

What does the share definition look like in smb.conf?  Perhaps you need to use "create mask" and "directory mask" directives.

What does your mount command look like?  You may want to use the "uid=1000,gid=1000" options as well (where 1000 is your userID from /etc/passwd, and gid is your groupID from /etc/group).

---

