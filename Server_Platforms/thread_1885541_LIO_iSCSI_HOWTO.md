---
title: "LIO iSCSI HOWTO?"
date: 2011-11-23
forum: Server Platforms
---

### Post by pneumatic on 2011-11-23
Does anyone know how to get the new LIO iSCSI target up and running?  The SCST seemed much better in that they had actual documentation and didn't require registration to download management tools but they appear to have pissed off Linus.

So now we're stuck with LIO, which has no documentation.  I've downloaded, compiled and installed kernel 3.1.2 in order to take advantage of this blessed new native iSCSI target but have no idea how to begin.  The lio-utils are supposed to be here:

git.kernel.org/pub/scm/linux/storage/lio/lio-utils

But this does not exist...  Here's the project website:

[http://www.linux-iscsi.org/wiki/Target](http://www.linux-iscsi.org/wiki/Target)

Anyone?

---

### Post by pneumatic on 2011-11-23
A potential "nevermind"... all of the documentation out there indicates that I need lio-utils but these are now deprecated in favor of rtsadmin:

[http://www.linux-iscsi.org/wiki/RTSadmin](http://www.linux-iscsi.org/wiki/RTSadmin)

I'll leave this thread here as a placeholder for google search "lio iscsi howto", since there are none for the latest iteration.

---

### Post by pneumatic on 2011-11-23
Digging more on trying to get this going and I found this:

[http://comments.gmane.org/gmane.linux.scsi/69966](http://comments.gmane.org/gmane.linux.scsi/69966)

I agree that this project is doomed and needs to be forked ASAP.  Linus made a poor choice here.

I hope SCST is still as good as they were before linus snubbed them.

---

### Post by pneumatic on 2011-11-23
I really tried but It looks like you can only get this to work if you pay for the commercial tools:

[http://www.spinics.net/lists/target-devel/msg00580.html](http://www.spinics.net/lists/target-devel/msg00580.html)

They indicate that lio-utils is deprecated and have since removed the source.  But they also indicate that lio-utils is required.  So you will wind up here (if you manage to fix their python2.5 dependency issues):

```
make[1]: Entering directory `/home/h2admin/rtsadmin/targetcli/build/targetcli-2.0rc1.4.g649ea1c'
dh_testdir
dh_testroot
rm -f build-stamp
/usr/bin/python2.6 ./setup.py --quiet clean
Traceback (most recent call last):
  File "./setup.py", line 21, in <module>
    import targetcli
  File "/home/h2admin/rtsadmin/targetcli/build/targetcli-2.0rc1.4.g649ea1c/targetcli/__init__.py", line 18, in <module>
    from ui_root import UIRoot
  File "/home/h2admin/rtsadmin/targetcli/build/targetcli-2.0rc1.4.g649ea1c/targetcli/ui_root.py", line 25, in <module>
    from tcm_dump import tcm_full_backup
ImportError: No module named tcm_dump
make[1]: *** [clean] Error 1
make[1]: Leaving directory `/home/h2admin/rtsadmin/targetcli/build/targetcli-2.0rc1.4.g649ea1c'
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2
```

So the new native iSCSI is only helpful for Rising Tide Systems - it is unusable by the community unless you pay them.

---

### Post by pneumatic on 2011-12-11
Just an update:

The scst project is still up-tp-date for the latest kernels.  I downloaded 3.1.4, applied the patches, compiled and installed the kernel and then compiled and installed the tools and everything works fine.  I have deployed the option as a pair of dual-primary HA servers using DRBD (you must use vdisk_blockio and nvcache 0 or active-active will not work) under VMware vSphere 5.

I am using a hardware raid1 with caching so performance is very good.  I can get 118 megabytes/second over gigabit, which is just shy of the theoretical max of 125 MB/s.

Thanks to the open source community, this setup has been deployed to production at 5 sites, saving us $30,000 over the chosen commercial solution.

---

### Post by ymmt2005 on 2012-06-09
Hi,

I just have blogged an article about LIO and targetcli.
[http://ymmt2005.blogspot.jp/2012/06/evaluating-lio-linux-iscsi-target.html](http://ymmt2005.blogspot.jp/2012/06/evaluating-lio-linux-iscsi-target.html)

---

