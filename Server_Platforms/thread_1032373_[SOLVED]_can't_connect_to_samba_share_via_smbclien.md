---
title: "[SOLVED] can't connect to samba share via smbclient, but can via nautilus network bro"
date: 2009-01-06
forum: Server Platforms
---

### Post by whoop on 2009-01-06
I have set up a samba share on an ubuntu server 8.10 following this tutorial on howtoforge:[http://howtoforge.com/ubuntu-home-fileserver](http://howtoforge.com/ubuntu-home-fileserver)

I can read/write to the share if I access it via Places --> Network just fine; I can even read/write from a windows xp machine. So actually it is working quite well (and I don't have to enter username/password anywhere). However I was experimenting with smbclient And I can't seem to log on with it.

smbclient -L //server1:
```

Domain=[SERVER1] OS=[Unix] Server=[Samba 3.2.3]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (server1 server (Samba, Ubuntu))
	sdb1 public hard disk Disk      Public Folder
	print$          Disk      Printer Drivers
Domain=[SERVER1] OS=[Unix] Server=[Samba 3.2.3]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
	MSHOME               SERVER1


```

smbclient //server1/sdb1%20public%20hard%20disk/
```

Domain=[SERVER1] OS=[Unix] Server=[Samba 3.2.3]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

```

smbclient //server1/sdb1%20public%20hard%20disk/ - U family
```

Domain=[SERVER1] OS=[Unix] Server=[Samba 3.2.3]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

```

so what am I doing wrong? How do I connect via smbclient?

---

### Post by HermanAB on 2009-01-06
Bad network name...

Try this:
$ smbclient //server1 -U family

and this:
$ smbclient //server1/sdb1\ public\ hard\ disk -U family

and this:
$ smbclient //server1/"sdb1 public hard disk" -U family

Anyhoo, now you can see why using spaces in file and directory names is a bad idea.  A space is a delimiter.  Convert them to dashes or underscores and save yourself from a big head-ache.

Cheers,

Herman

---

### Post by kamaji792 on 2009-01-06
It's nothing silly like you need to spell "Disk" with the capital 'D' is it :P

atb

---

### Post by whoop on 2009-01-06
second and third example worked. So it was all due to the crappy name (from the tutorial :P)

Thanks herman.

---

