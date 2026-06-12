---
title: "SCIM related packages in breezy-backports"
date: 2005-11-09
forum: Ubuntu Backports
---

### Post by minghua on 2005-11-09
Hi jdong and backports developers,

I'm writing to summarize the situation of SCIM related packages.  There seems to be a far cry about the qualities of SCIM packages in breezy, so I figure it won't be long before somebody  post backport requests here.  But SCIM packages has some tricky dependencies, so I want to help the backports developers to make it right.

I don't feel this post as a request (as my opinion is we should wait a little while before starting to backport SCIM packages), but feel free to move it to the request subforum.

The SCIM packages in dapper are generally in a quite good shape, with the following three packages as the exception:

**scim-tables**:  0.5.4-1 is in Debian new queue, when it enters sid and gets ported to dapper, it should be good to be backported.

**scim-m17n**:  need to apply a patch and rebuild against new SCIM 1.4 ABI.  Malone bug #3633, Debian BTS bug #335957.  If nothing happens in a few days (I'll ping the Debian maintainer), I'll upload a patched version for dapper to REVU.

**mlterm**:  mlterm builds a binary package mlterm-im-scim which links to scim libraries.  The version in dapper still links to the old ABI.  The version in sid is good, so if MOTUs resync/merge mlterm, it should be good.  I'm not familar with this package, but I'll have an eye on it (and maybe help MOTUs).

So after these three packages get sorted out, dapper will have a consistent sets of SCIM packages, and we can backport them all together to breezy-backports.  I would suggest not to backport any single packages before they are all ready, as SCIM 1.0 and SCIM 1.4 packages are not compatible, and backporting only some will break others that existed in breezy (altough there are many complaints, they do work well for some users).

What do you think?

Ming, Debian scim (and a few other SCIM related packages) maintainer

---

### Post by jdong on 2005-11-11
Sure -- sounds awesome.

As soon as these start hitting Dapper, notify me!

---

### Post by minghua on 2005-12-27
After disscusion with jdong on IRC, it seems SCIM packages won't be backported to breezy.  A more detailed explanation: [http://lists.ubuntu.com/archives/ubuntu-backports/2005-December/000626.html](http://lists.ubuntu.com/archives/ubuntu-backports/2005-December/000626.html)

---

