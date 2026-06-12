---
title: "Proxy server for Windows"
date: 2011-06-11
forum: Server Platforms
---

### Post by haode on 2011-06-11
Hi,

How do I set up a proxy server for Windows ? Can I use openssh ?

Thanks !

---

### Post by brighty22 on 2011-06-11
It depends on how you want to do it.

SSH tunnelling would secure  the traffic and mean you could circumvent web filtering (if that's why you're wanting a proxy).

Conversely installing Apache and using a PHP proxy high up in a Google search would mean less maintenance, although it would be less effective.

---

### Post by haode on 2011-06-11
> **brighty22 said:**
> It depends on how you want to do it.

SSH tunnelling would secure  the traffic and mean you could circumvent web filtering (if that's why you're wanting a proxy).

Conversely installing Apache and using a PHP proxy high up in a Google search would mean less maintenance, although it would be less effective.

Oh... I will use SSH tunneling instead. Any idea on how to do it ?

---

### Post by brighty22 on 2011-06-12
Obviously you need OpenSSH installed on your server, and an SSH client on any Windows machine you want to connect from - I believe [Putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html") is the most common.

On the server side, you need to make sure port forwarding is enabled in sshd_config. So from a terminal, enter

```
sudo nano /etc/ssh/sshd_config
```

and change the line 'AllowTcpForwarding no' to 'AllowTcpForwarding yes', then save (ctrl+x, 'y', enter) and restart ssh by entering

```
sudo /etc/init.d/ssh restart
```

I've never created a tunnel from windows (hopefully someone else can confirm), but [this]("http://www.devdaily.com/unix/edu/putty-ssh-tunnel-firefox-socks-proxy/1-putty-ssh-tunnel-introduction.shtml") looks like a reasonable tutorial using Putty.

Hope this helps :-)

---

### Post by BkkBonanza on 2011-06-13
The easiest way to tunnel/proxy on Windows is using ssh in "dynamic" mode. Once you install openssh on windows (there are many cygwin based installer packages around now that are almost one-click setups), you run the command,

ssh -fND 8080 user@server
(where user, server are your values for the server you proxy thru)

This will start a SOCKS5 proxy on port 8080 on your local machine. Now go into your browser (or other software like email), and change netowrk settings to use SOCKS5 proxy on localhost:8080. After that your browser traffic will be tunalled thru the local ssh proxy to your server and hit the net from there. Visited websites will see your visit as if it came from your server not your local conenction. This is a good method for securing traffic on a unsecure connection (like a wifi web cafe).

If this doesn't make sense for your usage then just provide more details about what you want to achieve.

Putty and other GUI clients can also do this. You just set the config options for "dynamic" tunnel and use whatever port (8080) you like. After that it's the same, set your browser to use SOCKS5 on localhost on selected port.

SSH only works if you have some external server to connect to or an online service that provides ssh access. I use on demand, temporary Amazon EC2 instances to do that for me as it's cheap/free.

---

### Post by haode on 2011-06-25
Thanks all of you for the reply ! :KS

---

