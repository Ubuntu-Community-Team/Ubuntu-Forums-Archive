---
title: "NFS client mounts ro instead of rw"
date: 2009-08-31
forum: Server Platforms
---

### Post by ShutterAce on 2009-08-31
I have two identical machines with NFS setup on both of them. They are both 9.04.

The issue is that I cannot get NFS to mount as rw. Well, I think that's the problem. It is listed as rw in mount but when I try to copy files to it I get an error.

Here is partial /etc/exports from the server:
```

# JAD 08/31/2009
/backup 192.168.1.10(rw,no_root_squash,async)

```

Here is the entry from the output of mount on the client:
```
192.168.1.20:/backup on /backup type nfs (rw,addr=192.168.1.20)

```

A sample of the scripts output:
```
cpio: cannot make directory `/backup/./jadeck': Permission denied
cpio: /backup/./jadeck/www/PHPMyAdmin-local/import.php: Cannot open: No such file or directory
cpio: cannot make directory `/backup/./jadeck': Permission denied
cpio: /backup/./jadeck/www/PHPMyAdmin-local/tbl_properties_export.php: Cannot open: No such file or directory
cpio: cannot make directory `/backup/./jadeck': Permission denied
cpio: /backup/./jadeck/www/PHPMyAdmin-local/server_binlog.php: Cannot open: No such file or directory

```

I have tried mounting with and without using sudo with no difference as well as executing the script with and without sudo.

I'm sure it's something simple but I'm stuck. Does anybody have any ideas?

Thank You!

---

### Post by eylisian on 2009-09-01
It's looking like an ownership issue on /backup although no_root_squash and sudo should have done the trick... Or maybe not, might take sudo su - and then running the script. But you don't want to have to call sudo anything for your backup really, so squash root and check permissions. The machine says read write on your NFS mount, and I am assuming that you are an NFS/NIS user with appropriate permissions...

Check this out;
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Thats a lot better than what my instructions would look like, plus I have only set up NFS/NIS on RHEL and it's been better than a year now.

Hope it goes well.

Regards

---

### Post by ShutterAce on 2009-09-02
Well I made two changes and now it's working. I'm not sure which change was the fix and I can't back them out at the moment because I have the backup running right now.

Heres what I did:
[LIST=1]
[*]sudo was broken on the server so I added the user back into the admin group. How it got removed is beyond me. I could see this being the problem.
[*]The drive was mounted as ro,relatime on the server. I changed it to defaults in the fstab and remounted. Could the server side mount being ro have done it?
[/LIST]

Like I said I don't know which fixed it but it works now.
:D

---

### Post by ShutterAce on 2009-09-02
Well I made two changes and now it's working. I'm not sure which change was the fix and I can't back them out at the moment because I have the backup running right now.

Heres what I did:
[LIST=1]
[*]sudo was broken on the server so I added the user back into the admin group. How it got removed is beyond me. I could see this being the problem.
[*]The drive was mounted as ro,relatime on the server. I changed it to defaults in the fstab and remounted. Could the server side mount being ro have done it?
[/LIST]

Like I said I don't know which fixed it but it works now.
:D

---

### Post by ShutterAce on 2009-09-02
I have verified it was the local ro mount on the server.:)

---

