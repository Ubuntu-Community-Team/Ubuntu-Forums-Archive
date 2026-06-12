---
title: "Apparmor_parser will not accept standard input"
date: 2012-03-10
forum: Security
---

### Post by Iotos on 2012-03-10
Hey forumgoers, 
I've recently set up a new samba share, and it works beautifully. The problem I have run into however first manifested when I tried to load an apparmor profile for samba.

The command I am using is:
```
cat /etc/apparmor.d/usr.sbin.smbd | sudo apparmor_parser -r

```

The response I am getting is:
```
Warning from stdin (line 1): apparmor_parser: cannot use or update cache, disable, or force-complain via stdin

```

I am using a slightly modified version of the default samba profile provided through apparmor-profiles, so thinking it was my modification, tried the vanilla profile, and got the same. Tried the whole command as root, made no difference. Got frustrated, tried other unmodified stock profiles, same error. Tried a nearly blank profile with a single correct line as a control, same error. File system permissions are all good.

sudo apparmor_status reveals that all the stock vanilla profiles are loaded. It just won't let me overwrite any of them. Removing and trying to add fresh gave the same error.

Mighty google has turned up nothing on this one, and the only other similar problem on the forum had additional information which pointed to a profile error. Its giving me no other info.

It doesn't seem to make any difference what I input, but here is my profile. Its just the stock one plus two lines:```
 #include <tunables/global>

/usr/sbin/smbd {
  #include <abstractions/authentication>
  #include <abstractions/base>
  #include <abstractions/consoles>
  #include <abstractions/cups-client>
  #include <abstractions/nameservice>
  #include <abstractions/samba>
  #include <abstractions/user-tmp>
  #include <abstractions/wutmp>

  capability net_bind_service,
  capability setgid,
  capability setuid,
  capability sys_resource,
  capability sys_tty_config,

  /etc/mtab r,
  /etc/printcap r,
  /proc/*/mounts r,
  /usr/sbin/smbd mr,
  /var/cache/samba/** rwk,
  /var/cache/samba/printing/printers.tdb mrw,
  /var/lib/samba/** rwk,
  /var/lib/samba/printers/** rw,
  /var/run/cups/cups.sock rw,
  /var/run/dbus/system_bus_socket rw,
  /var/run/samba/** rk,
  /var/run/samba/smbd.pid rw,
  /var/log/samba/cores/smbd/ rw,
  /var/log/samba/cores/smbd/** rw,
  /var/spool/samba/** rw,
  <MYFOLDERNAME> r,
  <MYFOLDERNAME>** rwkix,

  @{HOMEDIRS}/** lrwk,

  # Site-specific additions and overrides. See local/README for details.
  #include <local/usr.sbin.smbd>
}
```

For all I know, it might be something ridiculously easy, but I've been banging my head on this for nearly four hours. If anyone has some insights to share, it would be hugely appreciated.

---

### Post by Dave_L on 2012-03-10
```
sudo apparmor_parser -r /etc/apparmor.d/usr.sbin.smbd
```

---

### Post by Iotos on 2012-03-11
Thank you so much Dave, I cant believe I wasted so much time on that. Me: noob, You: hero.

---

### Post by Dave_L on 2012-03-11
No problem. :)

---

