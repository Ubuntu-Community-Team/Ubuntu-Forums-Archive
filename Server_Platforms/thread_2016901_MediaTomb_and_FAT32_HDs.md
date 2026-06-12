---
title: "MediaTomb and FAT32 HDs"
date: 2012-07-04
forum: Server Platforms
---

### Post by g2geo94 on 2012-07-04
I have an Ubuntu 12.04 Server 64 install setup with MediaTomb installed. On that server I also have a second hard drive (internal) formatted with FAT32 labeled "store" that has been a backup hard drive for me for quite some time (long before this server's establishing).

What I am wanting to do is something I would hope to be rather simple:
I want to set up a media server (through MediaTomb) using music located throughout the second hard drive. My problem? MediaTomb hasn't the permissions to access the hard drive. An "ls -l" tells me this:
```
drwxrwx---  44 root plugdev 16384 Dec 31  1969 store
```

Reading online I've noticed some have said that the user accessing the hard drive should be a part of the "plugdev" group, but there is no user for MediaTomb, nor do I know how to set one up. 

Obviously, I have tried "chmod -R 775 store/" but that just stalls for about a minute, then exits with no error, leaving store's permissions still the same as above.

So I ask, why is chmod unable to set the permissions for store, and, more importantly, how do I allow MediaTomb to read "store/"?

Your time is appreciated, and I thank in advance anyone who is able to provide to me any helpful information.

Regards,
Geoffrey

---

### Post by g2geo94 on 2012-07-16
As much as I'd really hate to bump, this is a matter I've found no other help on, and would like to address. I understand that it might seem trivial, but your help is appreciated nonetheless.

Thanks again,
Geoffrey

---

### Post by lukeiamyourfather on 2012-07-16
Don't use FAT32 unless there's a good reason for it. Instead use a Linux native filesystem like ext4. From there the ownership can be changed to a different user (with chown).

---

### Post by BalleClorin on 2012-07-16
I'd recommend against using MediaTomb in general. It has been dead upstream for years. Serviio and PS3 media server are the two DLNA servers I've found to work the best. The both have unofficial debs.

Running ps xau and grepping for mediatomb will tell you which user it runs under. Selecting the owner of a mounted drive can be done in fstab:
[http://serverfault.com/a/382566](http://serverfault.com/a/382566)

---

### Post by oldfred on 2012-07-16
Windows formats do not support ownership nor permissions. 

I also used FAT32 for backup, but lost a lot of backups as it does not support files over 4GB (I was saving as one large file) and has no journal so recovery is more difficult. It also does not support ownership & permissions which is ok for files that are just data, but will not work for anything system related.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[U]

[/U][]("http://ubuntu.swerdna.org/ubufat32.html")

---

