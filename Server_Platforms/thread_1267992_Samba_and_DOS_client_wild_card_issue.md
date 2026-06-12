---
title: "Samba and DOS client wild card issue"
date: 2009-09-16
forum: Server Platforms
---

### Post by d0lt on 2009-09-16
I'm having problems with DOS clients using the DEL *.* command from a DOS (not Windows) client to a Ubuntu 9.04 server version running Samba serving files and printers to DOS clients.  DEL file*.* also fails, not just *.*.

The delete doesn't work, and the error message returned to the DOS client is "file not found".  Deletes without wild cards work fine.  Deletes while logged on the server as the same user work as expected, so I think I have user/group permissions set up properly.  The problem does not happen in a DOS window running on a Windows Vista system, and I assume any other Windows box I connect, but that's an assumption.

Each client has DOS 6.22 running with Microsoft Network Client v3.0 for MS-DOS, over TCP/IP.

I tried different shares and configurations, some with all the various DOS name and case mangling options and as well on a share with just all defaults.

I've searched the forums here and at ubuntu.com, and googled.  I recall something like this from old LAN Manager installs, so I even dug through usenet groups posting from the 1990s, but no luck.  I'm remembering something about permissions all the way up to the root directory, or the share's mount point, but setting 777 all the way back to / doesn't work...

Any ideas?

---

### Post by rCXer on 2009-09-16
If you don't get an answer here the people at [this DOS fourm](http://www.bttr-software.de/forum/board.php) might be able to help.

---

### Post by d0lt on 2009-09-29
Ended up fixing it.  Some user/group permissions and group memberships were set up wrong.  In addition, some directories were created before we configured all the Samba configuration parameters for true DOS file naming and non-mangling of names.  We cleaned up the Samba conf, changed each set of files and directories, and everything is good.

---

