---
title: "ubuntu server samba public folder"
date: 2014-10-21
forum: Server Platforms
---

### Post by tsitras on 2014-10-21
hello there. in my server (12.04) i do need to have everyone to be able to read and write in a public folder.
i have done
```
sudo apt-get install samba
```
then i have edited the file /etc/samba/smb.conf and i have changed
```
security = share
guest account = nobody
```
then i have added at the end
```
[Share name]
    writable = yes
    path = /path/to/directory
    public = yes
    guest ok = yes
    guest only = yes
    guest account = nobody
    browsable = yes
```

unfortunatelly i can not see the machine to mount it in windows.

---

### Post by splintr on 2014-10-22
Hi,

you need to give the good permissions to your shared folder, you can do it with chmod and chown.
To advertise your share in your network, you can use Avahi

---

