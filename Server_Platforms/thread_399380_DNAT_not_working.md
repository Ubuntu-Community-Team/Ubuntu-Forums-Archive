---
title: "DNAT not working"
date: 2007-04-02
forum: Server Platforms
---

### Post by mopok on 2007-04-02
Hi!
I'm quite a newbie in configuring servers/firewalls under Linux.
Now I'm tryng to set up Ubuntu 6.06 to be a firewall and a proxy server.
I have two network cards:
Local interface 192.168.0.180 eth1 (loc zone in shorewall)
Interface to my ISP's VPN server 192.168.150.132 eth0 (net zone in shorewall)
My internet connection is established using PPTP-client connection.
I've installed shorewall and squid and provided internet access from the local network. 
Everythig went well before I've tried to permit access from internet to my local web server.
I've set up some DNAT rules in shorewall, but they don't work. 
In shorewall my ppp0 connection is zone net1.
The rule is:
DNAT net1 loc:192.168.0.101 tcp www
The shorewall net_dnat packet counter for this rule is 0.
Please help!

---

### Post by huygens on 2007-04-02
That is too long ago I did not play with shorewall and I have forgotten its syntax.
What I would recommend would be to use [webmin]("http://www.webmin.com/"). I do not know if it can use your shorewall configuration or not, so perhaps you would have to redefine the rules already specified in webmin. But it can configure NAT for you:
check [http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)

PS: I only found this resource googling around, and I do not know what it is worth...

PS2: I will try to look anyway at your configuration line of shorewall, and try to remember if there is not an obvious mistake... But I do not have the time right now...

---

