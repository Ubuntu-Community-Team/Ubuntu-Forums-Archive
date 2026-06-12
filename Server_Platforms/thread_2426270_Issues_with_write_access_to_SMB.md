---
title: "Issues with write access to SMB"
date: 2019-09-06
forum: Server Platforms
---

### Post by gemini05 on 2019-09-06
Greetings,

I'm new to the Linux world. I've recently purchased 2 RPi4 devices, with one of them serving as a media share. I'm about to mount the SMB share fine from my Win10 PC with RW but with the mount on my second RPi, I only have RX.

#1 has a USB HD mounted and shared using SMB (/media/USB1 which is presented as /media/Shared)
I've mounted this shared on #2 and I can access it but I can't write to it.

I've tried changing the permissions on the directory (/media/Shared) on  #2 so that it's owned by "pi" before even mounting and making sure that  UGO have RW. However, when I mount, it goes back to being owned by  "root" and GO only have RX. 

This is my smb.conf config on #1:
[Shared]
path = /media/USB1
read only=no
writeable=Yes
create mask=0777
directory mask=0777
public=no
force user=pi
force group=pi

and this is what I have in fstab on #1 to mount it on boot:
UUID=0042-6478  /media/USB1     auto    nofail,uid=1000,gid=1000,umask=0000,noatime 0 0


On #2, I have the following in fstab:
//RPi#1-IP/Shared /media/Shared cifs x-systemd.automount,users,credentials=/home/pi/.smbcred 0 0

where .smbcred has the credentials for the smbuser I setup on #1.

Is there something I'm missing?
Thank you in advance!

---

### Post by TheFu on 2019-10-15
I'm not any expert on Samba, but a few questions ... 

a) exactly which release and version of Ubuntu are you running on each Pi?

b) which file system is being used on the locally mounted storage?  Native Linux file systems make things easier. Non-native file systems make things hard to impossible.

c) why not use NFS between Linux systems?  NFS is the native file sharing protocol for Unix systems.

d) Please run **testparm** on each linux machine and clearly say which output goes with which specific machine. This will show us the actual samba config file, as read by the program.

e) Please post the fstab, unaltered for both systems.

Showing partial information means we have to be like dentists digging to get the data needed.

Also, please use _code tags_ when posting the commands and output.  The Advanced Editor has a button, #, for that.

I wouldn't use x-systemd.automount, either.

---

### Post by Morbius1 on 2019-10-16
Change this:
[highlight]//RPi#1-IP/Shared /media/Shared cifs x-systemd.automount,users,credentials=/home/pi/.smbcred 0 0[/highlight]
To this:
[highlight]//RPi#1-IP/Shared /media/Shared cifs x-systemd.automount,users,credentials=/home/pi/.smbcred[COLOR=#0000cd]**,uid=pi**[/COLOR] 0 0[/highlight]
Unmount the share:
```
sudo umount /media/Shared
```
Then do the systemd 2-step:
```
sudo systemctl daemon-reload
sudo systemctl restart remote-fs.target
```

CIFS is a virtual filesystem that creates a "view" of the shared resource. Without any modification to the permissions on that view the mounted share will be owned by root who has write access but with read access only to everyone else. The [COLOR=#0000cd]**uid=pi **[/COLOR]option will make the owner of the mounted share pi instead of root.

[COLOR=#0000cd]**Side note**[/COLOR]: If the intent of x-systemd.automount was to insure that the share will mount only when the network stack is operational you might consider adding another option: noauto:
[highlight]//RPi#1-IP/Shared /media/Shared cifs [COLOR=#0000cd]**noauto**[/COLOR],x-systemd.automount,users,credentials=/home/pi/.smbcred[COLOR=#0000cd]**,uid=pi**[/COLOR] 0 0[/highlight]

---

