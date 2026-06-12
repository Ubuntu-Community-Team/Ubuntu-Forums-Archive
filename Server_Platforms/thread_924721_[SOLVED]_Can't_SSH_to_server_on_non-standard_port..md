---
title: "[SOLVED] Can't SSH to server on non-standard port."
date: 2008-09-19
forum: Server Platforms
---

### Post by Sky Pixie on 2008-09-19
Client:  Hotdog
Server:  Pickleweasel

I can SSH from Hotdog to Pickleweasel using Port 22 and Passkey Authentication.

I want to change the port on which SSH listens to ### where ### is some number.

On Pickleweasel:
- Replaced Port 22 with Port ### in the /etc/ssh/sshd_config file
- Replaced Port 22 with Port ### in the /etc/ssh/ssh_config file
- Restarted the SSH server
```
sudo /etc/init.d/ssh restart
```
- Used Guarddog's Advanced tab to add SSH TCP service on Port ###
- Applied and exited Guarddog
- Checked which ports were listening
```
netstat -nltu
```
- Port ### was listening
- Port 22 was not listed

On Hotdog:
- Used Guarddog's Advanced tab to add SSH TCP service on Port ###
- Applied and exited Guarddog

Hotdog and Pickleweasel are on the same local network.  I'm not sure if Port ### must be forwarded through the Linksys WRT54GL router, but I did so for now.  Do I need to specify static local IP addresses if the computers are rarely rebooted?

On Router:
- Forwarded Port ### between the local IP addresses of Hotdog and Pickleweasel
- Save and exit

On Pickleweasel:
```
ssh localhost
```
Yields:
```
ssh: connect to host localhost port 22: Connection refused
```

```
ssh -p ### localhost
```
Yields:
```
Permission denied (publickey).
```

On Hotdog:
```
ssh user@192.168.x.xxx
```
```
ssh: connect to host 192.168.x.xxx port 22: Connection refused
```

```
ssh -vv -p ### user@192.168.x.xxx
```
Yields:
```
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.x.xxx [192.168.x.xxx] port ###.
debug1: connect to address 192.168.x.xxx port ###: Connection timed out
ssh: connect to host 192.168.x.xxx port ###: Connection timed out
```

In your opinions, is this a client, server, or router problem?  I read dozens posts from users with similar problems, but found no solution.

Thank you in advance.

---

### Post by Iowan on 2008-09-19
Just my opinion...
If both machines are in the same local network, the router shouldn't be involved.  I have a default Xubuntu setup which had no problem connecting to an SSH-server on my network - but I did need to give it the nonstandard port (**ssh -p 1234 server**). I don't have Guarddog. Once connected to the server, I tried **ssh localhost ** it mentioned localhost wasn't in ... continue (y/n).  I didn't pursue it further, but it looked like it would work.  If Pickelweasel has ssh-client and ssh-server, and cannot connect to itself, I'd suspect the firewall settings.

---

### Post by Sky Pixie on 2008-09-19
Thank you Iowan for the reply.  I agree the firewalls are the issue.

I looked closer at Guarddog's configuration.

On the "Protocol" tab, there is a list of "Network Protocols" with expansion menus.  One such Protocol is "User Defined."  The non-standard port I specified on the "Advanced" tab is listed here.  Checking those boxes under both Internet and Local Zones on both the client and the server modified both firewalls and permitted SSH to connect using the non-standard port.

The SSH protocol listed on Protocol > Interactive Session > SSH can be disabled on both machines when a non-standard port is specified for SSH.  That checkbox only affects port 22.

Problem solved and thread marked as such.

---

