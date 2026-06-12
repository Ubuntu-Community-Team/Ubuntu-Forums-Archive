---
title: "Apache getting hacked"
date: 2007-05-18
forum: Server Platforms
---

### Post by electronerdz on 2007-05-18
I have a server out on the Internet. For the longest time, this server was behind a regular router/firewall, forwarding port 80. I have now directly connected this machine to the Internet. It is a standalone web server. Not a router of any sort. Within a few days of being directly connected, it became a bot for some spammer or whatever. I put IPTABLES on it (I was in a rush when I moved it originally, and didn't think/take the time to put a firewall on it). I set IPTABLES to allow ports 22/80/10000. It is still getting hacked. However, it appears that it is actually getting hacked through Apache. The extra scripts that run (Perl scripts of some sort) are running as the www-data user. I just shut down the server remotely for now, so I don't have access to it. I am just wondering if there is some sort of known vulnerability in Apache at the moment, or maybe I should be adding something to httpd.conf that differs from a somewhat default setup.  When I go back to the office and start it up again, I can get parts of config files.

A little bit more about the virus:

It starts up more httpd processes:
www-data  4801     1  0  1231  2944   0 10:06 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL

It also seemed to startup inetd.

A listing in /tmp:

drwxrwxrwt  5 root     root      4096 2007-05-18 12:56 .
drwxr-xr-x 22 root     root      4096 2007-05-17 23:46 ..
-rwxrwxrwx  1 www-data www-data 28381 2007-05-16 16:00 b.txt
drwxrwxrwt  2 root     root      4096 2007-05-17 23:50 .ICE-unix
-rw-r--r--  1 www-data www-data 29730 2007-05-13 15:32 ircdd.txt
-rw-r--r--  1 www-data www-data 29730 2007-05-13 15:32 ircdd.txt.1
-rw-r--r--  1 www-data www-data 29730 2007-05-13 15:32 ircdd.txt.2
drwxr-xr-x  2 root     root      4096 2007-05-18 11:15 .webmin
drwxrwxrwt  2 root     root      4096 2007-05-17 23:50 .X11-unix

A couple of times, /var/tmp had stuff in it. Is there somewhere else I should also be looking?

Some of the things used on Apache:

WordPress 2.1.3
awstats
Gallery2

Thanks for any help you can provide.

Jason

---

### Post by electronerdz on 2007-05-18
Thought about it, but forgot to mention. apt-get is up to date and upgraded, including linux-image-server. It is 6.10 Server edition.

---

### Post by ricrac on 2007-05-18
First thing you should do is prepare to rebuild the server. Cleaning an infected system is much more complicated than re-installing in a more secure manner.  

Are you stating you are running a web server connected to the internet with No Firewall?
IPtables should be running locally on the web server, sometimes even if there is an external firewall.

If this is an ISP managed machine.  Tell them it's hacked, they should power off the system without shutting it down and do a forensic backup.  When you receive the backup you can attempt to discover the hack and damage using a forensic system.

Rebuild using secure methods.  Install only the packages required. (Inetd/xinetd, etc. should not be installed.)
Use Ubuntu Server vs. desktop.
Apply standard hardening steps to the server .
..here's a quick link but there are better tutorials available ..[http://www.utexas.edu/its/policies/checklists/redhat-linux.php](http://www.utexas.edu/its/policies/checklists/redhat-linux.php)

Install IPtables or other firewall
install snort or other intrusion detection
Install samhain or other file integrity 
Install Apache chrooted with the minimum required to run. Don't load modules you don't need. 
Install SSH with no root access, ip restricted
Install fail2ban  - if they get mad this may need to wait a bit

Using forensics try to determine any "bad" ips and block using iptables.  This only helps for bots   but sometimes it's automated and not personal.

---

### Post by craigp84 on 2007-05-18
I see no proof of hacking?

Show me what makes you think you've been hacked?

-c

---

### Post by MJN on 2007-05-18
The raw evidence does seem a little thin on the ground, but then the OP did say the machine is currently off hence they were probably privy to further info than shown when at the machine.

However, a quick search on ircdd.txt found the following, which looks to me like something you'd probably not want hanging around:

[http://www.overflow.netfast.org/ircdd.txt](http://www.overflow.netfast.org/ircdd.txt)

Did you (the OP) have a bulletin board running on your machine?

Mathew

---

### Post by craigp84 on 2007-05-18
> [http://www.overflow.netfast.org/ircdd.txt](http://www.overflow.netfast.org/ircdd.txt)

WooHoo now that sounds more like it.

Can you post a copy of the ircdd.txt from your server please - the latest version please. I;d like to have a wee play with the bot net if you don't mind :-)

-c

---

### Post by electronerdz on 2007-05-19
ricrac, the machine is my own. It is my play machine. I am thinking that there is still something on the machine though. However, I had something like this once before on a different distro, and just deleted it and rebooted, and I was fine (and did upgrades too). I am going to remove the inetd. I was already using server edition. And being that it is Ubuntu, there is no root. I have done a few things at the link, but I will go through them again. Thank you for that.

Craig, I have "evidence" of it being hacked because my connection disappears because it is saturated with junk. My other servers can't get out. I didn't think of the IPTables when I put it back on the Internet. I was moving it from my old office to my new one, and leaving for a short vacation the next day. I believe I deleted those files, but when I start it back up in a few hours, it probably won't take long for it to come back.

Mathew, I had no bulliten board. I am really just using the server for my blog right now. Which is why I just shut it off. It's not that important.

---

### Post by ricrac on 2007-05-19
If you have a spare machine lying around find a distro/tutorial you like that provides a transparent bridged firewall.  
No ip addresses, logs can't be erased.
Place in between the net and your machine to learn the hack, essentially turning your machine into a honeypot.  Use this for a day or two after the rebuild which will be the active time for re-infection.  If you do this you may want to rebuild the system using the same versions of software, same permissions on files and same username passwords, to watch and learn the re-infection methods.

Quick search, much better links out there, 
[http://www.securityfocus.com/infocus/1737](http://www.securityfocus.com/infocus/1737)

---

### Post by electronerdz on 2007-05-20
I have the machine back up. I used the same firewall conf as my other machine. Here is the old one:

*nat
:PREROUTING ACCEPT [9:2313]
:POSTROUTING ACCEPT [43:2806]
:OUTPUT ACCEPT [43:2806]
COMMIT
*mangle
:PREROUTING ACCEPT [163:10433]
:INPUT ACCEPT [162:10373]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [151:69344]
:POSTROUTING ACCEPT [151:69344]
COMMIT
*filter
:FORWARD ACCEPT [0:0]
:INPUT DROP [0:0]
:OUTPUT ACCEPT [0:0]
-A INPUT ! -i lo -j ACCEPT
-A INPUT -p tcp -m tcp --dport ssh -j ACCEPT
-A INPUT -p tcp -m tcp --dport 21 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 10000 -j ACCEPT
COMMIT


And here is the new one:

*filter
:FORWARD ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A INPUT -p tcp -m limit -m tcp --tcp-flags SYN,RST,ACK SYN --limit 100/sec -j ACCEPT
-A INPUT -p tcp -m tcp -d {ipaddr} -i eth0 --dport 1 --tcp-flags SYN,RST,ACK SYN -j ACCEPT
-A INPUT -p tcp -m tcp -d {ipaddr} -i eth0 --dport 80 --tcp-flags SYN,RST,ACK SYN -j ACCEPT
-A INPUT -p tcp -m tcp -d {ipaddr} -i eth0 --dport 10000 -j ACCEPT
-A INPUT -p tcp -m tcp -d {ipaddr} -i eth0 --dport 21 -j ACCEPT
-A INPUT -p tcp -m tcp -d {ipaddr} -i eth0 --dport 22 -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -p tcp -m tcp --tcp-flags SYN,RST,ACK SYN -j REJECT --reject-with icmp-port-unreachable
-A INPUT -p udp -m udp -j REJECT --reject-with icmp-port-unreachable
COMMIT
*mangle
:PREROUTING ACCEPT [987527:623190644]
:INPUT ACCEPT [987527:623190644]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [1061458:862341252]
:POSTROUTING ACCEPT [1061458:862341252]
COMMIT
*nat
:PREROUTING ACCEPT [21172:2672487]
:POSTROUTING ACCEPT [16251:1175464]
:OUTPUT ACCEPT [16251:1175464]
COMMIT

I've taken out the comments. The machine appears to be a little more stable this way. Albeit, a little slow when connecting, but I think I need to remove the limit line... 

The ircdd.txt file has not returned yet, but if I do ever get one, I will let you know.

I am going to let it run like this for a couple of days before I decide that this will work.

---

### Post by ricrac on 2007-05-20
-A INPUT -p tcp -m tcp -d {ipaddr} -i eth0 --dport 10000 -j ACCEPT

This is a nono.  Never allow administration from "anywhere". 

Use something like this to run webmin over ssh
ssh  -L 100001:webminserver-ip:10000 sshserver-ip cat -
lynx localhost:100001 displays webmin page

if webmin server is on same machine as ssh server located at 192.168.1.1
ssh  -L 100001:127.0.0.1:10000 192.168.1.1 cat -
lynx localhost:100001 displays webmin page

Webmin should then be restricted to ssl only and bound to ip address 127.0.0.1 only

The ssl is redundant but encouraged as a password eavesdropping safeguard.

Or if you only administrator from a single ip location you could use something like this
-A INPUT -p tcp -m tcp -d {ipaddr} -i eth0 -s 192.168.1.2 --dport 10000 -j ACCEPT
where -s 192.168.1.2 is the address of the remote machine used to administer webmin

If you mis-configure webmin and allow access to it, you're hosed.

---

### Post by electronerdz on 2007-05-20
Well, this is all eventually going behind a real firewall, and I would be using a VPN to get in. This is the way it was before, it wasn't outside accessible.

I also know I still have something on the system, but yet, it is dormant, or broken, as it hasn't made any outgoing connections, but this one line in ps is questionable.

www-data  4882     1  0 16:54 ?        00:00:00 /usr/bin/init.d/started

I've also noticed that AWStats is 6.5, not 6.6. I am thinking this is where I got compromised. It is getting disabled for the moment... or better yet, just not outside accessible, until I get a chance to actually upgrade that manually (since it is not updated in the repositories).

I am going to be looking into just clearing it all off and starting over again, probably with 7.04. It's just going to be a pain.

---

### Post by ricrac on 2007-05-20
Awstats or other admin pages and apps could be set up on it's own virtual host , named based if extra ip's are not available.  This is much easier to maintain and secure.

[www.mysite.com](www.mysite.com)   - has public and authenticated areas

admin.mysite.com  or [www.mysite.com:8080](www.mysite.com:8080)  or any other port than 80 (or 443 if used)
Admin can be restricted by ip, browser type, OS type, timeofday, ssl cert, or anything you can think of without impacting "public" sections.

I like this because it's easier to flag issues from the logs.  Admin.mysite.com will has it's own access and error logs.

On one machine with one instance of apache
You can run hundreds of domains on the same IP with different names, named based.
You can run hundreds of domains on the same IP with different ports, port based.
You can run hundreds* of domains and IP addresses on the same machine, ip based.
*usually only 2-7 IP's per card in general multihomed use in my experience, multiport cards (dual and quad are very popular in colo servers), combo's of cards and/or usb net devices
Any combination of the above.

And of course,
Multiple instances of Apache or other web server, each with any combo of above.

---

