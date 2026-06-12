---
title: "LAN ok, WAN no connection"
date: 2008-07-04
forum: Server Platforms
---

### Post by CyberDean on 2008-07-04
My server is now setup, with the assistance of the Linux community, so I can contact it with my LAN PC's, but when I go to a PC on the WAN, outside my LAN, no connection with either the IP address or domain name.  I am using Putty to test with.  Have verified that ddclient is running and DynDNS.org has my correct IP address, and of course they have my domain name.  DNS is turned off on my router.  Port forwarding is setup on my router pointing to my server.

I am still learning so don't feel bad about asking questions or what is in config files that may be simple to you.

Any ideas out there?

---

### Post by cariboo on 2008-07-04
This might be a dumb question, but do you have ddns turn on in your router?

Jim

---

### Post by CyberDean on 2008-07-04
> **cariboo907 said:**
> This might be a dumb question, but do you have ddns turn on in your router?

Jim

DNS is still turned off in my router as stated before.

I just did a "Traceroute" in "Network Tools", to my WAN IP address, the first IP returned is the PC running the traceroute, the next three entries are my router's IP address.  Never getting to the server.

Why would the router be stopping the request?

I did a "Ping" to my server using "Network Tools", and it appears to complete fine.

Any ideas?

I also put my server's internet IP address in Firefox address, and received a login screen, but my user name and password would not login to my server.  I also tried my router's login and both PC's, but would not login, it's getting a login from somewhere.

---

### Post by windependence on 2008-07-04
Something is not right here. You should be getting the Apache page not a login page. Make sure remote admin is turned OFF in your router. I have a feeling theis is the login page you are getting. Can you post a screen shot of the login page?

-Tim

---

### Post by cariboo on 2008-07-04
Just to clarify ddns=dynamic dns. I have a linksys wrt34g router, It has all sorts of good features like ddns and a dmz. I have no intention of using these features, but for the price, under $50.00, it can't be beat.

Jim

---

### Post by CyberDean on 2008-07-04
> **windependence said:**
> Something is not right here. You should be getting the Apache page not a login page. Make sure remote admin is turned OFF in your router. I have a feeling theis is the login page you are getting. Can you post a screen shot of the login page?

-Tim

Hi Tim, here is the screen shot, I just found out where it is coming from, my router.  But I tried the router username and password without success.  I also attached a screen shot of the router with this login screen.

I just tried to log in again with no luck.  For some reason, and I have no idea why, the router is stopping the request and not sending it to the server.  With the request looking for my server the router login name and password will not work, and it's not getting to the server to see the server's login.  I also re-verified the port forwarding in the router and all forwarding is to the static IP address from the router and assigned to my server. 

I see no option for remote login in the router.  I'll bet that is a remote login for my ISP and it does not show on any options I can see.

Any clues???????

---

### Post by CyberDean on 2008-07-04
> **cariboo907 said:**
> Just to clarify ddns=dynamic dns. I have a linksys wrt34g router, It has all sorts of good features like ddns and a dmz. I have no intention of using these features, but for the price, under $50.00, it can't be beat.

Jim

Hi Jim, I'm using my DSL modem as a router, Siemans Speedstream 6520, it has DNS built in, but it is disabled.  I setup static IP's for each of my computers using "Network" from Linux.  Windependence is one who helped me get the router configured to allow me to do port forwarding.

I am using DynDNS.org with my domain name and ddclient for my DNS.

Thanks for checking that I understood.

---

### Post by windependence on 2008-07-05
The problem is your router is already using port 80 for remote administration. You need to turn that off. Your ddns is working fine because you are being forwarded to your machine using the domain name. What is happening is that Apache and your router are listening on the same port. Your router has a mini web server built into the ROM and is superceeding your web server. The only way to fix this is to turn off the web server in your router (remote admin).

-Tim

---

### Post by CyberDean on 2008-07-05
I looked in the router and can not find anything that remotely might turn off remote admin for the router.  Again, I am not sure what I am looking for, but it still might be here, what should I be looking for?

I will go home for lunch from work and ensure the server is up and running, and then I will run some test from the WWW side of the router at work using Putty, psftp, FireFox, domain name, IP address and port numbers that have been forward to my server.  Maybe that will give us a better overall picture.  Maybe my ISP lied to me about blocking incoming traffic.

One point I wish to make sure I understand.  When I run FireFox and request a web site from WWW, it opens port 80 from internally and the web site slides on through.  But when a request comes from the outside world, WWW, the port is not open and the router sees that as a "remote admin" request or an intrusion attempt.  Is this basically correct?

Thanks, have a great day.

---

### Post by CyberDean on 2008-07-06
I am finally back.  Besides my router capturing the port 80 request I have discovered that ddclient is not auto updating my WAN IP address when it changes, and everything works like it use to, not right but is seen as my domain IP address.

