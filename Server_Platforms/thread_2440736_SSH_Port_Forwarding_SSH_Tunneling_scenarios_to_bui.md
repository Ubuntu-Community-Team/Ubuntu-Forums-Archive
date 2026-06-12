---
title: "SSH Port Forwarding/ SSH Tunneling scenarios to built up"
date: 2020-04-14
forum: Server Platforms
---

### Post by mangoooooooo on 2020-04-14
Hi,

first of all, this is my first post, english is not my native language, i already tried google and i am not 100% sure whether this is the right section. (If not, i am sorry!!!)
So pls don't be strict with me =P

For a school project i have to create tasks for other students to learn SSH.

I already have some tasks about the basic stuffs like connect to an ssh server, generate key pairs, copy files from the server...

One (or more) task should cover SSH Port Forwarding/ SSH Tunneling.
I have resources to provide more than 1 servers (machines), with what the students can work with.

My idea is to built up a scenario, where SSH Tunneling makes sense
and i let the students try to connect to an host, which is not reachable from their local host but from the ssh server host.
I saw scenarios where you use SSH Tunneling to get access to an email-server which listens to port 143, so you can forward a port in the local system to that 143 port through the SSH Tunnel.
But thats not implementable in my case.

Do you guys maybe have an idea for an possible scenario or applications where SSH Tunneling makes sense? 
I am pretty new in this stuff and am a linux beginner and i would be very thankful for any cause for thoughts. 

I am sorry if this what i wrote is super stupid...


Tank you for being patient

---

### Post by TheFu on 2020-04-14
SOCKS Proxy for web browsers.  Basically, a poor man's VPN, if you don't mind leaking DNS information.

Setup a ~/.ssh/config file to access a remote server using a host alias that fills in the remote username, non-standard port and ip address for all ssh-based connections.  Setup multiple host aliases to support different usernames.

Use ssh-copy-id to transfer keys.

Use sftp from a linux file manager to transfer files.  Use one of the host aliases.

Use rsync to synchronize a local directory to the server, recursively.  Use the other host alias.

install and configure fail2ban to block brute force attacks on the standard and non-standard ssh port.

Ensure that the root account cannot be used for any remote connections, except from 1 specific client machine, perhaps a backup server.

Those are just a few ideas. All very useful.

---

### Post by mangoooooooo on 2020-04-15
> **TheFu said:**
> SOCKS Proxy for web browsers.  Basically, a poor man's VPN, if you don't mind leaking DNS information.

Setup a ~/.ssh/config file to access a remote server using a host alias that fills in the remote username, non-standard port and ip address for all ssh-based connections.  Setup multiple host aliases to support different usernames.

Use ssh-copy-id to transfer keys.

Use sftp from a linux file manager to transfer files.  Use one of the host aliases.

Use rsync to synchronize a local directory to the server, recursively.  Use the other host alias.

install and configure fail2ban to block brute force attacks on the standard and non-standard ssh port.

Ensure that the root account cannot be used for any remote connections, except from 1 specific client machine, perhaps a backup server.

Those are just a few ideas. All very useful.

Thanks TheFu!

A ssh-copy-id task is already done.

fail2ban maybe goes bit too far for a ssh "crash course" 

And the rest is really interesting. I will read up on it.

But there is not really something where SSH Tunneling is to use, is there?
**edit: **I just saw Tunneling is used at SOCKS Proxy.

---

### Post by TheFu on 2020-04-15
> **mangoooooooo said:**
> Thanks TheFu!

A ssh-copy-id task is already done.

fail2ban maybe goes bit too far for a ssh "crash course" 

And the rest is really interesting. I will read up on it.

But there is not really something where SSH Tunneling is to use, is there?

SOCKS proxy uses an ssh-tunnel with a web-browser. Let me see if I can find it in these forums. It has been posted a few times. [https://ubuntuforums.org/showthread.php?t=2412982&p=13839332#post13839332](https://ubuntuforums.org/showthread.php?t=2412982&p=13839332#post13839332) has the little script.  Don't worry about using firejail if you don't want that part.  It is just a wrapper to limit access to the file system by program run under it.  It is a lite constraint system for GUI programs like web browsers or email clients. Firejail can be used for many purposes, sometimes to the point of making the core parts of a program non-working. 

Remote desktops based on NX use an ssh-tunnel, but hide the complexities.  The ssh part is built-into the NX protocol.  **x2go** has a client and a server for NX, though those are not compatible with other NX programs. Anyone still using VNC really should check out x2go.  Night (vnc) vs day (x2go).

**Fail2ban** is configured with reasonable defaults during install to protect ssh on port 22/tcp.  Just doing the install on any ubuntu system will enable that protection.  In a home environment, I have the WAN-router doing port translation so all the internal systems run sshd on the default port, but not for internet access to selected systems.  
```
  WAN --> 63999/tcp --> Router ---> 22/tcp LAN-server
```
Setup as many different WAN ports to be forwarded to specific LAN-servers as you need.

Perhaps a little more coverage on using ssh-keys for different purposes. The way that github.com uses them is very interesting to allow only 1 program to be run, but not allow generic ssh shell access.

If you have any slides, I'd be happy to look them over.  I did an impromptu ssh class for my LUG over a video conf a few weeks ago. Some of the old timers didn't realize how powerful the ~/.ssh/config was.  They liked it so much, they started training their peers at work.

---

### Post by mangoooooooo on 2020-04-19
Last 2 days i had no time to work on the project.

SOCKS proxy sounds interesting for me, but the script you posted seems a bit complicated for me yet.
But i will work for it.


One thing i tried since last time is:

I am hosting a simple nginx html page on an server via docker container. 
It is mapped on port 80. So when i browse [https://localhost](https://localhost) the page appears.

My plan was now to block all incoming requests to port 80 except from the host itself. 
So you can use an SSH tunnel from outside to that machine to reach that port 80 and let the page appear through your browser. 

Does this make any sense so far? Am I right about the usage of an SSH Tunnel at that point?


How ever, i tried to block all incoming requests with this:
> 
iptables -A INPUT -p tcp --dport 80 -s 1.2.3.4 -j ACCEPT
iptables -A INPUT -p tcp --dport 80 -j DROP

But even before building the tunnel, i still could call up the page from outside (from another machine in the same network.)
Is there anything False with the iptables command?

---

