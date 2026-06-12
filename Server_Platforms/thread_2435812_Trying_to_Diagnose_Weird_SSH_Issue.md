---
title: "Trying to Diagnose Weird SSH Issue"
date: 2020-01-26
forum: Server Platforms
---

### Post by springshades on 2020-01-26
I have a small box that I'm setting up to use as a small home file server, and ssh/sshd is giving me a headache.

The "server" (which is just a little mini pc connected to an external drive) is running Lubuntu 19.10. The machines connecting to it primarily run Windows 10. I have a desktop which is running Ubuntu 18.04 inside of WSL (the Windows implementation of Linux), and it can connect via ssh and RDP to the server without problems. Not sure how well known WSL is here, but it is not a VM. It's basically a program that runs inside of Windows 10. The issue is that I also have a notebook which also uses Ubuntu 18.04 inside of WSL. It seems to be able to connect to the server as long as I delete the ~/.ssh/known_hosts file first. If there is a key in known_hosts, the connection generally resets before it asks for my password. Once in a while, I'm able to log in and then the connection resets within seconds.

Seemed like maybe a firewall issue? Except I disabled ufw and set all policies in iptable to ALLOW. Still happens.

Maybe ssh is configured incorrectly on the notebook? Except I can connect to other computers from it via ssh. Just not this one.

Maybe the wifi in my house is laggy or messed up somehow? Except I have an ssh client on my phone. That works just fine.

...so it's this ONE notebook that can't connect to this ONE server, and I'm running out of ideas.


I can't make heads or tails of the debugging to see if there is anything obvious (note that I'm running the debugging on port 2222, so that I don't have to disable the main one on port 22):

