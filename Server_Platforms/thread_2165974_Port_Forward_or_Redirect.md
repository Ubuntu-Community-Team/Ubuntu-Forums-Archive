---
title: "Port Forward or Redirect"
date: 2013-08-07
forum: Server Platforms
---

### Post by nerdtron on 2013-08-07
Hi all, here's my setup

client --------- Server A ------- Server B

cllient is public, Server A has public IP, Server B is private and can only be accessed from Server A.
A client will connect to Server A, using ssh (or Filezilla) to upload some files, but client will be redirected to Server B. Which means, the client will see Server B when in reality he connects to Server A.

Is there a way to do this? A command line ssh willl do but it would be better if filezilla will work.

---

### Post by Lars Noodén on 2013-08-07
There are  several ways to do that.  One is to forward a port over an intermediate host, in this case being server A.  First set up the forwarding on the client:

```

ssh -L 2222:serverb:22 servera

```

That will forward port 2222 on the local client to port 22 on server B via server A.  You can also use options -N and -f if you like.

Then in another window, or using FileZilla, connect SFTP to port 2222 on the local host.

```

sftp -P 2222 localhost

```

That should then connect your client to server B.  There are some other examples in the sections on *Tunnels* and *Proxies and Jump Hosts* in the [Wikibook on OpenSSH](http://en.wikibooks.org/wiki/OpenSSH#Cookbook) I put together a while ago.

---

### Post by SeijiSensei on 2013-08-07
A simple iptables rule will do this, too:

```
/sbin/iptables -t nat -A PREROUTING -p tcp -d ext.ip.of.gateway --dport 22 -j DNAT --to-destination int.ip.of.server:22
```

where ext.ip.of.gateway is the IP address on the gateway's Internet-facing interface, and int.ip.of.server is the IP of the interface to which packets will be sent.

Remember you'll need to enable forwarding on the Internet-facing machine by uncommenting "net.ipv4.ipforward=1" in /etc/sysctl.conf.  If that machine has a firewall, as it should, you'll need to open port 22 as well, of course.

Another alternative is to use an application-level proxy like [tcpproxy](http://www.quietsche-entchen.de/cgi-bin/wiki.cgi/proxies/TcpProxy).  One attraction of this method is that you can wrap tcpproxy with [xinetd]("http://linux.die.net/man/8/xinetd") and use that to restrict access to the proxy.

---

### Post by markbl on 2013-08-07
> **Lars Noodén said:**
> 
```

ssh -L 2222:serverb:22 servera

```

It is slightly more efficient and a little easier to just configure a proxycommand, e.g. in your ~/.ssh/config on "client" pc:

```

Host serverb
  Proxycommand=ssh -qax -o "clearAllForwardings=yes" servera nc %h %p

```
then just "ssh serverb" from client pc will connect directly into serverb in the one command and will only create one encrypted tunnel, not a redundant second one.

---

### Post by nerdtron on 2013-08-07
Thanks for the replies! I will try them today.

---

