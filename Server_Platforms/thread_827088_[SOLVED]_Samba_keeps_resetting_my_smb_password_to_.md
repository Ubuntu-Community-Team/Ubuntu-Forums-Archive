---
title: "[SOLVED] Samba keeps resetting my smb password to the unix user password"
date: 2008-06-12
forum: Server Platforms
---

### Post by schallstrom on 2008-06-12
I'm running Ubuntu 8.04 Server Edition with a samba server. I set the samba password for the user like this:
```

$ sudo smbpasswd -a user

```
After doing it I can access the share with the password I configured via smbpasswd.

Now comes the strange thing: After a few minutes I can't access the share via this password anymore but only with the unix password of the user on the server! When I then set the password on the server again via smbpasswd, I again am able to access the share via this password and after a few minutes the story starts from the beginning.

My conclusion was that samba is on hardy per default configured in a way that it synchronizes the smbpasswd passwords with the shadow passwords and disabled this in smb.conf explicitly:
```

unix password sync = No

```
But to no avail... Whats going on?

I don't want the samba password to be the same as the unix password as I want to store the samba password in plain text in a credentials file on the client so I don't always have to type it when I mount the share.

Any hints would be greatly appreciated.

---

### Post by molotov00 on 2008-06-12
```
unix password sync = no
```

Note the lowercase n. Then restart samba.

```
sudo /etc/init.d/samba restart
```

---

### Post by andguent on 2008-06-12
Agreed with above. Also as a quick tip, always test your configuration with the command "testparm".

An advanced usage:
```
testparm -s 2>&1|grep unix
```

Linux is almost always case sensitive. There are many good reasons for it to be this way, none of which I will bore you with. :)

---

### Post by schallstrom on 2008-06-12
Thanks for your replies, but your suggestion does not apply.

Here's an example from the [official Samba guide]("http://us1.samba.org/samba/docs/man/Samba-Guide/simple.html#id341373"):
```

[global]
workgroup = MIDEARTH
printing = CUPS
printcap name = CUPS
map to guest = Bad User
[COLOR="Red"]show add printer wizard = No[/COLOR]
wins support = yes
[FTMFILES]
comment = Funds Tracking & Management Files
path = /data/ftmfiles
[COLOR="Red"]read only = No[/COLOR]
...

```

Here's the output of testparm:
```

Load smb config files from smb.conf
Processing section "[homes]"
Processing section "[media]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

```

---

### Post by andguent on 2008-06-12
Would you mind posting the rest of testparm? I'm still curious how it shows the unix password sync.

---

### Post by schallstrom on 2008-06-13
I found out that the default is already that syncing is disabled:
```

$ sudo testparm -sv /etc/samba/smb.conf|grep unix
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[media]"
Loaded services file OK.
Server role: ROLE_STANDALONE
        unix charset = UTF-8
        unix password sync = No
        unix extensions = Yes

```

Without the -v option "user password sync" does not get displayed at all because "No" is the default.

---

### Post by andguent on 2008-06-14
I assume you have restarted samba and/or the server recently. Other than that, I'm running out of ideas. Does google searching come up with anything?

---

### Post by schallstrom on 2008-06-14
> **andguent said:**
> I assume you have restarted samba and/or the server recently. Other than that, I'm running out of ideas. Does google searching come up with anything?

Restarting the Samba server fortunately does not change the passwords of the users.

I solved the problem in the meantime thanks to the ubuntu mailing list: I installed samba through tasksel which also installed the package libpam-smbpass. Ant this lib syncs the samba password with the unix passwords independently from any samba config. Removing the package resolved the issue.

Thanks anyway!

---

