---
title: "Cloud sync solution"
date: 2016-05-07
forum: Ubuntu Cloud and Juju
---

### Post by ScorpioTiger on 2016-05-07
I'm looking at how I might use an Ubuntu VPS as a cloud sync solution. I'd like to be able to sync a number of Windows PCs and Android phone to the VPS. The intention is to make files available across multiple devices and also provide a backup solution. Can anyone recommend how I might achieve this?

---

### Post by TheFu on 2016-05-07
1) rsync over ssh - bidirectional can be dangerous if there are conflicts.  I pick a source system and know when that box pushes changes to all other machines to avoid this issue.  Every OS that has networking has an rsync + ssh solution.
2) owncloud (only if you use a VPN too!!!!!!)
3) Seafile
4) Pydio

[https://www.reddit.com/r/sysadmin/comments/40226g/owncloud_vs_seafile_vs_pydio/](https://www.reddit.com/r/sysadmin/comments/40226g/owncloud_vs_seafile_vs_pydio/) has a comparison discussion.
Or just use sftp on all the remote systems. Life is much easier without Windows for stuff like this.  Then you can use sshfs on all the Linux and Android devices to directly access the files.

---

### Post by DuckHook on 2016-05-07
*Thread moved to **Ubuntu Cloud and Juju** as the more appropriate forum.*

---

### Post by ScorpioTiger on 2016-05-21
> **TheFu said:**
> 1) rsync over ssh - bidirectional can be dangerous if there are conflicts.  I pick a source system and know when that box pushes changes to all other machines to avoid this issue.  Every OS that has networking has an rsync + ssh solution.
2) owncloud (only if you use a VPN too!!!!!!)
3) Seafile
4) Pydio

[https://www.reddit.com/r/sysadmin/comments/40226g/owncloud_vs_seafile_vs_pydio/](https://www.reddit.com/r/sysadmin/comments/40226g/owncloud_vs_seafile_vs_pydio/) has a comparison discussion.
Or just use sftp on all the remote systems. Life is much easier without Windows for stuff like this.  Then you can use sshfs on all the Linux and Android devices to directly access the files.

Thanks for your thoughts. I've created a server with ownCloud and going through the process of seeing what it can do. Got it using Amazon S3 with encryption for storage which is a good start. It's a shame that the Firefox Sync extension no longer works with ownCloud; a big step backwards.

---

