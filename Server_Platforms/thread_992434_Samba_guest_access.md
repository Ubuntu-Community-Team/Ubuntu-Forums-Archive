---
title: "Samba guest access"
date: 2008-11-24
forum: Server Platforms
---

### Post by originlabs on 2008-11-24
Hi everyone,

I'm having great difficulty in allowing guest access to samba shares in Ubuntu Server 8.10.  I've tried using the same smb.conf file I have been using on an 8.04 server, but guest's (mapped to bad user) still cannot access any shares.

I'm not sure what's changed from Samba 3.0 to 3.2, but hopefully somebody can spot an obvious mistake :)

I decided to remove and purge samba and start from scratch with a basic config file,

**Heres the smb.conf i'm using: (output of testparm)**
```

[global]
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d

[homes]
        comment = Home Directories
        valid users = %S
        create mask = 0700
        directory mask = 0700
        browseable = No

[films]
        path = /media/storage/films
        guest ok = Yes
        locking = No


```

I've added my username using smbpasswd -a *username*, and I can access and write to my home dir and the films share.  To keep things simple, the unix permissions on the films dir are 775 (files 664).

Whenever a guest attempts to access the share, I get an NT access denied error message, and the samba log.*hostname* indicates ```
[2008/11/24 23:50:09,  0] smbd/service.c:make_connection_snum(1152)
  '/media/storage/films' does not exist or permission denied when connecting to [films] Error was Permission denied

```

Can anyone shed any light on this, I'm beginning to pull my hair out.  My 8.04 server (with samba 3.0.22) is working perfectly with a similar configuration!

Thanks,

Matt

Output of testparm -s -v | grep guest:
```
$ testparm -s -v | grep guest
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[films]"
Loaded services file OK.
Server role: ROLE_STANDALONE
        map to guest = Bad User
        guest account = nobody
        usershare allow guests = Yes
        guest only = No
        guest ok = No
        guest ok = Yes

```

---

### Post by BassKozz on 2008-12-09
Similar problem here too man: [http://ubuntuforums.org/showthread.php?t=1004776](http://ubuntuforums.org/showthread.php?t=1004776)
I am getting the same error message in my /var/log/samba folder "smbd/service.c:make_connection_snum(1152)"
Did you find a solution?

---

### Post by bab1 on 2008-12-09
I see you have in the global section:```
 map to guest = Bad User
```

But I don't see the guest defined there.  I see it in testparm though.

In my smb.conf file I have this for the actual guest:```
guest account = nobody
```

---

