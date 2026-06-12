---
title: "Tutorials - post the best Ubuntu tutorials ..."
date: 2008-04-09
forum: The Cafe
---

### Post by cwmoser on 2008-04-09
Tutorials on this forum and other places on the Internet are very helpful.  

How about we post here the the best tutorials we have found?

I'll start....

I struggled with setting up Ubuntu Server and found this tutorial very helpful:

[http://www.mysql-apache-php.com/](http://www.mysql-apache-php.com/)

It shows how to setup and configure:
Apache + MySQL + PHP + PhpMyAdmin + Webalizer + Mail Server (Postfix/Dovecot) + SquirrelMail + FTP Server (VSFtp) + ClamAV (Antivirus) + Webmin + IPTables Firewall + PHP-MySQL-Apache Server Kits 

Carl

---

### Post by Crafty Kisses on 2008-04-09
I always thought [PsychoCats]("http://www.psychocats.net") was a really good place for tutorials.

---

### Post by kpkeerthi on 2008-04-09
.... and the links in my signature.

---

### Post by StooJ on 2008-04-09
Wow. Tough question.

I have so many threads from this forum in my bookmarks, but here's a couple (in no particular order) that I have to recommend to people

[Setup Samba peer-to-peer with Windows]("http://ubuntuforums.org/showthread.php?t=202605")

[Mount SMB Shares]("http://ubuntuforums.org/showthread.php?t=280473")

[Share Thunderbird and Firefox data between Ubuntu and Windows]("http://ubuntuforums.org/showthread.php?t=203524")

Also have to mention the guide that really made me take the plunge with Ubuntu in the first place
[Bit-Tech: Build your own server Part 1]("http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1")
&
[Bit-Tech: Build your own server Part 2]("http://www.bit-tech.net/bits/2007/07/24/build_your_own_better_server/1")

---

### Post by philinux on 2008-04-09
Credit where it's due - Nathan did a great job here.

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by billgoldberg on 2008-04-09
> **StooJ said:**
> Wow. Tough question.

I have so many threads from this forum in my bookmarks, but here's a couple (in no particular order) that I have to recommend to people

[Setup Samba peer-to-peer with Windows]("http://ubuntuforums.org/showthread.php?t=202605")

[Mount SMB Shares]("http://ubuntuforums.org/showthread.php?t=280473")

[Share Thunderbird and Firefox data between Ubuntu and Windows]("http://ubuntuforums.org/showthread.php?t=203524")

Also have to mention the guide that really made me take the plunge with Ubuntu in the first place
[Bit-Tech: Build your own server Part 1]("http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1")
&
[Bit-Tech: Build your own server Part 2]("http://www.bit-tech.net/bits/2007/07/24/build_your_own_better_server/1")

Thanks, I've been looking forever to find a decent guide on how to set up a server and samba!

---

### Post by ByteJuggler on 2008-04-10
> **cwmoser said:**
> Tutorials on this forum and other places on the Internet are very helpful.  

How about we post here the the best tutorials we have found?

I'll start....

I struggled with setting up Ubuntu Server and found this tutorial very helpful:

[http://www.mysql-apache-php.com/](http://www.mysql-apache-php.com/)

It shows how to setup and configure:
Apache + MySQL + PHP + PhpMyAdmin + Webalizer + Mail Server (Postfix/Dovecot) + SquirrelMail + FTP Server (VSFtp) + ClamAV (Antivirus) + Webmin + IPTables Firewall + PHP-MySQL-Apache Server Kits 

Carl

Hey Carl,

Just to clarify -- I know you also set up a VPN together with most of the above on your server.  How exactly did you combine the VPN with the above (did you use another page, if so which one?) and what exactly did you do to get the routing/packet forwarding working properly, to allow you to connect to the machines on your LAN via the VPN (other than the VPN server itself).  Did you just use the above link's description/setup for the firewall/IPTables or did you use something else?

Thanks.

---

### Post by cwmoser on 2008-04-10
Here is my notes on installing pptpd VPN server.  This is a different VPN than the one in the link I mentioned.

The only way I was able to get VPN to work with all PC's on my LAN was the "echo 1 > /proc/sys/net/ipv4/ip_forward" command.  It lasts until rebooting.

Below are my notes:


pptpd VPN Server

Install:

      # sudo apt-get install pptpd


Temporarily enable packet forwarding:

        # echo 1 > /proc/sys/net/ipv4/ip_forward


To enable packet forwarding forever(after any restart) open /etc/sysctl.conf and uncomment this line:

net.ipv4.conf.default.forwarding=1


Edit: /etc/pptpd.conf

localip 192.168.0.100

remoteip 192.168.0.50-51

proxyarp


Notes:

    *

      localip is the IP of an adapter in the server.
    *

      remoteip: the IPs that clients are allowed to use  192.168.0.50 thru 192.168.0.51
    *

      Proxyarp: With this entry, you will be able to access other computers on the LAN rather than just the pptp server. Without proxyarp, you will only be able to tunnel to the pptp server computer.


Edit: /etc/ppp/chap-secrets

carl pptpd password

cwmoser pptpd password



Restart pptpd:

# /etc/init.d/pptpd restart



Messages:

check /var/log/messages



Client side Notes:

Don't forget to hit the IPv4 TCP/IP settings on your client machines for the VPN connection.

Uncheck: "Use default gateway on remote network" if you need to (you probably will).

Change some security settings: VPN Connection > Properties > [Security Tab] -> Advanced
Allow these protocols: Check: Microsoft CHAP Version2

---

### Post by Thingymebob on 2008-04-10
I created this quick ref card while I was learning [http://ubuntuforums.org/showthread.php?t=437266]("http://ubuntuforums.org/showthread.php?t=437266")

---

### Post by bodhi.zazen on 2008-04-10
Moved to the cafe as this is not a support question.

FYI: We highlight a "Tutorial of the week"

[Tutorial of the Week](http://ubuntuforums.org/showthread.php?t=655207)

All quality tutorials.

We will watch this thread for suggestions as well.

---

### Post by rodneyaltam on 2008-04-30
Here is also one of the best Ubuntu and other Linux help I was able to access......
The problem is the tutorial is pinoy version.....

See link below.......


[http://it1.com.ph/forum/viewtopic.php?t=71](http://it1.com.ph/forum/viewtopic.php?t=71)

Viper

---

### Post by duckgoesoink on 2008-04-30
> **kpkeerthi said:**
> .... and the links in my signature.

+1 for ubuntuguide.org and ubuntugeek.com

---

