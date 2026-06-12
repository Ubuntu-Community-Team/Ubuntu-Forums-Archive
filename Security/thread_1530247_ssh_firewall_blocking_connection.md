---
title: "ssh firewall blocking connection"
date: 2010-07-13
forum: Security
---

### Post by sbmmth on 2010-07-13
Hi Everyone,

when I am run:

ssh -v "login"@"server"

I get: 

OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to server ["address"] port 22.
debug1: connect to address "address" port 22: Connection timed out
ssh: connect to host "server" port 22: Connection timed out

I suppose this is because I am connecting from a public institute where there is a firewall that is  blocking an  outbound connection on port 22.

Is there anyway I can bypass the firewall using the internet ?


THANKS !!!

Sb
[/SIZE][/FONT]

---

### Post by spynappels on 2010-07-13
Google VPN

---

### Post by bodhi.zazen on 2010-07-13
> **sbmmth said:**
> [FONT=Arial][SIZE=1]Hi Everyone,

when I am run:

ssh -v "login"@"server"

I get: 

OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to server ["address"] port 22.
debug1: connect to address "address" port 22: Connection timed out
ssh: connect to host "server" port 22: Connection timed out

I suppose this is because I am connecting from a public institute where there is [/SIZE][/FONT][FONT=Arial][SIZE=1][COLOR=black][COLOR=black]a firewall that is  blocking an  outbound connection on port 22[/COLOR][/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=1].

Is there anyway I can bypass the firewall using the internet ?


THANKS !!!

Sb
[/SIZE][/FONT]

[SIZE=1][COLOR=yellow]Please use the default fonts. Your post is very hard to read. You are making an assumption so who knows the solution to your problem.[/COLOR]

[COLOR=pink]In addition we do not support punching holes in private networks. Please see your network admin[/COLOR][COLOR=blue]Thread closed[/COLOR][/SIZE]

---

