---
title: "SSH freezing after kernel update"
date: 2010-12-15
forum: Server Platforms
---

### Post by DerSeppel on 2010-12-15
Hi there, 

I'm experiencing a strange problem:

I updated the kernel on a ubuntu machine yesterday. No problems so far.
But after rebooting I couldn't login via SSH anymore. The session freezes right after authentication. Doesn't matter wether its pubkey or keyboard-interactive.

I couldn't find any hints so far. auth.log does not seem to show any warnings/errors.

Strange thing is: I'm able to log in via SFTP (SCP). I can even use WinSCP to open a "unix like" shell, but it only works for basic commands.

Here is the output of auth.log, when logging in via SFTP/SCP
```

Dec 15 09:42:41 srv01 sshd[32426]: debug1: Forked child 331.
Dec 15 09:42:41 srv01 sshd[331]: debug1: rexec start in 5 out 5 newsock 5 pipe 7 sock 8
Dec 15 09:42:41 srv01 sshd[331]: debug1: inetd sockets after dupping: 3, 3
Dec 15 09:42:41 srv01 sshd[331]: Connection from 109.91.145.14 port 7411
Dec 15 09:42:41 srv01 sshd[331]: debug1: Client protocol version 2.0; client software version WinSCP_release_4.2.9
Dec 15 09:42:41 srv01 sshd[331]: debug1: no match: WinSCP_release_4.2.9
Dec 15 09:42:41 srv01 sshd[331]: debug1: Enabling compatibility mode for protocol 2.0
Dec 15 09:42:41 srv01 sshd[331]: debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
Dec 15 09:42:41 srv01 sshd[331]: debug1: user root does not match group list scponly at line 80
Dec 15 09:42:41 srv01 sshd[331]: debug1: PAM: initializing for "root"
Dec 15 09:42:41 srv01 sshd[331]: debug1: PAM: setting PAM_RHOST to "ip-109-91-145-14.unitymediagroup.de"
Dec 15 09:42:41 srv01 sshd[331]: debug1: PAM: setting PAM_TTY to "ssh"
Dec 15 09:42:41 srv01 sshd[331]: Failed none for root from 109.91.145.14 port 7411 ssh2
Dec 15 09:42:41 srv01 sshd[331]: debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2047
Dec 15 09:42:41 srv01 sshd[331]: debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2047
Dec 15 09:42:41 srv01 sshd[331]: debug1: temporarily_use_uid: 0/0 (e=0/0)
Dec 15 09:42:41 srv01 sshd[331]: debug1: trying public key file /root/.ssh/authorized_keys
Dec 15 09:42:41 srv01 sshd[331]: debug1: fd 4 clearing O_NONBLOCK
Dec 15 09:42:41 srv01 sshd[331]: debug1: matching key found: file /root/.ssh/authorized_keys, line 1
Dec 15 09:42:41 srv01 sshd[331]: Found matching RSA key: f1:2e:b2:44:38:81:8f:27:a1:e1:2f:5b:33:e5:42:e7
Dec 15 09:42:41 srv01 sshd[331]: debug1: restore_uid: 0/0
Dec 15 09:42:41 srv01 sshd[331]: debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2047
Dec 15 09:42:41 srv01 sshd[331]: debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2047
Dec 15 09:42:41 srv01 sshd[331]: debug1: temporarily_use_uid: 0/0 (e=0/0)
Dec 15 09:42:41 srv01 sshd[331]: debug1: trying public key file /root/.ssh/authorized_keys
Dec 15 09:42:41 srv01 sshd[331]: debug1: fd 4 clearing O_NONBLOCK
Dec 15 09:42:41 srv01 sshd[331]: debug1: matching key found: file /root/.ssh/authorized_keys, line 1
Dec 15 09:42:41 srv01 sshd[331]: Found matching RSA key: f1:2e:b2:44:38:81:8f:27:a1:e1:2f:5b:33:e5:42:e7
Dec 15 09:42:41 srv01 sshd[331]: debug1: restore_uid: 0/0
Dec 15 09:42:41 srv01 sshd[331]: debug1: ssh_rsa_verify: signature correct
Dec 15 09:42:41 srv01 sshd[331]: debug1: do_pam_account: called
Dec 15 09:42:41 srv01 sshd[331]: Accepted publickey for root from 109.91.145.14 port 7411 ssh2
Dec 15 09:42:41 srv01 sshd[331]: debug1: monitor_child_preauth: root has been authenticated by privileged process
Dec 15 09:42:41 srv01 sshd[331]: debug1: PAM: establishing credentials
Dec 15 09:42:41 srv01 sshd[331]: pam_unix(sshd:session): session opened for user root by (uid=0)
Dec 15 09:42:41 srv01 sshd[331]: debug1: Entering interactive session for SSH2.
Dec 15 09:42:41 srv01 sshd[331]: debug1: server_init_dispatch_20
Dec 15 09:42:41 srv01 sshd[331]: debug1: server_input_channel_open: ctype session rchan 256 win 2147483647 max 16384
Dec 15 09:42:41 srv01 sshd[331]: debug1: input_session_request
Dec 15 09:42:41 srv01 sshd[331]: debug1: channel 0: new [server-session]
Dec 15 09:42:41 srv01 sshd[331]: debug1: session_new: session 0
Dec 15 09:42:41 srv01 sshd[331]: debug1: session_open: channel 0
Dec 15 09:42:41 srv01 sshd[331]: debug1: session_open: session 0: link with channel 0
Dec 15 09:42:41 srv01 sshd[331]: debug1: server_input_channel_open: confirm session
Dec 15 09:42:41 srv01 sshd[331]: debug1: server_input_channel_req: channel 0 request simple@putty.projects.tartarus.org reply 0
Dec 15 09:42:41 srv01 sshd[331]: debug1: session_by_channel: session 0 channel 0
Dec 15 09:42:41 srv01 sshd[331]: debug1: session_input_channel_req: session 0 req simple@putty.projects.tartarus.org
Dec 15 09:42:41 srv01 sshd[331]: debug1: server_input_channel_req: channel 0 request subsystem reply 1
Dec 15 09:42:41 srv01 sshd[331]: debug1: session_by_channel: session 0 channel 0
Dec 15 09:42:41 srv01 sshd[331]: debug1: session_input_channel_req: session 0 req subsystem
Dec 15 09:42:41 srv01 sshd[331]: subsystem request for sftp
Dec 15 09:42:41 srv01 sshd[331]: debug1: subsystem: exec() internal-sftp
Dec 15 09:42:41 srv01 sshd[426]: debug1: SELinux support disabled
Dec 15 09:42:41 srv01 sshd[426]: debug1: PAM: reinitializing credentials
Dec 15 09:42:41 srv01 sshd[426]: debug1: permanently_set_uid: 0/0

```

