---
title: "Missing Mapped Drives"
date: 2016-02-11
forum: Server Platforms
---

### Post by reubendevries on 2016-02-11
I'm not sure where to post this so I am basically going to post this  here, the Synology and the Plex forum. I have a Ubuntu headless server  that has my Synology diskstation has a shared folder that is mounted on.  Up until the weekend when I had a power outage it used to be able to  see all my media through Plex. Now it no longer is able to see my shared  files. When I check the /mnt/media folder where I used to be able to  find my media I can't find it any more, when I log in through the synology web  browser I can see the files. I can also play the files through VLC on my  windows machine - so I know that's not the issue. Worst case scenario I  could back up all my data and format my drive and restart but I do want  to avoid that as I think that might take me a few hours over the  weekend. If anyone has a solution other then that please let me know.

---

### Post by Bucky Ball on 2016-02-11
*Thread moved to **Server Platforms**.*

Or perhaps you might have better luck here. Welcome.

---

### Post by SeijiSensei on 2016-02-12
Have you tried mounting it manually with the mount command?  Do you see errors?

---

### Post by reubendevries on 2016-02-12
Hey Thanks for your reply, no I haven't because I don't use Ubuntu daily so I'm not really sure how to do that. Everything I've learned about linux is self taught, so I'll google search it when I get home hopefully that will work. Thanks for the heads up.

---

### Post by darkod on 2016-02-12
If the mount point is /mnt/media as you specified, and you have that entry in /etc/fstab, then simply run:
```
sudo mount /mnt/media
```

That would be mounting it manually. If it returns some error messages paste them here.

---

### Post by reubendevries on 2016-02-13
> **darkod said:**
> If the mount point is /mnt/media as you specified, and you have that entry in /etc/fstab, then simply run:
```
sudo mount /mnt/media
```

That would be mounting it manually. If it returns some error messages paste them here.

This is the error I get:

mount: wrong fs type, bad option, bad superblock on 192.168.1.18:/volume1/Media/,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by darkod on 2016-02-13
Do you have a password on the share? If you do, you will have to use the correct username and password to mount it. If not, you might be able to simply mount it or as guest. Try to specify the type of share (cifs), I forgot to add that last time:
```
sudo mount -t cifs //192.168.1.18/volume1/Media /mnt/media
sudo mount -t cifs //192.168.1.18/volume1/Media /mnt/media -o guest
```

In the above lines I'm not sure you need the : after the 192.168.1.18. You shouldn't need it because a cifs share can be specified as above.

---

### Post by bab1 on 2016-02-13
> **darkod said:**
> Do you have a password on the share? If you do, you will have to use the correct username and password to mount it. If not, you might be able to simply mount it or as guest. Try to specify the type of share (cifs), I forgot to add that last time:
```
sudo mount -t cifs //192.168.1.18/volume1/Media /mnt/media
sudo mount -t cifs //192.168.1.18/volume1/Media /mnt/media -o guest
```

In the above lines I'm not sure you need the : after the 192.168.1.18. You shouldn't need it because a cifs share can be specified as above.
The SMB share (SMB resource) should be located via UNC convention (e.g. //SERVER_NAME/share_name).  Not by a path to the share directory.  See the mount.cifs man page excerpt```
 The mount.cifs utility attaches the [I]UNC name (exported network resource) specified as
       service (**[COLOR="#FF0000"]using //server/share[/COLOR]** syntax[/I], where "server" is the server name or IP address
       and "share" is the name of the share) to the local directory mount-point.
```

---

### Post by darkod on 2016-02-13
@bab1

That's exactly what I was trying to do, of course not knowing the OP synology details 100%. Most of those devices actually have a volume1 in between the hostname/IP and the actual shared folder name. I know my WD network HDD also had Volume1 that you needed to put into the path.

And seeing the error it returned in post #6 I think the volume1 should be in there, but I might be wrong. On the other hand the share might be only /Media.

---

### Post by SeijiSensei on 2016-02-13
> This is the error I get:
mount: wrong fs type, bad option, bad superblock on 192.168.1.18:/volume1/Media/,


You need to install the package **nfs-common** on the client.  NFS client (or server) support is not provided in Ubuntu by default.

---

### Post by MAFoElffen on 2016-02-15
> **SeijiSensei said:**
> You need to install the package **nfs-common** on the client.  NFS client (or server) support is not provided in Ubuntu by default.
That depends really depends. If his NAS is left at it's default when he had set it up ... Synlology's NAS default "all protocols" is web, ftp, nfs and smb. So the others are on the right track.

From Synologys docs for an Apple client:
> 
Choose Go > Connect to Server from the menu bar. Type the IP address or name (appended with .local) of the
Synology NAS preceded by smb:// or afp:// in the Server Address field and click Connect. (e.g.
smb://EricaWang.local or afp://192.168.0.2)

Note: For better performance, it is recommended that you connect to the shared folders via SMB

Windows is via a mapped network drive via smb...

But by the Linux connection instructions from Synology that the OP described, it recommends connect to Linux clients via NFS...:
> 
Access Shared Folders from Linux
In [COLOR=#ff0000]Synology DiskStation Manager[/COLOR], Go to Main Menu > Control Panel > Shared Folder. Select the shared folder
you want to access, click NFS Privileges, and find the mount path at the bottom of the window that appears.
On a Linux computer, enter the mount path to mount the shared folders.


But since is is also doing smb... You could still mount that way...

My question is... let me the devil's advocate... If you have NAS which your local network clients can connect to directly, then why the middle man (The server)? Further Security?

---

### Post by Morbius1 on 2016-02-16
> **MAFoElffen said:**
> 
[QUOTE=SeijiSensei;13439354]You need to install the package **nfs-common** on the client.  NFS client (or server) support is not provided in Ubuntu by default.
That depends really depends. If his NAS is left at it's default when he had set it up ... Synlology's NAS default "all protocols" is web, ftp, nfs and smb. So the others are on the right track.[/QUOTE]
The others are right on track only if you want the OP to mount the share via cifs rather than what he is already doing - or trying to do - which is to mount via NFS.

This is an NFS error because of the syntax of the path:
> mount: wrong fs type, bad option, bad superblock on **192.168.1.18:/volume1/Media/** 
Had it been a cifs error it would have looked something like:
> mount: wrong fs type, bad option, bad superblock on** //192.168.1.18/volume1/Media**
Are you folks trying to convince him to mount it another way or are you trying to fix an NFS problem?

---

