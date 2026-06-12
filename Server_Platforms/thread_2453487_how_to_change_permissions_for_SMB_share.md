---
title: "how to change permissions for SMB share"
date: 2020-11-11
forum: Server Platforms
---

### Post by gebseng on 2020-11-11
Hello Everyone,

[COLOR=#242729][FONT=Arial]On a machine running Ubuntu Server 20.04, I want to share a local drive via SMB (CIFS?).

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]My respective entry in /etc/samba/smb.conf is:[/FONT][/COLOR]
```
[sharename]
comment = Shared Files
path = /media/sharename
browsable = yes
read only = no

```
[COLOR=#242729][FONT=Arial]
Now, when I connect to this share from a MacOS machine, using the same usernameas on the Ubuntu machine, the share shows up just fine, but is only readable. How do I make it writeable?

thanks, geb[/FONT][/COLOR]

---

### Post by howefield on 2020-11-11
Thread moved to the "*Server Platforms*" forum.

---

### Post by #&amp;thj^% on 2020-11-11
> **gebseng said:**
> Hello Everyone,

[COLOR=#242729][FONT=Arial]On a machine running Ubuntu Server 20.04, I want to share a local drive via SMB (CIFS?).

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]My respective entry in /etc/samba/smb.conf is:[/FONT][/COLOR]
```
[sharename]
comment = Shared Files
path = /media/sharename
browsable = yes
read only = no

```
[COLOR=#242729][FONT=Arial]
Now, when I connect to this share from a MacOS machine, using the same usernameas on the Ubuntu machine, the share shows up just fine, but is only readable. How do I make it writeable?

thanks, geb[/FONT][/COLOR]
I use something like this:
Change accordingly EXAMPLE ONLY.
```
[salesdoc] path = /home/shared/sales
writeable = Yes
```

---

### Post by darkod on 2020-11-11
I haven't used smb shares in a while now. First of all I would consider using nfs if possible. Linux and modern Windows versions support it, not sure about Mac.

Second, try the writeable = yes option suggested above and make sure you also check the unix permissions on the folder /media/sharename.

When a user tries to connect and use the share, it is not all about smb.conf only. The actual file permissions also play a big role. It is usually best to assign group ownership to the folder and then add all users to that group.

Of course, for any local user that connects from a client you would need to create the same user in ubuntu too, etc.

---

### Post by gebseng on 2020-11-11
Thanks for your suggestions! I'd like to stick with SMB for now.

I just found out that my other SMB shares on the Ubuntu Server machine are writeable, despite having the same entry in /etc/samba/smb.conf:

```
[sharename]
comment = Shared Files
path = /media/sharename
browsable = yes
read only = no
```

So, maybe this is, as Darko suggested, a local permissions problem. I tried ```
ls -l
``` on all my shared drives, here are the results:

```
[COLOR=#000000][FONT=Menlo]drwxr-xr-x  3 gebseng root 4096 Sep 22 21:25 [COLOR=#400bd9]**backup**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxrwxrwx 51 gebseng root 4096 Nov 11 23:33 [COLOR=#0000a3]video
[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxr-xr-x 9 root root 4096 Nov 11 00:55 [COLOR=#400BD9]**sharename**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxrwxrwx 3 bin  root 4096 Oct  9 08:48 [COLOR=#0000a3]temp[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxrwxrwx 5 root root 4096 Nov 11 23:32 [COLOR=#0000a3]time_machine[/COLOR][/FONT][/COLOR]

```

The shares **backup**, **video**, **temp**, **time_machine** are writeable over SMB by the user **gebseng**. Only the share **sharename** is not. 

Can I change that with chmod? Or do I have to change the username to **gebseng** with chown?

Thanks for your help!

geb

---

### Post by SeijiSensei on 2020-11-12
Change the username.
```
sudo chown -R gebseng sharename
```

If others need to access this directory, you'll need to explore using groups.

Another alternative if shared access is required is to use the "force user" and "force group" directives in [smb.conf]("https://www.samba.org/samba/docs/current/man-html/smb.conf.5.html").

---

### Post by TheFu on 2020-11-12
Samba access and local Unix access are different animals.  Samba runs as root, so all the permissions are handled by the smb.conf file.
Use the 
```
valid users = 
```
or
```
valid groups =
```
settings in the specific share config stanza. Also, be certain you've run smbpasswd to set passwords for these users.

You can use the *force user* and *force group* options too, if you want all samba users to write to the Unix disks with a single groupid or single userid.

If you want all users to have access and don't want to list them, use
```
valid users = %S
```
If you do that, you probably want to limit the clients which are allowed access using subnet controls.  All these settings are listed in the manpage for smb.conf. General warning about smb.conf: Unfortunately, some settings only make sense when used in combination with other settings. If only 1 of the settings are in the config file, but the others are not, it won't work. Sometimes the combined settings have to work together with specific options to work.  The valid users ones generally work without other complexities once the [global] setting of 
```
security = user
```
is set.

For anything that isn't a trivial change to the config, it is often best to find a working template in these forums for the specific client and specific server being run. In 2020, the defaults for Samba security changed which has been causing issues for people running old OSes or using old NAS systems.  Additionally, Win10 changed their defaults to improve security, also breaking access to older NAS devices.

Whenever changing any config file like the smb.conf, always make a backup BEFORE touching it.  It is common to just make a copy of the file in the same directory with a date-suffix (smb.conf-2020.11.12). Simple, quick and if you ever need to revert to that file, it is available. It is also handy to compare the new and old file once a working config has been found.

---

