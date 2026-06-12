---
title: "samba not listening on 139"
date: 2009-03-10
forum: Server Platforms
---

### Post by bartvh on 2009-03-10
I've apparently broken my samba server, but I don't know how. It worked fine before, but now I can't connect to it. Some inspection with ps and netstat (*netstat -lpn | grep 139*) show that smbd is running, but not listening on port 139 (which Windows connects to).
I've tried searching the web, but only get "not listening on this specific address" problems. From the config file, I don't see something obviously misconfigured. Can somebody tell me what's wrong?

```
[global]
        log file = /var/log/samba/log.%m
        guest account = guest
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        obey pam restrictions = yes
        map to guest = bad user
        encrypt passwords = true
        passwd program = /usr/bin/passwd %u
        passdb backend = tdbsam
        dns proxy = no
        server string = %h server (Samba, Ubuntu)
        unix password sync = yes
        workgroup = VANHEUKELOM
        os level = 20
        security = share
        syslog = 0
        usershare allow guests = yes
        panic action = /usr/share/samba/panic-action %d
        max log size = 1000
        pam password change = yes
        socket options = TCP_NODELAY

#======================= Share Definitions =======================

#[homes]
#   comment = Home Directories
#   browseable = no
#   read only = no
#   create mask = 0755
#   directory mask = 0755
#   valid users = %S

[share]
        guest ok = yes
        comment = Shared Files
        writeable = yes
        create mode = 775
        public = yes
        path = /home/share
        directory mode = 775

```

---