When DynDNS has my correct IP address, Putty port 22, and psftp port 21, will not connect with my server attempting to use the IP address or domain name.

I have a call into to friend of mine who works for my ISP, I'm going to check on them blocking ports a server would use.

So right now, I need to check why ddclient is not auto updating DynDNS.  Any hints?  If I do the following command, it appears to try to update.

~$ ddclient -daemon=0 -verbose

ddclient runs, checks, sees the IP at DysDNS is the same IP address found and closes.

Any help?

---

### Post by CyberDean on 2008-07-07
I believe I have the ddclient problem solved, copied my ddclient from /etc/ddclient/ddclient.conf to /etc/ddclient.conf, and unplugged the power to the router overnight.  Checked the IP going to my router this morning on a PC, turned the server on and as soon as the server completed bootup, the IP changed at DynsDNS.org.  I  give credit to my find to the community and would list the thread address, but I can not find it at this time. When I find it I will include it.

Called my ISP again, they still claim not blocking any ports other than 25, 135,137, 138, 139, 445 and 1025.  I went through the routine of what I'm doing again, they said to try NAT and/or DMZ configuration on the router so my server can be reached from the internet.  Anyone familiar with setting NAT and DMZ up? And what and how they do what they do.

Thanks, have a great day.

---

### Post by CyberDean on 2008-07-08
I have been googling and searching Wiki for "NAT", "NAPT" and "DMZ".  I now basically understand all three.  I am currently using NAPT to attempt port forwarding to my server from the router, and I have the firewall turned off in the router so DMZ would have no effect.

I have also changed my router's LAN IP addresses from 192.168.254.254 to 10.0.0.254 to see if that would make a difference. It does not.  By the way, in port forwarding when you input the Ip address to send the request, on the Siemen's Speedstream 6520, it will not accept a port number like ":80" after the IP address.

I have come to the conclusion that my router's port forwarding capability does not work for some unknown reason, or my ISP is still not telling the truth.

The only request from the internet, be it from "Putty", "FTP" or "HTTP" is "HTTP" to port "80", and it opens a login screen which I have been told is used for remote login to the router.

Internally in my LAN, I can contact my server from either PC by addressing the IP address, the server name or the domain name.

Anyone have any other suggestions to try, or see where I am doing something wrong?

Thanks in advance, have a great day.

**UPDATE: Tuesday 12:56 EST USA**

I have just been on the phone with my ISP for the last hour and a-half, and finally got to a person who, off the record, admitted that the phone company made a decision to block ports on residential service to protect the user against spam, intrusion, etc, etc, etc.  The only way to get around this is to get business service, with or without a static IP, but the overall service is configured differently than residential service.  Yes, the cost goes up, I am paying $44.00 per month now, and could get the business with static IP for $79.00 per month, or go for the more inexpensive business service (dynamic IP and 2 year contract) for $59.00 per month.  But, I have 90 days to cancel if the service is found not to work and/or the problem is found to be in the server.  They use the same Seimens DSL 6520 modem gateway or they could change the DSL modem.

Any opinions?  I'm out of ideas at this point.

Thanks, have a great day.

---

### Post by windependence on 2008-07-08
I'm sorry Dean, but you still are very confused with all this stuff. Your router DOES have port forwarding and there IS a way to do a custom setup. I saw it in the pics you posted. Now, I'm afraid you might be so mucked up we may have even more difficulty. I am not in any way trying to be rude here, just a bit frustrated I guess. One thing I learned quickly when I got in this business. Do ONE thing at a time, test it, and if it doesn't work, put it back the way it was. That way, you never mess anything up. 

OK that being said, let's keep trying to fix your problem. First of all, your EXTERNAL interface on your router should be set to DHCP if that is how your ISP wants it. You probably don't want to mess with however it is set up now if you have internet access and it's working.

On your INTERNAL LAN, set your IP subnet to whatever you are going to use. You can use 192.168.x.x or 10.x.x.x or 172.16.x.x or technically you could even use routable addresses but I wouldn't. OK so give your router an address, say 192.168.2.1. that is your GATEWAY address. All of the LAN PCs and servers must have an IP of 192.168.2.x to talk to the gateway. So next you will give your internal machines static IPs in that range.

Once that is all set up and you have internet going out, then you need to go in to your router's port forwarding config, it will not usually say it's port forwarding, and it may have some common ports already configured like port 80 for http. Don't worry about that, you are looking for a custom configuration where you can add your own application and port. This is where you are getting stuck. Is there anyone at your ISP that can walk you through port forwarding? When you make the entry, there should be a place for the IP of the LAN computer you want to forward to. There, use JUST the IP, no port no :80, just 192.168.2.2 or whatever. There will be another box or place for the port. In there you put 80 (or the port you want), not :80 or anything else, just plain 80. Then, save the connection. That's it, you have just forwarded a port. Let me see if I can find some pics on the net to make this clear with your router. I'll be back in a bit. Hang in there.

