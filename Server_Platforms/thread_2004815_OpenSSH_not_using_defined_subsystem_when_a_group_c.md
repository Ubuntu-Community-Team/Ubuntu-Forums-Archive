---
title: "OpenSSH not using defined subsystem when a group connects."
date: 2012-06-16
forum: Server Platforms
---

### Post by thingdeux on 2012-06-16
Ubuntu Server 11.04

Very odd issue here and I'm hoping it's just  some config setting I missed.  I've set ssh to use the internal-sftp  subsystem (config below) but it seems users in one group do not invoke  that subsystem when they connect.  I use a generic 'sftponly' group for  permissions to the folders and when a user from that group connects the  process that runs is sshd instead of the subsystem 'internal-sftp' and  no verbose logging is done.  I'm not sure why -  'log output below'


Relevant components of my sshd_config file: (I think)
```

# Logging
SyslogFacility AUTH
LogLevel VERBOSE

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*
Subsystem sftp internal-sftp -f AUTH -l VERBOSE

# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

Match group sftponly
ChrootDirectory /var/sftp
X11Forwarding no
AllowTcpForwarding no
ForceCommand internal-sftp

```
Output from an administrative user logging in via SFTP and downloading a file.
```

Jun 16 19:17:03 thingdeux internal-sftp[22269]: opendir "/home/thingdeux"
Jun 16 19:17:16 thingdeux internal-sftp[22269]: opendir "/home/thingdeux/Downloads"
Jun 16 19:18:03 thingdeux internal-sftp[22285]: open "/home/thingdeux/Downloads/systraversal.py flags READ mode 0666

```Output from any user in the 'sftponly' group:
```

Jun 16 19:44:21 thingdeux sshd[1500]: Accepted password for ****from **** port **** ssh2
Jun 16 19:44:21 thingdeux sshd[1500]: pam_unix(sshd:session): session opened for user **** by (uid=0)
Jun 16 19:45:22 thingdeux sshd[1500]: pam_unix(sshd:session): session closed for user *****

```

---

