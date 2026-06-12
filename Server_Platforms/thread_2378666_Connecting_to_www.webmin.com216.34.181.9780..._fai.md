---
title: "Connecting to www.webmin.com|216.34.181.97|:80... failed: No route to host."
date: 2017-11-25
forum: Server Platforms
---

### Post by xshadow101 on 2017-11-25
Hi all,

I am having trouble installing webmin on my ubuntu server 17.10. I have source added to /etc/apt/sources.list as

deb http:/download.webmin.com/download/repository sarge contrib

When I try to execute wget [http://www.webmin.com/jcameron-key.asc](http://www.webmin.com/jcameron-key.asc), I get the message:

Connecting to [www.webmin.com](www.webmin.com) ([www.webmin.com)|216.34.181.97|:80](www.webmin.com)|216.34.181.97|:80)... failed: No route to host.

I did little research and found that it is a firewall issue. I tried the solution as suggest on the link but that didn't work.
[https://www.digitalocean.com/community/questions/dns-wget-no-route-to-host](https://www.digitalocean.com/community/questions/dns-wget-no-route-to-host)

After trying the solution suggested in the link, my assessment was that it is not a firewall issue because I tried following commands to accept all trafic from webmin.com(216.343181.97):

sudo iptables -A INPUT -p tcp -m tcp -s 216.343181.97 --dport 80 -j ACCEPT
sudo iptables -A INPUT -p tcp -m tcp -s 216.343181.97 --dport 433 -j ACCEPT


I have bridge networking enabled in virtualbox network settings. I am able to ping google.com but I can't ping my host windows10 PC.

I can't ssh my ubuntu server machine also. I used following command to create a rule for my server machine to ssh connection using this command:

sudo iptables -A INPUT -p tcp -m tcp --dport 22 -j ACCEPT

But that didn't fix the ssh issue also. I am stuck and don't know what else to try. Any useful tip/idea/thought would be appreciated to work around the problem.

Thanks.

---

### Post by wildmanne39 on 2017-11-25
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by darkod on 2017-11-25
I would like to give you couple of advices before you continue troubleshooting this:

1. Use only LTS for servers, even for home ones. That means the latest LTS is 16.04 LTS, the next one will be 18.04 LTS next April. Non-LTS versions have very short support lifetime and are basically worthless for production servers (except short tests).
2. Don't use webmin. It is not supported and is not recommended.

If despite this you want to continue:
3. Check your internal LAN communication and VBox and ubuntu server settings. If you use bridged networking the server should have IP in the subnet range of your home router, not in the VBox virtual subnet. You should be able to ping your host and router on the LAN. You have to get the network settings and setup right.
4. Unless you set iptables to block outgoing traffic, you don't need to investigate it for reaching remote hosts. The http traffic reaches the destination host on port 80 ([www.webmin.com](www.webmin.com)), it doesn't come back to your server on port 80 so allowing it in iptables doesn't help. In fact, if the server is on your LAN with private IP why do you need iptables firewall anyway? Your router firewall is protecting you from the internet.

---

### Post by mastablasta on 2017-11-28
instead of Webmin try Zentyal (more aimed at business) or Ajenti.

---

