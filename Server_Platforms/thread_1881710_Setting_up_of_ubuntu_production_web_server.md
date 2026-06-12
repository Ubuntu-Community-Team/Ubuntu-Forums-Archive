---
title: "Setting up of ubuntu production web server"
date: 2011-11-16
forum: Server Platforms
---

### Post by JohanLombard on 2011-11-16
Hi there all ubuntu people.

I'm fairly new to the Debian/Ubuntu package.  Its seems to be much easier to find my way around it than 10 years ago.  I'm looking into setting up a production server to host multiple websites.  I've set up LAMP with Webmin and have been testing with EHCP.  

The trouble I have is to access my server from the outside.  My server is behind a router without static IP and I believe that I have trouble somewhere with the communication between the router and the server as well as the dns configuration.

In the past I've been able to set it up on WAMP using an old currently discontinued Apache2triad (windows) setup.

Can anyone walk me trough and shine a light on the subject?  My aim is to rather gain a clear understanding of the concepts.  Any help would greatly be appreciated.

---

### Post by HugoSerrano on 2011-11-16
Hello!

From what I understand, you need to:
- do port forwarding on your router (port 80 from router to 80 local address of your server);
- get a dynamic dns service (dyndns, no-ip, etc).

Best Regards!

---

### Post by JohanLombard on 2011-11-17
Yes Hugo.

I believe that's where my fault is.  I think that I may have been hasty by setting up easy hosting control panel (ehcp) without first setting up the port forwarding correctly.  Then testing the access.

