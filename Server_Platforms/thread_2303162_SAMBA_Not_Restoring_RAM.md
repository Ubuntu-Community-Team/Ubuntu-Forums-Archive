---
title: "SAMBA Not Restoring RAM"
date: 2015-11-16
forum: Server Platforms
---

### Post by xhitm3n on 2015-11-16
Hi all, 
I am having a little problem with Samba, i have LXC container with Samba on a Proxmox Host, the LXC is Ubuntu 15.04 with samba installed from apt, my problem is that when i transfer or download anything from the samba share it caches to the RAM, which i think its normal linux behavior, i have the LXC with 1CPU and 1GB of RAM, and when i do transfers it eats all the memory, for example until i reach 1GB of used memory i can transfer at 115mb/s, but when it reaches 1GB it slows down and starts spiking from 5mb to 70mb, after the transfer is finished the RAM stays and never restores, this make the samba share really slow and unstable i need to restart it every time it reaches max RAM!

The samba is connected directly to a Physical disk which i bind mount from the HOST, with a file system ext4 and as 500GB, while i was on ESXi it never happened but the disk was a VMDK image, instead of physical!

Here is my smb.conf:
```



[global]
        server string = %h server (Samba, Ubuntu)
        server role = standalone server
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        socket options = TCP_NODELAY IPTOS_LOWDELAY
        preferred master = Yes
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb


[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        print ok = Yes
        browseable = No


[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers


[xhitfile]
        path = /data
        read only = No
        guest ok = Yes

```

Here i downloaded a file and it cached to RAM 400mb that never restores if it reaches MAX
```

free -m
             total       used       free     shared    buffers     cached
Mem:          1024        447        576         56          0        430
-/+ buffers/cache:         17       1006
Swap:         7167         27       7140

```

Thanks in advance!

---

