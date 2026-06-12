---
title: "Samba4 top-level shares' permissions"
date: 2011-05-18
forum: Server Platforms
---

### Post by ZuOverture on 2011-05-18
Hello everybody.

My question probably is extremely easy, but I hadn't found a solution.

I have managed to set Samba4 working as a PDC, and now I also want to turn it into a file server. I've created shares for roaming profiles (called it "profiles") and a "test" share in smb.conf - they are accessible and all. If I create subfolders inside this shares, I can configure permissions for subfolders and they work as expected.

The problem is: I can't hide top-level system shares, such as "profiles", "sysvol" and "netlogon" from ordinary domain users. Moreover, I can't set up any permissions on them from MMC. All I get is

"The system encountered the following error while saving the properties of share profiles:
 Error 1: Incorrect function"

```
$ cat /etc/samba/smb.conf
# Global parameters
[global]
        server role = domain controller
        workgroup = MYDOMAIN
        realm = mydomain.dyndns.com
        netbios name = PDC1
        setup directory = /usr/share/samba/setup/

[netlogon]
        path = /var/lib/samba/sysvol/mydomain.dyndns.com/scripts
        read only = No

[sysvol]
        path = /var/lib/samba/sysvol
        read only = No

[test]
        path = /test
        read only = no

[profiles]
        path = /var/lib/samba/var/profiles
        read only = no
```

```
/$ ls -l
total 80
drwxr-xr-x   2 root     root      4096 2011-05-18 11:36 bin
drwxr-xr-x   3 root     root      4096 2011-05-16 10:48 boot
...
drwxr-xr-x   4 pdcadmin pdcadmin  4096 2011-05-18 12:48 test
...

/$ ls -l test
total 16
drwxr-xr-x 2 root users 4096 2011-05-17 16:54 Folder
drwxr-xr-x 2 root users 4096 2011-05-18 12:50 Folder2

/var/lib/samba/var$ ls -l
total 4
drwxr-xr-x 3 root root 4096 2011-05-18 09:33 profiles

/var/lib/samba/var/profiles$ ls -l
total 8
drwxr-xr-x 14 3000011 users 4096 2011-05-18 10:45 User1
```

Any suggestions appreciated.

---

### Post by ZuOverture on 2011-05-18
MMC doesn't work. Used Explorer instead.

---

