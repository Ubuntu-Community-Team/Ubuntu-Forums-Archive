---
title: "samba cifs permission denied"
date: 2014-01-04
forum: Server Platforms
---

### Post by Dreadslayer on 2014-01-04
Hi there

I'm having trouble with accessing a samba share:

```

morrow@sedna:~$ sudo mount -t cifs -o credentials=/etc/.smbcredentials //10.5.5.5/series /media/shares/series
$mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

To setup the user, share and access rights on the samba server, I did the following:

```

morrow@saturn:~$ sudo  adduser --no-create-home --disabled-login --shell /bin/false smbread
Adding user `smbread' ...
Adding new group `smbread' (1002) ...
Adding new user `smbread' (1002) with group `smbread' ...
Not creating home directory `/home/smbread'.
Changing the user information for smbread
Enter the new value, or press ENTER for the default
    Full Name []: 
    Room Number []: 
    Work Phone []: 
    Home Phone []: 
    Other []: 
Is the information correct? [Y/n] Y
morrow@saturn:~$ sudo smbpasswd -a smbread
New SMB password:
Retype new SMB password:
Added user smbread.
morrow@saturn:~$ sudo smbpasswd -e smbread
Enabled user smbread.
morrow@saturn:~$ sudo net usershare add series /media/md3/series "" smbread:r
morrow@saturn:~$ sudo net usershare info series
[series]
path=/media/md3/series
comment=
usershare_acl=SATURN\smbread:R,
guest_ok=n


morrow@saturn:~$ cd /media/md3/series/
morrow@saturn:/media/md3/series$ sudo chown -R smbread ./ && sudo chgrp -R smbread ./ && sudo chmod -R 770 ./
morrow@saturn:/media/md3/series$ sudo service smbd restart
smbd stop/waiting
smbd start/running, process 7029

```

I have no idea what I'm doing wrong. Does someone have an idea? Help is much appreciated

---

### Post by volkswagner on 2014-01-04
Perhaps the .credentials file is malformed or not readable by SAMBA.


Do you have cifs installed on the client?

```
mount.cifs -V

```


Can you mount it with credentials in plain text?

```
mount -t cifs //win-share-hostname/share /mnt/win -o username=user,password=passwd,domain=xxx
```


I'm not sure if it makes a difference but I usually put the option at the end of the command.

```
sudo mount -t cifs //10.5.5.5/series /media/shares/series -o credentials=/etc/.smbcredentials
```

---

### Post by Dreadslayer on 2014-01-04
Thanks for your answer volkswagner.

```

morrow@sedna:~$ mount.cifs -V
mount.cifs version: 6.0

```

I dont think the credentials file is malformed:

```

morrow@sedna:~$ cat /etc/.smbcredentials 
username=smbread
password=Asdf12345

```

also these bring up the same error:

```

morrow@sedna:~$ sudo mount -t cifs //10.5.5.5/series /media/shares/series -o credentials=/etc/.smbcredentials
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
morrow@sedna:~$ sudo mount -t cifs //10.5.5.5/series /media/shares/series -o username=smbread,password=Asdf12345
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

---

### Post by volkswagner on 2014-01-04
Did you restart samba after changing password?

Can the user smbread access the share directly on the server using smbclient?

I'm not sure if it's required, but I usually include the workgroup name as in domain=workgroup in above statement.

Also run testparm on server.

```
testparm
```

---

### Post by Dreadslayer on 2014-01-04
> **volkswagner said:**
> Did you restart samba after changing password?

Yes, I executed this:

```
sudo service smbd restart
```

> **volkswagner said:**
> Can the user smbread access the share directly on the server using smbclient?

Do you mean something like this (Executed on the server)?

```

morrow@saturn:~$ smbclient -U smbread //10.5.5.5/series
Enter smbread's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]
smb: \> ls
NT_STATUS_ACCESS_DENIED listing \*

```

> **volkswagner said:**
> I'm not sure if it's required, but I usually include the workgroup name as in domain=workgroup in above statement.

Also run testparm on server.

Adding "domain=workgroup" still throws the error.

```
morrow@saturn:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions


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
    usershare owner only = No
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

```

---

### Post by volkswagner on 2014-01-04
As you can see there is no share defined in smb.conf.

I have never setup usershare so I can't comment on best practices.

If you don't need users to create there own shares (purpose of usershare) I'd just setup a standard share inside smb.conf.

Check out samba docs for more help.
[http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)

or

[https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html)

---

### Post by Morbius1 on 2014-01-04
> [series]
path=/media/md3/series
comment=
usershare_acl=SATURN\smbread:R,
guest_ok=n
Let me volunteer for the stupid question. Did you verify the permissions along the entire path to /series to make sure smbread can open /media then /media/md3 to get to /series?

```
ls -al /media/md3
```

---

