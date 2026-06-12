---
title: "Putting server online"
date: 2008-04-04
forum: Server Platforms
---

### Post by subzero06 on 2008-04-04
Hello,

i have my home server...everything is installed webmin, apache, php phpmyadmin, mysql, ftp. Apache is working fine. The website only works on my localnetwork, but other people on the net cannot see my website...it never connects. i opened port 80 on my router for my server. but nothing. 
in the webmin control panel i found that the DCHP server is not running and when i try to start it it doesn't work. but the website  still works on the local network. i even bought a domain, when i type the domain it loads my website only for me, but not for other people.
my isp is cablevision - optimun online
i am running ubuntu server edition.
for the dns servers i am using dns server from zoneedit.com

---

### Post by PointyWombat on 2008-04-04
Can other machines on the LAN access your server, or can it only be accessed it locally?

---

### Post by subzero06 on 2008-04-04
> **PointyWombat said:**
> Can other machines on the LAN access your server, or can it only be accessed it locally?

every computer on my LAN can access it...but not people from other WAN address

---

### Post by tamoneya on 2008-04-04
It sounds to me like the problem is in your router.  You should be making a passthrough on your router not just opening the port.  This requires finding the local IP of your server and telling the router to send all data on port 80 to the server at port 80.  Also dont worry about the DHCP on your server.  Allow the router to do this.

---

### Post by subzero06 on 2008-04-04
> **tamoneya said:**
> It sounds to me like the problem is in your router.  You should be making a passthrough on your router not just opening the port.  This requires finding the local IP of your server and telling the router to send all data on port 80 to the server at port 80.  Also dont worry about the DHCP on your server.  Allow the router to do this.

Yes i have done that...

Port Range
Application----- 	Start-- 	End --	Protocol ---	IP Address 	--Enable
server    ------  -----       80  --    80     - ---   both      --      192.168.1.6     ----- yes


the local ip of my server is 192.168.1.6

---

### Post by tamoneya on 2008-04-04
I believe that is just opening the ports.  There should be another section in your router where it makes a pass through.  If you dont setup the pass through the router doesnt know which computer to send it to.  Currently you are just saying that it is okay for port 80 to be used on that computer.

---

### Post by subzero06 on 2008-04-04
If anyone would like to help i can give you access to my pc remotely to control the server and router.

---

### Post by tamoneya on 2008-04-04
give me access to the router and i will check the pass throughs for you

---

### Post by subzero06 on 2008-04-04
> **tamoneya said:**
> give me access to the router and i will check the pass throughs for you

do u have aim or msn?

---

### Post by tamoneya on 2008-04-04
aim: add an "a" to my user name at the end

---

### Post by PointyWombat on 2008-04-04
I would suggest you just let us know the model of your router instead of letting an unknown person external access to it. Too risky.

---

### Post by .nedberg on 2008-04-04
> **PointyWombat said:**
> I would suggest you just let us know the model of your router instead of letting an unknown person external access to it. Too risky.

+1

What adress are your friends connectiong to? Do they use your external ip?

---

### Post by subzero06 on 2008-04-04
I got it solved
we had a conversation with the user tamoneya, bcus he could connect to my router either...
so we got a conclusion,
the problem is my ISP dont allow webservers. i have to pay them more for it.

> 
Optimum Online:

Users may not run any type of server on the system. This includes but is not limited to FTP, IRC, SMTP, POP, HTTP, SOCKS, SQUID, DNS or any multi-user forums; Users may not register or point a domain, sub-domain, or hostname to any Optimum Online IP address. Moreover, Users may not have traffic redirected to The Service; Users may not resell, share, or otherwise distribute the Service or any portion thereof to any third party without the written consent of Cablevision. For example, Subscriber may not provide Internet access to others through a dial up connection, wireless access or host shell accounts over the Internet, provide e-mail or news service, or send a news feed. Users may not copy, distribute or sublicense any software provided by Cablevision, except that Subscriber may make one copy of each software program for back up or archival purposes only;

Optimum Online Boost:

