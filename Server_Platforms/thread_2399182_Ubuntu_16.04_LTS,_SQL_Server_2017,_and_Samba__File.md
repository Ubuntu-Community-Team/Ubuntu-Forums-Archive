---
title: "Ubuntu 16.04 LTS, SQL Server 2017, and Samba:  File Permission Problems"
date: 2018-08-22
forum: Server Platforms
---

### Post by kcconnor on 2018-08-22
I have a windows active directory domain run by two Server 2012R2 domain controllers, and a slew of MS-SQL servers (on windows server OS) in a dev/qa sandbox ranging from SQL2005 to SQL2017.  I need to deploy SQL2017 on linux into this sandbox environment, and I need to facilitate a windows-oriented workgroup being able to drop SQL .bak files onto an SMB/CIFS share using their preexisting domain creds, use windows authentication on MS-SQL on linux, and retrieve .BAK files from this server and transfer them elsewhere.

In order to accomplish this, SCP and FTP and NFS are not going to be acceptable solutions for file transfer.  Nor is a Samba config that uses its own internal credentialing.  I need to manage access via conventional Windows domain ACL's.

I've installed Ubuntu Server 16.04 LTS onto a HyperV server.

I've installed MS-SQL 2017 Dev edition according to Microsoft's instructions here:
[https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-ubuntu?view=sql-server-2017](https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-ubuntu?view=sql-server-2017)

I've enabled SQL Server Windows Authentication according to Microsoft's instructions here:
[https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-active-directory-authentication?view=sql-server-2017](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-active-directory-authentication?view=sql-server-2017)

And I've attempted to integrate Samba file sharing into my 2012R2 AD structure for this SQL Server as a member server.
My /etc/samba/smb.conf file:

```

[global]
workgroup = MYDOMAIN
realm = MYDOMAIN.COM
client signing = yes
client use spnego = yes
netbios name = MYLINUXSQLSERVER
security = ads
dedicated keytab file = /etc/krb5.keytab
kerberos method = secrets and keytab
domain master = no
local master = no
preferred master = no
os level = 20
dns forwarder = ip.of.AD.Server
idmap config *:backend = tdb
idmap config *:range = 5000-6000
idmap config MYDOMAIN:backend = rid
idmap config MYDOMAIN:range = 50000-60000
template homedir = /home/%U
template shell = /bin/bash
winbind use default domain = yes
winbind expand groups = 4
winbind offline logon = yes
winbind nss info = rfc2307
winbind refresh tickets = yes
winbind normalize names = yes
winbind enum users = yes
winbind enum groups = yes
vfs objects = acl_xattr
map acl inherit = yes
store dos attributes = yes
encrypt passwords = yes
name resolve order = host lmhosts wins bcast
map to guest = bad user
host msdfs = no
username map = /etc/samba/user.map
unix extensions = no
reset on zero vc = yes
hide unreadable = yes
load printers = no
printing = bsd
printcap name = /dev/null
disable spoolss = yes

[Backup]
path = /var/opt/mssql/backup
browseable = yes
read only = no

```

File permissions of /var/opt/mssql/backup (my target for SMB file transfers to and from this environment):
```


drwxrwx---+ 2 myadminaccount@mydomain.com domain admins@mydomain.com 4096 Aug 21 21:29 backup
drwxr-xr-x  2 mssql                   mssql                         4096 Aug 21 13:38 data
drwxr-xr-x  2 mssql                   mssql                         4096 Aug 22 08:32 log
-rw-rw-r--  1 mssql                   mssql                          119 Aug 21 14:14 mssql.conf
drwxr-xr-x  2 mssql                   mssql                         4096 Aug 21 14:07 secrets
drwxrwxr-x  2 mssql                   mssql                         4096 Aug 21 14:21 sqlbackup


```

With this config, I am able to open Computer Management on a Windows computer device while logged in as "myadminaccount@mydomain.com" and Windows Share Permissions are defaulted to Everyone (and I can adjust the Share Permissions to focus on relevant groups)... but when I attempt to adjust Windows File Permissions, I get the attached screenshot's series of errors when attempting to take ownership of the share/folder.  I cannot browse the folder, I cannot write anything to the folder with its current permissions (I get "Access is Denied" prompt in windows and request for alternate credentials).
[ATTACH=CONFIG]280814[/ATTACH]

Can anyone point me in a direction to go with this?  I'm not seeing any meaningful log events in anything in /var/log/samba.  Time of log files doesn't change when I attempt to open the share from a windows client and the files there don't contain anything pertaining to the connection attempt.

Some additional info:  kinit and klist results

```

administrator@MYLINUXSQLSERVER:/var/log/samba$ kinit myadminaccount
Password for myadminaccount@MYDOMAIN.COM:
administrator@MYLINUXSQLSERVER:/var/log/samba$ klist
Ticket cache: FILE:/tmp/krb5cc_1000_vOHKAs
Default principal: myadminaccount@MYDOMAIN.COM

Valid starting       Expires              Service principal
08/22/2018 09:22:25  08/22/2018 19:22:25  krbtgt/MYDOMAIN.COM@MYDOMAIN.COM
        renew until 08/29/2018 09:22:21


```

wbinfo -u and wbinfo -g return all the users and groups in my domain.

---

### Post by darkod on 2018-08-23
Maybe Samba internal credentials are not useful to you, but I would still create one matching linux user myadminaccount with matching password on the ubuntu server. And add it as Samba user too.

I believe that helps this user to control the Windows ACL on the backup folder. After that other users would have permissions you set in the ACL (in theory).

---

