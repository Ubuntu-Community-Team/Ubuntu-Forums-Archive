---
title: "ip routing / tunnel to host"
date: 2012-04-28
forum: Server Platforms
---

### Post by aaron.kyle on 2012-04-28
forgive my ignorance;  I am very new to Linux

let's say that I am connecting a home server to an EC2 instance via OpenVPN. I want my EC2 elastic IP to resolve to the home server--effectively making my home server (blocked by ISP NAT) public. Doing this should be a matter of assigning public IP traffic to resolve to the private IP of my server which is connected to the OpenVPN EC2 instance with a static IP, but I can't for the life of me figure this out.

Where to start? Apache? iptables? something else entirely?

---

### Post by SeijiSensei on 2012-04-28
You can forward specific ports from the external server back to your home server using iptables or application-level proxies like Apache's mod_proxy or a more general solution like [tcpproxy]("http://www.quietsche-entchen.de/cgi-bin/wiki.cgi/proxies/TcpProxy"). 

With iptables, you can write a rule on the EC2 server like this:

```
iptables -t nat -A PREROUTING -p tcp -d external.ip.of.remote --dport 80 -j DNAT --to tunnel.addr.at.home:80
```

Replace "external.ip.of.remote" with the EC2 instance's public IP and "tunnel.addr.at.home" with the VPN address of your home server.  This rule forwards HTTP traffic.  You'd need similar rules for any other services you need to forward like, say, port 25 for SMTP.  Note that the ports need not match; you could forward remote port 80 back to port 8000 on your home server if you had some reason to do so.  More commonly, you might choose to forward an arbitrary remote port like 22222 back to 22 at home to enable SSH access.

If you run this rule from the command prompt, you'll need to have root privileges.

---

### Post by aaron.kyle on 2012-04-30
Thanks for your lightening fast reply!

Unfortunately, I must still be doing something wrong.  Some additional context…

I installed OpenVPN as instructed here:

[http://en.wikibooks.org/wiki/How_to_Protect_your_Internet_Anonymity_and_Privacy/Your_own_proxy_and_VPN_on_Amazon_EC2](http://en.wikibooks.org/wiki/How_to_Protect_your_Internet_Anonymity_and_Privacy/Your_own_proxy_and_VPN_on_Amazon_EC2)

Specifically, I installed OpenVPN on EC2 and configured server.conf and client.conf, which I used to connect my local machine via EC2 to the public web (i.e. my public IP is now being shown as the EC2 elastic IP).

Each time I re-start the EC2 instance, I have to re-enter the following commands before I my internet is working “properly” (ie. Allowing regular browsing rather than just SSH commands between my terminal and EC2):

```
sudo modprobe iptable_nat
echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward
sudo iptables -t nat -A POSTROUTING -s 10.8.0.1/2 -o eth0 -j MASQUERADE
```

After entering this, I entered your code:

```
sudo iptables -t nat -A PREROUTING -p tcp -d EC2.elastic.IP --dport 80 -j DNAT --to 10.8.0.2:80
```

Alas!  Entering the EC2.elastic.IP still gives me only to Apache’s “It works!” output, whereas directly navigating to 10.8.0.2: gives me my home server.

Any suggestions?

---

### Post by SeijiSensei on 2012-04-30
Is the web site on your home server in /var/www, or did you create a separate <VirtualHost> container with a different DirectoryRoot?

If you use an IP-based URL like [http://10.8.0.2/](http://10.8.0.2/), you'll get the default page because the IP address doesn't match any ServerName directives in the virtual host definitions.  If you use [http://server.domain.name/](http://server.domain.name/) and that matches a virtual host with "ServerName server.domain.name" (or an equivalent ServerAlias directive), you'll get the DirectoryRoot associated with that name.

Your Amazon host needs to have proper domain name resolution set up and be reachable externally as server.domain.name in order for [name-based virtual hosting]("http://httpd.apache.org/docs/2.2/vhosts/") to work properly.

It's usually very helpful to follow the logs in /var/log/apache2 while troubleshooting.

If you want any connection to your web server to reach your custom site, you can either put the site in /var/www, or you can change the DirectoryRoot in /etc/apache2/sites-available/default to point to your site's directory.  If the directory sits below /home/username, you'll need to run "sudo chmod 711 /home/username" to let the "www-data" user that Apache runs as to see your site.

---

### Post by aaron.kyle on 2012-04-30
Thanks again for the reply!

I wonder if I haven&#8217;t confused the matter somewhat.  I shall try to clarify the situation:

I have a wiki installed in var/www/wiki/  I can reach the wiki by entering name-based-URL/wiki.  If I enter just EC2.IP.address I get the &#8220;It Works!&#8221; output.  All of this is fine.

For the rest of this, I am referring to IP-based URL as EC2.IP.address.

What I can&#8217;t do is reach my local (home) server by redirecting EC2.IP.address or by extending it as EC2.IP.address: PORT.  I run a MacMini server (a physically distinct server from the EC2 server), so it doesn't have a directory location on EC2.  Using OpenVPN, my MacMini is assigned a static internal IP address of 10.8.0.2.  While connected to EC2, I can enter 10.8.0.2 into my browser and see the default MacMini server page (If I enter this when not connected via VPN to EC2 I get nothing, because my server's static IP off the VPN is different).  When I enter 10.8.0.1 I see &#8220;It Works!&#8221; (also confirming I am connected to the VPN).  When I enter EC2.IP.address or EC2.IP.address:80 I also see &#8220;It Works&#8221; (this is normal behavior for the IP on the public internet).

I would like for some way to see the MacMini server page via the EC2.IP.address.

I attempting to use EC2 to enable access to my home files from a remote location.  I used to be able to do this without OpenVPN and EC2 using port forwarding and DynDNS.  I moved to Russia, however, and now my server is now stuck behind an ISP-imposed NAT.  I figured that since I can VPN through EC2 to reach the public internet, there should be a way to move backward from the public internet to my home computer as long as it, too, is connected to OpenVPN with a static IP.

Do you think this is possible?

---

### Post by aaron.kyle on 2012-08-28
UPDATE:

Here are some further suggestions I received when trying to solve this issue:

1. make changes persistent:

```
iptables-save > /etc/iptables.norules
do your custom iptables stuff
iptables-save > /etc/iptables.rules
```

add to the /etc/network/interfaces:

```
pre-up iptables-restore < /etc/iptables.rules
post-down iptables-restore < /etc/iptables.norules
```

ip_forward = 1 - to the end of /etc/sysctl.conf

2. if only needing access to your web site(http) but not ssh or so, use apache  mod_proxy. Like
```
ProxyPass / http://10.8.0.1 should work.
```

NOTE:  This MAY work with the config above to achieve my end goal.  I did eventually get this working, but using an entirely different approach.  It will take some time before I can document it all, but since I got this suggestion and it looks like to may have added the final working touches to the config I was detailing, I figured I'd add it in here.

---