I have set up a dns with [http://freedns.afraid.org](http://freedns.afraid.org)

Gimmy a sec just to retrieve the IP settings in my router and the server.  Then I'll post them here.

Thanks for responding. Hope we can solve the problem.

---

### Post by JohanLombard on 2011-11-17
My router (Edimax AR-7084gA) setup under NAT is like this.

**           [COLOR=#000000]Rule[/COLOR]            ****           [COLOR=#000000]Application[/COLOR]             ****           [COLOR=#000000]Protocol[/COLOR]          ****           [COLOR=#000000]Start Port[/COLOR]            ****           [COLOR=#000000]End Port[/COLOR]            ** **           [COLOR=#000000]Local IP Address[/COLOR]          **                               
1                                      HTTP_Server                                  TCP                   80                                                80                                  192.168.2.100                       
                                2                                      FTP                                                TCP                   21                                                21                                  192.168.2.100                                                       
3                                       SSH                                               TCP                   22                                                22                                  192.168.2.100                                                       
4                                      SMTP                                             TCP                                 25                                                25                                  192.168.2.100                       
                                5                                       POP3                                             TCP                      110                                             110                                 192.168.2.100                                                       
6                                      HTTPS                                           TCP                                443             443                                 192.168.2.100                       
                                7                                       TCP/UDP                                       ALL                                  53                                                53                                  192.168.2.100          

My server address on the LAN has been set to Static:  

Address:                             192.168.2.100
Broadcast:                          192.168.2.255
Subnet Mask of the LAN:      255.255.255.0
Default route:                     192.168.2.1
Primary DNS:                     192.168.2.1

My current IP Address on the internet is [I]

41.132.221.213

[SIZE=2]But this will only be today -  My ISP resets the IP dayly.[/SIZE]
[/I]

---

### Post by HugoSerrano on 2011-11-17
Hello!
I can see that your forwarding it's working, excluding port 80. Probably your router need some more teaks to allow port 80 forwarding. Try to google for that.

Regards!

---

### Post by volkswagner on 2011-11-17
Don't rule out the possibility your isp may block port 80.  I would be a little surprised since the other ports are open. 

You may want to test another port like 8080 and forward it to 80, so you won't need to change any settings on the server.  You would need to specify :8080 in the url.

---

### Post by Lars Noodén on 2011-11-17
You can also check to see if port 80 is blocked by using one of the public scanners like CanYouSeeMe?

[http://canyouseeme.org/](http://canyouseeme.org/)

---

### Post by JohanLombard on 2011-11-18
> **volkswagner said:**
> Don't rule out the possibility your isp may block port 80.  I would be a little surprised since the other ports are open. 

You may want to test another port like 8080 and forward it to 80, so you won't need to change any settings on the server.  You would need to specify :8080 in the url.

Hi Volkswagner.

My ISP was blocking port 80, but I've managed to disable that on my account.  However if I put in **41.132.221.213:80** then I'm presented with the log in for my router.  (A username and password are being requested by [http://41.132.221.213](http://41.132.221.213). The site says: "ADSL Modem")  I have tried surfing it through a anonymous proxy.  But no luck.

I'm still trying to set up port 8080 on the router.

---

### Post by JohanLombard on 2011-11-18
> **Lars Noodén said:**
> You can also check to see if port 80 is blocked by using one of the public scanners like CanYouSeeMe?

[http://canyouseeme.org/](http://canyouseeme.org/)

_Lars thanks for the link.  It actually states:  _[COLOR=red][FONT=Times New Roman]

Error:[/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman] I could [/FONT][/COLOR]**not**[COLOR=#000000][FONT=Times New Roman] see your service on [/FONT][/COLOR]**41.132.221.213**[COLOR=#000000][FONT=Times New Roman] on port ([/FONT][/COLOR]**80**[COLOR=#000000][FONT=Times New Roman])[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Reason:[/FONT][/COLOR] Connection timed out

_Lets check FTP_

[COLOR=green][FONT=Times New Roman]Success:[/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman] I can see your service on [/FONT][/COLOR]**41.132.221.213**[COLOR=#000000][FONT=Times New Roman] on port ([/FONT][/COLOR]**21**[COLOR=#000000][FONT=Times New Roman])[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Your ISP is not blocking port 21

[/FONT][/COLOR]What is interesting to see here is that my ISP is blocking port 80 even though I have unlocked their security features.

Is there a work around.

---

### Post by JohanLombard on 2011-11-21
Ok the server is up and running.  I have two domains to update the DNS record for, but I seem not to be able to edit the ddclient.conf

---

### Post by JohanLombard on 2011-11-23
I'm behind a router where my IP addresses change everytime it boot.  I'm using Ubuntu Precise Pangolin 12.04  (11.10)  as a web hosting server.

The server is up an running under two domains from [http://freedns.afraid.org:](http://freedns.afraid.org:)

[http://potjiekos.chickenkiller.com](http://potjiekos.chickenkiller.com)
[http://volksrust.mooo.com](http://volksrust.mooo.com)

Now it does not seem to update the ip's when the router has been booted.

Does anyone have a suggestion on what dns client I could use that would be best suited for the job.

I have tried setting up the client from the site of [http://freedns.afraid.org/scripts/freedns.clients.php](http://freedns.afraid.org/scripts/freedns.clients.php)

But I seem not to be able to configure it correctly.

[INDENT][FONT=verdana, Helvetica, Arial][SIZE=2][COLOR=black][afraid-dyndns (Multi-platform)]("http://perl.arix.com/")[/COLOR][/SIZE][/FONT][FONT=verdana, Helvetica, Arial][SIZE=2][COLOR=black]Client Requirement: **Perl**[/COLOR][/SIZE][/FONT][FONT=verdana, Helvetica, Arial][SIZE=2][COLOR=black]This  is a client for the afraid.org dynamic DNS service.  If a cron job  detects the external IP address has changed it connects to afraid.org  and updates the DNS entries of all the domains of the given account.[/COLOR][/SIZE][/FONT]
[FONT=verdana, Helvetica, Arial][SIZE=2][COLOR=black] [/COLOR][/SIZE][/FONT]
[FONT=verdana, Helvetica, Arial][SIZE=2][COLOR=black] This client is available in the YUM repo via : yum -y install afraid-dyndns[/COLOR][/SIZE][/FONT]
[FONT=verdana, Helvetica, Arial][SIZE=2][COLOR=black] [/COLOR][/SIZE][/FONT]
[FONT=verdana, Helvetica, Arial][SIZE=2][COLOR=black] It has also been tested on Mac OSX[/COLOR][/SIZE][/FONT]
[FONT=verdana, Helvetica, Arial][SIZE=2][COLOR=black] [/COLOR][/SIZE][/FONT]
[FONT=verdana, Helvetica, Arial][SIZE=2][COLOR=black] Written by: Erick Calder

[/COLOR][/SIZE][/FONT][/INDENT]All input is highly valued.

---

### Post by sandyd on 2011-11-23
> **JohanLombard said:**
> I'm behind a router where my IP addresses change everytime it boot.  I'm using Ubuntu Precise Pangolin 12.04  (11.10)  as a web hosting server.

The server is up an running under two domains from [http://freedns.afraid.org:](http://freedns.afraid.org:)

[http://potjiekos.chickenkiller.com](http://potjiekos.chickenkiller.com)
[http://volksrust.mooo.com](http://volksrust.mooo.com)

Now it does not seem to update the ip's when the router has been booted.

Does anyone have a suggestion on what dns client I could use that would be best suited for the job.

I have tried setting up the client from the site of [http://freedns.afraid.org/scripts/freedns.clients.php](http://freedns.afraid.org/scripts/freedns.clients.php)

But I seem not to be able to configure it correctly.
[INDENT][FONT=verdana, Helvetica, Arial][SIZE=2][COLOR=black][afraid-dyndns (Multi-platform)]("http://perl.arix.com/")[/COLOR][/SIZE][/FONT][FONT=verdana, Helvetica, Arial][SIZE=2][COLOR=black]Client Requirement: **Perl**[/COLOR][/SIZE][/FONT][FONT=verdana, Helvetica, Arial][SIZE=2][COLOR=black]This  is a client for the afraid.org dynamic DNS service.  If a cron job  detects the external IP address has changed it connects to afraid.org  and updates the DNS entries of all the domains of the given account.[/COLOR][/SIZE][/FONT]

[FONT=verdana, Helvetica, Arial][SIZE=2][COLOR=black] This client is available in the YUM repo via : yum -y install afraid-dyndns[/COLOR][/SIZE][/FONT]

[FONT=verdana, Helvetica, Arial][SIZE=2][COLOR=black] It has also been tested on Mac OSX[/COLOR][/SIZE][/FONT]

[FONT=verdana, Helvetica, Arial][SIZE=2][COLOR=black] Written by: Erick Calder

[/COLOR][/SIZE][/FONT][/INDENT]All input is highly valued.
How long did you set ddclient to update?

p.s. some routers have a DDNS updating thingy built in.

---

### Post by JohanLombard on 2011-11-24
Hi there Sorry I respond so late.

I've got no idea of how to set the ddclient's update time.

I'm using Edimax AR7084ga router.

---

### Post by sandyd on 2011-11-24
> **JohanLombard said:**
> Hi there Sorry I respond so late.

I've got no idea of how to set the ddclient's update time.

I'm using Edimax AR7084ga router.
[https://help.ubuntu.com/community/DynamicDNS#ddclient](https://help.ubuntu.com/community/DynamicDNS#ddclient)

Can't help you with the router, I use pure cisco.

---

### Post by JohanLombard on 2011-11-26
Hi there and thanx for the help Sandy

I noticed that my server was updating the dns server.  I just need to know where to config the ddclient.  It may just have taken some time.

I presume: sudo gedit /etc/ddclient.conf

---

### Post by JohanLombard on 2011-12-05
Hi there all.

I have since I've been on the last time been reinstalling the whole Ubuntu Server 11.10.

The thing that I am trying to setup is my automatic DNS updating serves here, since my server is behind a Router (with changing Ip's) I've got bind9 running with ISPconfig to host multiple websites.

However there should be a in bind9 a place where I could let bind9 log (with username and password) into freedns.afraid.org to change the IP addresses automatically when they have changed should there have been a power failure, or my ISP have changed the the Ip's.

Is there someone who could shed some light on the subject Please....  Or is it the same as what Sandy posted in the previous post?

Johan

---

### Post by JohanLombard on 2011-12-12
Hello all Ubuntu People

I have a router with switching Ip's.  I use an external DNS (freedns.afraid.org) service where I have a free domain.  The problem that I have is to set up Bind9 on the Ununtu server to log into my freedns.afraid.org using my username and password and then update the Ip should it have changed.

I have searched trough the web to find answers, but seem not to get my small understanding around the full scope of the protocol of DNS.  

Is there anyone who can point me in the correct direction.  I need to understand this a lot better in order to maintain the server better.

I have the router set up and can manually configure the outside IP, but for the server to update itself is the big problem.

JL

---

