---
title: "proftpd and symlinks"
date: 2009-02-10
forum: Server Platforms
---

### Post by shimrra on 2009-02-10
Hi
I have a little problem in setting up proftpd server. I have, say, /home/ftpdata as a default "jail" for ftp user. What I want to do is somehow add directories from other filesystems (and notably ntfs drives that ubuntu mounts automatically) so ftp user can browse and download files from them. Something like /home/ftpdata/music that actually is /media/disk_d/music. 
Symlinks won't work because they break when /home/ftpdata is chrooted.
I heard that *mount --bind* would help me. But I'm new to linux, not aware of the syntax and stuff. So I'm asking if you please could help me - what should I write in terminal to do the mount + what to put into /etc/fstab so these mounts are kept after reboot?

Thanks

---

### Post by cdenley on 2009-02-10
Add this line to the bottom of /etc/fstab, after your entry for /media/disk_d/music
```

/media/disk_d/music /home/ftpdata/music none defaults,bind 0 0

```
create the mount point
```

sudo mkdir /home/ftpdata/music

```
then mount it
```

sudo mount /home/ftpdata/music

```

---

### Post by shimrra on 2009-02-10
Thank you! Works like a charm

---

