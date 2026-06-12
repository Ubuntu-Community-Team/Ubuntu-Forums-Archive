---
title: "Problems with simple samba setup"
date: 2008-05-02
forum: Server Platforms
---

### Post by DrNick on 2008-05-02
Hi All

I'm trying to set up a machine with a simple samba configuration. I've written the config file with no problems, however any time I attempt to connect to the shares it doesn't work. Firstly, the smb.conf:

```

[global]
        netbios name = TEMPSRV
        workgroup = LIPSON
        map to guest = Bad User

[ittechs]
        comment = Should not see me...
        path = /var/smb/ittechs
        read only = no
        force user = ittechs
        force group = ittechs
        guest ok = no
        nt acl support = no
        browseable = no

[msoffice]
        comment = Microsoft Office test admin share
        path = /var/smb/msoffice
        read only = no
        force user = msoffice
        force group = msoffice
        guest ok = yes
        nt acl support = no
        browseable = no

```

When connecting to the ittechs share I get asked for a username/password as expected. When entering a valid one it throws a generic error... the usual "\\tempsrv\ittechs is not accessible, you might not have permission to use the network resource" blah blah.

When trying the msoffice share (which is guest ok), no prompt for a username/password appears (it shouldn't anyway), but instead of connecting to the share it displays the same generic error again, however this time with "The user name could not be found" on the end.

Firstly, permissions are correctly set on the path of the shares. I've tripple cheked this then tripple checked again. 
```

$ ls -l /var/smb
drwsrwsr-x 2 ittechs  ittechs  4096 2008-04-30 09:28 ittechs
drwsrwsr-x 2 msoffice msoffice 4096 2008-04-30 09:28 msoffice

```

Both the ittechs and msoffice users have an smb password set, again I've checked and re-checked.
```

$ cat /etc/samba/smbpasswd
sysadmin:1000:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:B05CCCD45E8C2F5CD6F24A5559634A97:[U          ]:LCT-481B292E:
ittechs:1102:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:647DA7AB3D9D46FF7163D94D628F5F75:[U          ]:LCT-4819D3A9:
msoffice:1103:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:FA5BBDDD74D108E0E7398A06F1083DA1:[U          ]:LCT-481883E1:

```

Next, I've examined /var/log/samba/log.smbd when attempting to connect to the shares. No joy apart from this:
```

[2008/05/02 15:40:41, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/05/02 15:40:41, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users

```

I've looked this up and apparantly this is a known problem which shouldn't affect normal operation so has no relivence to my problem.

Testparm also doesn't seem to see any problems with my config:
```

$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[ittechs]"
Processing section "[msoffice]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = LIPSON
        netbios name = TEMPSRV
        map to guest = Bad User

[ittechs]
        comment = Should not see me...
        path = /var/smb/ittechs
        force user = ittechs
        force group = ittechs
        read only = No
        nt acl support = No
        browseable = No

[msoffice]
        comment = Microsoft Office test admin share
        path = /var/smb/msoffice
        force user = msoffice
        force group = msoffice
        read only = No
        guest ok = Yes
        nt acl support = No
        browseable = No

```

The only odd thing which I have been able to discover is that winbindd *is* running. Now I read somewhere that it shouldn't be unless you're doing NT domain integration, which I'm not. This should just be a standalone server.

Any hints, suggesions or help most gratefully received...

---

### Post by ghostknife on 2008-05-03
Try mounting the shares from a Linux machine first. Does it fail this way as well.

Do (and paste output):
```

smbclient -L //ip.of.server
```

Then do (and paste output):
```

mount -t cifs //ip.of.server/sharename /path/to/mountpoint
```

---

### Post by DrNick on 2008-05-06
Thanks for your reply.

Have tried connecting to the shares from another linux box, and another XP machine outside the domain (but still in LIPSON workgroup.) Both failed, the XP machine with the same errors as above and the linux machine with just a generic "I can't connect to this share" error (this was from GNOME, see below for console).

smbclient doesn't see the shares interestingly:
```

sysadmin@gatekeeper:~$ smbclient -L //10.2.159.202
Password:
Domain=[TEMPSRV] OS=[Unix] Server=[Samba 3.0.28a]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       IPC Service (Samba 3.0.28a)
Domain=[TEMPSRV] OS=[Unix] Server=[Samba 3.0.28a]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        LIPSON               LIPSON1

```

smb-mounting them doesn't work either:
```

sysadmin@gatekeeper:~$ sudo mkdir /mnt/tmp && sudo mount -t cifs //tempsrv/ittechs /mnt/tmp
[sudo] password for sysadmin:
Password:
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

If it can't even see the shares itself then something's seriously wrong. As mentioned before, winbindd is running:
```

sysadmin@gatekeeper:~$ ps aux | grep winbindd
root      5375  0.0  0.1   8068  1576 ?        Ss   Apr28   0:06 /usr/sbin/winbindd
root      5384  0.0  0.1   8192  1688 ?        S    Apr28   0:02 /usr/sbin/winbindd
root      5535  0.0  0.0   8068   880 ?        S    Apr28   0:00 /usr/sbin/winbindd
root      5536  0.0  0.1   8196  1688 ?        S    Apr28   0:01 /usr/sbin/winbindd

```
Should this be the case if the samba server is just a stand alone server with no domain integration?

Thanks again for any help anyone can give...

---

### Post by DrNick on 2008-05-06
Bump!

No suggestions anyone?

---

### Post by ghostknife on 2008-06-11
> **DrNick said:**
> Bump!

No suggestions anyone?

You still have this problem?

---

### Post by mbeach on 2008-06-11
one thing that seems to pop up now and again is forgetting to add the users who can access your shares

search for the first occurance of the string "smbpasswd"
at
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

edit:
whoops - didn't read your post thoroughly enough - you've done this already

---

