---
title: "SSH server logs me out immediately?"
date: 2006-06-15
forum: Server Platforms
---

### Post by jolzee on 2006-06-15
Ok so I'm experiencing a bit of a problem SSHing on my Ubuntu Dapper box.

Ive been trying to figure this out for a while now and it's driving me nuts.
[B]
Problem description:[/B]


1. I ssh to it either from a remote box or from the same machine back to to itself
2. I'm asked for my password - fine
3. I'm presented with the intro notice from Ubuntu a note about having new mail, a last login time, etc
4. I immediately logged out by the server. :mad: 

```
jolzee@ubuntu-jolzee:~$ ssh jolzee@localhost -v
OpenSSH_4.2p1 Debian-7ubuntu3, OpenSSL 0.9.8a 11 Oct 2005
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/jolzee/.ssh/identity type -1
debug1: identity file /home/jolzee/.ssh/id_rsa type -1
debug1: identity file /home/jolzee/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.2p1 Debian-7ubuntu3
debug1: match: OpenSSH_4.2p1 Debian-7ubuntu3 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.2p1 Debian-7ubuntu3
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /home/jolzee/.ssh/known_hosts:3
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/jolzee/.ssh/identity
debug1: Trying private key: /home/jolzee/.ssh/id_rsa
debug1: Trying private key: /home/jolzee/.ssh/id_dsa
debug1: Next authentication method: password
jolzee@localhost's password:
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_GB.UTF-8
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
Linux ubuntu-jolzee 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have new mail.
Last login: Thu Jun 15 12:00:45 2006 from localhost.localdomain
debug1: channel 0: free: client-session, nchannels 1
Connection to localhost closed.
debug1: Transferred: stdin 0, stdout 0, stderr 33 bytes in 0.1 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 460.4
debug1: Exit status 254
jolzee@ubuntu-jolzee:~$
```

The Auth log **/etc/log/auth.log** reports the following:

```
Jun 15 12:16:51 localhost sudo:   jolzee : TTY=pts/0 ; PWD=/etc/ssh ; USER=root ; COMMAND=/etc/init.d/ssh stop
Jun 15 12:16:51 localhost sshd[4779]: Received signal 15; terminating.
Jun 15 12:16:56 localhost sudo:   jolzee : TTY=pts/0 ; PWD=/etc/ssh ; USER=root ; COMMAND=/etc/init.d/ssh start
Jun 15 12:16:56 localhost sshd[21914]: Server listening on 0.0.0.0 port 22.
Jun 15 12:17:01 localhost CRON[21924]: (pam_unix) session opened for user root by (uid=0)
Jun 15 12:17:01 localhost CRON[21924]: (pam_unix) session closed for user root

Jun 15 12:18:24 localhost sshd[22082]: Accepted password for jolzee from 127.0.0.1 port 54414 ssh2
Jun 15 12:18:24 localhost sshd[22099]: (pam_unix) session opened for user jolzee by (uid=0)
Jun 15 12:18:24 localhost sshd[22099]: error: PAM: pam_open_session(): Cannot make/remove an entry for the specified session
```

The weird thing is that sometimes I can login. Although one I've logged out of that session, I'm no longer able to login again using that user account. 
I can however use another account on the box which allows me in then refuses me access the next time around.

I've got no firewall restricting trafic and I know the ssh server is running:

```
jolzee@ubuntu-jolzee:~$ nmap localhost

Starting Nmap 4.03 ( http://www.insecure.org/nmap/ ) at 2006-06-15 12:05 BST
Interesting ports on localhost.localdomain (127.0.0.1):
(The 1669 ports scanned but not shown below are in state: closed)
PORT     STATE SERVICE
22/tcp   open  ssh
25/tcp   open  smtp
631/tcp  open  ipp
1723/tcp open  pptp
2000/tcp open  callbook

Nmap finished: 1 IP address (1 host up) scanned in 0.207 seconds
```

I've tried unistalling and reinstalling to no avail. I've even tried appending **AllowUser jolzee** to the end of **sshd_config**. The problem really seems to be with PAM and I've got no idea what to do next.
my **/etc/ssh/sshd_config** is the default so I would expect everything to work as per all the tutorials (Attached if anyone wants to have a look). 

Has anyone seen this before? :?:

---

### Post by DouglasDD on 2007-12-07
It's not just you.  
Also, it's not just Ubuntu (or Linux)

It's happening to me now on my Mac OS X box, after upgrading from Tiger (10.4.10) to Leopard (10.5.1).  

I'm getting the same symptoms, and even the same trace messages from `ssh -vvv` and `sshd -ddd` when trying to `ssh me@localhost`.

I'm using a hand-compiled sshd (from fink), which was compiled against the old (10.4) system's PAM libraries, which have probably change with my (10.5) major system update.  

Probably the same issue here for Ubuntu users. 
Suggested actions: [re]install your PAM and sshd packages to new versions that are consistent with your current OS release.  

(granted the message I'm replying to is a year+ old, but if I found it on Google others might too!)

Happy Hacking
./ddd

---

