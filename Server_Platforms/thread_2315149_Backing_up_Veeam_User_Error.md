---
title: "Backing up Veeam User Error"
date: 2016-02-26
forum: Server Platforms
---

### Post by Paul_Swiatek on 2016-02-26
Hi All 

I'm trying to create account on a 14.04 LTS Ubuntu Server, for which veeam backup with use for guest indexing will login, and backup the server.

I create the user as follows.

```
sudo adduser veeambackup
sudo gpasswd -a veeambackup sudo
```

I then modify the sudoers file with visudo to add the lines "Defaults:veeambackup !requiretty" and "veeambackup  ALL=(ALL) NOPASSWD: ALL"

```

#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset
Defaults        mail_badpass
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
Defaults:veeambackup !requiretty


# Host alias specification


# User alias specification


# Cmnd alias specification


# User privilege specification
root    ALL=(ALL:ALL) ALL


# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL


# See sudoers(5) for more information on "#include" directives:


#includedir /etc/sudoers.d


veeambackup  ALL=(ALL) NOPASSWD: ALL



```


This all works fine, and I can see in the auth.log the server connecting via SSH, running commands, and whatnot.

However when I try to modify line "veeambackup  ALL=(ALL) NOPASSWD: ALL" to limit what hosts this connection can come through it all breaks,


I've tried


```

veeambackup  abc.bbb.ccc.ddd=(ALL) NOPASSWD: ALL
veeambackup  veeamhostname=(ALL) NOPASSWD: ALL
veeambackup  veeamhostname.domain.com=(ALL) NOPASSWD: ALL

```
&
```

Host_Alias VEEAMSRV = abc.bbb.ccc.ddd,veeamhostname,veeamhostname.domain.com
veeambackup  VEEAMSRV=(ALL) NOPASSWD: ALL

```

Errors in the auth.log as as follows

```
Feb 26 13:00:23 server01 sshd[1352]: Accepted password for veeambackup from AAA.BBB.CCC.DDD port 49616 ssh2
Feb 26 13:00:23 server01 sshd[1352]: pam_unix(sshd:session): session opened for user veeambackup by (uid=0)
Feb 26 13:00:23 server01 sudo: pam_unix(sudo:auth): conversation failed
Feb 26 13:00:23 server01 sudo: pam_unix(sudo:auth): auth could not identify password for [veeambackup]
Feb 26 13:00:23 server01 sshd[1352]: pam_unix(sshd:session): session closed for user veeambackup
```

Can anyone provide insight into what I might be doing wrong.

Veaam gives me this error.
```
 2/26/2016 1:00:42 PM :: Checking Linux credentials Error: Failed to run command with sudo: no tty present and no askpass program specified 
```

Only post on the veeam forums I can find is this.
[https://forums.veeam.com/vmware-vsphere-f24/failed-to-run-command-with-sudo-t26973.html](https://forums.veeam.com/vmware-vsphere-f24/failed-to-run-command-with-sudo-t26973.html)


Cheers,

---

