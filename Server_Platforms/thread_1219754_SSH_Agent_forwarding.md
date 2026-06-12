---
title: "SSH Agent forwarding"
date: 2009-07-22
forum: Server Platforms
---

### Post by tsumaru on 2009-07-22
Hi, i recently colocated a server in the uk and it was working fine.

i have my key (id_rsa.pub) on my desktop computer along with my id_rsa on the server under my unsername

"ssh -A server" connects without needing a password.  However, i also have my id_rsa.pub in authorized keys on my root dir's ssh folder with from="127.0.0.1" at the beginning to only allow login to root from localhost

i have disabled the reverse dns lookup in my sshd config.

When i try to log in to root from the machine itsself with "ssh root@localhost" it gives me access denied (publickey) and drops me back to my shell.

the contents of my auth.log after this are: 

```
Jul 22 09:11:03 utsushi sshd[4721]: debug3: fd 4 is not O_NONBLOCK
Jul 22 09:11:03 utsushi sshd[5728]: debug1: rexec start in 4 out 4 newsock 4 pipe 6 sock 7
Jul 22 09:11:03 utsushi sshd[4721]: debug1: Forked child 5728.
Jul 22 09:11:03 utsushi sshd[4721]: debug3: send_rexec_state: entering fd = 7 config len 675
Jul 22 09:11:03 utsushi sshd[4721]: debug3: ssh_msg_send: type 0
Jul 22 09:11:03 utsushi sshd[4721]: debug3: send_rexec_state: done
Jul 22 09:11:03 utsushi sshd[5728]: debug1: inetd sockets after dupping: 3, 3
Jul 22 09:11:03 utsushi sshd[5728]: debug3: Normalising mapped IPv4 in IPv6 address
Jul 22 09:11:03 utsushi sshd[5728]: debug3: Normalising mapped IPv4 in IPv6 address
Jul 22 09:11:03 utsushi sshd[5728]: Connection from 127.0.0.1 port 38366
Jul 22 09:11:03 utsushi sshd[5728]: debug1: Client protocol version 2.0; client software version OpenSSH_4.7p1 Debian-8ubuntu1.2
Jul 22 09:11:03 utsushi sshd[5728]: debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
Jul 22 09:11:03 utsushi sshd[5728]: debug1: Enabling compatibility mode for protocol 2.0
Jul 22 09:11:03 utsushi sshd[5728]: debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
Jul 22 09:11:03 utsushi sshd[5728]: debug2: fd 3 setting O_NONBLOCK
Jul 22 09:11:03 utsushi sshd[5728]: debug2: Network child is on pid 5729
Jul 22 09:11:03 utsushi sshd[5728]: debug3: preauth child monitor started
Jul 22 09:11:03 utsushi sshd[5728]: debug3: mm_request_receive entering
Jul 22 09:11:03 utsushi sshd[5728]: debug3: monitor_read: checking request 0
Jul 22 09:11:03 utsushi sshd[5728]: debug3: mm_answer_moduli: got parameters: 1024 1024 8192
Jul 22 09:11:03 utsushi sshd[5728]: debug3: mm_request_send entering: type 1
Jul 22 09:11:03 utsushi sshd[5728]: debug2: monitor_read: 0 used once, disabling now
Jul 22 09:11:03 utsushi sshd[5728]: debug3: mm_request_receive entering
Jul 22 09:11:03 utsushi sshd[5728]: debug3: monitor_read: checking request 5
Jul 22 09:11:03 utsushi sshd[5728]: debug3: mm_answer_sign
Jul 22 09:11:03 utsushi sshd[5728]: debug3: mm_answer_sign: signature 0xb7f9d778(271)
Jul 22 09:11:03 utsushi sshd[5728]: debug3: mm_request_send entering: type 6
Jul 22 09:11:03 utsushi sshd[5728]: debug2: monitor_read: 5 used once, disabling now
Jul 22 09:11:03 utsushi sshd[5728]: debug3: mm_request_receive entering
Jul 22 09:11:03 utsushi sshd[5728]: debug3: monitor_read: checking request 7
Jul 22 09:11:03 utsushi sshd[5728]: debug3: mm_answer_pwnamallow
Jul 22 09:11:03 utsushi sshd[5728]: debug2: parse_server_config: config reprocess config len 675
Jul 22 09:11:03 utsushi sshd[5728]: debug3: mm_answer_pwnamallow: sending MONITOR_ANS_PWNAM: 1
Jul 22 09:11:03 utsushi sshd[5728]: debug3: mm_request_send entering: type 8
Jul 22 09:11:03 utsushi sshd[5728]: debug2: monitor_read: 7 used once, disabling now
Jul 22 09:11:03 utsushi sshd[5728]: debug3: mm_request_receive entering
Jul 22 09:11:03 utsushi sshd[5728]: debug3: monitor_read: checking request 48
Jul 22 09:11:03 utsushi sshd[5728]: debug1: PAM: initializing for "root"
Jul 22 09:11:03 utsushi sshd[5728]: debug1: PAM: setting PAM_RHOST to "127.0.0.1"
Jul 22 09:11:03 utsushi sshd[5728]: debug1: PAM: setting PAM_TTY to "ssh"
Jul 22 09:11:03 utsushi sshd[5728]: debug2: monitor_read: 48 used once, disabling now
Jul 22 09:11:03 utsushi sshd[5728]: debug3: mm_request_receive entering
Jul 22 09:11:03 utsushi sshd[5728]: debug3: monitor_read: checking request 3

Jul 22 09:11:03 utsushi sshd[5728]: debug3: mm_answer_authserv: service=ssh-connection, style=, role=
Jul 22 09:11:03 utsushi sshd[5728]: debug2: monitor_read: 3 used once, disabling now
Jul 22 09:11:03 utsushi sshd[5728]: debug3: mm_request_receive entering
Jul 22 09:11:03 utsushi sshd[5728]: debug1: do_cleanup
Jul 22 09:11:03 utsushi sshd[5728]: debug1: PAM: cleanup
Jul 22 09:11:03 utsushi sshd[5728]: debug3: PAM: sshpam_thread_cleanup entering

```

This isnt giving me any indications as to what the problem is and why i cant log in.

On another note, if i copy my id_rsa to my home dir on the server it works without the agent forwarding, it just seems to be ignoring it,

I have also run "ssh-add" on my desktop to allow my key to be forwarded

Any help on this would be much appreciated

---

### Post by tsumaru on 2009-07-22
**bump**

---

