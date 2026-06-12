---
title: "What happens if ISP blocks port 80?"
date: 2006-08-20
forum: Server Platforms
---

### Post by lugos on 2006-08-20
After doing some research on why users outside of my little home network cannot access my website, I found, using [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2), that ports 0 - 1056 are all blocked by my ISP.  Is there a way to get around that?  Would some DMZ configuration work?

Any help would be greatly appreciated.

Thanks,
lugos

---

### Post by dazedandconfused on 2006-08-20
Hiya,

It's more likely that you have a firewall on your side than the ISP is blocking.

Install Nmap using synaptic or apt and then open a terminal and type:

nmap -sT localhost

You should get a list of available services on your machine like this:

Starting nmap 3.81 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2006-08-20 19:58 BST
Interesting ports on poggle.homenet.ldm (127.0.0.1):
(The 1661 ports scanned but not shown below are in state: closed)
PORT    STATE SERVICE
22/tcp  open  ssh
111/tcp open  rpcbind


The list will vary depending on what you run but 80 should be in there if Apache is running.

If you run a router it's likely you have a built in firewall and you should use the port forwarding setting to forward port 80 on the router through to port 80 on your web server's internal IP. I hope you're not running the web server on your desktop machine as that's a hell of a security risk;)
 
Have you installed a firewall on the Ubuntu box, e.g did you install and configure Guarddog, Shorewall or FWBuilder?

Any one of these is more likely that the ISP blocking =. Try the above and let me know what happens,

Cheers,

Jools

---

### Post by lugos on 2006-08-20
Jools,

Thanks for the info.  I installed nmap, and ran that command and it does show that 80/tcp is open and the service is http.  I do have a Netgear router and I have set the port forwarding to forward all http requests to my webserver.  To my knowledge, I have not installed a firewall.  If it was not installed by default, then there should be no firewall.

So, if nmap shows that port 80 is open, I am at a loss as to what I should do next.  Any more tips or directions you can point me in will be very much appreciated.

BTW, I am not running the server on my desktop.  It is Ubuntu Server 6.06 that I have on my machine.  I did install Xubuntu to make set up easier, but probably for no reason since I have been mostly using the terminal.

Thanks,
lugos

---

### Post by scxtt on 2006-08-20
you can use any port you want (w/in reason) ... edit /etc/apache2/ports.conf and change the 80, then restart apache2 ... i randomly picked 6550 and it worked for me ... of course, when going to your site, you'll have to use **http://<ip-address>:6550** to connect ...

---

### Post by lugos on 2006-08-21
I just contacted my ISP and they have assured me that they do not block port 80.

---

### Post by Gouki on 2006-08-21
ISP normally don't block access to X, Y or Z ports. What they do is give you little to no upstream bandwidth so you almost fell obligated to buy some hosting plan.

Now, about your problem.

Normally for HTTP servers, I recommend keeping the default port. [80]

You said you have this computer just for server, so why not put it on the DMZ?

If you are running just an HTTP server, I recommend adding the following rules to your IPTable:

```
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -j DROP
```

This allows incoming traffic to port 80 and rejects all other traffic. You can now add [before the reject all command] other ports you need open (ssh for example).

---

### Post by lugos on 2006-08-21
Gouki, thanks for the info.  How do I put it on the DMZ?  Is that something I do through the router?

---

### Post by Gouki on 2006-08-21
> **lugos said:**
> Gouki, thanks for the info.  How do I put it on the DMZ?  Is that something I do through the router?

Yes it is. I don't know where you can find it on your specific router, but search for DMZ. It's pretty simple to setup. You just need to enter the servers IP address in front of your WAN IP address.

---

