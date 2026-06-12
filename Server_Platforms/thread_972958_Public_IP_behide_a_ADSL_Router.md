---
title: "Public IP behide a ADSL Router"
date: 2008-11-06
forum: Server Platforms
---

### Post by spamhub on 2008-11-06
Dear all, I m new to ubuntu and linux. Please help solving my problems. Please see my case as below:

1. I've just joint an ISP for broadband Internet which come with a static IP address. Then I ALSO ORDER 8 STATIC ip addresses from the same ISP.

2. How can I configure Ubuntu 8.10 to connect to the internet with the one of the additional PUBLIC static IP address?

3. I've tried hours with no luck.

Please help!!! Many thanks in advance!

---

### Post by mbeach on 2008-11-06
If you have an extra machine around, I believe pfsense can handle this for you, although I haven't tried it.  From the features page at [http://www.pfsense.org/index.php?option=com_content&task=view&id=40&Itemid=43](http://www.pfsense.org/index.php?option=com_content&task=view&id=40&Itemid=43)
"Port forwards including ranges and the use of multiple public IPs"

---

### Post by koenn on 2008-11-06
I'd say all you need is a router (one that doesn't do NAT ), and plug in the PC. For up to 8 pc's, you'll need a hub or a switch if the router doesn't have 8 LAN ports built in.

What are you going to do with 8 IP addresses ? 

You have to be aware that all 8 public IP addresses are accessible from the internet so you might want to consider using a firewall if you're planning on enabling services such as samba, nfs, remote desktops, etc.

---

### Post by cariboo on 2008-11-06
There is probably a better way to do what you want, but have a connected the modem to a switch and just set up each computer with the static ip address that I was assigned.

Jim

---

### Post by spamhub on 2008-11-06
Thanks for your replies.

Actually, I want to setup web server, mail server and ftp server in my office and so I buy 8 ips from the isp.

Among those 8 ip addresses, I know the first one and the last one are to be used as network address and broadcast address and so I have only 6 ip address left for other use.

I am currently using Netgear D834G which is a normal wireless router with ADSL modem built-in.

Any suggestion is appreciated.

---

### Post by blazerw on 2008-11-06
To configure for a static IP address, use the GUI.
You should have the connected network icon up near the clock. Right-click on that and choose "Edit Connections"
Then in the "Wired" tab, select "Auto eth0" (assuming that it's named the same as mine).
Then click "Edit".
Click the "IPv4 Settings".
Change the Method to "Manual" and fill in the rest. NOTE, the "fill in the rest" part will take some research by you. You need to know what your Netgear is doing. It's possible that it is making your external IP addresses available to any box you connect to it. If that is the case, you should be good to go by setting the IP address to one of your static's and setting up the gateway and DNS servers to those provided by your ISP.

If the above does not work, then your Netgear is NATting your connection. You don't need 8 static IP addresses in this case. You should change "Auto eth0" to "Automatic", then configure your Netgear to always give your server the same IP (you don't care what the IP is and you definitely DON'T want it to be the same as the static's you got). Next, you need to forward ports via your Netgear to the server. The ports you'd want are 80, 25, (whatever POP is). Unfortunately, I can't help you on the Netgear, but I bet its manual could.

I hope this gives you some help.

---

### Post by koenn on 2008-11-07
According to the D834G reference manual, you can turn of NAT, which would allow you to use the addresses you bought.
You'll have to configure your servers with static IP addresses, eg the way blazerw explained, or check whether you can set dhcp reservations in the netgear's dhcp server.

Still according to the manual, the D834G will set up a route between your network and your ISP, but you can also set static routes if need be.

---

### Post by spamhub on 2008-11-07
> **koenn said:**
> According to the D834G reference manual, you can turn of NAT, which would allow you to use the addresses you bought.
You'll have to configure your servers with static IP addresses, eg the way blazerw explained, or check whether you can set dhcp reservations in the netgear's dhcp server.

Still according to the manual, the D834G will set up a route between your network and your ISP, but you can also set static routes if need be.

Thanks for your reply.

I have disabled the NAT from the router, and used one ip address to be the router's lan address. Now the static ips are able to access the outside world. HOWEVER, I can not ping those static ips from the outside world.

That means, those PUBLIC ip address were been treated as private ips in the private network?

So much confised.


@ blazerw - Thanks for your advise, but I installed the server version of ubuntu and so no GUI is installed on my boxes.

---

### Post by koenn on 2008-11-07
> **spamhub said:**
> 
I have disabled the NAT from the router, and used one ip address to be the router's lan address. Now the static ips are able to access the outside world. 

so far so good, this means you've set it all up correctly, network-wise.

> **spamhub said:**
> 
HOWEVER, I can not ping those static ips from the outside world.

That means, those PUBLIC ip address were been treated as private ips in the private network?

your netgear router has a builtin firewall. It's possible that it's blocking incoming connections by default, which would be a sane and secure default.

You could try "traceroute your_server_ip_address" (on Windows : tracert) from outside, and see where the trace stops ; probably at your routers external IP address

Read the manual's chapter on firewall, and see if you find a setting that blocks incoming by default and a setting that allows you to say something like
(for web server: ) allow incoming with destination = ('any address' or) address_of_webserver port 80/tcp
likewise for other services you want open to the internet.




> **spamhub said:**
> 
So much confised.
This is very basic networking, you should familiarize yourself with these things if you're planning to run public servers. 

The part that can be slightly confusing is that home networks (and adsl routers sold for home use) often default to NAT, and most help on a forum like this will implicitly presume you're using a NAT router. But in fact, NAT is an exception and a workaround to connect multiple private address to the internet through 1 public address. 
What you"re doing here is 'the real thing'.

---

### Post by spamhub on 2008-11-07
YES the tracert stopped at the external ip of the router and I believe that it will be the case of firewall blocking incoming traffic. I should realize that at the beginning.

YES again I know I should make my mind more smart before opening the network to the public.. haha... was familiar with TCP/IP and router things but it was more than 15 years ago. And yes the new home-purposed router confused me as they are totally different from what I "touching" back 15 yrs ago.

Since I m home now and so will try configure the firewall setting on the router tomorrow.

Anyway, THANK SO MUCH to YOU and ALL OTHERS who had tried to help. I m really appreciated!

---

### Post by spamhub on 2008-11-08
Hi all,

Just a quick update here...

After changing the firewall rules by adding the needed ports to the allowed incoming list, all works great!

Thanks again for those who have tried to help. Special help to Koenn for the straight hints on the firewall thing.

---

### Post by glen_2180 on 2008-12-18
nice pet. more pics of this pet plz!!! thanks

---

### Post by Ferret-Simpson on 2008-12-20
In order to have desktop machines as well, I would advise purchasing a second router which plugs into a LAN port on your switch. (Apple Airports, USR5461, most routers you plug into a cable modem should be fine) Give THAT router a static IP too, and let it NAT to firewalled internal IP's like a normal home network. That's how my Rack is set up. :)

---

