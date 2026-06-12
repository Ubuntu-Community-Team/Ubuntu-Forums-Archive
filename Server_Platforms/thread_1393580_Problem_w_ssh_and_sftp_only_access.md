---
title: "Problem w ssh and sftp only access"
date: 2010-01-29
forum: Server Platforms
---

### Post by adrian18w on 2010-01-29
Hi Guys,

I have tried to set up my server with couple users, and I wanted for each one to have access only to his folder in the public html section. I had to do a clean install of openssh. I found online a tutorial that gave some hints, and I came up with this sshd_config, but once the user tries to login to sftp the connection is dropped. What can be wrong?

I'm running openssh5.3 with ssl and ubuntu 8.04 LTS.

```

#	$OpenBSD: sshd_config,v 1.80 2008/07/02 02:24:18 djm Exp $

# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.

# This sshd was compiled with PATH=/usr/bin:/bin:/usr/sbin:/sbin

# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options change a
# default value.

Port 32
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::

# Disable legacy (protocol version 1) support in the server for new
# installations. In future the default will change to require explicit
# activation of protocol 1
Protocol 2

# HostKey for protocol version 1
#HostKey /etc/ssh/ssh_host_key
# HostKeys for protocol version 2
#HostKey /etc/ssh/ssh_host_rsa_key
#HostKey /etc/ssh/ssh_host_dsa_key

# Lifetime and size of ephemeral version 1 server key
#KeyRegenerationInterval 1h
#ServerKeyBits 1024

# Logging
# obsoletes QuietMode and FascistLogging
#SyslogFacility AUTH
#LogLevel INFO

# Authentication:

#LoginGraceTime 2m
PermitRootLogin no
#StrictModes yes
#MaxAuthTries 6
#MaxSessions 10

#RSAAuthentication yes
#PubkeyAuthentication yes
#AuthorizedKeysFile	.ssh/authorized_keys

# For this to work you will also need host keys in /etc/ssh/ssh_known_hosts
#RhostsRSAAuthentication no
# similar for protocol version 2
#HostbasedAuthentication no
# Change to yes if you don't trust ~/.ssh/known_hosts for
# RhostsRSAAuthentication and HostbasedAuthentication
#IgnoreUserKnownHosts no
# Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes

# To disable tunneled clear text passwords, change to no here!
PasswordAuthentication yes
#PermitEmptyPasswords no

# Change to no to disable s/key passwords
#ChallengeResponseAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes
#KerberosGetAFSToken no

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

# Set this to 'yes' to enable PAM authentication, account processing, 
# and session processing. If this is enabled, PAM authentication will 
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
#UsePAM no

#AllowAgentForwarding yes
#AllowTcpForwarding yes
#GatewayPorts no
#X11Forwarding no
#X11DisplayOffset 10
#X11UseLocalhost yes
#PrintMotd yes
#PrintLastLog yes
#TCPKeepAlive yes
#UseLogin no
#UsePrivilegeSeparation yes
#PermitUserEnvironment no
#Compression delayed
#ClientAliveInterval 0
#ClientAliveCountMax 3
#UseDNS yes
#PidFile /var/run/sshd.pid
#MaxStartups 10
#PermitTunnel no
#ChrootDirectory none

# no default banner path
#Banner none

# override default of no subsystems
#Subsystem	sftp	/usr/libexec/sftp-server
Subsystem sftp internal-sftp

# Example of overriding settings on a per-user basis
#Match User anoncvs
#	X11Forwarding no
#	AllowTcpForwarding no
#	ForceCommand cvs server

Match User dama1
      ChrootDirectory /home/public_html/abcabcabc.com/public
      ForceCommand internal-sftp
      X11Forwarding no
      AllowTcpForwarding no
```

Thanks :)

---

### Post by cdenley on 2010-01-29
Are you sure you're using openssh5.3? Did you compile it yourself? What are the permissions on the chroot directory?
```

ls -ld /home/public_html/abcabcabc.com/public

```

Any clues in auth.log?
```

grep sshd /var/log/auth.log

```

---

### Post by adrian18w on 2010-01-29
The permissions are: drwxrwxr-x.

