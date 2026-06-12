---
title: "Problems with libc6 update"
date: 2013-04-21
forum: Ubuntu Development Version
---

### Post by Billxyzzy on 2013-04-21
I have been trying to update my system for a few days now.  Total failure.
Here is the message I get:
A copy of the C library was found in an unexpected directory:
  '/lib/x86_64-linux-gnu/libm-2.17.so.dpkg-new'
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library or get it out of
'/lib/x86_64-linux-gnu' and try again.

dpkg: error processing /var/cache/apt/archives/libc6_2.17-0ubuntu5_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.17-0ubuntu5_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Because of this error no updates are posssible.  
Is anyone else seeing this?
What is the workaround?
Have filed a bug report but nothing yet.
Thanks

---

### Post by cariboo on 2013-04-21
Have you checked to see if /lib/x86_64-linux-gnu/libm-2.17.so.dpkg-new exists, and removed it if it does, like the error message suggested?

---

### Post by Billxyzzy on 2013-04-21
Yep I have removed it several times along with the -tmp file.
As soon as I try to update it is back.  Not shure how to permanetly remove those files.
I still think this is a system problem and need a proper fix

---

### Post by Billxyzzy on 2013-04-21
My memory has failed.  I thought that there was a feature in synaptic to allow pinning a pariticuar item and it will not be updated.
I have just forgotten the steps for pinning.  I think then the rest of the update would be ok.
Need a few suggestions here.
We are so close to release I just wonder what is going on with updates right now.
I will just run with the ver 17 kernel for now and let it go at that.
I will just abandon raring soon and move on.

---