### Post by huygens on 2007-04-02
How many network interface do you have? It seems you have 3:[LIST]
[*]eth0 - 192.168.150.0/24 (?) - connected to a VPN (?, I'm not sure I understand...)
[*]ppp0 - ?.?.?.? - internet connection
[*]eth1 - 192.168.0.0/24 - your local network where you have your computer but also your server[/LIST]Could you confirm this? Also, could you tell me what is the use of this VPN?

To clarify my notation, when I say 192.168.0.0/24, it means that IP addresses range from 192.168.0.1 to 192.168.0.254.

The zone names in shorewall for those 3 interfaces are (as I understood them, please confirm)[LIST]
[*]eth0: ?
[*]ppp0: net1
[*]eth0: loc[/LIST]Am I correct?

Then your entry (see below) seems correct to me.
```
 DNAT net1 loc:192.168.0.101 tcp www
```(assuming 192.168.0.101 is the IP address of your server)

Now, about your test. From where do you test this rule? You cannot test it from a computer in the loc zone, neither from the computer where the firewall is running. You have to test it from a computer that belongs to only the net1 zone.

Furthermore, this guide might of some help to you: [http://www.shorewall.net/1.4/shorewall_quickstart_guide.htm](http://www.shorewall.net/1.4/shorewall_quickstart_guide.htm) (pick-up the right guide that applies to your case)

---

### Post by mopok on 2007-04-03
Hi everyone!
2 huygens:
I really have 3 network interfaces:
eth0 192.168.150.129 netmask 255.255.255.192; net zone in shorewall; is used for transport purposes to ISP's VPN server
eth1 192.168.0.180/24; loc zone in shorewall; local interface to my network
ppp0 XXX.XXX.XXX.XXX - PPTP client connetion and my real internet connection.
I have tested my web server availability from outside my firewall. From local network everything works fine couse I've configured routeback on my eth1 and set up some rules to redirect traffic from local machines addressed to external firewall interface to local web server. But from internet while trying to access web server nothing happens. Frankly, there is not only web server, to which I want to connect from internet. There also are mail server and MS Terminal server. And the behavior of this servers while connecting from internet is quite curiously. In the log of mail server I see the following lines:
POP3 server connection brocken (user [email]username@mydomain.com[/email] from XXX.XXX.XXX.XXX) (10054) Remote host has brocken the existing connection
I think it means, that some traffic passes the firewall. But shorewall nat counters for my dnat rules are still 0.
If it can help here is my route -n output
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.149.1   192.168.150.129 255.255.255.255 UGH   0      0        0 eth0
195.98.64.240   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.150.128 192.168.150.129 255.255.255.192 UG    0      0        0 eth0
192.168.150.128 0.0.0.0         255.255.255.192 U     0      0        0 eth0
192.168.0.0     192.168.0.180   255.255.255.0   UG    0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         195.98.74.194   0.0.0.0         UG    0      0        0 ppp0

---

### Post by mopok on 2007-04-03
Stunning update: I've just tested from remote machine. Remote users can access smtp server and successfully send mail! But cannot access POP3 and WEB servers!

---

### Post by huygens on 2007-04-03
just to try it out. Could you use telnet to access the HTTP and POP service?

What you have to do is open a terminal (or console, it is in the Applications->Accessories sub-menu) and execute the following command
*(note that you could execute this command with the same syntax for a Windows command tool - cmd.exe - or from a Mac OS X or any UNIX terminal)*
_For HTTP_: ```
telnet <internet ip or dyn dns host> 80
```then once connected try to type something (whatever like "hello") and press the enter key. Your Apache server should tell that this method is not implemented and close the connection. But at least you know it is reachable.

_For POP_: ```
telnet <internet ip or dyn dns host> 110
```then once connected, the POP3 server should response to you with a message like '+OK POP3 server ready' (at least starting with +OK), you could just type QUIT to exit then, or you might want to try to authenticate and check for the number of e-mails on your POP server. (warning, the method below will send your password in clear), so once connected just type in the following:
```
USER your-box-name
PASS secret
STAT
QUIT
```If you replace your-box-name by the user name you use to access your POP account, you should be able to then the next command where you type in your password (replace 'secret' by your password, but _take care_ that this password will be sent in clear). After successful completion of this command, the STAT command will return you two numbers which I think are the number of messages on the POP server and the amount of bytes for this messages. QUIT will close the session.

---

### Post by huygens on 2007-04-03
Some extra information I have found reading [http://www.shorewall.net/two-interface.htm](http://www.shorewall.net/two-interface.htm).

> If your external interface is ppp0 or ippp0 then you will want to set CLAMPMSS=yes in /etc/shorewall/shorewall.conf.

> If you have an ADSL Modem and you use     PPTP to communicate with a server in that modem, you     must make the changes recommended [here]("http://www.shorewall.net/PPTP.htm#PPTP_ADSL") in addition to those detailed below.     ADSL with PPTP is most commonly     found in Europe, notably in Austria.

Then for trouble shooting DNAT: [http://www.shorewall.net/FAQ.htm#faq1a](http://www.shorewall.net/FAQ.htm#faq1a) (check FAQ 1a and FAQ 1b)

And finally to log your firewall actions: [http://www.shorewall.net/shorewall_logging.html](http://www.shorewall.net/shorewall_logging.html)

---

### Post by mopok on 2007-04-03
Thanks huygens. But I've tested it in the way you propose some time ago and got no result.
Well, it seems I've got a guess.
I think, the problem is in routing back traffic from my local server to client machine trough firewall. I'm not very skilled in SMTP, POP3 or RDP protocols, but it seems SMTP protocol has one-way direction: from client to server. And it supposes little or no interaction between server and client. But, POP3 or HTTP is the other case. They suppose intensive interaction between server and client. So due to my POP3 and Terminal servers behavior, I guess the problem is somewhere in back routing of packets.
Where to look at this routing rules?

---

### Post by mopok on 2007-04-03
Quote:
If your external interface is ppp0 or ippp0 then you will want to set CLAMPMSS=yes in /etc/shorewall/shorewall.conf.

Already made.

Quote:
If you have an ADSL Modem and you use PPTP to communicate with a server in that modem, you must make the changes recommended here in addition to those detailed below. ADSL with PPTP is most commonly found in Europe, notably in Austria.

Not my case - I have no ADSL modem with installed PPTP server. I use PPTP client directly on my server.

---

### Post by huygens on 2007-04-03
> **mopok said:**
> [...] I think, the problem is in routing back traffic from my local server to client machine trough firewall. [...] Where to look at this routing rules?

Perhaps, you could try the link I have gave you in my last post about Shorewall logging facility. You could then find out if this is the part that goes wrong.

However, for your information, I have a HTTP server behind a firewall (my adsl router), and I just activated the DNAT for port 80 for the HTTP and it is working.
You could have trouble with the back traffic when the server is spawning a new process to handle the connection further (case of FTP). However, I'm unaware that HTTP or POP does such things. When you connect to a POP server, all traffic goes to port 110 and back from that one too. Same for HTTP with port 80.

If you could try again at least the telnet for SMTP and POP. For SMTP you could try the following scenario after successful telnet connection:
```
EHLO your-hostname
QUIT
```
Then after testing both SMTP and POP via telnet, you could check the log from Shorewall and the log in /var/log/messages to see any difference why one is accepted and not the other.

---

### Post by mopok on 2007-04-03
I'll try...

---

