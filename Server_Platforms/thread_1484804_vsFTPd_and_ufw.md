---
title: "vsFTPd and ufw"
date: 2010-05-16
forum: Server Platforms
---

### Post by tim_wright on 2010-05-16
_*Summary*_: vsFTPd will not allow FTP (Explicit SSL) logins after login. The ufw must be restarted and then connections are allowed. The server is Ubuntu 10.04 LTS x86 and is being accessed over LAN.

*_Details_*: When the server is turned on I connect using my windows machine (filezilla client). This is all set up correctly as it works after ufw is restarted on the server. There are two different things which happen...

1. First time you attempt to login

Status:	        TLS/SSL connection established.
Response:	331 Please specify the password.
Command:	PASS **********

2. Second and subsequent times you try and login

Status:	Connecting to 192.168.1.237:21...
Status:	Connection established, waiting for welcome message...

_*Configurations / Errors*_:

[B]1. ufw
[/B]
Status: active

To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere
21/tcp                     ALLOW       Anywhere
20                         ALLOW       Anywhere
2020:2030/tcp              ALLOW       Anywhere

**2. Netstat -a | grep ftp**

tcp        0      0 *:ftp                   *:*                     LISTEN     
tcp        1      0 192.168.1.237:ftp       192.168.1.4:1648        CLOSE_WAIT 
tcp        0      0 192.168.1.237:ftp       192.168.1.4:1657        ESTABLISHED
tcp        1      0 192.168.1.237:ftp       192.168.1.4:1637        CLOSE_WAIT 
tcp        1      0 192.168.1.237:ftp       192.168.1.4:1651        CLOSE_WAIT 
tcp        1      0 192.168.1.237:ftp       192.168.1.4:1532        CLOSE_WAIT 
tcp        1      0 192.168.1.237:ftp       192.168.1.4:1536        CLOSE_WAIT 
tcp        1      0 192.168.1.237:ftp       192.168.1.4:1652        CLOSE_WAIT 
tcp        1      0 192.168.1.237:ftp       192.168.1.4:1535        CLOSE_WAIT 

**3. vsftpd (relevant bits**)

ftp_data_port=20
pasv_min_port=2020
pasv_max_port=2030

_*Comments*_: It seems that ufw is holding on to the closed connections? When it is restarted these close_wait connections disappear and ftp works like a charm. This is a clean install, with nothing other than the default settings and vsftpd!

---

### Post by mituw16 on 2010-05-16
Why not just write a quick and simple ip tables script to allow port 21 and the passive ports then block everything else, or you could create a rule to allow all traffic from your LAN subnet and drop everything other than FTP for people outside your LAN

---

### Post by tim_wright on 2010-05-16
I'm no expert on IPtables and for what I need to do, ufw is the best and simplest option. With respect, the main question is why ufw is holding onto close_wait connections and how it can be fixed. Any ideas?

---

### Post by tim_wright on 2010-05-16
I've found some more information about the underlying issues. The first connection allowed the password to be sent but it couldn't get a response. Then subsequent connections stopped at the welcome message. I found this piece of information on derkeiler.com:

> First, the entries with CLOSE_WAIT are all different connections. A TCP/IP connection is determined by four numbers: server IP address, server port, client IP address and client port. These entries have different client port numbers. What happened was that the 192.168.3.78 client made several connections and broke them. A broken connection persists for 2*MSL (Maximum Segment Lifetime), typically 4 minutes, to wait for possibly delayed segments. Please check the description of the TCP/IP state diagram and protocol for details.

While this helps to explain why the logon process gets stuck at the welcome message on the 2nd try, but it does not explain why the whole thing goes heads up when the server starts. 

Can anyone help? Thanks

---

### Post by mituw16 on 2010-05-16
If yup said it works after restart ufw right? A quick and dirty hack would be to just add the command to restart ufw at the end of the /etc/init.d/rc.local     file. That's how I execute my rather long iptables script when my server starts

---

### Post by tim_wright on 2010-05-16
The issues seem to go a bit beyond that now. I enabled anonymous logins and that works perfectly, without and without the firewall enabled.

Similarly, a test user (U:test P:test) running with and without SSL works fine, without or without the firewall.

I've been able to narrow it down to the fact that I can't login with my main account using SSL or not. This occurs both when I am, and when I am not logged in on the server. 

Is there any information about logging in under the main account that I should be aware of? The main account is the one which was setup when the server was installed.

---

### Post by tim_wright on 2010-05-16
Some more information:

If I login with my default account the original output occurs. However, this prevents anyone else from logging in for a period of time. 

If I login with my U:test P:test account straight away, there are no issues, and others can login after... however, if I login after with my default account the server locks up as per usual.

---

