---
title: "Sharing a second disk"
date: 2009-06-19
forum: Server Platforms
---

### Post by Vegan on 2009-06-19
On a server with a single disk /dev/sda is fine for a web server. If I add a disk, I expect it as /dev/sdb no problem.

So I am using SAMBA to share files with Windows clients. So how should I deploy the disk? I can make a symbolic link with ln, to a folder on the /dev/sda but I was wondering if SAMBA can make do without the symbolic link.

---

### Post by windependence on 2009-06-19
It's gonna see the second disk as whatever the volume name is. You can name the volume whatever you want.

-Tim

---

### Post by Vegan on 2009-06-19
So can SAMBA make do with a direct volume path?

---

### Post by cariboo on 2009-06-20
This is waht the output of smbclient  on my server looks like:

```
smbclient -L willy -U%
Domain=[APLUS] OS=[Unix] Server=[Samba 3.3.2]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (willy server (Samba, Ubuntu))
	images          Disk      mounted iso images
	stuff           Disk      whatever fits
	documents       Disk      documents and such
	music           Disk      tunes
	movies          Disk      Movies and TV
	print$          Disk      Printer Drivers
	HPLaserjet      Printer   laser printer
Domain=[APLUS] OS=[Unix] Server=[Samba 3.3.2]

	Server               Comment
	---------            -------
	RISKY                Windows computer
	WILLY                willy server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	APLUS                WILLY
```

The shares are spread out over 4 different hard drives. The drives are all mounted via /etc/fstab, the shares use the mount points, not the device labels.

---

### Post by Vegan on 2009-06-20
Here are a couple of configs I have in my smb.conf

[web-site]
path = /var/www
writeable = yes
force create mode = 0777
force directory mode = 0777
force user = nobody
force group = nogroup
guest ok = yes

[mp3]
path = /music
writeable = yes
force create mode = 0777
force directory mode = 0777
force user = nobody
force group = nogroup
guest ok = yes

So I was suspecting I would need to ln more disks.

---

### Post by windependence on 2009-06-21
Not very secure. Why 777 permissions?

-Tim

---