-Tim

---

### Post by windependence on 2008-07-08
OK,

login to the modem - admin/admin
click on the security icon on the left side.
click on the address translation icon on the right side.
click on configure next to NAPT.
click on "add a custom bypass entry"

Choose TCP as protocol, fill in the port in both the following boxes. Make sure you have a static IP Adress and fill in that in the: Redirect selected protocol/service to IP Address: 
That shouuuuld be it!


You can also try this. It is for a Bell speedstream but it's the same router:

[http://www.portforward.com/english/routers/port_forwarding/Bell/Speedstream6520/Speedstream6520index.htm](http://www.portforward.com/english/routers/port_forwarding/Bell/Speedstream6520/Speedstream6520index.htm)

-Tim

---

### Post by CyberDean on 2008-07-08
> **windependence said:**
> OK,

login to the modem - admin/admin
click on the security icon on the left side.
click on the address translation icon on the right side.
click on configure next to NAPT.
click on "add a custom bypass entry"

Choose TCP as protocol, fill in the port in both the following boxes. Make sure you have a static IP Adress and fill in that in the: Redirect selected protocol/service to IP Address: 
That shouuuuld be it!


You can also try this. It is for a Bell speedstream but it's the same router:


[http://www.portforward.com/english/routers/port_forwarding/Bell/Speedstream6520/Speedstream6520index.htm](http://www.portforward.com/english/routers/port_forwarding/Bell/Speedstream6520/Speedstream6520index.htm)

-Tim


Hi Tim,

Yes, I know I can get all mucked up, but believe it or not I think I'm starting to get it.

The above procedure is what I've been doing.

Currently I have - and they are all enabled
TCP     HTTP/80     10.0.0.4 (static IP)
TCP          22     10.0.0.4 (static IP)
UDP      DNS/53     10.0.0.4 (static IP)
TCP      FTP/21     10.0.0.4 (static IP)
UDP          443    10.0.0.4 (static IP)

I have static IP's on my LAN for all PC's and the server.  I have no problem connecting to the server within my LAN.

Thanks for sticking with me.


**UPDATE Jul 8 2:35 EST USA**

Went to the site and followed the instructions after deleting all entries I made.  I found one area that I had not input all the data.  where you input the port number, there is two (2) boxes, if you are using only one port number, does that port number need to go in both boxes?  Like 22-22. After inputting, applied and rebooting the router, everything seams the same here, need to get to the office to check from outside my LAN.  If you would like to check it, I have enabled SSH port 22, IP address 74.46.254.38.  I tried from within my LAN to see if I could go to the internet first and come back in, but it times out.


**UPDATE: Jul 8 6:25 EST USA**

Went to the office and tried to connect to the server using Putty (SSH) with my domain name and IP address, both timed out, no connection.  Where do I go from here?  I'm totally confused, this should work.  I will post a screen print in the next post.

---

### Post by CyberDean on 2008-07-08
Here is the screen print of the configuration page in Speedstream.:confused:

---

### Post by CyberDean on 2008-07-08
Here is something that has bothered me in the past, but most things are working so it sort of got pushed into the back on my mind, but it still bothers me.

The first screen shot showing PPPoA(0) 0/35 with my IP address to the right.

The second screen shot showing the current routing table to include PPPoA(0) 0/35.

The third screen shot showing the ATM Virtual Circuit Wizard, which also includes PPPoA(0) 0/35, but look at the setting of that circuit.  That is the way it has been since I started looking into the router configuration.  Disabled, that makes no sense to me, but the router allows the server and PC'c to connect to the internet, so I have not said anything about it till now.

---

### Post by rugbert on 2008-07-08
I too cannot get to my server using DYNDNS. I can ssh in but I cant pull any webpages from apache.

(behind my router I have no problem at all resolving, which is weird because shouldnt my request have to go out to the closest server, over to dyndns's database and then back to my router?)

Im thinking that maybe my ISP is blocking port 80 from being served? Im not using that dns client that was mentioned earlier in the thread, but if Im  able to telnet in that shouldnt matter right?

---

### Post by windependence on 2008-07-08
Both of you should make sure apache is running and listening on port 80. Then, go to canyouseeme.org and see if your port 80 is open. If not, there is either a problem with your ISP blocking the port, your port forwarding, or you have a firewall up that you don't know about.

Dean, you can't reach your site using the outside domain name on the inside of your network unless you put an alias in your /etc/hosts file on the computer you are using to access the site. On Windows, this file is in C:\Windows\system32\drivers\etc\.

-Tim

---

### Post by rugbert on 2008-07-09
> **windependence said:**
> Both of you should make sure apache is running and listening on port 80. Then, go to canyouseeme.org and see if your port 80 is open. If not, there is either a problem with your ISP blocking the port, your port forwarding, or you have a firewall up that you don't know about.

Dean, you can't reach your site using the outside domain name on the inside of your network unless you put an alias in your /etc/hosts file on the computer you are using to access the site. On Windows, this file is in C:\Windows\system32\drivers\etc\.

-Tim

that link helped alot, thanks! looks like my ISP was blocking port 80 so screw them! but i got my website up anyway!

---

### Post by windependence on 2008-07-09
Good deal! Let us know how it turns out.

-Tim

---

### Post by CyberDean on 2008-07-09
> **windependence said:**
> Both of you should make sure apache is running and listening on port 80. Then, go to canyouseeme.org and see if your port 80 is open. If not, there is either a problem with your ISP blocking the port, your port forwarding, or you have a firewall up that you don't know about.

Dean, you can't reach your site using the outside domain name on the inside of your network unless you put an alias in your /etc/hosts file on the computer you are using to access the site. On Windows, this file is in C:\Windows\system32\drivers\etc\.

-Tim

I checked the config file for Apache2, IP address is correct, and it is listening on port 80.

How do I get the status of Apache2 and to check if a firewall is running on my server?  Firewall on the router has been disabled, and I have not setup iptables on the server.  Is there a default iptables config file? I have looked but got more confused.

canyouseeme.org does not see port 80 on my server.

In a previous post I included a screen shot of the router port forwarding page.  I can not see anything wrong, can you?

C:\Windows\system32\drivers\etc\hosts has been updated with my domain IP and name for the WAN, currently 74.46.254.38 romneysecuredata.com, and I realize each time the IP address changes I need to update it.

Got to get back to work, later.

Thanks, have a great day, mine can only get better.

---

### Post by windependence on 2008-07-09
To see if Apache is running, run top in a terminal and see if you see any processes running as user www-data. If you do, then your web server is running.

You should stop turning things off and on in the router. your firewall on the router should be ON. If your port 80 is forwarded back to your server, this won't affect it at all, but you don't want to run wide open to the internet like that. 

To open up IPtables, let's do these commands:

```
sudo iptables -X
sudo iptables -t nat -F
sudo iptables -t nat -X
sudo iptables -t mangle -F
sudo iptables -t mangle -X
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
```

Then, restart your network and Apache:

```
sudo /etc/init.d/networking restart
sudo /etc/init.d/apache2 restart 

```

Now, after all that is done, go to the canyouseeme site and see if your port is open.

Your port forwarding looks fine except that 443 protocol should also be TCP, but that won't matter for your web site at this point. DO NOT mess with the ATM stuff. 

Also, show me where you say DNS is turned off in your router. This should not be the case. If you could post a screen shot of where this setting is, I will take a look at it.

-Tim

---

### Post by CyberDean on 2008-07-09
> **windependence said:**
> To see if Apache is running, run top in a terminal and see if you see any processes running as user www-data. If you do, then your web server is running.

**Ran top in a terminal, only root and myself are users.**

You should stop turning things off and on in the router. your firewall on the router should be ON. If your port 80 is forwarded back to your server, this won't affect it at all, but you don't want to run wide open to the internet like that. 

**Turned the firewall back on.**

To open up IPtables, let's do these commands:

```
sudo iptables -X
sudo iptables -t nat -F
sudo iptables -t nat -X
sudo iptables -t mangle -F
sudo iptables -t mangle -X
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
```

**Completed**

Then, restart your network and Apache:

```
sudo /etc/init.d/networking restart
sudo /etc/init.d/apache2 restart 

```

[B]Completed
 * Restarting web server apache2                                                
apache2: Could not reliably determine the server's fully qualified domain name, using 10.0.0.4 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 10.0.0.4 for ServerName

What config file does Apache2 use to qualify the domain name?
[/B]

Now, after all that is done, go to the canyouseeme site and see if your port is open.

[B]Went to canyouseeme.org, did not see port 80 or 443, timed out
[/B]
Your port forwarding looks fine except that 443 protocol should also be TCP, but that won't matter for your web site at this point. DO NOT mess with the ATM stuff. 

[B]Did nothing to port forwarding.  Leaving ATM as is.
[/B]
Also, show me where you say DNS is turned off in your router. This should not be the case. If you could post a screen shot of where this setting is, I will take a look at it.

[B]I had read many post that said to turn off DNS in your router, so I did.  Screenshot is attached.
[/B]
-Tim

Hi Tim, my results is in your post in **BOLD**.


**UPDATE: JUL 9, 9:12pm EST**

Ran a test while I was out working, turned the power off on my router so I could trigger an update on my IP address from my ISP to check ddclient with DNS in the router still off.  Turned the router back on and within ten minutes the IP address updated at DynDNS.org to the new IP address, it's working.

---

