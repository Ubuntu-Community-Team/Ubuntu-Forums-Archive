---
title: "SSH Chrooting to Jail environment not working for non-root users"
date: 2010-05-21
forum: Security
---

### Post by anagri on 2010-05-21
I have a Dell E6500, Ubuntu Karmic Koala 64 bit. 

I have created a jail environment on my laptop using instructions [https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

The chroot environment is working fine. I am now trying to create a ssh jailed environment using the instructions [http://www.debian.org/doc/manuals/securing-debian-howto/ap-chroot-ssh-env.en.html](http://www.debian.org/doc/manuals/securing-debian-howto/ap-chroot-ssh-env.en.html)

The chroot environment is working fine for my root user, but when I try to login using other created user (eg. jail0), the terminal hangs after giving these output on client side
==========
Linux ****** 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:27 UTC 2010 x86_64

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

Last login: Fri May 21 00:13:30 2010 from localhost
==========

The server side log is following
==========
May 21 21:00:03 ******* sshd[25172]: debug1: rexec start in 5 out 5 newsock 5 pipe 7 sock 8
May 21 21:00:03 ******* sshd[1290]: debug1: Forked child 25172.
May 21 21:00:03 ******* sshd[25172]: debug1: inetd sockets after dupping: 3, 3
May 21 21:00:03 ******* sshd[25172]: Connection from ::1 port 46301
May 21 21:00:03 ******* sshd[25172]: debug1: Client protocol version 2.0; client software version OpenSSH_5.1p1 Debian-6ubuntu2
May 21 21:00:03 ******* sshd[25172]: debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
May 21 21:00:03 ******* sshd[25172]: debug1: Enabling compatibility mode for protocol 2.0
May 21 21:00:03 ******* sshd[25172]: debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2
May 21 21:00:03 ******* sshd[25172]: debug1: list_hostkey_types: ssh-rsa,ssh-dss
May 21 21:00:03 ******* sshd[25172]: debug1: SSH2_MSG_KEXINIT sent
May 21 21:00:03 ******* sshd[25172]: debug1: SSH2_MSG_KEXINIT received
May 21 21:00:03 ******* sshd[25172]: debug1: kex: client->server aes128-cbc hmac-md5 none
May 21 21:00:03 ******* sshd[25172]: debug1: kex: server->client aes128-cbc hmac-md5 none
May 21 21:00:03 ******* sshd[25172]: debug1: SSH2_MSG_KEX_DH_GEX_REQUEST received
May 21 21:00:03 ******* sshd[25172]: debug1: SSH2_MSG_KEX_DH_GEX_GROUP sent
May 21 21:00:03 ******* sshd[25172]: debug1: expecting SSH2_MSG_KEX_DH_GEX_INIT
May 21 21:00:03 ******* sshd[25172]: debug1: SSH2_MSG_KEX_DH_GEX_REPLY sent
May 21 21:00:03 ******* sshd[25172]: debug1: SSH2_MSG_NEWKEYS sent
May 21 21:00:03 ******* sshd[25172]: debug1: expecting SSH2_MSG_NEWKEYS
May 21 21:00:03 ******* sshd[25172]: debug1: SSH2_MSG_NEWKEYS received
May 21 21:00:03 ******* sshd[25172]: debug1: KEX done
May 21 21:00:03 ******* sshd[25172]: debug1: userauth-request for user jail0 service ssh-connection method none
May 21 21:00:03 ******* sshd[25172]: debug1: attempt 0 failures 0
May 21 21:00:03 ******* sshd[25172]: debug1: PAM: initializing for "jail0"
May 21 21:00:03 ******* sshd[25172]: debug1: PAM: setting PAM_RHOST to "localhost"
May 21 21:00:03 ******* sshd[25172]: debug1: PAM: setting PAM_TTY to "ssh"
May 21 21:00:03 ******* sshd[25172]: Failed none for jail0 from ::1 port 46301 ssh2
May 21 21:00:03 ******* sshd[25172]: debug1: userauth-request for user jail0 service ssh-connection method publickey
May 21 21:00:03 ******* sshd[25172]: debug1: attempt 1 failures 0
May 21 21:00:03 ******* sshd[25172]: debug1: test whether pkalg/pkblob are acceptable
May 21 21:00:03 ******* sshd[25172]: debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
May 21 21:00:03 ******* sshd[25172]: debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
May 21 21:00:03 ******* sshd[25172]: debug1: temporarily_use_uid: 1001/1002 (e=0/0)
May 21 21:00:03 ******* sshd[25172]: debug1: trying public key file /home/jail0/.ssh/authorized_keys
May 21 21:00:03 ******* sshd[25172]: debug1: restore_uid: 0/0
May 21 21:00:03 ******* sshd[25172]: debug1: temporarily_use_uid: 1001/1002 (e=0/0)
May 21 21:00:03 ******* sshd[25172]: debug1: trying public key file /home/jail0/.ssh/authorized_keys2
May 21 21:00:03 ******* sshd[25172]: debug1: restore_uid: 0/0
May 21 21:00:03 ******* sshd[25172]: Failed publickey for jail0 from ::1 port 46301 ssh2
May 21 21:00:06 ******* sshd[25172]: debug1: userauth-request for user jail0 service ssh-connection method password
May 21 21:00:06 ******* sshd[25172]: debug1: attempt 2 failures 1
May 21 21:00:06 ******* sshd[25172]: debug1: PAM: password authentication accepted for jail0
May 21 21:00:06 ******* sshd[25172]: debug1: do_pam_account: called
May 21 21:00:06 ******* sshd[25172]: Accepted password for jail0 from ::1 port 46301 ssh2
May 21 21:00:06 ******* sshd[25172]: debug1: PAM: establishing credentials
May 21 21:00:06 ******* sshd[25172]: pam_unix(sshd:session): session opened for user jail0 by (uid=0)
May 21 21:00:07 ******* sshd[25172]: debug1: Entering interactive session for SSH2.
==========


I think the issue is with permissions for /dev/pts, or some permissions/privileges issue with users.

Can someone point me how solve this issue.

Thanks,
Amiruddin Nagri

---

### Post by bodhi.zazen on 2010-05-21
I can no tell what your problem is from that output.

Depending on what you are trying to accomplish, it may be easier to use LXC (Linux containers) or ssh keys with forced commands.

[http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/](http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/)

With LXC you can mount (bind) any shared directories you wish ($Home, var/www/site) and you will achieve very nice isolation.

---

### Post by kevdog on 2010-05-23
Can you tell me more about LXC and what other applications you may use this?  Is it different than a jail?

---

### Post by bodhi.zazen on 2010-05-24
> **kevdog said:**
> Can you tell me more about LXC and what other applications you may use this?  Is it different than a jail?

LXC, AKA Linux Containers are similar to (BSD) jails or chroot or OpenVZ, however they are not the same thing.

The technology can be used to isolate a single application (such as a ssh server or a web server) or an entire system (think VPS).

The capability is part of the mainstream kernel, so unlike Openvz, there is no need to apply any type of kernel patch.

LXC use cgroups to manage resources.

LXC is in rapid development and both user tools, migration tools, and documentation are lagging (which is the downside).

There will soon be an option to mount the host file system ro and use it as a guest.

The reason I suggested it as an option, however, it IMO it is as easy to learn LXC as it is to learn to run a ssh server in a chroot, both will take some time and trial and error.

See : [http://www.ibm.com/developerworks/linux/library/l-lxc-containers/index.html](http://www.ibm.com/developerworks/linux/library/l-lxc-containers/index.html)

---

