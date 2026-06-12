---
title: "Specific Project"
date: 2014-12-01
forum: Server Platforms
---

### Post by Khionu_Pluffy on 2014-12-01
Ok, I have a rather complex project, and I'm not sure how to approach it. The idea is on the right. The "services" would be a Minecraft server (and other game servers), FTP, and Remote Desktop, hosted on my home network. Maybe others in the future.
So, I'm not sure how I would program such a gateway..... I would like to keep it as integrated in the system processes as possible, as opposed to through a Web Application.

I have programming experience, but nothing on this scale. I know Perl and Java. Any resources for building blocks that I could string together would be amazing.[ATTACH=CONFIG]258300[/ATTACH]

---

### Post by newbie-user on 2014-12-01
Kinda sounds like you just want port forwarding on your home router. If you want to use Ubuntu as your home router, then you might want to use iptables to port forward to your servers. I assume your intention is something like this:  domain ==> home router (ubuntu) ==> home network (ftp, minecraft, RDP)

So on the ubuntu router, you should first enable ip forwarding in /etc/sysctl.conf by uncommenting the following line:
```
#net.ipv4.ip_forwarding=1
```

Then set up iptables:
```
iptables -t nat -A PREROUTING -i *[name of your external interface, such as eth0]* -p tcp --dport 3389 -j DNAT --to-destination *[ip address of RDP server]*:3389
iptables -t nat -A PREROUTING -i *[name of your external interface, such as eth0]* -p tcp --dport 21 -j DNAT --to-destination *[ip address of FTP server]*:21
iptables -t nat -A PREROUTING -i *[name of your external interface, such as eth0]* -p tcp --dport *[minecraft port]* -j DNAT --to-destination *[ip address of minecraft server]*:3389
iptables -t nat -A POSTROUTING -j MASQUERADE
```

Next, save the iptables configuration:
```
iptables-save > *[some location, such as /etc/iptables.rules]*
```

---

### Post by Khionu_Pluffy on 2014-12-01
Huh.... that would leave it unsecure (forgot to mention that aspect), but I could always incorporate a tunnel. It actually is a much easier solution than I thought would have to be made. I would just get clever with creating batch files that use PuTTY (console), so that people don't complain about me over complicating things (they will already, but it will be shorter this way).

Thank you :)

---

### Post by newbie-user on 2014-12-06
Do you not want your servers to be publicly accessible? If you want them to be private, then you could specify source ip addresses in your iptables rules. That way only traffic from known sources are accepted and transmitted to your servers.

---

### Post by TheFu on 2014-12-06
This is fairly simple.

a) don't use FTP, use sftp.  Plain FTP use should have ended in 1995.
b) setup either ssh or openvpn and use those to secure the transport from anywhere in the world.  openvpn is best if you want every port to your network to be secured, but ssh is 100x easier and can be used to forward a small number of ports fairly easily.
c) Putty - that's the hard way. If you use Linux clients, life gets much easier by using the ~/.ssh/config file to manage the settings for each remote system.  ssh, scp, sftp, x2go, rsync, rdiff-backup ... anything that uses ssh will honor that config on UNIX-like systems.
d) remote desktop for Linux is securely, easily, solved using **x2go**. Install the server on your remote Linux desktop machine, it uses ssh (and the ~/.ssh/config file plus any ssh-keys) for connections and encrypted transport from anywhere in the world.  x2go uses NX, which feels 2-3x more efficient when compared to VNC or RDP.  From the LAN or from around the world, x2go is amazing.

Java really shouldn't be allowed onto the internet. It is just too much of a security nightmare these days - like php.  Both these tools are fine inside a LAN or when accessed via a VPN, just not on the internet.  Read the OWASP.org pages on both languages and if you have to use one, be certain to follow/check the top 10 OWASP list for application developers.

Oh - no programming needed.  ssh is amazing, secure, more convenient than pretty much any other tool.  Learn it. Know it. Love it.  Of course, with that power comes lots of folks who will try to hack into your network using it.  So ... don't use passwords for ssh, only keys.  Don't allow brute force attacks, use denyhosts or fail2ban - be certain to verify that fail2ban is working - in 14.04+ is seems the default setup isn't working.  Do not allow remote root access over ssh (ever).

---

