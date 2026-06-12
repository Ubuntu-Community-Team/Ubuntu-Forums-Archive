---
title: "New Ubuntu Server 10.10 installed, out-of-the-box security?"
date: 2010-10-11
forum: Server Platforms
---

### Post by Jeinhor on 2010-10-11
Hello,

I've just setup a new Ubuntu Server 10.10 serving SVN through Apache (HTTP, HTTPS).

It seems all ports are open by default on this new server. Why is this? Do I need to lock it down with iptables, or is it secure as it is anyway (somehow)?

Thanks in advance!

---

### Post by HermanAB on 2010-10-11
Hmm, you cannot possibly be running 65000 services, so no, all ports are most probably not open.

However, you said that you installed Apache and Subversion, so port 80, 443 and 3690 should be open.  If you want them closed, disable those services.

You can see what you are doing with top, ps and netstat.

---

### Post by Jeinhor on 2010-10-14
Port 80 and port 443 are indeed open. 3690 is as far as I know not open, as I publish Subversion using Apache and the dav_svn-mod.

With "open" I mean that if a service (trojan or other dangerous software) would start listening on that port, users would be able to connect. Perhaps there are also some other services running on Ubuntu by default which potentially could introduce a security breach.

In Windows, for example, there is a firewall enabled by default. If I don't open the ports there, no incoming connections will get through to my services. If a harmful service would start listening on port 5456 (for example), that port would need to be enabled in the firewall before any connections can get through.

But perhaps that's just an unnecessary feature of Windows, as Windows runs more services listening on various ports by default? You're saying there's no need to enable iptables and set it up to block access to all ports except 80 and 443 on a new, public Ubuntu server?

Thanks for your answer.

---

### Post by CharlesA on 2010-10-14
Linux is not Windows. See the security sticky [here]("http://ubuntuforums.org/showthread.php?t=510812").

It's always a good idea to use a firewall, but if you only have apache listing for requests, and that's the only service on the machine, you could probably get by without using one.

That being said, I always firewall server boxes.

---

### Post by HermanAB on 2010-10-14
Howdy,

Most firewalls run Linux.  So would you put a firewall in front of your firewall recursively?

A properly configured server doesn't need a firewall.

---

### Post by koenn on 2010-10-14
> **Jeinhor said:**
> 
In Windows, for example, there is a firewall enabled by default. If I don't open the ports there, no incoming connections will get through to my services. If a harmful service would start listening on port 5456 (for example), that port would need to be enabled in the firewall before any connections can get through.
If a harmful service would manage to get itself installed and running on your server, could it not just as easily add a rule to your firewall to allow connections (if that firewall is on the same machine as the server, obviously)

> **Jeinhor said:**
> 
But perhaps that's just an unnecessary feature of Windows, as Windows runs more services listening on various ports by default? You're saying there's no need to enable iptables and set it up to block access to all ports except 80 and 443 on a new, public Ubuntu server?

do a port scan. If all you get is ports 80 and 443 open, how's adding a firewall that allows connections to those ports, add to your security ?

---

### Post by Jeinhor on 2010-10-17
Good points! Just wanted to know I didn't do anything really stupid...

Thank you for your input.

---

