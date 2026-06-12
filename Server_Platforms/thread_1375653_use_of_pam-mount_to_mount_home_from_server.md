---
title: "use of pam-mount to mount home from server"
date: 2010-01-08
forum: Server Platforms
---

### Post by dinuzz on 2010-01-08
hi there
 
I'm trying to mount the home directories of the users on the server to the respective desktops. I would like to use the libpam-mount module. do you guys know, how make it run? Im using 9.10 both server and desktop and the most recent pam-mount module.
 
I know that the **/etc/security/pam_mount.conf.xml** needs to be edited.
 
I added the following to it:
```
 
<volume user="username" fstype="cifs" server="IP-Server" path="/home/username" mountpoint="/media/server" />

``` 
 
anybody successfully made it run?
 
 
cheers

---

### Post by BkkBonanza on 2010-01-08
I believe you want to use %(USER) variables in your volume statement, 
and mount to the user's home, eg.

**<volume fstype="cifs" server="IP-Server" path="/server_path_to_homes/%(USER)" mountpoint="~" />**

Note no user tag if you don't want to limit which user can mount the volume. You may use sgrp="whatever" if you want a group of users to have remote mounted homes.

You may also want,
**<mkmountpoint enable="1" remove="true" />**
if you don't have user home directories existing for each user on all machines.

And then you will need to add the pam_mount module to the pam stack for logins. On Ubuntu I believe this is "/etc/pam.d/common-auth". I'm not sure about that but I've been looking at how my encrypted home gets mounted and this appears to be the right place to add,

**auth    optional        pam_mount.so** 

