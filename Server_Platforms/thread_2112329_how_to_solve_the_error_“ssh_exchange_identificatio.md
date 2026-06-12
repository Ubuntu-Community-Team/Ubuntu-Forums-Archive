---
title: "how to solve the error: “ssh_exchange_identification: connection closed by remote hos"
date: 2013-02-04
forum: Server Platforms
---

### Post by 0xeb on 2013-02-04
I have been researching for hours and still unable to solve my problem.

This error "ssh_exchange_identification: Connection closed by remote host" has many proposed solutions but none seem to solve my problem.

This is what I want to accomplish:

I have a server (@10.0.0.5) with SSH on it. The server has the following users and their shells:

passport, shell=/bin/false
user1, shell=git-shell
user2, shell=git-shell
me, shell=bash

The sshd_config file, has the following entry at the end:

```
# Disable forwarding by default
AllowTcpForwarding no

# Enable conditional forwarding
Match User passport,user1,user2
      AllowTcpForwarding true
      PermitOpen 10.0.0.5:8080
      PermitOpen 10.0.0.5:22

```

I also enabled public key authentication. The goal is to disable all 
tcp forwarding from SSH and only allow the users mentioned above to have forwarding on two ports:

- SSH
- a web server

In my /etc/hosts.allow and .deny files there are **no** entries.

I setup the appropriate authorized_keys file (just the ssh-rsa ... line) in /home/passport/.ssh/authorized_keys

From a Windows machine, try to ssh:

```
ssh passport@10.0.0.5 -N -L 22:10.0.0.5:22 -L 8080:10.0.0.5:8080
```

This works fine when "I try to surf to http://127.0.0.1:8080"

This means my port forwarding works fine.

Now, I want to try to SSH through that tunnel and use 'user1':

```
ssh -N user1@127.0.0.1

```

At this moment, I get:

```
ssh_exchange_identification: Connection closed by remote host
```

Whereas, if I just SSH directly from my Windows machine, I succeed:

```
ssh -N user1@10.0.0.5
```

I don't know why it does not work.


If I re-edit my sshd_config file and remove the "Match" directive and allow uncoditional port forwarding then SSHing to 127.0.0.1 works fine again!


I inspect /var/log/auth.log and observe:

```
Feb  4 10:28:23 myhost sshd[2097]: debug1: server_input_channel_open: ctype direct-tcpip rchan 257 win 16384 max 16384
Feb  4 10:28:23 myhost sshd[2097]: debug1: server_request_direct_tcpip: originator 0.0.0.0 port 0, target 10.0.0.5 port 22
Feb  4 10:28:23 myhost sshd[2097]: Received request to connect to host 10.0.0.5 port 22, but the request was denied.
Feb  4 10:28:23 myhost sshd[2097]: debug1: server_input_channel_open: failure direct-tcpip

```
I try to flush the iptable with -F and try restarting sshd, but still I get a connection closed error.

Why can't I ssh via the tunnel?

The reason I created "passport" user is to allow users to remotely login to my network. They will be able to use the web server.

Now if they want to use GIT, they will use the following for example:

git clone ssh://user1@127.0.0.1/repos/repo.git

Please advise on how to solve my problem. I tried all of the solutions listed for the question with the same title as my question but to no avail!

---

### Post by Lars Noodén on 2013-02-04
What about like this:

```

ssh passport@10.0.0.5 -N -L 22:localhost:22 -L 8080:localhost:8080

```

Edit: never mind that gives the same error.

---

