---
title: "Problem preserving timestamps and permissions when copying to samba-share"
date: 2010-05-05
forum: Server Platforms
---

### Post by stn21 on 2010-05-05
Hi,

my samba-shares are mounted in fstab.

Everything works fine except for one small issue: when copying files from the local PC to the share the files are copied but the timestamps and permissions of the files are not. Instead a message "operation not permitted" appears.

'root' on the client can copy files WITH timestamp etc, a normal user cannot.

Below the line in fstab on the client and smb.conf on the server.

Any ideas?

THX, stn



/etc/fstab on client
------------------------------------------------------
//192.168.1.2/myshare /media/myshare cifs defaults,file_mode=0777,dir_mode=0777,username=me,password="" 0 0
------------------------------------------------------



/etc/samba/smb.conf on server
------------------------------------------------------
[global]
    force create mode = 777
    force directory mode = 777
    workgroup = WORKGROUP
    passdb backend = tdbsam
    printing = cups
    printcap name = cups
    printcap cache time = 750
    cups options = raw
    map to guest = Bad User
    include = /etc/samba/dhcp.conf
    logon path = \\%L\profiles\.msprofile
    logon home = \\%L\%U\.9xprofile
    logon drive = P:
    usershare allow guests = Yes
    add machine script = /usr/sbin/useradd  -c Machine -d /var/lib/nobody -s /bin/false %m$
    domain logons = Yes
    domain master = Yes
    local master = Yes
    netbios name = pc-4850
    os level = 65
    preferred master = Yes
    security = user
    usershare max shares = 100
    wins support = No
    unix extensions = no
    follow symlinks = Yes
    wide links = Yes
[homes]
    comment = Home Directories
    valid users = %S, %D%w%S
    browseable = No
    read only = No
    inherit acls = Yes
[profiles]
    comment = Network Profiles Service
    path = %H
    read only = No
    store dos attributes = Yes
    create mask = 0600
    directory mask = 0700
[users]
    comment = All users
    path = /home
    read only = No
    inherit acls = Yes
    veto files = /aquota.user/groups/shares/
[groups]
    comment = All groups
    path = /home/groups
    read only = No
    inherit acls = Yes
[printers]
    comment = All Printers
    path = /var/tmp
    printable = Yes
    create mask = 0600
    browseable = No
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/drivers
    write list = @ntadmin root
    force group = ntadmin
    create mask = 0664
    directory mask = 0775

[hdd2$]
    inherit acls = Yes
    path = /media/hdd2
    read only = No
    guest ok = Yes

[hde2$]
    inherit acls = Yes
    path = /media/hde2
    read only = No
    guest ok = Yes

[netlogon]
    comment = Network Logon Service
    path = /var/lib/samba/netlogon
    write list = root
------------------------------------------------------

---

### Post by volkswagner on 2010-05-07
You can try adding a couple extra criteria to your fstab entry.

First try adding the domain name.  If that does not work, try adding the uid and gid appropriate for actual user.





```
//192.168.1.118/share /path/to/share cifs defaults,username=DOMAINNAME/user,password=somepassword,uid=1000,gid=1000 0 0
```


Or replace defaults with 'rw' rather than specifying file_mode=0777,dir_mode=0777.

---

### Post by stn21 on 2010-05-11
> **volkswagner said:**
> You can try adding a couple extra criteria to your fstab entry.
First try adding the domain name.  If that does not work

No sure what exactly you mean. So I tried the hostname of the samba-server, it's IP, the name of the workgroup and the full internet domainname.

All authenticated the user. Giving the wrong password/username gave "access denied" (had to add 'guest ok = no' to the shares, that was frustrating :frown:)

Example (using mount, not fstab, should be the same):

```
sudo mount //<IP>/<sharename> <mountpoint> -o password="pass",username="<full nslooup-domainname>/<username>"
```None allowed the user on the client-pc to modify the timestamps and permissions on the server.






> **volkswagner said:**
>  ... try adding the uid and gid appropriate for actual user... ,uid=1000,gid=1000 ...

That works, obviously.
But only for ONE user.
I was kind of hoping for a more universal solution.

---

### Post by stn21 on 2010-05-11
Hm!

The whole issue may have something to do with the priviledges on the server itself. 
If you login a different users or root on the server itself you get some really strange phenomena too.
Starting a new thread on that ...

---