### Post by scxtt on 2006-08-21
FWIW, i can't think of any good reason why you can't use port 80 (esp. if your ISP assured you they don't block it) ... it's simply a matter of forwarding port 80 to you local IP (if you have a firewall, it would stop it, but other than that as long as apache2 is running you should be good to go), i'd get to the bottom of that before using DMZ ...

---

### Post by lugos on 2006-08-21
Do I also have to make a change to my hosts file?  Here is what it looked like before:

127.0.0.1       localhost
127.0.1.1       lugosamuel

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Here is what I think I have to change it to:

127.0.0.1       localhost
192.168.0.2     [www.lugosamuel.com](www.lugosamuel.com)      lugosamuel

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Is that correct?

---

### Post by chrisfay on 2006-08-21
You do not need to add your LAN IP to /etc/hosts. It is correct the way it is.

When you ran nmap, did you use your LAN or WAN IP? If you have a router config problem, and ran nmap using your LAN IP, it would show port 80 open internally but would not tell you whether or not its open externally. 

Make sure and run nmap using the WAN/Public IP. 

Also, you can try telneting as well.

Start, Run...
telnet x.x.x.x 80
(from a windows machine)

You should get a repsonse indicating apache listening on port 80. If not, then either your ISP 'does' block the ports and just isn't telling you or you have a portforwarding problem. 

I would also check to make sure that Apache is listening to port 80 in ports.conf and make sure that Apache is configured to use the ports.conf file in apache2.conf.

---

### Post by lugos on 2006-08-21
chrisfay, thanks for the info.

I changed my hosts file back to what it initially was.

I ran **nmap -sT *public IP*** and saw that port 80 is open.

I did a **telnet *public IP* 80** from a windows machine and got the command window, but no response.

I also checked the ports.conf file and it is listening to port 80.  And I checked the apache2.conf to make sure that Apache is configured to use ports.conf.

Can I safely assume that I have a port forwarding problem?

Thanks again for the help.

---

### Post by lugos on 2006-08-22
In doing some research I ran across the following:

"The router's DHCP function must be disabled to use Forwarding."

Does anyone know how accurate that is?  Is doesn't seem like it would be wise to turn off DHCP on the router.

Thanks for the help,
lugos

---

### Post by NetworkGuy on 2006-08-22
They probably want DHCP turned off so you don't have to keep changing your forwarding information in your router each time your server gets a new IP address from the router.  

It makes sense if you think about it.

---

### Post by eternalsword on 2006-08-22
> **lugos said:**
> In doing some research I ran across the following:

"The router's DHCP function must be disabled to use Forwarding."

Does anyone know how accurate that is?  Is doesn't seem like it would be wise to turn off DHCP on the router.

Thanks for the help,
lugos

there should be a way to specify a static ip for one machine via mac address while leaving DHCP on then you specificy that static ip to forward http traffic to.  also if you have NAT enabled on the router you need to make sure that you're using the public ip address to access the server.

---

### Post by lugos on 2006-08-22
This may be a dumb question, but what is NAT?

Thanks for the info.

lugos

---

### Post by NetworkGuy on 2006-08-22
Network Address Translation

Think of it as a forwarding address.   The address your PC is at can not be routed over the Internet.  Your router changes the IP address of your PC to the public address of your router.  When the information comes back, your router translates it to your PC's address.

PC (192.168.1.x)---> Router (1.2.3.4) ---> [www.ubuntuforums.com](www.ubuntuforums.com) (205.234.170.217)

---

### Post by chrisfay on 2006-08-22
> "The router's DHCP function must be disabled to use Forwarding."

You definately do NOT have to turn off your DHCP server in your router to allow portforwarding. I have my Linksys WRT54G router currently handing down static IP's + Portforwarding to two of my pc's. I then have it dynamicaly assigning IP's to two others. 

All you need to do is make sure and assign your static IP in your etho setup, make sure you have your gateway set to your router, then forward the ports to the specified IP.

Another thing to look out for:

If you have your DHCP setting in your router handing IP addresses for say range   192.168.1.50 - 192.168.1.100 make sure that you didn't specify a static ip that is in that range. Or you will be having conflicts between DHCP and your static IP's

---

### Post by lugos on 2006-08-23
> All you need to do is make sure and assign your static IP in your etho setup, make sure you have your gateway set to your router, then forward the ports to the specified IP

How do I go about doing that?

> 
Network Address Translation

Think of it as a forwarding address. The address your PC is at can not be routed over the Internet. Your router changes the IP address of your PC to the public address of your router. When the information comes back, your router translates it to your PC's address.

I will look more into that and see if my router is configured to do that.

All, thank you for the info and the assistance.

---

### Post by lugos on 2006-08-23
Alright, I wanted to find out if it was truly my router that was the problem, so I disconnected the router and directly connected my DSL modem to the web server.  I ran **nmap -sT 138.88.126.41**, and received the following response: **All 1674 scanned ports on pool-138-88-126-41.res.east.verizon.net (138.88.126.41) are: closed**.  So, it appears that my ISP *does* block port 80 :---).  Am I right? Does that appear to be the case?

---

### Post by NetworkGuy on 2006-08-23
Where are you running the scan from?  To run the scan correctly, you should be running it from somewhere other than your place, or get someone else to run the scan for you.

---

### Post by chrisfay on 2006-08-23
If you can telnet from another machine outside your network to your Ubuntu box running the servers than you are good. If not, than most likely you have an ISP that is blocking those ports.

Make sure that apache or whatever server you are testing with is correctly listening on the specified port.

Have someone from another machine telnet to your box on those ports. If they get no repsonse from your servers, than odds are your ports are blocked. You can also try changing the listening ports in your servers to some high random port like 9900 or something. 

Then retry telneting. If you get through on a random port than you are blocked by your ISP in a certain range. 

I was helping someone out the other day having this problem and found his ISP blocked both 80 and 8080 but changed apache to listen on 423 and got through...go figure

---

### Post by compunuts on 2006-08-23
ISPs usually blocked server ports such as 80, 21, 25 to prevent you from running servers. If you complain, they point you to user aggrement (EULA). That's when you know you need to switch ISP.

My ISP capped the speed to 128K upload just enough to run small test servers but not enough to run fairly media intensive web site. Works for me since all I need is test some stuff on web server, run a small email server for a few peole and stuff.

---

### Post by lugos on 2006-08-26
All,

It appears that my ISP did not give me accurate info when they told me that they do not block port 80.  I configured apache to listen to port 6550, as scxtt suggested, and it works just fine.  Thank you all for the help, it was very much appreciated.

lugos

---

