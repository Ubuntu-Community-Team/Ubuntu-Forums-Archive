---
title: "Linux-to-Linux Samba/CIFS/SMB Spawning Infinite cifsd Processes/Connections"
date: 2018-03-20
forum: Server Platforms
---

### Post by xnaas on 2018-03-20
I've been trying to Google this issue one and off for weeks now, but all of my results always turn up something related to Windows..._**Windows is not involved!**_

My setup is quite simple, I think:

[LIST=1]
[*]Synology box with samba server running 
[*]Ubuntu Server 16.04 mounts some folders 
[/LIST]

Super basic, I hope.

I mount the shares permanently using /etc/fstab:
```

//server/path1/path2 /path/folder cifs ro,credentials=/home/xnaas/.smbcredentials,vers=3.02,_netdev,auto,noexec 0 0

//server/path1/path2/path3/path4 /path/folder cifs ro,credentials=/home/xnaas/.smbcredentials,vers=3.02,_netdev,auto,noexec 0 0

//server/path1/path2 /path/folder cifs ro,credentials=/home/xnaas/.smbcredentials,vers=3.02,_netdev,auto,noexec 0 0

```

Note: SMBv1 is disabled on the NAS. I've tried every version of SMB from 2.0 to 3.02. The behavior is always the same.

Still all pretty basic stuff, I'm hoping. This works. It mounts the shares. However, on the Ubuntu server, this starts to spawn an infinite number of cifsd process and the Synology NAS shows all of those processes being connected as well. I think the highest count to date is about 6400 processes. Fortunately, this isn't *that* CPU-intensive, but this really starts to chew through RAM on the NAS side, eventually.

I'm at a loss for why Ubuntu is asking for an infinite number of connections to be made. I've recently turned on the **deadtime** option and set it to 5, but it will take time to see if it's any use.

In the meantime, any thoughts on this? I'm pretty sure it's not normal for Ubuntu to try and make an infinite number of active connections.

Edit: Possible thoughts: Because the folders are being read by nginx, could that be causing issues?

Edit: Small discovery...if nginx is shutdown, the number of processes spawning slows significantly. Something is still causing processes to spawn infinitely, but it's *slightly* slower when nginx is shut down.

---

### Post by xnaas on 2018-03-20
After waiting some time with the deadtime option set, it's currently working its way towards hitting 200 processes anyway. All that option seems to do is barely slow down the inevitable. :(

---

### Post by xnaas on 2018-03-20
As a follow-up question, would it be worth it to investigate just using NFS? I've *never *used NFS before, but am more than willing to look into it as an option, if that makes more sense.

---

### Post by SeijiSensei on 2018-03-20
Yes.  For *nix-to-*nix networking NFS is a much better choice.

My server runs both NFS and Samba offering up the same home directories.  Most of my machines run Linux and use NFS, but I do run occasionally run Windows in virtual machines and connect them to the server with CIFS.

Both NFS and rsync will preserve "POSIX" file characteristics like modification time and permissions.  Because those features are not native to Windows and CIFS, the only reliable way to transfer a Linux filesystem using CIFS is to create a compressed archive in a format like bzip2, gzip or ZIP, move the archive over the network, and decompress it on the target.

---

### Post by xnaas on 2018-03-20
> **SeijiSensei said:**
> Yes.  For *nix-to-*nix networking NFS is a much better choice.
Ah, figured as much. I've never had to mess with *nix-to-*nix networking before last year, funny enough.

> **SeijiSensei said:**
> My server runs both NFS and Samba offering up the same home directories.  Most of my machines run Linux and use NFS, but I do run occasionally run Windows in virtual machines and connect them to the server with CIFS.

Both NFS and rsync will preserve "POSIX" file characteristics like modification time and permissions.  Because those features are not native to Windows and CIFS, the only reliable way to transfer a Linux filesystem using CIFS is to create a compressed archive in a format like bzip2, gzip or ZIP, move the archive over the network, and decompress it on the target.

Guess I get to learn something new, sweet! :D

> **SeijiSensei said:**
> Both NFS and rsync will preserve "POSIX" file characteristics like modification time and permissions.

This'll actually be huge for me. Awesome!

---

### Post by xnaas on 2018-03-20
Well, I gave NFS an honest try. After spending the past couple of hours making sure everything was perfect, it still refused to work. I'm not going to spend any more time on it.

I'll keep tolerating these obnoxious issues with samba/Ubuntu and work on another solution in the meantime.

Thanks, anyway, though.

---

### Post by xnaas on 2018-03-20
Well, this is quite embarrassing...

I've had this in my crontab all this time...

```
* * * * 2 /bin/mount -a -t cifs -o remount
```

Of course, at the end of months of wondering "wtf" and "how have 0 people ever had this issue??" we finally find the user error!

 ):P :KS:lolflag::guitar::cool:

---

### Post by LHammonds on 2018-03-21
I'm glad you found the source of the problem and that you shared it with future readers.

Thanks,
LHammonds

---

### Post by SeijiSensei on 2018-03-21
> **xnaas said:**
> I'll keep tolerating these obnoxious issues with samba/Ubuntu and work on another solution in the meantime.

SSHFS is another option to consider. It's pretty easy to set up and preserves POSIX features.

---

