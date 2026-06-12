---
title: "sshd tries to spawn new process every other second"
date: 2017-10-26
forum: Security
---

### Post by fomember on 2017-10-26
I recently migrated my virtual server with plesk and ubuntu 16.04 to a more powerful package.
After the migration I transferred the domains and configured the eMail and all seems to work well except for a strange ssh phenomenon.
No matter if I'm logged in via ssh or not, the sshd tries to start a new session every other second like shown in the process list below and my auth.log is full of messages from pam and ssh.
I already rebooted the server but no change.
Any clues how I can troubleshoot the problem?

```
# ps -ef | grep -v grep | grep ssh
root       **406     1  0 Oct25 ?        00:00:30 /usr/sbin/sshd -**D
root     28440   406  0 22:00 ?        00:00:00 sshd: root [priv]
sshd     28441 28440  0 22:00 ?        00:00:00 sshd: root [net]
root     **32602   406  0 21:33 ?        00:00:00 sshd: root@pts/0**
# ps -ef | grep -v grep | grep ssh
root       **406     1  0 Oct25 ?        00:00:30 /usr/sbin/sshd -D**
root     **32602   406  0 21:33 ?        00:00:00 sshd: root@pts/0**
# ps -ef | grep -v grep | grep ssh
root       **406     1  0 Oct25 ?        00:00:30 /usr/sbin/sshd -D**
root     28463   406  0 22:00 ?        00:00:00 sshd: [accepted]
sshd     28464 28463  0 22:00 ?        00:00:00 sshd: [net]
root     **32602   406  0 21:33 ?        00:00:00 sshd: root@pts/0**
# ps -ef | grep -v grep | grep ssh
root       **406     1  0 Oct25 ?        00:00:30 /usr/sbin/sshd -D**
root     **32602   406  0 21:33 ?        00:00:00 sshd: root@pts/0**

```

```
Oct 26 21:55:53 h... sshd[23596]: Accepted publickey for root from xx.xx.xx.xx port 36291 ssh2: RSA SHA256:pr...
Oct 26 21:55:53 h... sshd[23596]: pam_unix(sshd:session): session opened for user root by (uid=0)
Oct 26 21:55:53 h... systemd-logind[11782]: New session 2525464 of user root.
Oct 26 21:55:53 h... sshd[23596]: pam_systemd(sshd:session): Cannot create session: Already running in a session
Oct 26 21:55:53 h... sshd[23596]: Received disconnect from xx.xx.xx.xx port 36291:11: disconnected by user
Oct 26 21:55:53 h... sshd[23596]: Disconnected from xx.xx.xx.xx port 36291
Oct 26 21:55:53 h... sshd[23596]: pam_unix(sshd:session): session closed for user root
Oct 26 21:55:53 h... systemd-logind[11782]: Removed session 2525464.
Oct 26 21:55:54 h... sshd[23633]: Accepted publickey for root from xx.xx.xx.xx port 36292 ssh2: RSA SHA256:pr...
Oct 26 21:55:54 h... sshd[23633]: pam_unix(sshd:session): session opened for user root by (uid=0)
Oct 26 21:55:54 h... systemd-logind[11782]: New session 2525465 of user root.
Oct 26 21:55:54 h... sshd[23633]: pam_systemd(sshd:session): Cannot create session: Already running in a session
Oct 26 21:55:54 h... sshd[23633]: Received disconnect from xx.xx.xx.xx port 36292:11: disconnected by user
Oct 26 21:55:54 h... sshd[23633]: Disconnected from xx.xx.xx.xx port 36292
Oct 26 21:55:54 h... sshd[23633]: pam_unix(sshd:session): session closed for user root
Oct 26 21:55:54 h... systemd-logind[11782]: Removed session 2525465.
Oct 26 21:55:56 h... sshd[23652]: Accepted publickey for root from xx.xx.xx.xx port 36293 ssh2: RSA SHA256:pr...
Oct 26 21:55:56 h... sshd[23652]: pam_unix(sshd:session): session opened for user root by (uid=0)
Oct 26 21:55:56 h... systemd-logind[11782]: New session 2525466 of user root.
Oct 26 21:55:56 h... sshd[23652]: pam_systemd(sshd:session): Cannot create session: Already running in a session
Oct 26 21:55:56 h... sshd[23652]: Received disconnect from xx.xx.xx.xx port 36293:11: disconnected by user
Oct 26 21:55:56 h... sshd[23652]: Disconnected from xx.xx.xx.xx port 36293
Oct 26 21:55:56 h... sshd[23652]: pam_unix(sshd:session): session closed for user root
Oct 26 21:55:56 h... systemd-logind[11782]: Removed session 2525466.

```

---

### Post by TheFu on 2017-10-26
Is root from xx.xx.xx.xx an IP you know/own?  What is spawning all the ssh connections from that client?  Use lsof to figure it out and stop it.

In the meantime, 

First, NEVER allow remote root ssh logins.  Force normal userids to ssh in, then use sudo. That is part of Ubuntu security.

2nd, install fail2ban.  It is best to setup firewall rules to block all inbound ssh from all IPs except those you actually use, but fail2ban will block brute force attempts better than nothing.

3rd, move the sshd listener to almost any other port than 22.  This will drastically reduce the brute force attempts and clear the logs of all that stuff.  I do it in the router, so that LAN connections all still use 22/tcp and fail2ban configs don't need to be modified.

4th, only allow ssh-key based logins over the internet, never passwords.  NEVER (well, except the 1 you need to put your keys on the system).

---

### Post by fomember on 2017-10-27
The IP address xx.xx... is my very own address.  
I agree with you on the other points and my systems are setup with fail2ban, different ssh port and no pw for root.  
As I said I have the old server which is setup alike and which doesn't show the problem.  
In the meantime I have found that the new system also floods the syslog every other second with the messages shown below.  
So the real cause of the problem may come from the overly complex systemd.  

Oct 27 07:42:39 h2... systemd[19421]: Startup finished in 5ms.  
Oct 27 07:42:39 h2... systemd[19421]: Stopped target Default.  
Oct 27 07:42:39 h2... systemd[19421]: Stopped target Basic System.  
Oct 27 07:42:39 h2... systemd[19421]: Stopped target Timers.  
Oct 27 07:42:39 h2... systemd[19421]: Stopped target Sockets.  
Oct 27 07:42:39 h2... systemd[19421]: Reached target Shutdown.  
Oct 27 07:42:39 h2... systemd[19421]: Starting Exit the Session...  
Oct 27 07:42:39 h2... systemd[19421]: Stopped target Paths.  
Oct 27 07:42:39 h2... systemd[19421]: Received SIGRTMIN+24 from PID 19447 (kill).  
Oct 27 07:42:40 h2... systemd[19468]: Reached target Paths.  
Oct 27 07:42:40 h2... systemd[19468]: Reached target Timers.  
Oct 27 07:42:40 h2... systemd[19468]: Reached target Sockets.  
Oct 27 07:42:40 h2... systemd[19468]: Reached target Basic System.  
Oct 27 07:42:40 h2... systemd[19468]: Reached target Default.  
Oct 27 07:42:40 h2... systemd[19468]: Startup finished in 6ms.

---

