---
title: "Server side connection closed for sshd."
date: 2013-01-30
forum: Server Platforms
---

### Post by sometimeforget on 2013-01-30
I am struggling to figure out why my ubuntu (precise) server always close an connection from the server side at around 24hours. I am using putty in winxp to connect, the server is behind a LAN, but all ports direct to the server by default.
And it is not not some restart of router/server, since if i start another ssh session, this one is not closed.
Putty message is " Server unexpected close connection".

Trying to check which setup option could cause this.
I turned on TCPKeepalive.

---

### Post by Doug S on 2013-01-30
Hi and welcome to Ubuntu forums.
 
This is an odd one... I run putty sessions on windows computers to my Ubuntu servers for days and days. However not from a windows XP computer, at least recently.
 
The only suggestion I can provide is that you check the log files for any clue as to why the connection was terminated. Note the time of the connection closing. Look in the directory /var/log at least at the file auth.log and maybe some others ( kern.log, syslog ). Look for lines with "sshd", example:```
grep sshd /var/log/auth.log | more
``` and look around the above noted time of loss of connection.
 
You might try to increase the log level for more information, in /etc/ssh/sshd_config. This line:```
LogLevel VERBOSE
```maybe try DEBUG or DEBUG1 or... see "man sshd_config for the LogLevel options.

---

### Post by tgalati4 on 2013-01-30
Is it possible that the router renews the DHCP lease every 24 hours?  That might break an ssh connection if the link goes down long enough.

---

### Post by CharlesA on 2013-01-30
> **tgalati4 said:**
> Is it possible that the router renews the DHCP lease every 24 hours?  That might break an ssh connection if the link goes down long enough.

Possibly.

I have had a putty session open for 14 days on one of my VMs before - it was waiting for a response to "read" because I was accessing a service on the server via that machine.

Otherwise, if I leave a putty session sitting at the prompt with nothing running it will timeout eventually - usually in an hour or two.

---

### Post by sometimeforget on 2013-02-01
> **tgalati4 said:**
> Is it possible that the router renews the DHCP lease every 24 hours?  That might break an ssh connection if the link goes down long enough.
Not really , since the same machine, if I started a new session that is less than 24hr, it will be alive.

I have to rethink the problem again, actually there are so many layers I use for now, so perphaps this is not sshd 's fault, since I connect my sshd through a proxytunnel (http), I am connecting by establish a tunnel, the client connect to a local port, the local port is established by proxytunnel which connect a fire-walled proxy to my own squid proxy, then my own squid proxy passthrough to sshd.

Too many layers....  maybe the fire-walled proxy have 24hr reset, I do not see anything others have an setup like that.

Probably too hard to figure this out, but anyone could give me some debug tips

---

### Post by btindie on 2013-02-01
A few years ago I used to have a similar problem at work, though the connection would die after an hour or 2. It turned out that it was a timer on a Cisco ASA firewall that was killing the connection. Ended up adding a classmap to the firewall config to set the timeout to something more sensible.

It may not be a Cisco firewall in your case but it sounds more than likely to be a timeout on something in the path, especially if it happens after a fixed period of time.

---

### Post by sometimeforget on 2013-02-01
> **btindie said:**
> A few years ago I used to have a similar problem at work, though the connection would die after an hour or 2. It turned out that it was a timer on a Cisco ASA firewall that was killing the connection. Ended up adding a classmap to the firewall config to set the timeout to something more sensible.

It may not be a Cisco firewall in your case but it sounds more than likely to be a timeout on something in the path, especially if it happens after a fixed period of time.
Quite possibly, not sure I could change anything about the firewalled-proxy layer, is there anyway to re-conitinue an ssh session and setup some auto script to do this?

---

### Post by btindie on 2013-02-03
> **sometimeforget said:**
> Quite possibly, not sure I could change anything about the firewalled-proxy layer, is there anyway to re-conitinue an ssh session and setup some auto script to do this?

You could run something like tmux within your ssh session so that if your ssh connection drops you can simply reattach to your tmux session, anything running in that will carry on running.

---

### Post by CharlesA on 2013-02-03
> **btindie said:**
> You could run something like tmux within your ssh session so that if your ssh connection drops you can simply reattach to your tmux session, anything running in that will carry on running.

This would probably help. tmux is basically the same as screen but with more features.

[SIZE="1"]I prefer screen.[/SIZE]

---

