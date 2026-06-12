---
title: "[SOLVED] ssh problems"
date: 2008-12-27
forum: Server Platforms
---

### Post by crypto91 on 2008-12-27
I have a LAMP server set up with the package openssh-server installed. I used the command ufw allow 22 so that connections to my server via port 22 should be allowed. Yet every time I try to access my server via ssh on my desktop, it says that the connection was refused to port 22. I'm using a dynamic dns to keep my ip address up to date, so that shouldn't be a problem. Any help would be appreciated.

---

### Post by quad3d@work on 2008-12-27
Let me get this straight....

Server (At home) <===> Router (At home) <===> ((( INTERNET ))) <===> Desktop (somewhere else).

Your server at home, or rather... your router is configured to talk to to dynamic dns service to reset to new IP. From your desktop, outside the house, you cannot SSH to your server, at home. Even port 22 forwarding is set set between your server and router?

---

### Post by hictio on 2008-12-27
> **quad3d@work said:**
> Let me get this straight....

Server (At home) <===> Router (At home) <===> ((( INTERNET ))) <===> Desktop (somewhere else).

Your server at home, or rather... your router is configured to talk to to dynamic dns service to reset to new IP. From your desktop, outside the house, you cannot SSH to your server, at home. Even port 22 forwarding is set set between your server and router?

++
First, make sure you can connect to the SSH server from within your LAN, did you try that? Did it work?
Then, make sure you all the in between boxes, router, firewalls are allowing SSH access and redirection, if necessary, to the SSH server on your Server.

One the easiest and fastest ways of testing your SSH connection is:
```

telnet IP.address.server 22 (ENTER)

```

You'll have to see something like this:
```

Trying ip.address.here...
Connected to localhost.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1

Protocol mismatch.
Connection closed by foreign host.

```

Type a few Enters to go back to the prompt.

Are you sure that the firewall its not blocking it, can you disable it a minute for the tests?

---

### Post by crypto91 on 2008-12-27
I'm attempting to ssh via a desktop in my house. However, because I'm attempting to do so through dyndns, it should be the same as accessing it through the internet at a remote location, right? Or am I wrong?

When I try telnet I see this... ```
Trying ip.address.here...
telnet: Unable to connect to remote host: Connection refused
```

This is the same after disabling the firewall.

I'm sorry if this seems weird, I'm new to the whole server/ssh thing.

---

### Post by hictio on 2008-12-27
> **crypto91 said:**
> I'm attempting to ssh via a desktop in my house. However, because I'm attempting to do so through dyndns, it should be the same as accessing it through the internet at a remote location, right? Or am I wrong?

When I try telnet I see this... ```
Trying ip.address.here...
telnet: Unable to connect to remote host: Connection refused
```

This is the same after disabling the firewall.

I'm sorry if this seems weird, I'm new to the whole server/ssh thing.

Sorry, you are typing this, right?
```

telnet ip.address.here 22 (ENTER)

```

And, since you are inside your LAN, 'ip.address' is the private one, right?

---

### Post by crypto91 on 2008-12-29
It works with the private ip. I tried ssh with the private ip and it works too. Now it's just the public login that doesn't work. Thanks for that tip.

---

### Post by mbeach on 2008-12-30
some routers don't deal well with resolving back to themselves - you could be running into that issue.  Try from a place outside of your network, or have a friend try.  Also, visiting:
[http://www.canyouseeme.org/](http://www.canyouseeme.org/)
might let you know if they can see your port.
good luck,
mb.

---

### Post by hictio on 2008-12-30
Is your router forwarding the SSH port to the IP (the private one) of the Ubuntu Server?
If yes.

Does your ISP block that port? Perhaps you can change the listening port (on the router) to something like 2202, and forward that to the port 22 (SSHD' standard port) and see if you can connect to the ssh server on the Ubuntu Server from the outside, test it kike this:

```

telnet public.IP.address 2202 (ENTER)

```

If your router is correctly configured, it will direct anything that comes to the public IP and the port 2202 (for instance) to the port 22 of the Ubuntu Server.

---

### Post by crypto91 on 2008-12-31
I got it fixed! 

It turned out to be my router firewall that was blocking it, but I fixed it and can now ssh to my server through the internet. Thank you all!

---

