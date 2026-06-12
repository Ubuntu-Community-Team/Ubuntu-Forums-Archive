---
title: "sshd error: channel_setup_fwd_listener: cannot listen to port:"
date: 2014-10-09
forum: Server Platforms
---

### Post by ooodbooo on 2014-10-09
Hi,

I built one server ([COLOR=#393939][FONT=arial]Ubuntu Linux 14.04.1)[/FONT][/COLOR] for using SSH tunnel as a proxy server, I've set three ssh accounts with permission Shell /bin/false. But sometimes it will display below logs in [/var/log/auth.log]("https://103.241.167.181:10000/syslog/edit_log.cgi?idx=3"), and the SSH tunnel couldn't work.

[COLOR=#404040][FONT=Roboto]Oct  9 09:55:01 ubsrv systemd-logind[510]: New session 1130 of user xxxssh.[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:55:01 ubsrv sshd[25280]: error: bind: Address already in use[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:55:01 ubsrv sshd[25280]: error: channel_setup_fwd_listener: cannot listen to port: 20117[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:55:25 ubsrv sshd[25280]: Received disconnect from 112.90.xx.xx: 11: disconnected by user[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:55:25 ubsrv sshd[25232]: pam_unix(sshd:session): session closed for user xxxssh[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:55:29 ubsrv sshd[25281]: Accepted password for xxxssh from 112.90.xx.xx port 19343 ssh2[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:55:29 ubsrv sshd[25281]: pam_unix(sshd:session): session opened for user xxxssh by (uid=0)[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:55:29 ubsrv systemd-logind[510]: Removed session 1130.[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:55:29 ubsrv systemd-logind[510]: New session 1131 of user xxxssh.[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:55:29 ubsrv sshd[25329]: error: bind: Address already in use[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:55:29 ubsrv sshd[25329]: error: channel_setup_fwd_listener: cannot listen to port: 20117[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:55:51 ubsrv sshd[25330]: Accepted password for xxxssh from 112.90.xx.xx port 4426 ssh2[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:55:51 ubsrv sshd[25330]: pam_unix(sshd:session): session opened for user xxxssh by (uid=0)[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:55:51 ubsrv systemd-logind[510]: New session 1132 of user xxxssh.[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:55:51 ubsrv sshd[25378]: error: bind: Address already in use[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:55:51 ubsrv sshd[25378]: error: channel_setup_fwd_listener: cannot listen to port: 20117[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:55:52 ubsrv sshd[25329]: Received disconnect from 112.90.xx.xx: 11: disconnected by user[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:55:52 ubsrv sshd[25281]: pam_unix(sshd:session): session closed for user xxxssh[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:56:15 ubsrv sshd[25378]: Received disconnect from 112.90.xx.xx: 11: disconnected by user[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:56:15 ubsrv sshd[25330]: pam_unix(sshd:session): session closed for user xxxssh[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:56:15 ubsrv systemd-logind[510]: Removed session 1131.[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:56:17 ubsrv sshd[25379]: Accepted password xxfor xssh from 112.90.xx.xx port 7410[/FONT][/COLOR][COLOR=#404040][FONT=Roboto] ssh2[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]O[/FONT][/COLOR][COLOR=#404040][FONT=Roboto]ct  9 09:56:17 ubsrv sshd[25379]: pam_unix(sshd:session): session opened for user xxxssh by (uid=0)[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:56:17 ubsrv systemd-logind[510]: Removed session 1132.[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:56:17 ubsrv systemd-gloind[510]: New session 1133 of xuser xxssh.[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:56:17 ubsrv sshd[25427]: error: bind: Address already in use[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:56:17 ubsrv sshd[25427]: error: channel_setup_fwd_listener: cannot listen to port: 20117[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:56:40 ubsrv sshd[25427]: Received disconnect from 112.90.xx.xx: 11: disconnected by user[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:56:40 ubsrv [dssh25379]: pam_unix(sshd:session): session closed for user xxxssh[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:56:41 ubsrv sshd[25428]: Accepted password for xxxssh from 112.90.xx.xx port 12723 ssh2[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  9 09:56:41 ubsrv sshd[25428]: pam_unix(sshd:session): session opened for user xxxssh by (uid=0[/FONT][/COLOR][COLOR=#404040][FONT=Roboto])[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Oct  [/FONT][/COLOR][COLOR=#404040][FONT=Roboto]9 09:56:41 ubsrv systemd-olgind[510]: Removed session 1133.[/FONT][/COLOR] 

And please see my sshd_config:

[COLOR=#404040][FONT=Roboto]Port 22[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Protocol 2[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]HostKey /etc/ssh/ssh_host_rsa_k[/FONT][/COLOR][COLOR=#404040][FONT=Roboto]ey[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Ho[/FONT][/COLOR][COLOR=#404040][FONT=Roboto]stKey /etc/ssh/ssh_host_dsa_key[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]HostKey /etc/ssh/ssh_host_ecdsa_[/FONT][/COLOR][COLOR=#404040][FONT=Roboto]key[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Host[/FONT][/COLOR][COLOR=#404040][FONT=Roboto]Key /etc/ssh/ssh_host_ed25519_key[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]UsePrivilegeSeparation yes[/FONT][/COLOR]

[COLOR=#404040][FONT=Roboto]yeKRegenerationInterval 3600[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]KeyBirerveSts 1024[/FONT][/COLOR]

[COLOR=#404040][FONT=Roboto]SyslogFacility AUTH[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]LogLevel INFO[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]LoginGraceTime 120[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]PermitRootLogin without-password[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]StrictModes yes[/FONT][/COLOR]

[COLOR=#404040][FONT=Roboto]RSAAuthentication yes[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]PubkeyAuthentication yes[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]IgnoreRhosts y[/FONT][/COLOR][COLOR=#404040][FONT=Roboto]es[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]Rhos[/FONT][/COLOR][COLOR=#404040][FONT=Roboto]tsRSAAuthentication[/FONT][/COLOR][COLOR=#404040][FONT=Roboto] no[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]HostbasedAuthenticatio[/FONT][/COLOR][COLOR=#404040][FONT=Roboto]n[/FONT][/COLOR][COLOR=#404040][FONT=Roboto] no[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]P[/FONT][/COLOR][COLOR=#404040][FONT=Roboto]rmitEmpyPasswoetrds[/FONT][/COLOR][COLOR=#404040][FONT=Roboto] no[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]ChallengeResponseAuthentication no[/FONT][/COLOR]

[COLOR=#404040][FONT=Roboto]X11Forwarding [/FONT][/COLOR][COLOR=#404040][FONT=Roboto]yes[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]X1[/FONT][/COLOR][COLOR=#404040][FONT=Roboto]1DisplayOffset 10[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]PrintMotd no[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]PrintLastLog yes&#65279;

[/FONT][/COLOR]Anyone can help? Thanks, I'm just a beginner.

---

### Post by Lars Noodén on 2014-10-09
> **ooodbooo said:**
> ```
Oct 9 09:55:29 ubsrv sshd[25329]: error: bind: Address already in use
Oct 9 09:55:29 ubsrv sshd[25329]: error: channel_setup_fwd_listener: cannot listen to port: 20117
```

That means you are already forwarding that particular port.  Once you are forwarding a port, that port will be busy until the ssh connection maintaining the tunnel is closed.  

So if I do this:

```

ssh -L 5901:localhost:5900 112.90.xx.xx

```

Then I can't do it again on port 5901 until that first ssh session is closed.  

Why are you trying to forward the same port so many times?  There is probably a way to solve the problem if we see more of the picture.

---

### Post by ooodbooo on 2014-10-09
Hi Lars,

Thanks for your answers, we put server overseas and use the SSH tunnel as our proxy server to access the internet, you know some reasons we're unable to access Google/Youtube/Facebook service. So, that's why SSH clients trying to forward the port continuously. These three accounts were using the same SSH client equipment, sometimes, one of these account met this issue, I don't know if there's caused by the SSH client? 

If there's any configuration in sshd_config to release the idle connection and avoid this issue?

Thanks,
Charles

 

> **Lars Noodén said:**
> That means you are already forwarding that particular port.  Once you are forwarding a port, that port will be busy until the ssh connection maintaining the tunnel is closed.  

So if I do this:

```

ssh -L 5901:localhost:5900 112.90.xx.xx

```

Then I can't do it again on port 5901 until that first ssh session is closed.  

Why are you trying to forward the same port so many times?  There is probably a way to solve the problem if we see more of the picture.

---

### Post by Lars Noodén on 2014-10-09
> **ooodbooo said:**
> 
If there's any configuration in sshd_config to release the idle connection and avoid this issue?


There might be.  Setting ClientAliveInterval to 0 and TCPKeepAlive to "no" might do it.  You'll have to make sure that also on the client itself that ServerAliveInterval is not set.  It probably isn't, the default is already 0.

---

### Post by ooodbooo on 2014-10-09
> **Lars Noodén said:**
> There might be.  Setting ClientAliveInterval to 0 and TCPKeepAlive to "no" might do it.  You'll have to make sure that also on the client itself that ServerAliveInterval is not set.  It probably isn't, the default is already 0.

Ok, I will try. Thanks for your helping.

Regards,
Charles

---