More info here,
[http://manpages.ubuntu.com/manpages/karmic/man5/pam_mount.conf.5.html](http://manpages.ubuntu.com/manpages/karmic/man5/pam_mount.conf.5.html)

You may want to enable debug mode in the conf to help track down what isn't right.
It's been a while since I did this, so I'm going on memory here.

---

### Post by dinuzz on 2010-01-08
Hmmm... Still doesn't work, how can I get to the debug information to check whats going wrong?
thanks

---

### Post by BkkBonanza on 2010-01-08
According to the docs,

<debug enable="1" />

in the pam_mount.conf.xml should output log messages to /var/log/syslog (and also stderr). I haven't tried it. If you get some output relayed to pam_mount then post it here and maybe can help.

---

### Post by dinuzz on 2010-01-08
Hmmm, this entry in the syslog seems interesting:

```
Jan  8 16:04:24 desktop kernel: [   42.965294]  CIFS VFS: cifs_mount failed w/return code = -6
```

---

### Post by BkkBonanza on 2010-01-08
As far as I can tell that -6 error means "non-existant share". I couldn't find a reliable docs page defining the error codes so this may not be right.

I may be wrong up above regarding the user=... maybe you need it so pam passes on the user name for authenticating like, user="%(USER)"

Make sure any mount you try can be mounted manually first before trying it through the pam_mount. It's too bad it doesn't seem to give more info about the actual mount it's trying.

---

### Post by dinuzz on 2010-01-08
Yeah - Tried to look for the same explanation, but found the same info in different forums...
 
I mounted the share already manually and it worked fine... I will test this later again, since Im working on a virtual machine, both client and server... so this could be an issue...
 
will test this later on a different infrastructure and post back here if the same error occurs and also if I was successful...
 
thanks for now...

---

### Post by BkkBonanza on 2010-01-08
Regarding my idea for user="..." - I now think that is wrong. I believe the user needs to be passed as a mount option after the mount point... so smbmount gets it.
eg.

<volume fstype="cifs" server="IP-Server" path="/server_path_to_homes/%(USER)" mountpoint="~" options="username=%(USER)" />

Here is a useful page,
[http://www.kroon.co.za/howto.php?howto=cifs_pam_mount](http://www.kroon.co.za/howto.php?howto=cifs_pam_mount)
it's OLD so uses the old format for the volume. But I think some of the other info is probably right. Like there needs to be two entries made in /etc/pam.d/common-auth - one for auth and one for session.

---

### Post by dinuzz on 2010-01-10
all right, I tested the config on my other infrastructure... it works now... pretty easy, all I had to do is adding the share definition to the config file /etc/security/pam_mount.conf.xml


the user needs to be added to the share definition, since the credentials will be used from the login procedure on ubuntu login.

thanks
cheers

---

### Post by BkkBonanza on 2010-01-10
Can you post a working example of the config file. I would be interested in the final syntax that works. Thanks.

---

### Post by dinuzz on 2010-01-11
Yes, here we go:
 
```
<?xml version="1.0" encoding="utf-8" ?>
<!DOCTYPE pam_mount SYSTEM "pam_mount.conf.xml.dtd">
<!--
    See pam_mount.conf(5) for a description.
-->
 
<pam_mount>
 
<!-- Volume definitions -->
 
<volume  user="username"  fstype="cifs"  server="192.168.1.100"  path="%(USER)" mountpoint="/media/server" />
 
<!-- pam_mount parameters: General tunables -->
 
<debug enable="0" />
<!--
<luserconf name=".pam_mount.conf.xml" />
-->
 
<!-- Note that commenting out mntoptions will give you the defaults.
     You will need to explicitly initialize it with the empty string
     to reset the defaults to nothing. -->
<mntoptions allow="nosuid,nodev,loop,encryption,fsck,nonempty,allow_root,allow_other" />
<!--
<mntoptions deny="suid,dev" />
<mntoptions allow="*" />
<mntoptions deny="*" />
-->
<mntoptions require="nosuid,nodev" />
<path>/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin</path>
 
<logout wait="0" hup="0" term="0" kill="0" />
 
 
        <!-- pam_mount parameters: Volume-related -->
 
<mkmountpoint enable="1" remove="true" />
 
 
</pam_mount>

```

---

### Post by dinuzz on 2010-01-11
And here's a working Samba configuration example:
 
```
[global]
    workgroup = workgroup
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
    disable spoolss = Yes
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
 
[homes]
    comment = Home of user "%S"
    valid users = %S
    read only = No
    create mask = 0775
    directory mask = 0775
    browseable = No
    browsable = No

```

---

### Post by thabeat on 2010-05-03
I have a similar problem but don't get how you solved it.

I'm using LDAP authentication on a domain controller, now, the user can login on the client when only added to the domain server, but, it has no /home/user so cannot log on gdm. 

My idea was to use pam_mount to pick his home from the server (the home dir is shared)

This is my conf.xml: ```
<pam_mount>

<!-- Volume definitions -->
<!--
%(USER)
        The username of the user logging in.
%(DOMAIN_NAME), %(DOMAIN_USER)
        Winbind has special UNIX usernames in the form of "domain\username",
        and %(DOMAIN_NAME) and %(DOMAIN_USER) provide the split parts of it.
        This is useful when a sharename on an MSAD server is the same as the username,
        e.g. <volume fstype="cifs" server="fsbox" path="%(DOMAIN_USER)" />.
%(USERUID), %(USERGID)
        The numeric UID and GID of the primary group of the user logging in.
        This is obtained via getpw*(), not getuid().
        It is useful in conjunction with the uid= or gid= mount options,
        e.g. <volume options="uid=%(USERUID)" />.
        Note that you do not need to specify uid=%(USERUID) for smbfs or cifs
        mounts because this is already done automatically by pam_mount.
%(GROUP)
        The name of the group for %(USERGID).
-->

<volume user="%(USER)" fstype="cifs" server="192.168.1.205" path="/home/%(USER)" mountpoint="~" options="uid=%(USERUID),gid=%(USERGID),serverino,iocharset=utf8"/>

<!-- pam_mount parameters: General tunables -->

<debug enable="1" />

<!--
<luserconf name=".pam_mount.conf.xml" />
-->

<!-- Note that commenting out mntoptions will give you the defaults.
     You will need to explicitly initialize it with the empty string
     to reset the defaults to nothing. -->
<mntoptions allow="nosuid,nodev,loop,encryption,fsck,nonempty,allow_root,allow_other" />
<!--
<mntoptions deny="suid,dev" />
<mntoptions allow="*" />
<mntoptions deny="*" />
-->
<mntoptions require="nosuid,nodev" />

<path>/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin</path>

<logout wait="0" hup="0" term="0" kill="0" />

<!-- pam_mount parameters: Volume-related -->

<mkmountpoint enable="1" remove="true" />

</pam_mount>

```

And this is the debug on stderr when loging in console mode: 

```
May  3 19:30:30 ubuntCLIENT kernel: [15708.401071] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
May  3 19:30:30 ubuntCLIENT kernel: [15708.401134]  CIFS VFS: Send error in SessSetup = -13
May  3 19:30:30 ubuntCLIENT kernel: [15708.540930]  CIFS VFS: cifs_mount failed w/return code = -13
May  3 19:30:40 ubuntCLIENT kernel: [15718.574775] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
May  3 19:30:40 ubuntCLIENT kernel: [15718.574819]  CIFS VFS: Send error in SessSetup = -13
May  3 19:30:40 ubuntCLIENT kernel: [15718.710285]  CIFS VFS: cifs_mount failed w/return code = -13

```

It seems like doesn't find the share... maybe some permission problems? the users are added on the samba shared /home as valid users. Do I miss something?


Thanks!

---

