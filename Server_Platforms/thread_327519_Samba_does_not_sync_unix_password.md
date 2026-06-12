---
title: "Samba does not sync unix password"
date: 2006-12-29
forum: Server Platforms
---

### Post by Martin-Robert on 2006-12-29
Hello Samba-cracks

On a dapper server, I have installed Samba, security = user, but no PDC settings, since this is a very small network.  Everything works, except that after a change of the Samba password with

sudo smbpasswd -a <samba-user>

the unix password of the equally named unix user is not adapted.:(  Can anybody give me a hint what's wrong?

Here is a copy of the [global] section of smb.conf:

[global]

   workgroup = ARBEITSGRUPPE

   security = user

   encrypt passwords = true

   invalid users = root

   server string = %h (Samba, Ubuntu)

   dns proxy = no

   log file = /var/log/samba/log.%m

   max log size = 1000

   syslog = 0

   panic action = /usr/share/samba/panic-action %d

   passdb backend = tdbsam

   obey pam restrictions = yes

    unix password sync = yes

   passwd program = /usr/bin/passwd %u

   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

   socket options = TCP_NODELAY

---

