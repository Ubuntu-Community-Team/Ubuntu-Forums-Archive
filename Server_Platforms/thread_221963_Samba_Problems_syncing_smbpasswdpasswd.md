---
title: "Samba: Problems syncing smbpasswd/passwd"
date: 2006-07-24
forum: Server Platforms
---

### Post by dhoughal on 2006-07-24
Dear all!

Since several days I'm trying to get Samba's unix password sync to work for me, but I still have problems. I'm using the Samba 3.0.22 binaries that come with Ubuntu 6.06 and this is the [global] section of my smb.conf:

[global]
workgroup = TEST
domain logons = yes
preferred master = yes
wins support = yes
username map = /etc/samba/smbusers
syslog = 100
add machine script = /usr/sbin/useradd -s /bin/false -d /var/lib/nobody '%u'
logon path = \\%L\profiles\%U
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n

When I'm logged on to my WinXP workstation and try to change my SMB password, Windows hangs, doesn't respond anymore. Im my log.smbd I get the following message:

[2006/07/24 13:03:55, 0] lib/debug.c:reopen_logs(597)
Unable to open new log file /var/log/samba/log.smbd: Permission denied

Sometimes, this lets the Samba server hang up (no restart possible), so that I have to reboot the server machine. When rebooted, the smbpasswd/passwd sync is made.

Any idea how to solve this problem?

Cheers
Bernd

---

### Post by LordHunter317 on 2006-07-24
This indicates you either:[list][*]Have a serious configuration problem[*]Are hitting a samba bug[/list]First, /var/log is writable by root, correct?  The filesystem isn't getting mounted read-only or something (usually in response to an HDD error)?

If so, you are starting Samba as root, correct?  I can't see how you wouldn't be, but I need to ask anyway.

---

### Post by dhoughal on 2006-07-24
> **LordHunter317 said:**
> This indicates you either:[list][*]Have a serious configuration problem[*]Are hitting a samba bug[/list]First, /var/log is writable by root, correct?  The filesystem isn't getting mounted read-only or something (usually in response to an HDD error)?

Yes. /var/log/samba and the files log.nmbd and log.smbd are writeable by root. 

> **LordHunter317 said:**
> If so, you are starting Samba as root, correct?  I can't see how you wouldn't be, but I need to ask anyway.

I've installed Samba using Synaptic. Samba is started on server boot, so I assume that it is started as root.

---

### Post by LordHunter317 on 2006-07-24
Then it is.  I think you've found a bug.

---

