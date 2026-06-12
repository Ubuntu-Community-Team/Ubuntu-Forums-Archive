---
title: "Banner in xinetd"
date: 2018-02-12
forum: Server Platforms
---

### Post by lp.descamps on 2018-02-12
hi
i tried to use /etc/motd as banner for ssh in xinetd but no luck.

```
cat /etc/xinetd.d/ssh 
service NONE
{
        type		= UNLISTED
	socket_type     = stream
        port		= 35350
	protocol        = tcp
        wait            = no
        user            = root
        server          = /usr/sbin/sshd
        server_args     = -i
        per_source      = UNLIMITED
        log_on_failure  = USERID HOST
	banner		= /etc/motd
}

```

```
cat /etc/motd
The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.

```

if i use sshd it´s working but if i stop sshd and use xinetd, i dont get the banner

thanks

---