This is the output when trying to open a real ssh session:
```

Dec 15 09:44:41 srv01 sshd[32426]: debug1: Forked child 429.
Dec 15 09:44:41 srv01 sshd[429]: debug1: rexec start in 5 out 5 newsock 5 pipe 7 sock 8
Dec 15 09:44:41 srv01 sshd[429]: debug1: inetd sockets after dupping: 3, 3
Dec 15 09:44:41 srv01 sshd[429]: Connection from 109.91.145.14 port 7442
Dec 15 09:44:42 srv01 sshd[429]: debug1: Client protocol version 2.0; client software version PuTTY_Release_0.60
Dec 15 09:44:42 srv01 sshd[429]: debug1: no match: PuTTY_Release_0.60
Dec 15 09:44:42 srv01 sshd[429]: debug1: Enabling compatibility mode for protocol 2.0
Dec 15 09:44:42 srv01 sshd[429]: debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
Dec 15 09:44:44 srv01 sshd[429]: debug1: user root does not match group list scponly at line 80
Dec 15 09:44:44 srv01 sshd[429]: debug1: PAM: initializing for "root"
Dec 15 09:44:44 srv01 sshd[429]: debug1: PAM: setting PAM_RHOST to "ip-109-91-145-14.unitymediagroup.de"
Dec 15 09:44:44 srv01 sshd[429]: debug1: PAM: setting PAM_TTY to "ssh"
Dec 15 09:44:44 srv01 sshd[429]: Failed none for root from 109.91.145.14 port 7442 ssh2
Dec 15 09:44:44 srv01 sshd[429]: debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2047
Dec 15 09:44:44 srv01 sshd[429]: debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2047
Dec 15 09:44:44 srv01 sshd[429]: debug1: temporarily_use_uid: 0/0 (e=0/0)
Dec 15 09:44:44 srv01 sshd[429]: debug1: trying public key file /root/.ssh/authorized_keys
Dec 15 09:44:44 srv01 sshd[429]: debug1: fd 4 clearing O_NONBLOCK
Dec 15 09:44:44 srv01 sshd[429]: debug1: matching key found: file /root/.ssh/authorized_keys, line 1
Dec 15 09:44:44 srv01 sshd[429]: Found matching RSA key: f1:2e:b2:44:38:81:8f:27:a1:e1:2f:5b:33:e5:42:e7
Dec 15 09:44:44 srv01 sshd[429]: debug1: restore_uid: 0/0
Dec 15 09:44:44 srv01 sshd[429]: debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2047
Dec 15 09:44:44 srv01 sshd[429]: debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2047
Dec 15 09:44:44 srv01 sshd[429]: debug1: temporarily_use_uid: 0/0 (e=0/0)
Dec 15 09:44:44 srv01 sshd[429]: debug1: trying public key file /root/.ssh/authorized_keys
Dec 15 09:44:44 srv01 sshd[429]: debug1: fd 4 clearing O_NONBLOCK
Dec 15 09:44:44 srv01 sshd[429]: debug1: matching key found: file /root/.ssh/authorized_keys, line 1
Dec 15 09:44:44 srv01 sshd[429]: Found matching RSA key: f1:2e:b2:44:38:81:8f:27:a1:e1:2f:5b:33:e5:42:e7
Dec 15 09:44:44 srv01 sshd[429]: debug1: restore_uid: 0/0
Dec 15 09:44:44 srv01 sshd[429]: debug1: ssh_rsa_verify: signature correct
Dec 15 09:44:44 srv01 sshd[429]: debug1: do_pam_account: called
Dec 15 09:44:44 srv01 sshd[429]: Accepted publickey for root from 109.91.145.14 port 7442 ssh2
Dec 15 09:44:44 srv01 sshd[429]: debug1: monitor_child_preauth: root has been authenticated by privileged process
Dec 15 09:44:44 srv01 sshd[429]: debug1: PAM: establishing credentials
Dec 15 09:44:44 srv01 sshd[429]: pam_unix(sshd:session): session opened for user root by (uid=0)
Dec 15 09:44:44 srv01 sshd[429]: debug1: Entering interactive session for SSH2.
Dec 15 09:44:44 srv01 sshd[429]: debug1: server_init_dispatch_20
Dec 15 09:44:44 srv01 sshd[429]: debug1: server_input_channel_open: ctype session rchan 256 win 16384 max 16384
Dec 15 09:44:44 srv01 sshd[429]: debug1: input_session_request
Dec 15 09:44:44 srv01 sshd[429]: debug1: channel 0: new [server-session]
Dec 15 09:44:44 srv01 sshd[429]: debug1: session_new: session 0
Dec 15 09:44:44 srv01 sshd[429]: debug1: session_open: channel 0
Dec 15 09:44:44 srv01 sshd[429]: debug1: session_open: session 0: link with channel 0
Dec 15 09:44:44 srv01 sshd[429]: debug1: server_input_channel_open: confirm session
Dec 15 09:44:44 srv01 sshd[429]: debug1: server_input_channel_req: channel 0 request pty-req reply 1
Dec 15 09:44:44 srv01 sshd[429]: debug1: session_by_channel: session 0 channel 0
Dec 15 09:44:44 srv01 sshd[429]: debug1: session_input_channel_req: session 0 req pty-req
Dec 15 09:44:44 srv01 sshd[429]: debug1: Allocating pty.
Dec 15 09:44:44 srv01 sshd[429]: debug1: session_pty_req: session 0 alloc /dev/pts/22
Dec 15 09:44:44 srv01 sshd[429]: debug1: SELinux support disabled
Dec 15 09:44:44 srv01 sshd[429]: debug1: server_input_channel_req: channel 0 request shell reply 1
Dec 15 09:44:44 srv01 sshd[429]: debug1: session_by_channel: session 0 channel 0
Dec 15 09:44:44 srv01 sshd[429]: debug1: session_input_channel_req: session 0 req shell
Dec 15 09:44:44 srv01 sshd[520]: debug1: Setting controlling tty using TIOCSCTTY.
Dec 15 09:44:44 srv01 sshd[520]: debug1: PAM: reinitializing credentials
Dec 15 09:44:44 srv01 sshd[520]: debug1: permanently_set_uid: 0/0

```

The output of "who" shows me, that the sessions are opened and kept open, even if the client is closed. I can even see sessions from yesterday, when the problem first occured.

SSHd: OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
kernel: 2.6.32-27-server
Ubuntu: Ubuntu 10.04.1 LTS

I dont know where to look anymore. Couldnt find any clues so far.

---

### Post by puppykhan on 2010-12-16
Sounds like a rogue process. Have you tried killing all open SSH connections? Run:

> ps -auxThen kill any process that
a. is named "**sshd: *username *[priv]**"
b. is named "**sshd: *username*@pts/#**"
c. under TTY column has "**pts/#**"

Note killing one may kill the rest as they are all dependent on the same connection.

Then restart your SSH daemon for good measure.

Also, made any changes to **/etc/ssh/sshd_config** lately?

---

