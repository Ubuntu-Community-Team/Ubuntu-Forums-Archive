---
title: "set access restrictions for SFTP authenticated via LDAP"
date: 2011-06-21
forum: Server Platforms
---

### Post by vilwarin on 2011-06-21
Hey Ho!

what I try to set up is an ubuntu based SFTP server, 
that allows users existing in LDAP
read/write access to certain directories
depending on their membership of certain LDAP groups.

e.g. uid=john is member of cn=admin
so he should have full access to /ftp 
but uid=jane, member of cn=team
should only have read access to /ftp/something
none should be able to read/write or even list anything outside of /ftp


I managed to set up OpenSSH to allow SFTP-access to read / for all users that can authenticate via LDAP. But I find nothing that would allow me to restrict this access.
chroot-jail only seems to work for users existing locally being member of a certain group. However none of the LDAP-users exist locally, so this seems no option.

Any help or ideas would be appreciated!

vilwarin

---

### Post by luvshines on 2011-06-21
If the LDAP users are honored on the system, you should be able to set the access restrictions that you want.
Does your system list LDAP users if you hit```

getent passwd # List all users

id <an-LDAP-user> # Get info of a particular user
```

---

### Post by vilwarin on 2011-06-22
thanks luvshines for your input!

getent passwd lists all exisiting LDAP users
and id gives me some details about them.
So this looks fine. :)

So I tried the sftp-server Match directive (see below), but once that directive is there, no LDAP user can connect to the sftp-server anymore:

```
Subsystem sftp internal-sftp
Match User john
    ChrootDirectory /srv/ftp
    AllowTCPForwarding no
    X11Forwarding no
    ForceCommand internal-sftp

```

I also tried to use the userid returned by id john, but it won't take the id either.

Here's what sftp -v -v john@localhost returns:
```

sftp -v -v john@localhost
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [::1] port 22.
debug1: connect to address ::1 port 22: Connection refused
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: connect to address 127.0.0.1 port 22: Connection refused
ssh: connect to host localhost port 22: Connection refused
Couldn't read packet: Connection reset by peer

```

let's see why the connection was refused: /var/log/auth.log doesn't list anything. the last entry is giving me sudo rights to restart sshd.
/var/log/syslog also doesn't say anything about that. strange. 

If I uncomment #Match User john in sshd.conf everything works. All users are chroot-jailed to /srv/ftp and /var/log/auth.log shows successfull authentification via LDAP.

So although LDAP users and groups are known to the system, I seem unable to use them with the Match clause in sshd.conf. Or were you thinking of something else?

---

### Post by vilwarin on 2011-06-22
I found the problem! :)

Most tutorials and articles (like this one: [http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)) on the web tell you to make the chroot-jail clause in sshd.conf like this:

```

Match group sftponly
    ChrootDirectory /home/%u
    X11Forwarding no
    AllowTcpForwarding no
    ForceCommand internal-sftp

```

However as can be guessed from the indentation, the Match clause needs to be closed! Strange that all tutorials/articles seem to be missing this crucial point. 
Anyway the Match User and Group work perfectly well with LDAP. :) The correct entry in sshd.conf looks like this:

```

Subsystem sftp internal-sftp
Match Group mygroup
    ChrootDirectory /srv/ftp
    AllowTCPForwarding no
    X11Forwarding no
    ForceCommand internal-sftp
Match

```

hope this helps someone, stumbling into the same pitfall!

---

