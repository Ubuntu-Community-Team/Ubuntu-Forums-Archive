---
title: "Very slow SSH login response time"
date: 2017-01-28
forum: Server Platforms
---

### Post by ericadamkatz on 2017-01-28
I am running Ubuntu Server 16.04.1 LTS on a relatively new beefy box, w/ 16GB of RAM.

Just started experiencing this within the last few weeks.  After entering my password via SSH, or direct login, there is a very long delay before getting to a prompt.  My syslog is filled with this:

Jan 28 16:53:55 nas systemd[1]: systemd-logind.service: Main process exited, code=exited, status=1/FAILURE
Jan 28 16:53:55 nas systemd[1]: Failed to start Login Service.
Jan 28 16:53:55 nas systemd[1]: systemd-logind.service: Unit entered failed state.
Jan 28 16:53:55 nas systemd[1]: systemd-logind.service: Failed with result 'exit-code'.
Jan 28 16:53:55 nas systemd[1]: systemd-logind.service: Service has no hold-off time, scheduling restart.
Jan 28 16:53:55 nas systemd[1]: Stopped Login Service.
Jan 28 16:53:55 nas systemd[1]: Starting Login Service...
Jan 28 16:53:55 nas systemd[1]: Failed to forward Released message: No buffer space available

Anyone have any ideas?

Regards,

Eric Katz

---

### Post by TheFu on 2017-01-28
Disable ipv6.

Make certain both systems know about each other by name and IP.

From a client, try to connect to the server with higher verbosity.
$ ssh -vvv me@server

Where do the logs seem to get stuck?

---

### Post by ericadamkatz on 2017-01-29
Disabled ipv6, did not fix it.

Used the ssh suggestion above.  Here is the result:

```
eric@nas's password:
debug3: send packet: type 50
debug2: we sent a password packet, wait for reply
debug3: receive packet: type 52
debug1: Authentication succeeded (password).
Authenticated to nas ([192.168.1.241]:22).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug3: send packet: type 90
debug1: Requesting [EMAIL="no-more-sessions@openssh.com"]no-more-sessions@openssh.com[/EMAIL]
debug3: send packet: type 80
debug1: Entering interactive session.
debug1: pledge: network
```
---- it got stuck here, until resuming ----
```
debug3: receive packet: type 80
debug1: client_input_global_request: rtype [EMAIL="hostkeys-00@openssh.com"]hostkeys-00@openssh.com[/EMAIL] want_reply 0
debug3: receive packet: type 91
debug2: callback start
debug2: fd 3 setting TCP_NODELAY
debug3: ssh_packet_set_tos: set IP_TOS 0x10
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug3: send packet: type 98
debug1: Sending environment.
debug3: Ignored env TERM_PROGRAM
debug3: Ignored env TERM
debug3: Ignored env SHELL
debug3: Ignored env TMPDIR
debug3: Ignored env Apple_PubSub_Socket_Render
debug3: Ignored env TERM_PROGRAM_VERSION
debug3: Ignored env TERM_SESSION_ID
debug3: Ignored env USER
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env __CF_USER_TEXT_ENCODING
debug3: Ignored env PATH
debug3: Ignored env PWD
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: send packet: type 98
debug3: Ignored env ITERM_PROFILE
debug3: Ignored env XPC_FLAGS
debug3: Ignored env XPC_SERVICE_NAME
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env COLORFGBG
debug3: Ignored env ITERM_SESSION_ID
debug3: Ignored env LOGNAME
debug3: Ignored env _
debug2: channel 0: request shell confirm 1
debug3: send packet: type 98
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug3: receive packet: type 99
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug3: receive packet: type 99
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
Welcome to Ubuntu 16.04.1 LTS (GNU/Linux 4.4.0-59-generic x86_64)
```

I want to add that when doing a port forward (ssh -L 4200:localhost:4243 eric@192.168.1.241), it works just fine, there is no lag after authentication.   Very odd.

---

### Post by TheFu on 2017-01-29
Google found this:
[https://unix.stackexchange.com/questions/302677/ssh-does-not-respond-only-from-ubuntu](https://unix.stackexchange.com/questions/302677/ssh-does-not-respond-only-from-ubuntu)
and
[https://ubuntuforums.org/showthread.php?t=1448030](https://ubuntuforums.org/showthread.php?t=1448030) has a few other options.

I always assume it is DNS issues first.

---

### Post by Doug S on 2017-01-29
> **ericadamkatz said:**
> After entering my password via SSH, [COLOR="#FF0000"]or direct login[/COLOR], there is a very long delay before getting to a prompt. Perhaps take a step back and leave ssh out of it, at first. Do you still have issues with  the systemd-logind.service? Check via:```
sudo systemctl status systemd-logind.service
```

---

### Post by TheFu on 2017-01-29
Been searching for ideas ... 

Any stale cifs, nfs, or sshfs mounts?  
Does restarting the networking make it faster again?
Was the system in standby or hibernation?

---

### Post by SeijiSensei on 2017-01-29
[http://serverfault.com/questions/792486/ssh-connection-takes-forever-to-initiate-stuck-at-pledge-network](http://serverfault.com/questions/792486/ssh-connection-takes-forever-to-initiate-stuck-at-pledge-network)

Seems like a systemd problem (watta surprise!).  Yet another reason to stick with 14.04 until it reaches end-of-life in 2019.

One of the answers suggested setting UsePAM to no, but that was on a network using LDAP authentication so it probably doesn't apply to you.

---

