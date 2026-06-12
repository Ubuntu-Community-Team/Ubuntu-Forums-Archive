---
title: "Newb: How do I use 'gnome-user-share' (X-posted)"
date: 2007-10-01
forum: Server Platforms
---

### Post by Smartin on 2007-10-01
Hi,

Sorry to cross post this but I'm not getting any joy in the General help forum...

I'm just trying to get to grips with Ubuntu 7, having come from OSX...

I have installed gnome-user-share but how on earth do I use it?

I have tried to create a folder named 'Public' and then set it to be shared but I get an error relating to NFS and SMB services not being installed.

I particularly want to use gnome-user-share because it's using WebDav rather than NFS/SMB.

What am I not understanding?

Thanks!

Simon

---

### Post by dantrevino on 2007-10-04
Did you separately install gnome-user-share?  Because it seems to me you're accessing the 'shares-admin' tool under the administration menu.  That tool (as you've noticed) is for sharing via NFS or SMB.  gnome-user-share, as you mention only depends on apache2 being installed.

Dan

---

### Post by Smartin on 2007-10-11
> **dantrevino said:**
> Did you separately install gnome-user-share?  Because it seems to me you're accessing the 'shares-admin' tool under the administration menu.  That tool (as you've noticed) is for sharing via NFS or SMB.  gnome-user-share, as you mention only depends on apache2 being installed.

Dan

Dan,

Didn't realise you had responded...

I now have apache2 running fine but still don't know how to interface with gnome-user-share.

The shares-admin tool you mention is not hooking up to GUS. It's samba and NFS only as you say...

Any thoughts?

Simon

---

