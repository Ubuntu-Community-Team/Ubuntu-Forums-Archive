---
title: "Baffling permissions issue"
date: 2019-06-26
forum: Server Platforms
---

### Post by DaleHutch1 on 2019-06-26
Greetings,

I hope this is the correct forum to place this support request.

I have a Ubuntu 18.04 server in operation. I have installed Samba onto the server and configured a share. I would like anyone to have full read/write access. So I changed the permissions to the share to nobody:nogroup. Here is my samba conf.

[users]
        path = /samba/users
        browseable = yes
        read only = no
        force create mode = 0775
        force directory mode = 2770
        valid users = @sambashare @sadmin dalehutch @nogroup
        force user = nobody
        public = yes
        write list = dalehutch @sambashare @nogroup
        writeable = yes
        guest account = nobody


Here is the strange part. My Windows 10 systems (I have 4 total) can view the share once authenticated.  Only two can copy (click and drag) a folder into the share and it copies. The other two can't. They all use the same username and password and all belong to the same workgroup. They click and drag a folder to the share and a little "no" symbol appears and they can't copy to the folder. All Windows 10 systems can create a new folders in the share and copy to that folder. I remember something about how Windows 10 uses the File Explorer in a way that sends a different user name and that may be the issue. It has to be some permissions issue. I have tried settings the folders to 777 with the same results. 

How can I get the Windows 10 systems who can't copy to a share working?

Thanks

---

