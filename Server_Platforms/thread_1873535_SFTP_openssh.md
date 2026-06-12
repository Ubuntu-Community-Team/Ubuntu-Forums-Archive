---
title: "SFTP openssh"
date: 2011-11-01
forum: Server Platforms
---

### Post by benj2400 on 2011-11-01
Dear All,

I'm on Ubuntu Server 10.04 LTS 64bit. I've install OpenSSH. I've configure SFTP with ChrootDirectory. It work very fine but last week I've do an update (bad idea) an after this SFTP doesn't work any more. OpenSSH is now OpenSSH_5.3p1 Debian-3ubuntu7, OpenSSL 0.9.8k 25 Mar 2009

I've in my sshd_config :
Subsystem sftp /usr/lib/openssh/sftp-server  Match group sftpuser ChrootDirectory /srv/XXXX/%u X11Forwarding no AllowTcpForwarding no ForceCommand internal-sftpthe directory on wich I do the chroot have right like this :
drwxr-xr-x 6 root root 

I've this in my log (sshd on debug 3)
reprocess config:90 setting ChrootDirectory /srv/XXXX/%u debug3: reprocess config:91 setting X11Forwarding no debug3: reprocess config:92 setting AllowTcpForwarding no debug3: reprocess config:93 setting ForceCommand internal-sftp
.....
debug3: safely_chroot: checking '/' fatal: bad ownership or modes for chroot directory component "/"

I know that a lot of package have change when I've do the update.

Thanks very much for your help

---

### Post by benj2400 on 2011-11-03
I've found :

chown root.admin /
chmod 755 /

Very simple.

---

