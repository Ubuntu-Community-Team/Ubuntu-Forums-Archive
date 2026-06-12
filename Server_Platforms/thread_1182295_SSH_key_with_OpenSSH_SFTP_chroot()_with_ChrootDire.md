---
title: "SSH key with OpenSSH SFTP chroot() with ChrootDirectory"
date: 2009-06-08
forum: Server Platforms
---

### Post by orudie on 2009-06-08
Greetings.
I cant find a way to to connect with ssh key when using chroot in sshd_config. What should the path to the authorized_keys br when following instructions in the following guide [http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

---

### Post by orudie on 2009-06-09
Double posting because no replay in 10 hours. If anyone knows please let me know.

---

### Post by orudie on 2009-06-09
anyone?

---

### Post by ram.coelho on 2009-06-20
Hi,

  This worked for everybody but me:


It is on a VMWare 64 bits running Ubuntu 8.10:

uname -a:
Linux server 2.6.27-7-server #1 SMP Fri Oct 24 07:37:55 UTC 2008 i686 GNU/Linux

This is what I am trying to do.
What follows was done locally, but happens just the same on remote clients:


user@server:/var$ sftp 192.45.2.137
Connecting to 192.45.2.137...
user@192.45.2.137's password:
Couldn't read packet: Connection reset by peer



/var/log/auth.log:

Jun 18 20:45:57 server sshd[23658]: debug1: Bind to port 22 on ::.
Jun 18 20:45:57 server sshd[23658]: Server listening on :: port 22.
Jun 18 20:45:57 server sshd[23658]: debug1: Bind to port 22 on 0.0.0.0.
Jun 18 20:45:57 server sshd[23658]: Server listening on 0.0.0.0 port 22.
Jun 18 20:46:03 server sshd[23658]: debug1: Forked child 23664.
Jun 18 20:46:03 server sshd[23664]: debug1: rexec start in 5 out 5 newsock 5 pipe 7 sock 8
Jun 18 20:46:03 server sshd[23664]: debug1: inetd sockets after dupping: 3, 3
Jun 18 20:46:03 server sshd[23664]: Connection from 192.45.2.137 port 42626
Jun 18 20:46:03 server sshd[23664]: debug1: Client protocol version 2.0; client software version OpenSSH_5.1p1 Debian-3ubuntu1
Jun 18 20:46:03 server sshd[23664]: debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*
Jun 18 20:46:03 server sshd[23664]: debug1: Enabling compatibility mode for protocol 2.0
Jun 18 20:46:03 server sshd[23664]: debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1
Jun 18 20:46:05 server sshd[23664]: debug1: user user matched group list sftp at line 80
Jun 18 20:46:05 server sshd[23664]: debug1: PAM: initializing for "user"
Jun 18 20:46:05 server sshd[23664]: debug1: PAM: setting PAM_RHOST to "192.45.2.137"
Jun 18 20:46:05 server sshd[23664]: debug1: PAM: setting PAM_TTY to "ssh"
Jun 18 20:46:05 server sshd[23664]: Failed none for user from 192.45.2.137 port 42626 ssh2
Jun 18 20:46:06 server sshd[23664]: debug1: PAM: password authentication accepted for user
Jun 18 20:46:06 server sshd[23664]: debug1: do_pam_account: called
Jun 18 20:46:06 server sshd[23664]: Accepted password for user from 192.45.2.137 port 42626 ssh2
Jun 18 20:46:06 server sshd[23664]: debug1: monitor_child_preauth: user has been authenticated by privileged process
Jun 18 20:46:06 server sshd[23664]: debug1: PAM: establishing credentials
Jun 18 20:46:06 server sshd[23664]: pam_unix(sshd:session): session opened for user user by (uid=0)
Jun 18 20:46:06 server sshd[23671]: debug1: SELinux support disabled
Jun 18 20:46:06 server sshd[23671]: debug1: PAM: establishing credentials
Jun 18 20:46:06 server sshd[23664]: User child is on pid 23671
Jun 18 20:46:06 server sshd[23664]: debug1: PAM: cleanup
Jun 18 20:46:06 server sshd[23664]: debug1: PAM: deleting credentials
Jun 18 20:46:06 server sshd[23664]: debug1: PAM: closing session
Jun 18 20:46:06 server sshd[23664]: pam_unix(sshd:session): session closed for user user



/etc/passwd:

user:1003:1003:User,,,:/:/usr/sbin/nologin



/etc/group:

sftp:1004:user



/etc/ssh/sshd_config:

# Logging
SyslogFacility AUTH
LogLevel DEBUG
Subsystem sftp internal-sftp
Match group sftp
ForceCommand internal-sftp
ChrootDirectory /var/sshbox



user@server:/var$ ls -l
drwxr-x--- 2 root root 4096 2009-06-18 20:05 sshbox



Did I miss something?

---

### Post by jayleonfb99 on 2010-02-08
I was having the same issue.  I had no idea where to put the authorized_keys file.  After some trial and error i found out the home directory in /etc/passwd has to be set to /home/username, that's the only way it will work.  If I change the users home directory in /etc/passwd to /username it won't work.  The .ssh directory has to have the authorized_key file, and also be in /home/username, not /home/username/home/username.  Obviously you need to create /home/username/home/ and /home/username/home/username.  Good stuff!

---