```
$ sudo /usr/sbin/sshd -dd -p 2222
debug2: load_server_config: filename /etc/ssh/sshd_config
debug2: load_server_config: done config len = 257
debug2: parse_server_config: config /etc/ssh/sshd_config len 257
debug1: sshd version OpenSSH_8.0, OpenSSL 1.1.1c  28 May 2019
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-dd'
debug1: rexec_argv[2]='-p'
debug1: rexec_argv[3]='2222'
debug1: Set /proc/self/oom_score_adj from 0 to -1000
debug2: fd 3 setting O_NONBLOCK
debug1: Bind to port 2222 on 0.0.0.0.
Server listening on 0.0.0.0 port 2222.
debug2: fd 4 setting O_NONBLOCK
debug1: Bind to port 2222 on ::.
Server listening on :: port 2222.
debug1: Server will not fork when running in debugging mode.
debug1: rexec start in 5 out 5 newsock 5 pipe -1 sock 8
debug1: inetd sockets after dupping: 3, 3
Connection from 192.168.1.106 port 55682 on 192.168.1.10 port 2222
debug1: Local version string SSH-2.0-OpenSSH_8.0p1 Ubuntu-6build1
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.6p1 Ubuntu-4ubuntu0.3
debug1: match: OpenSSH_7.6p1 Ubuntu-4ubuntu0.3 pat OpenSSH_7.0*,OpenSSH_7.1*,OpenSSH_7.2*,OpenSSH_7.3*,OpenSSH_7.4*,OpenSSH_7.5*,OpenSSH_7.6*,OpenSSH_7.7* compat 0x04000002
debug2: fd 3 setting O_NONBLOCK
debug2: Network child is on pid 2743
debug1: permanently_set_uid: 121/65534 [preauth]
debug1: list_hostkey_types: rsa-sha2-512,rsa-sha2-256,ssh-rsa,ecdsa-sha2-nistp256,ssh-ed25519 [preauth]
debug1: SSH2_MSG_KEXINIT sent [preauth]
debug1: SSH2_MSG_KEXINIT received [preauth]
debug2: local server KEXINIT proposal [preauth]
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1 [preauth]
debug2: host key algorithms: rsa-sha2-512,rsa-sha2-256,ssh-rsa,ecdsa-sha2-nistp256,ssh-ed25519 [preauth]
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com [preauth]
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com [preauth]
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1 [preauth]
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1 [preauth]
debug2: compression ctos: none,zlib@openssh.com [preauth]
debug2: compression stoc: none,zlib@openssh.com [preauth]
debug2: languages ctos:  [preauth]
debug2: languages stoc:  [preauth]
debug2: first_kex_follows 0  [preauth]
debug2: reserved 0  [preauth]
debug2: peer client KEXINIT proposal [preauth]
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1,ext-info-c [preauth]
debug2: host key algorithms: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-ed25519,rsa-sha2-512,rsa-sha2-256,ssh-rsa [preauth]
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com [preauth]
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com [preauth]
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1 [preauth]
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1 [preauth]
debug2: compression ctos: none,zlib@openssh.com,zlib [preauth]
debug2: compression stoc: none,zlib@openssh.com,zlib [preauth]
debug2: languages ctos:  [preauth]
debug2: languages stoc:  [preauth]
debug2: first_kex_follows 0  [preauth]
debug2: reserved 0  [preauth]
debug1: kex: algorithm: curve25519-sha256 [preauth]
debug1: kex: host key algorithm: ecdsa-sha2-nistp256 [preauth]
debug1: kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none [preauth]
debug1: kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none [preauth]
debug1: expecting SSH2_MSG_KEX_ECDH_INIT [preauth]
debug2: monitor_read: 6 used once, disabling now
debug2: set_newkeys: mode 1 [preauth]
debug1: rekey out after 134217728 blocks [preauth]
debug1: SSH2_MSG_NEWKEYS sent [preauth]
debug1: expecting SSH2_MSG_NEWKEYS [preauth]
debug1: SSH2_MSG_NEWKEYS received [preauth]
debug2: set_newkeys: mode 0 [preauth]
debug1: rekey in after 134217728 blocks [preauth]
debug1: KEX done [preauth]
debug1: userauth-request for user user_name service ssh-connection method none [preauth]
debug1: attempt 0 failures 0 [preauth]
debug2: parse_server_config: config reprocess config len 257
debug2: monitor_read: 8 used once, disabling now
debug2: input_userauth_request: setting up authctxt for user_name [preauth]
debug2: input_userauth_request: try method none [preauth]
debug1: PAM: initializing for "user_name"
debug1: PAM: setting PAM_RHOST to "192.168.1.106"
debug1: PAM: setting PAM_TTY to "ssh"
debug2: monitor_read: 100 used once, disabling now
debug2: monitor_read: 4 used once, disabling now
debug1: userauth-request for user user_name service ssh-connection method password [preauth]
debug1: attempt 1 failures 0 [preauth]
debug2: input_userauth_request: try method password [preauth]
debug1: PAM: password authentication accepted for user_name
debug1: do_pam_account: called
debug2: do_pam_account: auth information in SSH_AUTH_INFO_0
Accepted password for user_name from 192.168.1.106 port 55682 ssh2
debug1: monitor_child_preauth: user_name has been authenticated by privileged process
debug1: monitor_read_log: child log fd closed
debug1: PAM: establishing credentials
debug2: do_pam_session: auth information in SSH_AUTH_INFO_0
User child is on pid 2764
debug1: SELinux support disabled
debug1: PAM: establishing credentials
debug1: permanently_set_uid: 1000/1001
debug2: set_newkeys: mode 0
debug1: rekey in after 134217728 blocks
debug2: set_newkeys: mode 1
debug1: rekey out after 134217728 blocks
debug1: ssh_packet_set_postauth: called
debug1: active: key options: agent-forwarding port-forwarding pty user-rc x11-forwarding
debug1: Entering interactive session for SSH2.
debug2: fd 7 setting O_NONBLOCK
debug2: fd 8 setting O_NONBLOCK
debug1: server_init_dispatch
debug1: server_input_channel_open: ctype session rchan 0 win 1048576 max 16384
debug1: input_session_request
debug1: channel 0: new [server-session]
debug2: session_new: allocate (allocated 0 max 10)
debug1: session_new: session 0
debug1: session_open: channel 0
debug1: session_open: session 0: link with channel 0
debug1: server_input_channel_open: confirm session
debug1: server_input_global_request: rtype no-more-sessions@openssh.com want_reply 0
debug1: server_input_channel_req: channel 0 request pty-req reply 1
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req pty-req
debug1: Allocating pty.
debug2: session_new: allocate (allocated 0 max 10)
debug1: session_new: session 0
debug1: SELinux support disabled
debug1: session_pty_req: session 0 alloc /dev/pts/1
debug1: server_input_channel_req: channel 0 request env reply 0
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req env
debug2: Setting env 0: LANG=C.UTF-8
debug1: server_input_channel_req: channel 0 request shell reply 1
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req shell
Starting session: shell on pts/1 for user_name from 192.168.1.106 port 55682 id 0
debug2: fd 3 setting TCP_NODELAY
debug2: channel 0: rfd 11 isatty
debug2: fd 11 setting O_NONBLOCK
debug1: Setting controlling tty using TIOCSCTTY.
Read error from remote host 192.168.1.106 port 55682: Connection reset by peer
debug1: do_cleanup
debug1: temporarily_use_uid: 1000/1001 (e=1000/1001)
debug1: restore_uid: (unprivileged)
debug1: do_cleanup
debug1: PAM: cleanup
debug1: PAM: closing session
debug1: PAM: deleting credentials
debug1: temporarily_use_uid: 1000/1001 (e=0/0)
debug1: restore_uid: 0/0
debug1: session_pty_cleanup2: session 0 release /dev/pts/1
debug1: audit_event: unhandled event 12
```


