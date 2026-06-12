---
title: "Samba recycle bin configuration"
date: 2018-08-05
forum: Server Platforms
---

### Post by irojas31 on 2018-08-05
Can I make the configuration of the recycle bin with the active directory? I did tests, deleting but it only gives me the information of a user that had deleted a folder, what other parameters are necessary so that they are shown of all the users who deleted some file or folder?
This is my configuration


----------------
# Global parameters
[global]
        workgroup = SOPORTE
        realm = SOPORTE.LOCAL
        netbios name = DC1
        server role = active directory domain controller
        server services = s3fs, rpc, nbt, wrepl, ldap, cldap, kdc, drepl, winbindd, ntp_signd, kcc, dnsupdate
        idmap_ldb:use rfc2307 = yes
        winbind enum users = yes
        winbind enum groups = yes


[netlogon]
        path = /var/lib/samba/sysvol/soporte.local/scripts
        read only = No


[sysvol]
        path = /var/lib/samba/sysvol
        read only = No
[TI]
        path = /opt/sistemas
        read only = no


[RECYCLE BIN]
        comment = Recycle Bin
        path = /opt/recycle
        public = yes


# Recycle Bin
        vfs objects = recycle full_audit
        recycle:repository = /opt/recycle/recycle_TI/%u/%m
        recycle:versions = Yes
        recycle:keeptree = Yes
        recycle:touch = yes
----------------------------------------
root@DC1:/opt/recycle/recycle_TI# ll
total 12
drwx------ 3 SOPORTE\cmiranda users 4096 ago  4 19:13 ./
drwxrwxr-x 3 root             users 4096 ago  4 19:13 ../
drwx------ 3 SOPORTE\cmiranda users 4096 ago  4 19:13 SOPORTE\cmiranda/

---

