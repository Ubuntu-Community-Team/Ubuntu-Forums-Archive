---
title: "Samba 4.13 + Ubuntu 20.04 - Recycle bin"
date: 2022-03-14
forum: Server Platforms
---

### Post by pdiego.silva on 2022-03-14
Hello everyone,

I'm trying to setup recycle bins in my shares, according to the following configs (changed the domain-related settings for securitry reasons):

```
[global]
        netbios name = SU20-FILESERVER
        server string = 'SU20-FILESERVER'
        dns forwarder = 192.168.0.201


        security = ads
        kerberos method = secrets and keytab
        dedicated keytab file = /etc/krb5.keytab


        realm = DOMAIN.COM
        workgroup = DOMAIN


        log file = /var/log/samba/log.%m
        max log size = 1000
        logging = file


        panic action = /usr/share/samba/panic-action %d
        server role = standalone server


        obey pam restrictions = yes
        unix password sync = yes


        passwd program = /usr/bin/passwd %u
        passwd chat = *Informe\sa\snova\s*\ssenha:* %n\n *Confirme\sa\snova\s*\ssenha:* %n\n *Senha\satualizada\scom\ssucesso* .


        pam password change = yes
        map to guest = bad user


        template homedir = /home/%U
        template shell = /bin/bash


        winbind refresh tickets = Yes
        winbind use default domain = yes
        winbind offline logon = false
        winbind enum users = yes
        winbind enum groups = yes


        idmap config * : backend = tdb
        idmap config * : range = 3000-7999
        idmap config DOMAIN : backend = rid
        idmap config DOMAIN : range = 10000-999999

        vfs objects = acl_xattr recycle
        map acl inherit = Yes
        acl allow execute always = yes
        store dos attributes = Yes


        recycle:repository = /tmp/recycle/%U
        recycle:touch = yes
        recycle:keeptree = yes
        recycle:versions = yes
        recycle:directory_mode = 0777
        #recycle:noversions = *.tmp,*.temp,*.o,*.obj,*.TMP,*.TEMP
        #recycle:exclude = *.tmp,*.temp,*.o,*.obj,*.TMP,*.TEMP
        #recycle:excludedir = /recycle,/tmp,/temp,/TMP,/TEMP
        #recycle:maxsize = 999999


        load printers = no
        printing = bsd
        printcap name = /dev/null
        disable spoolss = yes


[homes]
        comment = Home folders
        browseable = no
        read only = no
        create mask = 4750
        directory mask = 4750
        valid users = %S

[Main]
        comment = Company main fileshare
        path = /var/share/main
        available = yes
        browseable = yes
        guest ok = no
        public = no
        read only = no



```

Shares are working fine for months, using ACLs for domain related permissions.

My problem with recycle bin has been:

- On Windows, I go to share Main > FolderA and create a text test file
- Put some text in it
- Delete it
- On my Ubuntu Server, it creates a full tree in the recycle, like this: /tmp/recycle/myuser/Main/FolderA
- But no files are moved there, it just creates the tree

I tried a combination of settings, like maxsize and permissions, but no success. I noticed the tree is being created with 755 permissions, owner is myuser and group is the user's main group in Active Directory.

What am I missing?

Thank you in advance!

---

### Post by pdiego.silva on 2022-03-14
After enabling full_audit I was able to figure it out. In the logs I saw a message of samba trying to move the deleted file to recycle bin and the following error: "Invalid cross-device link".

Some googling later, the problem is my shares are on different disks, and /tmp/recycle in yet another disk. I couldn't find a suitable solution, some suggested to use crossrename module, but this could cause performance issues and audit log issues.

So I decided to create a bin folder in eache of my shares, here's my final working setup:

- Bin enabled for files smaller than 1 GB
- Global configs for all shares, and then a separate bin folder for each share
- Cron will clean deleted files older than 90 days
- Home folder is in Disk 1
- /var/share is in Disk 2
- /var/adm/share is in Disk 3
- So 3 disks with multiple different shares require different bin folders

smb.conf

```

[global]
        netbios name = SU20-FILESERVER
        server string = 'SU20-FILESERVER'
        dns forwarder = 192.168.0.201




        security = ads
        kerberos method = secrets and keytab
        dedicated keytab file = /etc/krb5.keytab




        realm = DOMAIN.COM
        workgroup = DOMAIN




        log file = /var/log/samba/log.%m
        max log size = 1000
        logging = file




        panic action = /usr/share/samba/panic-action %d
        server role = standalone server




        obey pam restrictions = yes
        unix password sync = yes




        passwd program = /usr/bin/passwd %u
        passwd chat = *Informe\sa\snova\s*\ssenha:* %n\n *Confirme\sa\snova\s*\ssenha:* %n\n *Senha\satualizada\scom\ssucesso* .




        pam password change = yes
        map to guest = bad user




        template homedir = /home/%U
        template shell = /bin/bash




        winbind refresh tickets = Yes
        winbind use default domain = yes
        winbind offline logon = false
        winbind enum users = yes
        winbind enum groups = yes



        idmap config * : backend = tdb
        idmap config * : range = 3000-7999
        idmap config DOMAIN : backend = rid
        idmap config DOMAIN : range = 10000-999999


        vfs objects = acl_xattr recycle full_audit
        map acl inherit = Yes
        acl allow execute always = yes
        store dos attributes = Yes


        recycle:touch = yes
        recycle:keeptree = yes
        recycle:versions = yes
        recycle:noversions = ~*.*,.~*.*,*.tmp,*.temp,*.o,*.obj,*.TMP,*.TEMP
        recycle:exclude = ~*.*,.~*.*,*.tmp,*.temp,*.o,*.obj,*.TMP,*.TEMP
        recycle:excludedir = /recycle,/tmp,/temp,/TMP,/TEMP
        recycle:directory_mode = 0750
        recycle:maxsize = 1073741824


        full_audit:success = open, mkdirat, renameat, unlinkat, write
        full_audit:failure = connect, create_file, mkdirat, open, read, readdir, renameat, unlinkat, write
        full_audit:prefix = %u|%I|%S full_audit:failure = none
        full_audit:facility = local5
        full_audit:priority = notice



        load printers = no
        printing = bsd
        printcap name = /dev/null
        disable spoolss = yes




[homes]
        comment = Home folders
        browseable = no
        read only = no
        create mask = 4750
        directory mask = 4750
        valid users = %S

        recycle:repository = /home/%U/.recycle



[Main]
        comment = Company main fileshare
        path = /var/share/main
        available = yes
        browseable = yes
        guest ok = no
        public = no
        read only = no

        recycle:repository = /var/share/.recycle/%U

[ADM]
        comment = IT fileshare
        path = /var/adm/share/it
        available = yes
        browseable = yes
        guest ok = no
        public = no
        read only = no

        recycle:repository = /var/adm/share/.recycle/%U

```

/etc/cron.daily/samba (include at the end of the file)

```

find /var/share/.recycle -mtime +90 -type f -delete
find /var/adm/share/.recycle -mtime +90 -type f -delete

```

Hope this helps someone!

---

