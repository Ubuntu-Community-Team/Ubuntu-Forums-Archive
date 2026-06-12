---
title: "Mount AD Share On Ubuntu Server"
date: 2016-06-03
forum: Server Platforms
---

### Post by elcidsps on 2016-06-03
I have been up and down the web trying to figure this out but still running into trouble.  I have an Ubuntu 15.04 Server running Samba and Active Directory.  My Samba config look like this:

```
    [global]
            workgroup = MYDOMAIN
            realm = MYDOMAIN.LOCAL
            netbios name = AD-FILESERVER
            server role = active directory domain controller
            dns forwarder = 192.168.10.4
            idmap_ldb:use rfc2307 = yes
    
    [netlogon]
            path = /var/lib/samba/sysvol/mydomain.local/scripts
            read only = No
    
    [sysvol]
            path = /var/lib/samba/sysvol
            read only = No
    [Home]
            path = /Server/Home
            read only = No
    
    [Profile]
            path = /Server/Profile
            read only = No
    
    [Documents]
            path= /Server/Documents
            read only = No
            writeable = yes
            create mask = 0777
            force create mode = 0777
            available = yes
```

I have configured the users accordingly and my windows users have no problem accessing any of the shares.

I set up another Ubuntu server and wanted access to the Documents share (from fstab):

   ```
 //MYDOMAIN.LOCAL/Documents /shares/documents cifs sec=ntlmv2,credentials=/etc/.adcredentials,file_mode=0777,dir_mode=0777,uid=1000,gid=1000
```
My .adcredentials file:

   ```
 username=username@MYDOMAIN.LOCAL
    password=password
```
The share mounts without issue; however, when I navigate to the /shares/documents folder I get a permission denied.
Obviously I am approaching this the wrong way.  Can someone give me an idea of what I am doing wrong? Are there additional steps needed to connect to an AD share over a regular Samba share?  Thank you.

---

### Post by elcidsps on 2016-06-06
I hate to bump posts, but I really need some help with this.

---

### Post by howefield on 2016-06-06
Let's move your thread to a more appropriate place.. the "*Server Platforms*" forum.

Bumping your posts is a perfectly legitimate way to attract attention, sometimes it is all it takes. About once a day should be ok.

Incidentally, 15.04 is way past end of life, if you weren't already aware.

---

### Post by elcidsps on 2016-06-06
Thanks Howefeld.  I am aware that 15.04 is past EOL.  At this point, I just need to get it working so I can move on to upgrading my servers.

---

### Post by darkod on 2016-06-06
I would use //ad-fileserver/documents instead of //mydomain.local/documents or the server IP instead of server name.

Use the IP or the machine name, not the domain name.

Also, once mounted on /shares/documents the access will depend on the permissions of that folder. From the second server run:
```
cd /shares
ls -l
```

I think the permission denied is because of the permissions you have on /shares/documents.

---

