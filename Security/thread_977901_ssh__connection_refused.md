---
title: "ssh : connection refused"
date: 2008-11-10
forum: Security
---

### Post by leonardevens on 2008-11-10
I just got a new laptop running ubuntu 8.04.  It is on a local network, and I can ping its ip address, so I know it is there.  I also have another machine running Fedora.  I can ssh and scp from the ubuntu machine to the Fedora machine, but when I try to ssh in the reverse order from the Fedora machine to the ubuntu machine, I get "connection refused".

I presume something has to be reconfigured?  What?


More generally,

I am pretty familiar with Fedora and other RedHat like Linuxes, so I would know what to look at if the situation were reversed.  But I can't ffind familar commands under Ubuntu.

What corresponds to iptables under ubuntu, for example?

What command is equivalent to /sbin/service?

Is there somewhere that I can find a list of differences between these different Linuxes?   Anything for a quick summary of how to use ubuntu?

---

### Post by HermanAB on 2008-11-10
By default, Ubuntu desktop doesn't run any services.  So you need to install OpenSSL, run the sshd daemon and enable port 22 incoming in your firewall.

Use "ssh -vvv user@server" to debug ssh connections.

Cheers,

Herman

---

### Post by blackened on 2008-11-10
Have you installed the openssh-server package? There's a short decent tutorial [here]("http://www.cyberciti.biz/tips/howot-install-ubuntu-linux-ssh-server.html") (use or omit the change to port settings at will, I personally don't use port 22 forwarding at the router level).

---

### Post by Sarmacid on 2008-11-11
Iptables is the same for ubuntu, and the services are found in /etc/init.d/

So for example for apache
```
/etc/init.d/apache2 start|stop
```

---

