---
title: "Setting up synchronization with Samba"
date: 2010-07-14
forum: Server Platforms
---

### Post by neon401 on 2010-07-14
Hi

I have two 1TB hard drives, one in my Linux server (running Debian, but I thought I'd ask here anyway) and one in my Windows desktop.

What I would like is a file synchronization program that will automatically (or scheduled via cron) synchronize my hard drive on Linux with my hard drive on Windows via Samba.

How would I go about doing this?

I hope I made myself clear, thanks.

---

### Post by brettg on 2010-07-14
On which system do you want to run the sync daemon?

If you want to run it on the nix host then I would simply [mount the Windows drive using samba]("http://tuxnetworks.blogspot.com/2009/09/mounting-samba-shares.html").

Install smbfs;

```
sudo apt-get install smbfs
```

Put something like this in your fstab;
```

//ntserver/docs /mnt/samba smbfs username=docsadm,password=D1Y4x9sw 0 0
```

and then use rsync to sync the drives.

```
rsync -parv /mnt/samba /mnt/localhdd
```

Hope this helps

---

