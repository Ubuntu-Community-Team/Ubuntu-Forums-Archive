---
title: "Moving contents of /var/backup/site1 to a Windows 2003 NAS server share"
date: 2007-10-06
forum: Server Platforms
---

### Post by kpm on 2007-10-06
I have a LAMP server being used to develop an intranet.  I am using cron to dump the MySQL database to /var/backup/site1/ on an hourly, daily, and weekly basis. However, the LAMP server itself is not being backed up in our Windows environment so I am attempting to mount a Windows backup share on the LAMP server so I can dump the MySQL database there but have not been able to.

We are in an Windows Active Directory environment and I  have successfully brought the LAMP server into the AD domain.  I have also shared the /var/www/ directory so Windows client users who belong to the 'webmaster' security group can access that share.

I created a a service account with  user name ' backup'  and gave backup full read write permissions to the //Windows2003Server/backupShare directory and I am issuing the following commands:

```
mkdir /mnt/backUpDirectory
```

```
mount -t smbfs -o -username=backup,password=secret //Windows2003Server/backupShare /mnt/backUpDirectory
```

Then I get the following result and error:
```

opts: rw
opts: -username=backup
opts: password=secret
passthrough options '-username=backup'
mount.smbfs started (version 3.0.22)
added interface ip=10.2.0.26 bcast=10.2.15.255 nmask=255.255.240.0
resolve_hosts: Attempting host lookup for name Windows2003Server<0x20>
Connecting to 10.2.0.11 at port 445
15351: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

```

If I test the ability of the user backup to see the shares on the Windows2003Server with the following command:

```
smbclient -L Windows2003Server/backupShare -U backup
```

A list of sharenames, servers,  and all the clients on the WAN are listed

I am logged in as root on the LAMP server.
Can anyone fill me in on what I am forgetting?

Thanks

---

### Post by HermanAB on 2007-10-06
Active Directory - my sincere condolences...

Check some things:
$ wbinfo -t
If it fails, then you didn't join the domain.

$ wbinfo -u
List of users should be returned.

$ wbinfo -g
List of groups should be returned.

Test authentication:
$ kinit [email]username@DOMAIN.TLD[/email]

If nothing is returned, and there are no errors in /var/log/messages, then it is OK.

With smbclient, it gets more complicated.  You have to do Kerberos authentication, using the '-k' parameter:
smbclient -k \\\\server\\share -U username%password

'Hope that helps!

Herman

---