And the client-side output for the same connection:

```
$ ssh -vv -p 2222 user_name@192.168.1.10
OpenSSH_7.6p1 Ubuntu-4ubuntu0.3, OpenSSL 1.0.2n  7 Dec 2017
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "192.168.1.10" port 2222
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to 192.168.1.10 [192.168.1.10] port 2222.
debug1: Connection established.
debug1: key_load_public: No such file or directory
debug1: identity file /home/user_name/.ssh/id_rsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/user_name/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/user_name/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/user_name/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/user_name/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/user_name/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/user_name/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/user_name/.ssh/id_ed25519-cert type -1
debug1: Local version string SSH-2.0-OpenSSH_7.6p1 Ubuntu-4ubuntu0.3
debug1: Remote protocol version 2.0, remote software version OpenSSH_8.0p1 Ubuntu-6build1
debug1: match: OpenSSH_8.0p1 Ubuntu-6build1 pat OpenSSH* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to 192.168.1.10:2222 as 'user_name'
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: local client KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1,ext-info-c
debug2: host key algorithms: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-ed25519,rsa-sha2-512,rsa-sha2-256,ssh-rsa
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com,zlib
debug2: compression stoc: none,zlib@openssh.com,zlib
debug2: languages ctos:
debug2: languages stoc:
debug2: first_kex_follows 0
debug2: reserved 0
debug2: peer server KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1
debug2: host key algorithms: rsa-sha2-512,rsa-sha2-256,ssh-rsa,ecdsa-sha2-nistp256,ssh-ed25519
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com
debug2: compression stoc: none,zlib@openssh.com
debug2: languages ctos:
debug2: languages stoc:
debug2: first_kex_follows 0
debug2: reserved 0
debug1: kex: algorithm: curve25519-sha256
debug1: kex: host key algorithm: ecdsa-sha2-nistp256
debug1: kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Host '[192.168.1.10]:2222' is known and matches the ECDSA host key.
debug1: Found key in /home/user_name/.ssh/known_hosts:1
debug2: set_newkeys: mode 1
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug2: set_newkeys: mode 0
debug1: rekey after 134217728 blocks
debug2: key: /home/user_name/.ssh/id_rsa ((nil))
debug2: key: /home/user_name/.ssh/id_dsa ((nil))
debug2: key: /home/user_name/.ssh/id_ecdsa ((nil))
debug2: key: /home/user_name/.ssh/id_ed25519 ((nil))
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs=<ssh-ed25519,ssh-rsa,rsa-sha2-256,rsa-sha2-512,ssh-dss,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521>
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/user_name/.ssh/id_rsa
debug1: Trying private key: /home/user_name/.ssh/id_dsa
debug1: Trying private key: /home/user_name/.ssh/id_ecdsa
debug1: Trying private key: /home/user_name/.ssh/id_ed25519
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
user_name@192.168.1.10's password:
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
Authenticated to 192.168.1.10 ([192.168.1.10]:2222).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: pledge: network
debug1: client_input_global_request: rtype hostkeys-00@openssh.com want_reply 0
debug2: channel_input_open_confirmation: channel 0: callback start
debug2: fd 3 setting TCP_NODELAY
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug1: Sending environment.
debug1: Sending env LANG = C.UTF-8
debug2: channel 0: request env confirm 0
debug2: channel 0: request shell confirm 1
debug2: channel_input_open_confirmation: channel 0: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
Welcome to Ubuntu 19.10 (GNU/Linux 5.3.0-26-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

Last login: Sun Jan 26 14:09:17 2020 from 192.168.1.106
Environment:
  LANG=en_US.UTF-8
  USER=user_name
  LOGNAME=user_name
  HOME=/home/user_name
  PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
  SHELL=/bin/bash
  TERM=xterm-256color
  MOTD_SHOWN=pam
  QT_QUICK_BACKEND=software
  LC_ADDRESS=en_US.UTF-8
  LC_IDENTIFICATION=en_US.UTF-8
  LC_MEASUREMENT=en_US.UTF-8
  LC_MONETARY=en_US.UTF-8
  LC_NAME=en_US.UTF-8
  LC_NUMERIC=en_US.UTF-8
  LC_PAPER=en_US.UTF-8
  LC_TELEPHONE=en_US.UTF-8
  LC_TIME=en_US.UTF-8
  SSH_CLIENT=192.168.1.106 55682 2222
  SSH_CONNECTION=192.168.1.106 55682 192.168.1.10 2222
  SSH_TTY=/dev/pts/1
Connection reset by 192.168.1.10 port 2222
```

