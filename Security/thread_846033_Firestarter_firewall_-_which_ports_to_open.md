---
title: "Firestarter firewall - which ports to open?"
date: 2008-07-01
forum: Security
---

### Post by primky on 2008-07-01
I downloaded Firestarter some time ago, and it's really a handy application. 
For outbound connections i set to option "Restrictive, whitelist traffic" which means i have to specify which ports can be opened.

I opened port 80 for HTTP, port 443 for HTTPS and port 1863 for Emsene. Which other ports should be opened to  ?

What about inbound ports?

---

### Post by kevdog on 2008-07-01
If you dont have any servers running then it really doesnt matter.  If there are no listening processes (ssh, samba etc), it doesnt really matter if the firewall is open or closed for incoming connections.

---

### Post by hyper_ch on 2008-07-01
by default, no firewall is needed ;)

---

### Post by primky on 2008-07-01
> **kevdog said:**
> If there are no listening processes (ssh, samba etc), it doesnt really matter if the firewall is open or closed for incoming connections.

Thanks.

I just tried nmap-online.com few minutes ago, and it said that "host is offline", although i'm connected on internet.
 I know that it's because I use mobile phone to connect to internet with pc, and my ISP uses NAT, so inside this network i have internal IP, and outside i have external IP, which is IP of server of my ISP, which is also working as router.
Does that mean I am more secure, because no one can actually come to my PC?

---

### Post by kevdog on 2008-07-01
NAT is definitely a security measure, since incoming connections must first get through the NAT prior to coming to your pc.  I'd be curious however if you could run a server behind your NAT gateway.  Have you tried this -- for example setting up an ssh server or apache web server and attempting to connect to it from a computer outside the local LAN?  If you don't need to do this, then don't bother, however in my experience Ive found that many people in fact do want to run servers -- for example an ftp or ssh server for access to their home computer from work or vice versa.

---

### Post by primky on 2008-07-01
> **kevdog said:**
> Have you tried this -- for example setting up an ssh server or apache web server and attempting to connect to it from a computer outside the local LAN?

Actually that is the thing I would love to sort out :D
My friend has server and i tried to backconnect from it, but it didn't work. 
What should i do in this case? 

I'm trying to figure this out for weeks now, but i gave it up with no success :(

---

### Post by kevdog on 2008-07-01
First of all -- dont worry about a firewall right now.  Turn off the firewall, flush the iptables, etc.

Install on your local computer the ssh server

sudo aptitude install openssh-server

Go with the defaults.

You can create keys later if you want since with the default ssh is set for password authentication.  Also be default it runs on port 22.

List your local IP address:
ifconfig

Find your external ip address (Cut and paste this into terminal)
wget -q -O - [http://showmyip.com](http://showmyip.com) - | grep -m 1 'IP' | awk '{ print $8 }'

Somehow at the NAT level you need to translate incoming requests on port 22 with external IP address to be forwarded to your local IP address on port 22.  

See if you can simply do a port scan from your friend's computer to your local computer
nmap -p22 <external ip address as you determined above>

---

### Post by primky on 2008-07-01
Ok, I did everything as you said, also started ssh-server with
> sudo /etc/init.d/ssh start

My friend is not online right now, so i just used [www.nmap-online.com](www.nmap-online.com) with **-p22 <my-external-IP>**
It still says "**Host seems down.**".

Is it because i used online nmap? I doubt...
[B]
*/EDIT:[/B]
Also my friend tried, and got same results.

---

### Post by kevdog on 2008-07-01
Can you tell me the exact line you typed when using nmap?

Please post the exact line 

Thanks.


Please also post the following from the ssh server:

sudo netstat -lnptu

---

### Post by primky on 2008-07-01
> **kevdog said:**
> Can you tell me the exact line you typed when using nmap?

When i did online scan i typed
**-p22 213.229.209.97**
Because there is no need to type "nmap" before.

When my friend tried with netstat on windows, he typed
**nmap -p22 213.229.209.97**

> 
Please also post the following from the ssh server:
sudo netstat -lnptu

Here it is (typed command you gave me in terminal):

```

primky@c0dehunter-0x:~$ **sudo /etc/init.d/ssh start**
[sudo] password for primky: 
 * Starting OpenBSD Secure Shell server sshd                             [ OK ] 
primky@c0dehunter-0x:~$ **sudo netstat -lnptu**
Active Internet connections (only servers)
**Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name**
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      5181/exim4      
tcp6       0      0 :::22                   :::*                    LISTEN      22175/sshd      
udp        0      0 0.0.0.0:51363           0.0.0.0:*                           4811/avahi-daemon: 
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           4811/avahi-daemon: 

```

---

### Post by kevdog on 2008-07-01
It seems you are connecting through a router or gateway with a very restrictive firewall in place.  Its blocking ping requests, but I was able to get a response from your server:

$ nmap -PN -p22 213.229.209.97

Starting Nmap 4.60 ( [http://insecure.org](http://insecure.org) ) at 2008-07-01 10:45 Central Daylight
Time
Interesting ports on internet-209-97.narocnik.mobitel.si (213.229.209.97):
PORT   STATE    SERVICE
22/tcp filtered ssh

Nmap done: 1 IP address (1 host up) scanned in 2.611 seconds


Port 22 is filtered, and hence not forwarded to your own computer.  You would have to adjust the iptables on this router computer to open a port and forward it to your local port.  Can you do this?

---

### Post by primky on 2008-07-01
> **kevdog said:**
> Port 22 is filtered, and hence not forwarded to your own computer.  You would have to adjust the iptables on this router computer to open a port and forward it to your local port.  Can you do this?

I think that server is at my ISP's headquarters, so I don't think i can manipulate with iptables there :D

I guess there is nothing more to do.. Except if I call my ISP and tell them to do that, but i doubt they will :confused:

Or maybe there is any other way? 
If this doesn't work, maybe if I buy VPN, would that work?

---

### Post by kevdog on 2008-07-01
I have no idea what ISP you use, but you can't be the only one wanting to run a server.  This really seems in my opinion a very restrictive policy.  If all else fails, its possible to run an ssh server with reverse tunneling.  That would be one way around the issue :)

---

