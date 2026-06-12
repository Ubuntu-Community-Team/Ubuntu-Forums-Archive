---
title: "rpc_wait_bit_killable process status with nfs based homes"
date: 2010-07-09
forum: Server Platforms
---

### Post by N-t-F on 2010-07-09
Hello everyone!

I have a serious issue with NFS, that I first described in the Desktop Environment section because I thought it was a Gnome issue. Here is the thread: [http://ubuntuforums.org/showthread.php?t=1526520]("http://ubuntuforums.org/showthread.php?t=1526520").

Basically, some applications, but not all of them, freeze for users whose home directory is served through NFS. When checking in the System Monitor, such frozen applications are tagged as "rpc_wait_bit_killable".

Examples of applications that freeze:
- Gnome interface (the desktop icons take about an hour to appear and the environment is still not usable after that)
- Open Office
- Firefox
- Mupad (mathematics non-free application)

Examples of applications that seem to work fine:
- XFCE interface
- Gimp
- Gedit
- Kile
- Terminal and command-line applications within it

If I redirect home directories to local folders, everything works well, even for users authenticated through LDAP on the server. On the other hand, users who authenticate locally through shadow accounts but have their home served by NFS do experience applications freezing.

I think the problem is on server's side because connecting clients to my old Slackware nfs server works.

Server: Ubuntu 10.04 Server (64 bits), using NFSv3
Client: Ubuntu 10.04 Desktop (32 bits)

I don't really know what to try now and would really appreciate advice or clues.

PS: here's my /etc/exports, just in case...
```
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#

# NFSv3 (en attendant mieux)
#/home  -rw,sync,no_subtree_check,root_squash 192.168.1.*
/home  192.168.1.0/255.255.255.0(rw,sync,no_subtree_check,root_squash)
# NFSv4 (to be confirmed)
#/home   -rw,sync,no_subtree_check,root_squash,sec=krb5 192.168.1.*

```

Thank you. :)

---

### Post by N-t-F on 2010-07-19
Hello again. I have asked the question in the other thread because other have participated there, but I guess it is more in line with this sub-forum's theme : has anyone here managed to setup a working NFS server using Ubuntu Server Edition 10.04 ? :???:

---

