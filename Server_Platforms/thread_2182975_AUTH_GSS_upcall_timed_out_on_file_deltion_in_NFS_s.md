---
title: "AUTH_GSS upcall timed out on file deltion in NFS shares"
date: 2013-10-23
forum: Server Platforms
---

### Post by deephack on 2013-10-23
Hello all,

I have an Ubuntu 12.04 LTS server providing NFS home shares for a few Ubuntu 13.10 desktop computers.  I'm finding that everything is working fine until I try to delete a file from my home folder, when I do the progress bar sits at 0% for a very long time in Nautilus and eventually the file is deleted. If I use rm from the command line I get no errors and no pause.  In the server logs I get the following during this process.

```
Oct 23 10:41:42 office kernel: [406568.806179] RPC: AUTH_GSS upcall timed out.
Oct 23 10:41:42 office kernel: [406568.806179] Please check user daemon is running.
Oct 23 10:42:00 office kernel: [406586.839669] RPC: AUTH_GSS upcall timed out.
Oct 23 10:42:00 office kernel: [406586.839669] Please check user daemon is running.
Oct 23 10:42:18 office kernel: [406604.883364] RPC: AUTH_GSS upcall timed out.
Oct 23 10:42:18 office kernel: [406604.883364] Please check user daemon is running.
```

Incidentally the same was happening when the desktop machines were running Ubuntu 13.04.

I set my system up using the instructions from this blog post [http://www.danbishop.org/2012/06/02/ubuntu-12-04-ultimate-server-guide/](http://www.danbishop.org/2012/06/02/ubuntu-12-04-ultimate-server-guide/)

/etc/exports (on server)
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
/export *(rw,fsid=0,crossmnt,insecure,async,no_subtree_check,sec=krb5p:krb5i:krb5)
/export/home *(rw,insecure,async,no_subtree_check,sec=krb5p:krb5i:krb5)
/export/Maven *(rw,insecure,async,no_subtree_check,sec=krb5p:krb5i:krb5)

```

I'm using autofs as per the blog post on the client machines to mount the home shares

/etc/auto.master (On client machines)
```
## Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#
#/misc  /etc/auto.misc
#
# NOTE: mounts done from a hosts map will be mounted with the
#       "nosuid" and "nodev" options unless the "suid" and "dev"
#       options are explicitly given.
#
#/net   -hosts
#
# Include /etc/auto.master.d/*.autofs
#
#+dir:/etc/auto.master.d
#
# Include central master map if it can be found using
# nsswitch sources.
#
# Note that if there are entries for /net or /misc (as
# above) in the included master map any keys that are the
# same will not be seen as the first read key seen takes
# precedence.
#
#+auto.master
/home /etc/auto.home
/nfs /etc/auto.nfs
```

/etc/auto.home (On client machines)
```
* -fstype=nfs4,rw,hard,intr,sec=krb5 office.mavennetwork.co.uk:/home/&
```

Have I done something wrong in my set up or is this a bug?  (I'm guessing I did something wrong.)

Thanks!

---

### Post by deephack on 2013-11-02
Okay done some further tests on this and my Kerberos/NFS4 setup seems just fine.  I can't reproduce this problem from anywhere other than within Nautilus.  In addition if I enable the ability to delete files without moving them into the recycle bin then the problem doesn't occur.

I'm going to investigate this further but I'm starting to think that this is a Nautilus bug.

UPDATE

Just created this Launchpad bug
[https://bugs.launchpad.net/ubuntu/+bug/1247407](https://bugs.launchpad.net/ubuntu/+bug/1247407)

---

