---
title: "Samba, net usershare and permissions"
date: 2013-07-31
forum: Server Platforms
---

### Post by Dreadslayer on 2013-07-31
Hi there

I am currently setting up my home server wit ubuntu server 12.04 for the first time and ran into some issues. For my shares I want to use Samba due to several Windows machines within the network. I'd like to run Apache HTTP Server on a VM (also ubuntu server 12.04). DocumentRoot should be set to a share. Now I'm having trouble with the rights management. What I did so far:

I created a share with "*net usershare add*" for the server side user "*smbuser*", with the needed permissions for the local folder which should be shared, see:
```
$ net usershare info
[www]
path=/media/md1/www
comment=
usershare_acl=SERVER\smbuser:F,
guest_ok=n
```
```
$ ll /media/md1
...
drwxrwx--- 17 smbuser smbuser  4096 Jul 29 16:33 www/
```

Next I mounted said share on the VM:
```
sudo mount -t cifs -o credentials=/etc/.smbcredentials //10.0.5.5/www /media/shares/www
```
```
$ ll /media/shares
...
drwxrwx--- 17 1001 1001    0 Jul 29 16:12 www/
```

My problem now is that only with root I can access the share, however on the VM the Apache user "www-data" needs rw permissions for this share because I want to use it as DocuementRoot. How can this be achieved? I cannot chown it on the VM. 

Help would be much appreciated!

---

### Post by Morbius1 on 2013-07-31
> sudo mount -t cifs -o credentials=/etc/.smbcredentials //10.0.5.5/www /media/shares/www
It's sorta kinda like mounting an NTFS partition:

_*Take possession of the mounted share:*_
> sudo mount -t cifs -o credentials=/etc/.smbcredentials[COLOR=#0000cd]**,uid=1000**[/COLOR] //10.0.5.5/www /media/shares/www
_*OR, open it up to all local users:*_
> sudo mount -t cifs -o credentials=/etc/.smbcredentials[COLOR=#0000cd]**,dir_mode=0777,file_mode=0666,nounix**[/COLOR] //10.0.5.5/www /media/shares/www

---