I compiled it myself from freshly downloaded source, sure it's 5.3 . I have couple users, if the username is not in the match user block in sshd_config, he is able to login normally, but has access to all the folders.

The log shows:

```
Jan 29 15:05:14 mail sshd[3045]: Accepted password for dama1 from 96.xxx.xxx.xxx port 4193 ssh2
Jan 29 15:05:14 mail sshd[3047]: fatal: bad ownership or modes for chroot directory component "/home/public_html/"

```

Hmm, I check that folder and I get:

drwxrwxr-x 5 root root 4096

---

### Post by cdenley on 2010-01-29
Is "/home/public_html/" owned by root?
> 
**ChrootDirectory**
Specifies a path to chroot(2) to after authentication.  *This path, and all its components, must be root-owned directories* that are not writable by any other user or group.

```

sudo chmod 755 /home/public_html
sudo chown root:root /home/public_html

```

Make sure all the components are owned by root.
```

chrootdir="/home/public_html/abcabcabc.com/public"
ls -ld "$chrootdir"
while [ "$chrootdir" != "/" ]
do
    chrootdir=`dirname "$chrootdir"`
    ls -ld "$chrootdir"
done

```

---

### Post by adrian18w on 2010-01-29
/home/public_html is owned by root. When I run the script i got:

```
-rwxrwxr-x 1 dama dama    88 Jan 29 09:47 index.php
-rw-r--r-- 1 adi  adi  41089 Jan 29 13:05 logo.JPG
drwxr-xr-x 6 root root 4096 Jan 28 12:50 /home/public_html/abcabcabc.com
drwxr-xr-x 5 root root 4096 Jan 28 12:50 /home/public_html
drwxr-xr-x 6 root root 4096 Jan 29 13:49 /home
drwxr-xr-x 21 root root 4096 Jul  3  2008 /
```

Those two files index.php and logo.JPG were put by other users not using the chroot system.

---

### Post by cdenley on 2010-01-29
Sorry, forgot a "d" in that code. Anyway perhaps you need to take away write permission from the root group.
```

sudo chmod 755 /home/public_html/abcabcabc.com/public

```

Other than that, the permissions look correct to me.

---

### Post by adrian18w on 2010-01-29
I run that command and still nada, same error:

```
fatal: bad ownership or modes for chroot directory "/home/public_html/abcabcabc.com/public
```

](*,)

---

### Post by cdenley on 2010-01-29
Is it owned by root? I thought you said it was, but I think you were referring to "/home/public_html", not "/home/public_html/abcabcabc.com/public".
```

sudo chown root:root /home/public_html/abcabcabc.com/public

```
As I pointed out, all the components of that path must be owned by root and writable by no other user.

---

### Post by adrian18w on 2010-01-29
Well the ../public was owned by two users, now that I set it up to be owned by root, I can login and enter it :D


But i'm not able to write to that folder :( since it's owned by the root.

---

### Post by cdenley on 2010-01-29
> **adrian18w said:**
> Well the ../public was owned by two users, now that I set it up to be owned by root, I can login and enter it :D


But i'm not able to write to that folder :( since it's owned by the root.

That is correct. The directory must not be writable by a non-root user.

---

### Post by adrian18w on 2010-01-29
> **cdenley said:**
> That is correct. The directory must not be writable by a non-root user.

But I would want my nonroot user to write in that folder.

Ok, so I have changed the chroot to /home/public_html/abcabcabc.com, set the owner of /home/public_html/abcabcabc.com/public back again to dama1 and group and now everything works great :)

Thank you for the help :D

---

### Post by hugo87 on 2010-09-15
> **adrian18w said:**
> Well the ../public was owned by two users, now that I set it up to be owned by root, I can login and enter it :D


But i'm not able to write to that folder :( since it's owned by the root.

Each file or directory can only be owned by ONE user at a time; don't confuse users and groups.

---

### Post by tacom6 on 2010-10-08
Hey guys.

Can anything be done about .bash files that show up in the chrooted folder? For instance can they be hidden so they are not visible when a user SFTPs?

Thanks! :)

---

