---
title: "Ubuntu LAMP Server - Help Required."
date: 2007-09-21
forum: Server Platforms
---

### Post by pmoseley on 2007-09-21
I have an Athlon machine running Ubuntu Server 'Fiesty' 7.04 will all the latest updates installed, including the kernel.

I've installed LAMP on the server (manually with 'apt-get') and installed the e107 CMS on it. I can access the website from my home network fine, from the internet however is a completely different story...

I've setup a firewall rule in my NETGEAR DG834PN router/modem to allow incoming packets via tcp to be forwarded to the ubuntu server. This had no effect, I still could not access the website from the internet. Next I tried changing the port to something obscure such as 8008 both on the server and the router. Still no joy. Finally I resorted to putting the ubuntu machine in the DMZ of the router, and guess what? Still nothing...

I know that my ISP (plusnet) allows traffic such as this as I made a webserver previously, running on Suse and IIS 6.0 (Win Server 2003). From the web I can access my router configuration on port 8009 so the traffic is allowed and there's no packet filtering or firewall on my account used by my ISP.

What I was wondering was does Ubuntu refuse to respond to any request from the internet because it is not configured to? Or is there a built in firewall by default? Although I believe it's configured to listen to address 0.0.0.0, this area is not my speciality so I would appreciate any advice.

Phil

---

### Post by chrisxp on 2007-09-21
> **pmoseley said:**
> Although I believe it's configured to listen to address 0.0.0.0, this area is not my speciality so I would appreciate any advice.

Phil

maybe change 0.0.0.0 to your actual internal IP? im not really to grips with ubuntu but just a suggestion :)

---

### Post by James79 on 2007-09-22
By default Apache will accept connections from the "outside" as well.

Also, every Ubuntu server I've tried (6.06->7.04) have had no firewall enabled by default.

From the server itself, what output do the following commands give you?

```
sudo iptables -L
```

and

```
nmap 127.0.0.1
```

If the nmap command fails, you might need to install it first:

```
sudo apt-get install nmap
```

---

### Post by pmoseley on 2007-09-22
Here ya go:

'**sudo iptables -L**':

[I]Chain INPUT (Policy ACCEPT)
target          prot  opt  source                   destination

Chain FORWARD (Policy ACCEPT)
target          prot  opt  source                   destination

Chain OUTPUT (Policy ACCEPT)
target          prot  opt  source                   destination[/I]


'**sudo nmap 127.0.0.1**

[I]Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-09-23 00:18 BST

Interesting ports on localhost (127.0.0.1)
Not shown: 1696 closed ports

PORT        STATE        SERVICE
80/tcp      open           http[/I]


I hope that helps... 
I only have apache2 installed now, I removed php5 and mysql in the hope of finding out what the problem may be by simplifying things.

Another thing too: When I type in 'http://pjmserv:80' from my other linux box I don't get anything (even though the server name is pjmserv). However, when I type 'http://192.168.1.4:80' the website is shown fine.

Is there a possibility that the server only thinks its 127.0.0.1? If so I don't understand why it returns requests as 192.168.1.4 from the network.

Regards, Phil

---

### Post by g14 on 2007-09-22
If apache is listening on 0.0.0.0, that means it will listen on all available ip addresses no matter what. The most likely thing is that your router or dsl/cable modem needs to set up port forwarding to allow this traffic.

You can make this a lot easier with dyndns.org. Especially if you have a linksys router that will run ddclient for you.

---

### Post by pmoseley on 2007-09-23
My router is not the issue, it has worked on other webservers with exactly the same config. as in place now...

Packets are being forwarded (supposedly) to the server according to the web config of my netgear router.

I think i will have to install a packet sniffer on the network to see exactly what traffic is being forwarded but even if it is a problem with packet forwarding, when the server goes into the DMZ theres still no sign of a website from the web.

I have a static IP address and domain name correctly pointing to my router so i wont need to DYNDNS.org...

I've tried accessing the website through [http://domain.com](http://domain.com) [http://www.domain.com](http://www.domain.com) and [http://ipaddress:80](http://ipaddress:80)

---

### Post by pmoseley on 2007-09-23
Do I need to add something to the IPTable (if it exists)? I'm not experienced in this area.

---

### Post by James79 on 2007-09-23
Ok well it looks like your webserver is listening on 80. It is very common for ISPs to filter out this port to prevent people from running their own webservers.

Just to cover all our bases, we'll start over from the beginning. Change apache to listen to another port, I chose 8080. Update your router's port forwarding rules accordingly (forward all requests to 8080 to 192.168.1.4:8080).

Don't forget to restart apache:

```
sudo /etc/init.d/apache2 restart 
```

Confirm that it is indeed listening on the new port using the nmap command again.

[Go to grc.com and run a port scanner]("https://www.grc.com/x/ne.dll?bh0bkyd2") on yourself and see if it can detect your webserver. Some routers also allow you to run a port scan on yourself. Try nmap with your* public ip* to see and post your results.

> **pmoseley said:**
> 
Another thing too: When I type in 'http://pjmserv:80' from my other linux box I don't get anything (even though the server name is pjmserv). However, when I type 'http://192.168.1.4:80' the website is shown fine.


If you want to be able to access the server by name (as opposed to ip), add this line to your /etc/hosts:

192.168.1.4       pjmserv

---

### Post by pmoseley on 2007-09-23
I Found the solution!!

Last month I was forced to upgrade my broadband package because I was exceeding my monthly usage allowance. Prior to the switch I had a the ISP firewall completely off. However, after the switch, the stupid folk at plusnet enabled it for some stupid reason...

When I logged in to Plusnet's website I had a message saying someone had tried hacking my router on port 80. I thought WTF and found the darned firewall enabled. I switched it off and all is perfect!

Thanks for the help guys. There's a lesson to be learnt here, always check the basics even if ur pretty sure...

---

### Post by pmoseley on 2007-09-23
I Found the solution! Thanks for the help Guys!

---