Users may not run any servers except for a webserver (HTTP) and mail (SMTP) on the system. This includes but is not limited to FTP, IRC, POP, SOCKS, SQUID, DNS or any multi-user forums. Users who opt to run a webserver must do so on port 80 only. Webservers running on any other port will be deemed a violation of these terms. Similarly, users who opt to run a mailserver (SMTP) must do so on port 25 only. Mailservers running on any other port will be deemed a violation of these terms. Users opting to run web or mail servers are expected to secure those services and maintain the security of those services on an ongoing basis. Mailservers are to be configured against open relay and third party exploitation. Users may not resell, share, or otherwise distribute the Service or any portion thereof to any third party without the written consent of Cablevision. For example, Subscriber may not provide Internet access to others through a dial up connection, wireless access or host shell accounts over the Internet, provide e-mail or news service, or send a news feed. Users may not copy, distribute or sublicense any software provided by Cablevision, except that Subscriber may make one copy of each software program for back up or archival purposes only."



i have to buy optimun boost.

---

### Post by subzero06 on 2008-04-04
wait a second...i already have optimun boost on my billing statement...:lolflag:

wtf is wrong then

---

### Post by 3rdalbum on 2008-04-04
Sorry if this is a dumb question. But what IP address are you trying to access?

Go to [www.whatismyip.com](www.whatismyip.com) and make note of what "your" IP address is. The address it gives is the IP address of the router itself, that identifies it to the outside world. This is the address that your visitors need to put into their web browser in order to look at your website.

EDIT: Once you've determined that, give us your router's IP address and we can test out your web site, if you want.

---

### Post by PointyWombat on 2008-04-04
Perhaps open up SSH and test that. It's unlikely they are blocking port 22.  It will at least confirm your setup and understanding.

---

### Post by tamoneya on 2008-04-04
Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-04-04 01:29 EDT
Initiating Parallel DNS resolution of 1 host. at 01:29
Completed Parallel DNS resolution of 1 host. at 01:29, 0.01s elapsed
Initiating Connect Scan at 01:29
Scanning _removed_ (a.b.c.d) [1714 ports]
Completed Connect Scan at 01:30, 5.43s elapsed (1714 total ports)
Initiating Service scan at 01:30
SCRIPT ENGINE: Initiating script scanning.
SCRIPT ENGINE: rpcinfo.nse is not a file.
SCRIPT ENGINE: Aborting script scan.
Host _removed_ (a.b.c.d) appears to be up ... good.
All 1714 scanned ports on _removed_
 (a.b.c.d) are filtered ( 1688 ) or closed (26)

---

### Post by PointyWombat on 2008-04-04
You can also open up a couple ports and go to [ShieldsUp]("https://www.grc.com/x/ne.dll?bh0bkyd2") to se if those ports are visible on the outside.

---

### Post by tamoneya on 2008-04-04
Everything is being filtered by the ISP.  Nothing on the modem side will allow ports to be opened.

---

### Post by subzero06 on 2008-04-04
from shields up:



GRC Port Authority Report created on UTC: 2008-04-04 at 16:12:09

Results from scan of ports: 0-1055

    0 Ports Open
    0 Ports Closed
 1056 Ports Stealth
---------------------
 1056 Ports Tested

ALL PORTS tested were found to be: STEALTH.



-------------------------------


TruStealth: FAILED - ALL tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - A PING REPLY (ICMP Echo) WAS RECEIVED.
/////////////////////////////////////////////////////////

EDIT: OK I GOT IT SOLVED:
I CALLED OPTIMUM AND THEY OPENED PORTS 80 AND 25 BECAUSE THAT SHOULD BE INCLUDED IN MY OPTIMUM BOOST PACKAGE......SO EVRYTHING IS SET NOW!!!

---

### Post by cuz on 2008-05-08
There is probably a better place to post this, but since this thread led to my solution, hopefully it will help others.

I have not been trying to run a server on Optimum Online, but I have been trying to set up ssh, which sounds like it is within the non-Boost terms of use. After many hours of futzing about, this thread led me to the Shields Up site. In place of the public IP address using whatismyip.com or the listing on my router, I tried the reverse DNS listing Shields Up provided. Works beautifully.

---

