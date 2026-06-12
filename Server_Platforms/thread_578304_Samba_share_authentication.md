---
title: "Samba share authentication"
date: 2007-10-17
forum: Server Platforms
---

### Post by blackjackchik on 2007-10-17
Hello. I have Samba server (Ubuntu 7.04) an two clients (Ubuntu 7.04). Samba must authenticate group users when they make connection to samba share. It`s work fine but when i try connect and authenticate to share simultaneously first client saccesfuly login and second client login fail. 
It`s my config samba

```
[global]
        name resolve order = wins bcast hosts lmhosts
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n
        add group script = /usr/sbin/groupadd %g
        delete group script = /usr/sbin/groupdel %g
        add user to group script = /usr/sbin/usermod -G %g %u
        logon drive = H:
        username map = /etc/samba/smbusers
        encrypt passwords = yes
        passwd program = /usr/bin/passwd %u
        passdb backend = tdbsam
        wins support = true
        dns proxy = yes
        netbios name = samba24
        server string = %h server (Samba24)
        logon script = scripts/logon.bat
        default = labs
        local master = yes
        workgroup = labs-ef.local
        logon path = \\samba24\profile\%U
        os level = 255
        add user script = /usr/sbin/useradd -m %u
        security = user
        add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u
        delete user script = /usr/sbin/userdel -r %u
        log level = 3
        domain logons = yes
[labs]
        locking = no
        valid users = @users
        writeable = yes
        path = /home/shares/labs
```

---

### Post by XeroxGUI on 2007-10-17
tsk tsk tsk... why are you using samba to network lin to lin? Really reccomend NFS for that as linux has some odd behaviour w/ samba. I use samba on win servers, and use nfs on the same server(sometimes via vmware) for linux clients. try nfs.

---