---

### Post by wildmanne39 on 2020-01-26
*Thread moved to **Server Platforms a more appropriate sub-forum**.*

---

### Post by springshades on 2020-02-03
I still don't know what is actually going on, but I figured out what was different about the one notebook and was able to work around the problem.

It is still unclear whether this is actually a client-side or a server-side problem, so it's hard to tell how to categorize this.

Digging with some google-fu led me to find out that some versions of OpenSSH have a bug with the way they deal with unusual MTU settings. One of the authentications packets has the potential to be very large, and a lower than average MTU setting sometimes leads to unexpected behavior from the SSH server that can disconnect the client. That wasn't my problem. I checked my MTU settings at every step. They are the extremely common 1500. However, it made me think that it could be a compatibility issue between the OpenSSH version and something to do with wifi. I discovered that this notebook was the only machine on my network connected at 2.4 GHz rather than 5.0 GHz. That didn't stop it from connecting to other machines via other protocols and even ssh sessions to different OpenSSH versions, but it seems to cause issues with this particular version of the server. Connecting the notebook via wired connection or 5.0 GHz frequency makes everything work. I don't know why. I'm assuming it's a similar bug in the OpenSSH server, but it could be something else.

I'm going to call this solved.

---

### Post by LHammonds on 2020-02-03
I don't know about your specific scenario but we had to disable 2.4 GHz on our wifi because our device would shift everyone on the faster 5.0 band down to 2.4 if a single device connected on 2.4...thus causing everyone to slow down and congesting the connection.  Once we disabled 2.4, the congestion issue went away.

---

