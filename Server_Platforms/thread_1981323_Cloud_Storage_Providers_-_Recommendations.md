---
title: "Cloud Storage Providers - Recommendations?"
date: 2012-05-16
forum: Server Platforms
---

### Post by anonymouschief on 2012-05-16
Hello,

May I please have recommendations for Cloud Storage providers whose drives I can mount to my server. Please recommend solutions that meet the following conditions:

[LIST]
[*]No API-type connection methods.
[*]I would like all my file management features to work on it e.g mv, cp, mkdir, rm, rmdir, cat, tail, grep.
[*]No web inteface to access the drive, just native drive mounting as if the drive is local to my machine.
[*]No Dropbox, Google or Box.net hacks
[/LIST]

I used to use a service from ThePlanet, stopped using it, ThePlanet got acquired by Softlayer, and that Cloud Storage product was discontinued.

I need this for home use, I will only need about 20GB of storage max.

---

### Post by cmont899 on 2012-05-16
You could get a VM from any cloud provider and server up some iscsi.

---

### Post by anonymouschief on 2012-05-16
> **cmont899 said:**
> You could get a VM from any cloud provider and server up some iscsi.

Maybe an iSCSI host would do, as long as I can easily mount that drive so that it appears to be local to my server. I do not want to have a second server. I would have to then manage 2 servers. Another suggestion?

---

### Post by Cheesemill on 2012-05-16
I haven't used them myself, but I have been recommended [http://www.evbackup.com/](http://www.evbackup.com/) by people at work.

The provide sshfs access so you can just add an entry in your fstab and have the remote storage mounted in your local filesystem.

---

### Post by Habitual on 2012-05-16
> **Cheesemill said:**
> I haven't used them myself, but I have been recommended [http://www.evbackup.com/](http://www.evbackup.com/) by people at work.

The provide sshfs access so you can just add an entry in your fstab and have the remote storage mounted in your local filesystem.

fuse-over-amazon (s3fs) in use over here mounting a few s3 bitbuckets.

---

