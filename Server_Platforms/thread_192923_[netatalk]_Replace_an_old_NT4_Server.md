---
title: "[netatalk] Replace an old NT4 Server"
date: 2006-06-09
forum: Server Platforms
---

### Post by the_g_cat on 2006-06-09
Hi there,

I have to replace an old NT4 server serving files through smb and appletalk. I tried to configure the netatlk so that I get one world-writable guest-only share, and a one-user only password protected share. I managed to get the guest-only share, but it's not writable. The clients are OS 8 and 9 machines. As my experience with netatlak/appletalk is null, any help would be much appreciated.

Here are my config files:
```
$ cat /etc/netatalk/afpd.conf | grep -v "^#"  | grep -v "^$"
- -transall -uamlist uams_guest.so -nosavepassword -guestname "samba"

$ cat /etc/netatalk/AppleVolumes.default | grep -v "^#"  | grep -v "^$"
/home/samba/Global      "Donald"        rwlist:guest volcharset:UTF8 options:mswindows
```

The folder the share points to is naturally 7 for the user samba, so there should be no problems on the unix side of the thing.

Thanks a lot for your help,

the_g_cat


P.S. I also need to set up the same shares with samba for NT4 Desktops, but have quirks there too, maybe you could also help me [in this topic]("http://www.ubuntuforums.org/showthread.php?t=192917")

---

