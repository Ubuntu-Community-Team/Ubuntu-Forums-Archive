---
title: "OpenSSH Chroot + LDAP"
date: 2009-02-19
forum: Server Platforms
---

### Post by DeepThoughts on 2009-02-19
I've set up my server to chroot some sftp users (instead of running an ftp server), which worked really good until I threw in OpenLDAP in the mix. After setting up OpenLDAP (which is a p.i.t.a. since Ubuntus documentation page about OpenLDAP is wrong) and migrating users and the sftponlygroup to LDAP people in the sftponly-group can login but they are unable to perform "ls" and therefore can't view the contents of the server.

As I said this worked fine when OpenLDAP wasn't running and no changes have been made to the sshd_config. All user that aren't in the sftponly-group can login and ls without issues.

As I understand it SSH logs to /var/log/auth.log and this is how it looks like for a chrooted user when it fails:

```
Feb 18 15:29:06 [hostname] sshd[19959]: Accepted password for [username] from [ip] port [port] ssh2
Feb 18 15:29:07 [hostname] sshd[19959]: pam_unix(sshd:session): session opened for user [user] by (uid=0)
Feb 18 15:29:07 [hostname] sshd[19959]: User child is on pid 19967
Feb 18 15:29:07 [hostname] sshd[19967]: Changed root directory to "/home/chroot/"
Feb 18 15:29:28 [hostname] sshd[19959]: pam_unix(sshd:session): session closed for user [user]
```

This is my chroot-config:

```
Match group sftponly
         ChrootDirectory /home/chroot
         X11Forwarding no
         AllowTcpForwarding no
         ForceCommand internal-sftp
```

Can someone tell me what the issue is or at least point me to where I can find more information about what's failing?

---

### Post by DeepThoughts on 2009-03-03
So after a little bit troubleshooting I've found this:

If I comment out ldap from the group entry in /etc/nsswitch.conf the users can login in the server again but they must be a member of the local sftponly group (kinda obvious). My /etc/nsswitch.conf looks like this after my modification:

```
# pre_auth-client-config # passwd:         compat
passwd: files ldap
# pre_auth-client-config # group:          compat
group: files #ldap
# pre_auth-client-config # shadow:         compat
shadow: files ldap

```

The million dollar question is: Why doesn't it work with ldap enabled for the group? Is it because the group exists directly on the server and in the LDAP-tree? Or have configured the ldap-server wrong? (Highly probabable)

Please any help would be appreciated

---

