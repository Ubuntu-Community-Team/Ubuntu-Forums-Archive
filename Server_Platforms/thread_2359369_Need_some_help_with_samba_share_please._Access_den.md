---
title: "Need some help with samba share please. Access denied"
date: 2017-04-23
forum: Server Platforms
---

### Post by biggyk on 2017-04-23
Using Ubuntu server 16.04. Iv been using it as a media server with a couple folders inside /smb/Media set at 777 so no anyone can access them and those are not a problem. I just created a folder (/smb/Mike that only I want to be able to access. I have set that folder to 700 and I have tried my user name and root for ownership. In samba, I have used the same permissions and made it writable. On my windows 10 machine when I get my login prompt, I enter my credential but i get access denied?????  Anything Im missing here?


Side question....that media folder even though it is open to all, windows still makes me log into it. But using a media player such as kodi, I dont get a login prompt.

---

### Post by Tadaen_Sylvermane on 2017-04-23
```
sudo smbpasswd $USER 
```
Then restart samba service.

---

### Post by biggyk on 2017-04-23
> **Tadaen_Sylvermane said:**
> ```
sudo smbpasswd $USER 
```
Then restart samba service.


mike@ubuntu:~$ sudo smbpasswd $USER
[sudo] password for mike:
New SMB password:
Retype new SMB password:
Failed to find entry for user mike.

---

### Post by Morbius1 on 2017-04-23
```
sudo smbpasswd -a $USER
```

---

### Post by Tadaen_Sylvermane on 2017-04-23
Indeed. Forgot that switch

---

