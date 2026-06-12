---
title: "my server is attacched"
date: 2016-06-23
forum: Server Platforms
---

### Post by Simone_Bianchin on 2016-06-23
Hi guys, every day a recive a segnalation by Hetzner.com (my host) with the following message :

Your server has been attaccked bla bla bla (personal information), and they attach the following log file:

```
[FONT=arial]> Note: Local timezone is +0300 (EEST)[/FONT]
[FONT=arial]> Jun 20 12:51:47 sweba1 sshd[5483]: Did not receive identification string from 138.201.92.98[/FONT]
[FONT=arial]> Jun 20 12:51:47 sweba1 sshd[5484]: Did not receive identification string from 138.201.92.98[/FONT]
[FONT=arial]> Jun 20 12:53:40 sweba1 sshd[7358]: Invalid user hadoop from 138.201.92.98[/FONT]
[FONT=arial]> Jun 20 12:53:40 sweba1 sshd[7357]: Invalid user hadoop from 138.201.92.98[/FONT]
[FONT=arial]> Jun 20 12:53:43 sweba1 sshd[7358]: Failed password for invalid user hadoop from 138.201.92.98 port 48114 ssh2[/FONT]
[FONT=arial]> Jun 20 12:53:43 sweba1 sshd[7358]: Received disconnect from [/FONT][138.201.92.98]("http://138.201.92.98/")[FONT=arial]: 11: Bye Bye [preauth][/FONT]
[FONT=arial]> Jun 20 12:53:43 sweba1 sshd[7357]: Failed password for invalid user hadoop from 138.201.92.98 port 46006 ssh2[/FONT]
[FONT=arial]> Jun 20 12:53:43 sweba1 sshd[7357]: Received disconnect from [/FONT][138.201.92.98]("http://138.201.92.98/")[FONT=arial]: 11: Bye Bye [preauth][/FONT]
[FONT=arial]> Jun 20 12:55:56 sweba1 sshd[9995]: Invalid user hadoop from 138.201.92.98[/FONT]
[FONT=arial]> Jun 20 12:55:56 sweba1 sshd[9996]: Invalid user hadoop from 138.201.92.98[/FONT]
[FONT=arial]> Jun 20 12:55:58 sweba1 sshd[9995]: Failed password for invalid user hadoop from 138.201.92.98 port 54722 ssh2[/FONT]
[FONT=arial]> Jun 20 12:55:58 sweba1 sshd[9996]: Failed password for invalid user hadoop from 138.201.92.98 port 56830 ssh2[/FONT]
[FONT=arial]> Jun 20 12:55:58 sweba1 sshd[9995]: Received disconnect from [/FONT][138.201.92.98]("http://138.201.92.98/")[FONT=arial]: 11: Bye Bye [preauth][/FONT]
[FONT=arial]> Jun 20 12:55:58 sweba1 sshd[9996]: Received disconnect from [/FONT][138.201.92.98]("http://138.201.92.98/")[FONT=arial]: 11: Bye Bye [preauth][/FONT]
[FONT=arial]>[/FONT]
```

Very thanks for the help!:D

---

### Post by TheFu on 2016-06-23
Never allow password-based logins over the internet.  Always setup ssh-key-based authentication. It is more secure AND more convenient.

Running **fail2ban** would be a good start towards blocking these attacks.  Lots of how-tos for securing ssh exist. Pick one and follow it. The key would be to have the firewall dynamically block attempts for a day or month or year or forever. Fail2ban does that.  

If you are trying to run hadoop on this VPS, then it really needs to be setup with key-based authentication.  Could it be that someone else running hadoop is confused and thinks that your system is part of their cluster?

---

### Post by Habitual on 2016-06-24
fail2ban
tcpwrapper if the server's openssh is less than 6.7, see [http://ubuntuforums.org/showthread.php?t=2318000&p=13459876#post13459876](http://ubuntuforums.org/showthread.php?t=2318000&p=13459876#post13459876)
for the how to.

installing failban will protect your server from ssh dictionary attacks.
But first, passwords are insecure, so ssh-keys...

[How To Configure SSH Key-Based Authentication on a Linux Server.]("https://www.digitalocean.com/community/tutorials/how-to-configure-ssh-key-based-authentication-on-a-linux-server")

Once ssh keys are established and working,  password authentication should be disabled.

---

