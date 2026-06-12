---
title: "Looking for more awesome things to do with ubuntu server"
date: 2009-07-16
forum: Server Platforms
---

### Post by Belnoctourne on 2009-07-16
the title pretty much sums it up but I've got ubuntu server 9.04 running on a raid array with a 3 terrabyte hard-drive, its joined to my windows domain, its running dhcp, secondary dns, masquerading, and nat for the network, its all going into a gigabyte switch afterwards then to the random dozen computers stored throughout my house, I've got a dd-wrt (hacked linksys firmware) g wireless router, running a pppoe client on the server it does samba sharing, ftp, webmin, I've got my netbook running 8.10 and I can run gui programs through X (gnome is installed but not activated) setup the socks5 proxy and compression over ssh 

ssh -C -X -D 1234(port of your choosing) [email]whatever@server.com[/email]
(then just launch a program from terminal)

I was thinking about trying to setup a graphics cluster to play crazy **** on my netbook but theres not a whole lot of point in it, and I can't seem to find any real info on it besides lab studies so I think I might end up passing on that one unless someone can illustate why its righteous but I'd love it if this thread could be a list of just cool little ubuntu server tricks cause we could use one of those, I'd say try and post in a basic format of just

**name of cool thing**

description of why almost everyone should do it....
_links to more information_

---

### Post by Belnoctourne on 2009-07-16
**ssh proxying**

SSH proxying is awesome because it allows you to create a tunnel to your home network and run all your network traffic through it with ssh's strong encryption so when anyone looks at your network traffic even if your watching movies online or dicking around they wont see anything on there network except for a stream of packets to your home ip, and you can run it on any outgoing port, at the vary least most systems have to allow 80 outgoing and you can run ssh over port 80 so it doesn't even look like theres traffic running on random ports, or 443 if you dont use https on your site, this site has a nice guide on it

[_https://calomel.org/firefox_ssh_proxy.html_]("https://calomel.org/firefox_ssh_proxy.html")

---

### Post by FakeOutdoorsman on 2009-07-16
**tor relay**

If this is a "for fun" server and can spare a small amount bandwidth you can run a Tor relay to help those in countries whose governments clamp down on internet freedom and/or to provide anonymity for yourself.  From the [Tor](http://www.torproject.org) web site:
> Tor protects you by bouncing your communications around a distributed network of relays run by volunteers all around the world: it prevents somebody watching your Internet connection from learning what sites you visit, and it prevents the sites you visit from learning your physical location. Tor works with many of your existing applications, including web browsers, instant messaging clients, remote login, and other applications based on the TCP protocol.

[Configuring a Tor relay](http://www.torproject.org/docs/tor-doc-relay.html.en)

Want to separate Tor from your main OS?  Give it a virtual machine and throw it in that battle-axe called FreeBSD with...

**virtualization**

This is a fun subject.  Use one physical computer to run as several at once, completely separated from each other.

[The Virtualization Mega-Thread](http://ubuntuforums.org/showthread.php?t=973756)

---

