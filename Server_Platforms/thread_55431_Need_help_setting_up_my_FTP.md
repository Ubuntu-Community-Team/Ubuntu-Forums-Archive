---
title: "Need help setting up my FTP"
date: 2005-08-08
forum: Server Platforms
---

### Post by arcanistherogue on 2005-08-08
Hey, I am setting up an FTP on my server.  I apt-get installed ProFTPd, and I changed hte port in /etc/proftpd.conf to 21219.  I opened the port in my router, checked "Protocol TCP" and "Protocol UDP" in port forwarding in my router, and applied the changes. I then Restarted proFTPd.

I then made an account with a generic password, and asked my friend to connect.  he was using FileZIlla (a windows FTP client) and got hte following error:

> [SIZE=1]Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/home/lol" is current directory.
Command:	PORT 10,0,1,3,11,135
Response:	500 Illegal PORT command
Error:	Could not retrieve directory listing[/SIZE]

I have tried this with many different ports, and neither of my two friends can connect (one on windows, one on linux.).  I think i have messed up configuring the FTP.

Can someone tell me a step by step instructions, from when you apt-get proftpd, to how to configure it properly?  just very basic, to make sure I haven't skipped a step.  Or, if you know why it wont work and how to fix it or an alternative, please post it. 

Thanks.

by the way, the server works, i have the site up ([http://arcanis.is-a-geek.com:81](http://arcanis.is-a-geek.com:81)) but I can't add any files from another computer.

---

### Post by flyinglizard on 2005-08-10
I don't know if FTP will work thorugh a NAT router.  

[http://slacksite.com/other/ftp.html](http://slacksite.com/other/ftp.html)

FTP actually creates more than one connection,  one is control the other is data.  You might be able to configure the clients to use passive mode,  but I am not sure if this will work with the NAT router or not.  Try to google on the subject,  your router may have special FTP logic that will allow it to work,  but I doubt you would be able to change to a port other than 21.

Another solution would be to use ssh and scp,  however you would want to somehow chroot the ssh server so the remote users would only have access to the directories you allow.

---

### Post by arcanistherogue on 2005-08-10
I have a Linksys router.  

And I don't know if I can use ports 20 and 21.

---

### Post by Timppis on 2005-08-11
Hi!

i have also problem with a ftp-server, vsftpd. i have setted up that so far that i can connect on it through LAN but, nobody cannot connect it via internet, i think its a port problem (or firewall?), ISP have maybe blocked those default ports (incoming traffic). does ubuntu (5.04) have a integrated firewall OR can i change vsftpd`s ports somehow ? 

Thankfully

Timppis

---

### Post by relix42 on 2005-08-11
Standard FTP uses two ports - 20 and 21 - one for data transfer and the other for information about the session.  In order for FTP to work across many firewalls, they need to have an FTP protocol helper.  (ip_nat_ftp for iptables for instance).

As a way to help with this, many FTP servers supports a passive mode FTP which uses only one port.  However, the port is somewhat randdom.  So, direct port forwarding won't work correctly.

The easiest solution is to map another public IP through your firewall to your FTP server and encourage the use of passive FTP.  This way, people are using the single port FTP (passive) but, since an IP isforwarded through, the randomness of the passive FTP problem is reduced.

If your router/firewall will support port forwarding, NAT and has an FTP protocol helper, you can get away with the additional public IP for mapping.

Getting FTP to work across a firewall isn't a small task.

---

### Post by frodon on 2005-09-05
This is my [way](http://ubuntuforums.org/showthread.php?t=51611)  to configure proftpd, maybe it could help you.

---

### Post by LordHunter317 on 2005-09-05
[QUOTE=flyinglizard]I don't know if FTP will work thorugh a NAT router.[/quote]It will, if you follow these rules:[list][*]If the server is behind NAT and the client is not, the client must use active FTP[*]If the client is behind NAT and the server is not, the client must use passive FTP[*]If both are behind a firewall, an ftp-proxy must be used.[/list]I suspect the OP is in the third case based on the session.

> however you would want to somehow chroot the ssh server so the remote users would only have access to the directories you allow.Which rssh provides.

[quote=relix42]Standard FTP uses two ports - 20 and 21 - one for data transfer and the other for information about the session.[/quote]You're correct about it using 2 ports, incorrect about which ones.  Port 20 only must be used if the server is making an active data connection to a port under 1024.  Otherwise, it can use any port to originate the data connection, if it desires to.  

Passive FTP obviously uses a random high-level port number on the server.

Port 20 is only of interest if you're doing any egress filtering.

> As a way to help with this, many FTP servers supports a passive mode FTP which uses only one port. Nope, it still uses two.  What it changes is who listens during the data connection (from the client to the server).  This allows clients behind NAT to function with FTP.

The issue here is that both client and server are behind a firewall, so unless his router has an internal FTP proxy, he's stuck unless he replaces it.

---

### Post by Beernut on 2005-09-06
Maybe this will help.  [Ubuntu HowTo: ProFTPD Behind NAT](http://tsb.blogdns.org/2005/06/05/ubuntu-howto-proftpd-behind-nat/) Works with my Linksys router.

---

