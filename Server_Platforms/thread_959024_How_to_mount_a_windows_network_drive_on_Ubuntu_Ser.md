---
title: "How to mount a windows network drive on Ubuntu Server"
date: 2008-10-26
forum: Server Platforms
---

### Post by NeoGreen on 2008-10-26
I just installed and configured a Ubuntu 8.04 Server.  I installed LAMP and the Samba File Server.  I Know want to be able to access/mount a Windows Shared Network Drive.  Is this possible?  If so how?  Any advice will be appreciated. :)Thanks.

---

### Post by ezacon on 2008-10-26
My prefered way is:

Add this line to /etc/fstab:
```

//smbserver/sharename /mountpoint cifs credentials=/home/user/.smbpasswd,uid=user,gid=group 0 0

```

Create a file called .smbpasswd wich contains:

```

username=user
passwod=yourpass

```

Now you can mount your share with:

```
mount /mountpoint

```

---

### Post by david_lynch on 2008-10-26
> **ezacon said:**
> My prefered way is:

Add this line to /etc/fstab:
```

//smbserver/sharename /mountpoint cifs credentials=/home/user/.smbpasswd,uid=user,gid=group 0 0

```

Create a file called .smbpasswd wich contains:

```

username=user
passwod=yourpass

```

Now you can mount your share with:

```
mount /mountpoint

```

That works, but it's an old school way. I prefer to use autofs, to automatically mount such network drives on demand, and automatically unmount them after some configurable idle period.

I find that if windows "shares" are statically mounted for too long, they go stale and start having I/O problems.

---

### Post by Iowan on 2008-10-26
[Here]("http://ubuntuforums.org/showthread.php?t=288534") is a good How-To you should see.

---

### Post by NeoGreen on 2008-10-27
Thank you very much for the advice.  I will try them.  :)

---

### Post by alienprdkt on 2008-10-27
I use pmount to auto mount ntfs drives

sudo apt-get install pmount

sudo apt-get install ntfs-3g

reboot

If auto-mount failed you can try to mount your drive manually with this command:

sudo pmount-hal /dev/sda1 (or whatever drive you are trying to mount)

---

