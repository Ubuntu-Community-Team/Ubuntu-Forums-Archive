---
title: "Samba Configuration Difficulties"
date: 2009-11-15
forum: Server Platforms
---

### Post by jakj on 2009-11-15
Using standard Ubuntu 9.10 32-bit. I have configured two shares, one of which is /home/foo/share, the other which is /aux/share. (/aux is a second hard drive mount.) Both directories have these permissions.

drwxr-xr-x  2  foo  foo  .....  share

I am able to manipulate both directories normally from a terminal on the host box. My Windows box is able to gain read access to both shares, but only the /home/foo/share allows write access. /aux/share cannot be written to or modified at all.

[musteline aux]
        path = /aux/share
        writeable = yes
;       browseable = yes
        valid users = foo

[musteline]
        path = /home/foo/share
        writeable = yes
;       browseable = yes
        valid users = foo

I tried to access it in Nautilus on the host box, and again it denied permission to /aux/share even on the same box, when going through Samba instead of direct access.

Tried using both nautilus-share package and, now, system-config-samba package.

---

### Post by capscrew on 2009-11-15
> **jakj said:**
> Using standard Ubuntu 9.10 32-bit. I have configured two shares, one of which is /home/foo/share, the other which is /aux/share. (/aux is a second hard drive mount.) Both directories have these permissions.

drwxr-xr-x  2  foo  foo  .....  share

I am able to manipulate both directories normally from a terminal on the host box. 

Are you using smbclient or are you interacting directly with the Linux filesystem?

> 
My Windows box is able to gain read access to both shares, but only the /home/foo/share allows write access. /aux/share cannot be written to or modified at all.

Have you added the Windows box user (if different) to the the smbusers database? ```
smbpasswd -a <windows_user>
```

If not then it thinks the user is a guest.

> 

[musteline aux]
        path = /aux/share
        writeable = yes
;       browseable = yes
        valid users = foo

[musteline]
        path = /home/foo/share
        writeable = yes
;       browseable = yes
        valid users = foo

The above does not allow for guests.  I believe that *guests ok =no * is the default.  In addition in the global smb.conf section you need to specify the *bad user *directive.  Bad user means Samba can't find the user, so it will default to a specified guest account.

> 
I tried to access it in Nautilus on the host box, and again it denied permission to /aux/share even on the same box, when going through Samba instead of direct access.

Tried using both nautilus-share package and, now, system-config-samba package.

The most direct way fix is to edit the /etc/samb/smb.conf file.  If you use Nautilus to configure then the bulk of the config files are at /var/lib/samba.

The best information is at the [**_[COLOR="DarkSlateGray"]Samba [/COLOR]_**]("http://samba.org/samba/docs/")website.  The one I think will serve you the best is the [**_[COLOR="DarkSlateGray"]By Example[/COLOR]_**]("http://samba.org/samba/docs/man/Samba-Guide/") guide.

---

