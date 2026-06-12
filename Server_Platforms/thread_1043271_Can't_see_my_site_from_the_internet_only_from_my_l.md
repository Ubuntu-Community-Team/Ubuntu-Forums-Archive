---
title: "Can't see my site from the internet only from my lan"
date: 2009-01-18
forum: Server Platforms
---

### Post by Master_God on 2009-01-18
Hello,

I've been digging into this forum for the last 30 hours seeking an answer, trying everything I read on the many threads I've found but I didn't found a solution to my problem.

What I want basically is running an Ubuntu Server 8.10 on my VMWare virtual machine and let anyone access the "It works!" page.

I've followed these tutorials to install Ubuntu Server v8.10 and Webmin:
Installing Ubuntu Server 8.10 - [http://www.ubuntugeek.com/step-by-step-ubuntu-810-intrepid-ibex-lamp-server-setup.html](http://www.ubuntugeek.com/step-by-step-ubuntu-810-intrepid-ibex-lamp-server-setup.html)
Setting up Webmin - [http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html](http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html)

I didn't installed any gui on the server, it is still console-only.

The server and Webmin has been installed just like the tutorials said, with just one exception:
The tutorial I followed to install the server said something about setting a static IP. I didn't do that because for start I just want this to work and after that I'll think on setting something more permanent so I won't need to reconfigure stuff every time I lose my IP.

Now when I log into [http://192.168.109.129](http://192.168.109.129) I can see the "It works!" page.
I even set up another website (if I understand right this is what I did) using Webmin under the path /var/www/pimpmyhouse and uploaded using Webmin an Index.html with some basic html displaying a text.
I can log into this new website using [http://192.168.109.129/pimpmyhouse](http://192.168.109.129/pimpmyhouse)

When I say I can log in I mean only my pc (which is on the same network as the server because it is on a virtual machine [using VMware]).

I've also read somewhere on the Ubuntu forums and help (and google) that there's something called a DNS which gives a name for an IP so when the IP changes you only need to update the DNS server with the new IP and it would be transparent to anyone using the addressed provided by the DNS Server. - Correct my if I got it wrong please.

So following that I went to [http://DynDNS.org](http://DynDNS.org) and registered a free account and created a new DNS domain.
In the IP field I gave it 192.168.109.129
Again it worked only on my PC but when I tried logging into this URL with my mobile phone or my friend's PC (who is not on my network) it didn't work.
In some other tutorial (on Ubuntu's help site which I can't find a like to - sorry) they said that some routers support DNS thingy and fortunately my router support [http://DynDNS.org](http://DynDNS.org)

My guess is that the server is just fine and ready to serve HTML pages using HTTP protocol with Apache2 under Ubuntu Server v8.10 but the only problem is that I don't know its full address so I can't log into it or register it to some domain.

Some technical info about my router:
**Siemens ADSL SL2-141**
Copy-Paste from the Status page.
[HTML]System Up Time 09:08:29:38 
ADSL Speed (DS/US) 1856/192 Kbps 
LAN IP Address 10.0.0.138 
Default Gateway 79.183.14.1 
Primary DNS server 62.219.186.7 
Secondary DNS server 192.117.235.235 

Firmware Version 3.02.02.08b_A2pB020a.d17f 
Boot Loader Version 1.0.37-0.6.5 
Wireless Driver Version 3.91.41.0 (Wireless is enabled) 
Wireless BSSID 00:16:E3:94:E3:E5 
Ethernet MAC Address 00:16:E3:94:E3:E2 [/HTML]


My host machine is Windows XP SP3 by the way.
This is the first time I ever done something like this.
I'm not so familiar with the terms in this business so please be gentle with me :P.

Thank you for even trying to help! I really appreciate it.

---

### Post by hictio on 2009-01-18
> 
So following that I went to [http://DynDNS.org](http://DynDNS.org) and registered a free account and created a new DNS domain.
In the IP field I gave it 192.168.109.129



You are giving your DynDNS host the wrong IP address, for what I can see.
You have to give that host, your public IP address, to get it, form a box inside your LAN, open: [Current IP Check](http://checkip.dyndns.org/), also, when you are setting up or updating a host thru DynDNS webfront site, you can actually use a function on the same webpage (if you are doing it form within your LAN that is) to actually use the public IP address; click on "Use auto detected IP address xxx.xxx.xxx.xxx."

---

### Post by dragos_iliescu_2005 on 2009-01-18
If I well understand, you run on a Win XP, under VMWare, Ubuntu Server and Webmin. OK, more, your settings is made your server available LAN only.
1. It is not recommended to run such a server on a virtual machine (except for testing).
2. Check on your virtual machine if you enabled the network (you must to set a bridge between your virtual ubuntu network and your Win actual network.
3. Check the firewall permission on virtual Ubuntu

Hope it help.

---

### Post by Master_God on 2009-01-18
> **hictio said:**
> You are giving your DynDNS host the wrong IP address, for what I can see.
You have to give that host, your public IP address, to get it, form a box inside your LAN, open: [Current IP Check](http://checkip.dyndns.org/), also, when you are setting up or updating a host thru DynDNS webfront site, you can actually use a function on the same webpage (if you are doing it form within your LAN that is) to actually use the public IP address; click on "Use auto detected IP address xxx.xxx.xxx.xxx."

If I set up my actual IP, when I try to go to [http://DNS's](http://DNS's) Domain it asks for my router's username and password.

@dragos_iliescu_2005: It is just for testing indeed.

After I set the network configuration on VMware to bridge and use my real IP on the DNS server I can't log into 192.168.109.129 anymore..
I can log in on 127.0.1.1 (on the server itself using the terminal)

---

### Post by Master_God on 2009-01-18
Okay, I found the new address:
It is now 10.0.0.6.
But again, same problem - I can log into the site and see the "It works!" page using this url: [http://10.0.0.6](http://10.0.0.6) and log into webmin using this Url: [https://10.0.0.6:10000](https://10.0.0.6:10000)

Is it good? Does it mean something?...

---

### Post by hictio on 2009-01-18
> **Master_God said:**
> Okay, I found the new address:
It is now 10.0.0.6.
But again, same problem - I can log into the site and see the "It works!" page using this url: [http://10.0.0.6](http://10.0.0.6) and log into webmin using this Url: [https://10.0.0.6:10000](https://10.0.0.6:10000)

Is it good? Does it mean something?...

That IP address will always work inside your LAN, but never coming from the outside of it.
It is an IP address range used for private LANs.
[Private network](http://en.wikipedia.org/wiki/Private_network)

---

### Post by Master_God on 2009-01-18
I understand that.
So how can I find my public/external address of the server?

My IP itself doesn't seem to be enough.. As I said trying to get into it asks me for my router's username and password..

---

### Post by hictio on 2009-01-18
> **Master_God said:**
> I understand that.
So how can I find my public/external address of the server?

My IP itself doesn't seem to be enough.. As I said trying to get into it asks me for my router's username and password..

Check my first post :D

---

### Post by Master_God on 2009-01-18
Then that's not the solution to my problem..:(
When I type in, in the address bar, the IP address I get from your site, it asks for the user name and password of my router - just like when I log in to open some ports or change some other settings..
I need something that identifies my server in the world wide web.
Maybe some configurations to my router? but which? if that's even the solution.
If not, maybe I need to set some configuration within the server itself?

I'm lost..:(

---

### Post by cariboo on 2009-01-18
Check [canyouseeme]("http://www.canyouseeme.org/") to see if you have any open ports on your router. It may be that your ISP is blocking any of the normal server ports.

Jim

---

### Post by hictio on 2009-01-18
> **Master_God said:**
> Then that's not the solution to my problem..:(
When I type in, in the address bar, the IP address I get from your site, it asks for the user name and password of my router - just like when I log in to open some ports or change some other settings..
I need something that identifies my server in the world wide web.
Maybe some configurations to my router? but which? if that's even the solution.
If not, maybe I need to set some configuration within the server itself?

I'm lost..:(

If I understand you correctly, if you setup the public IP address on the DynDNS host, and you then you try to access that IP address, you get prompted for a user/passwd login, then, I would check on the router if the remote administration is allowed, if its, on which port it is listening.

---

### Post by mbeach on 2009-01-18
check your manual pages at:
[http://www.iad.cz/prez/ADSL_SL2-141_User_Manual.pdf](http://www.iad.cz/prez/ADSL_SL2-141_User_Manual.pdf)

looks like page 86 of the file (numbered as 74) outlines what you need to do.

good luck,
mb.

---

### Post by Master_God on 2009-01-19
> **mbeach said:**
> check your manual pages at:
[http://www.iad.cz/prez/ADSL_SL2-141_User_Manual.pdf](http://www.iad.cz/prez/ADSL_SL2-141_User_Manual.pdf)

looks like page 86 of the file (numbered as 74) outlines what you need to do.

good luck,
mb.

Wow this looks like the exact problem and the most reasonable solution.
I'll try that as soon as I can and report back.

Thanks!!

---

### Post by aaron.d on 2009-01-19
yeah dude. If you get the router login screen, of YOUR router, it is because you have allowed "remote administration". It is a REALLY good idea to disable remote administration of your home router (for obvious reasons).

Then you just need to setup a port forward on your router that directs all http(port 80) traffic hitting your WAN interface (external IP) to go inside your network (LAN) to the server hosting the website (private IP).

That much is detailed by the pages in the pdf posted by mbeach, but check [http://portforward.com/](http://portforward.com/) to see if they have a walkthrough for your specific device.

---

### Post by Master_God on 2009-01-19
I'm desparate..
I tried to do as the manual said but nothing has changed.

Here is everything:
[IMG]http://img132.imageshack.us/img132/324/portshr2.png[/IMG]

[IMG]http://img104.imageshack.us/img104/7414/firewallko7.png[/IMG]

[IMG]http://img443.imageshack.us/img443/5781/dnsaq4.png[/IMG]

[IMG]http://img502.imageshack.us/img502/4125/itworksvd0.png[/IMG]

[IMG]http://img104.imageshack.us/img104/8729/401qc0.png[/IMG]

[IMG]http://img104.imageshack.us/img104/6982/natey7.png[/IMG]

[IMG]http://img187.imageshack.us/img187/2473/vmwarehi2.png[/IMG]


What? What else can I do? What have I not done right..

---

### Post by aaron.d on 2009-01-19
1- remove all the IP FILTERING crap.

2- You need ONE rule to forward http/HTTPS (port 80/443) to the server IP. You have about 3 configured. delete the ones for the 10.x.x.x ip, since you are not using that private IP range on your network. Delete the ones for 192.168.109.1, since .1 is your router. This should leave you with forwards on port(s) 80/443 ONLY going to 192.168.109.129. 

****NOTE: This should work, but keep in mind the DHCP lease for that IP could expire, and your server might end up with something other than .129 the next time it renews. But just follow #2 for now, and we can make sure it continues to work later.

3- your DYNDNS config is fine. Which is clear, since you are being forwarded to your routers interface and asked to login. This should go away and be replaced by the expected webpage once you disable the forwarding of port 80/443 to the routers IP (as shown in #2).

---

### Post by aaron.d on 2009-01-19
well now, after checking all your attached screens, it is clear to me that you are running nix in a VM ON a windows box. Can you answer a question?

Is the 192.168.109.x network a subnet that ONLY the windows box and its VMs know about?

If this is the case you have a few options, but I thought we should clarify that. 

I was wondering where you got the 10.x.x.x IPs, now I see that this may be the routers DCHP range, and you basically have NAT enabled for your VM "interface". 
In this situation, your router will have NO IDEA where 192.168.109.x is. To fix this easily, a static route on the router is required to say, basically:

"Everything going to 192.168.109.x needs to be passed to __________", where 'blank' is the gateway to the 'unknown network'. the bad thing is, most home "routers" do not allow addition of static routes. This is non optimal.

Basically, if the above is the case, you need to get that VM server onto the local network (with an IP in the same range of your router). I use Vbox (sun xvm) and not vmware, so im no expert there, but I think you are looking for "bridged" mode in VMware, not "NATed".

---

### Post by Master_God on 2009-01-19
> **aaron.d said:**
> 1- remove all the IP FILTERING crap.

2- You need ONE rule to forward http/HTTPS (port 80/443) to the server IP. You have about 3 configured. delete the ones for the 10.x.x.x ip, since you are not using that private IP range on your network. Delete the ones for 192.168.109.1, since .1 is your router. This should leave you with forwards on port(s) 80/443 ONLY going to 192.168.109.129. 

****NOTE: This should work, but keep in mind the DHCP lease for that IP could expire, and your server might end up with something other than .129 the next time it renews. But just follow #2 for now, and we can make sure it continues to work later.

3- your DYNDNS config is fine. Which is clear, since you are being forwarded to your routers interface and asked to login. This should go away and be replaced by the expected webpage once you disable the forwarding of port 80/443 to the routers IP (as shown in #2).
Ok. I will leave only those for 10.0.0.6 because if I set the bridged configuration in VMware this is what I get instead of 192.168.109.129

> **aaron.d said:**
> well now, after checking all your attached screens, it is clear to me that you are running nix in a VM ON a windows box. Can you answer a question?

Is the 192.168.109.x network a subnet that ONLY the windows box and its VMs know about?

If this is the case you have a few options, but I thought we should clarify that. 

I was wondering where you got the 10.x.x.x IPs, now I see that this may be the routers DCHP range, and you basically have NAT enabled for your VM "interface". 
In this situation, your router will have NO IDEA where 192.168.109.x is. To fix this easily, a static route on the router is required to say, basically:

"Everything going to 192.168.109.x needs to be passed to __________", where 'blank' is the gateway to the 'unknown network'. the bad thing is, most home "routers" do not allow addition of static routes. This is non optimal.

Basically, if the above is the case, you need to get that VM server onto the local network (with an IP in the same range of your router). I use Vbox (sun xvm) and not vmware, so im no expert there, but I think you are looking for "bridged" mode in VMware, not "NATed".
"Is the 192.168.109.x network a subnet that ONLY the windows box and its VMs know about?" yes, I guess.

If I change the configuration from NAT to bridged then the server's IP on the network is 10.0.0.6 which is the equivalent for 192.168.109.129 in terms of functionality I mean if I enter [http://10.0.0.6](http://10.0.0.6) I get "It works!" page - so I don't completely understand what this suppose to change but I'll do it anyways.
There isn't any 192.168.109.129 address now after I changed it to bridged.

Here's the status now:
[IMG]http://img525.imageshack.us/img525/7715/svripconfigpp8.png[/IMG]
[IMG]http://img104.imageshack.us/img104/3626/portsil1.png[/IMG]
[IMG]http://img405.imageshack.us/img405/1619/firewallzt1.png[/IMG]
[IMG]http://img297.imageshack.us/img297/226/itworks10006gp9.png[/IMG]
[IMG]http://img186.imageshack.us/img186/6074/staticim7.png[/IMG]

And here are few more screen shots for info you might need:
[IMG]http://img297.imageshack.us/img297/9889/lan1pk7.png[/IMG]
[IMG]http://img297.imageshack.us/img297/7012/lan2hh8.png[/IMG]
[IMG]http://img90.imageshack.us/img90/1/staticdnsconfigiz2.png[/IMG]

---

### Post by Master_God on 2009-01-19
And this is why I added everything for port 10000 which is Webmin's port:
[IMG]http://img523.imageshack.us/img523/8173/webminzd2.png[/IMG]

---

### Post by Maheriano on 2009-01-19
This shouldn't be so complicated, just forward port 80 on your router to your 10.0.0.6 IP and then follow your 192.168.xxx (or whatever) IP from any computer and it should work. Or simply buy a better router that already forwards port 80 for you (my Netgear does it). Some reasons it might not work are if you are forwarding the port but it is closed, you have to make sure it is actually open. Or if your ISP blocks port 80, you have to forward it to another port from the DNS (registrar) to get around that. I know Telus here in Canada blocks that port.

---

### Post by Master_God on 2009-01-19
The server has nothing to do with 192.168.xxx.xxx now that the settings are "bridged" and not "NAT".

And you can see from the images that I do forward port 80.
I know that it does open the port cause my eMule application uses those ports and it works for it just as it suppose.

P.S
I'll try setting eMule to use port 80 and see if it works also, interesting..

---

### Post by Master_God on 2009-01-19
I'm going to try switching the ports to the ones eMule uses as I **know** these are working and see if this fixes the problems.
Maybe my ISP does block port 80 and I don't know..

Just where do I change the ports on the server?
Which files should I edit?

Edit: **Only WHILE** eMule is running [http://canyouseeme.org](http://canyouseeme.org) says "Success" on the eMule ports.

---

### Post by aaron.d on 2009-01-19
a) dont forward webmin ports, that is a bad idea. Keep anything related to configuration OFF the WAN.

b)Maheriano is correct, in that this shouldnt be complicated. However,

> just forward port 80 on your router to your 10.0.0.6 IP and then follow your 192.168.xxx

makes no sense.

Your external IP is (as of last DynDNS update) 79.183.14.155. that ip will cause you, from the internet, to hit your router.

At this point, we just need to tell the router:

"send all http traffic (port 80) to ______ IP"

You have done that, with the IP 10.0.0.6, which works on the internal lan. 

That is all you should need to do. 

Forget the static route crap i mentioned, as you have made it clear that bridging work for you, with 10.0.0.6 as the nix servers IP.

make sure the external IP is updated correctly:

pinging 'pimpmyhouse.kicks-***.net' should yield the same IP as you are given if you visit 'www.whatismyip.com' If they dont match, that is part of the problem. Try putting the IP given to you from 'www.whatismyip.com' into the browser address bar to test without screwing around with your dynDNS setup.

---

### Post by aaron.d on 2009-01-19
it is doubtful they block port 80, although that is common. We already confirmed that you could get a login prompt to your router at home on that port.

If you want to test with a higher random port though, you can forward any port on the outside to port 80 running on 10.0.0.6 inside the lan.

In the port forwarding section on YOUR router, try setting up:

EXTERNAL PACKET
IP address = ALL
protocol = TCP
port = 8888

INTERNAL PACKET
IP address = 10.0.0.6
Port = 80

then hit the external IP you get from 'whatismyip.com' (trying to leave dynDNS out of this for now)

---

### Post by Master_God on 2009-01-19
> **aaron.d said:**
> In the port forwarding section on YOUR router, try setting up:

EXTERNAL PACKET
IP address = ALL
protocol = TCP
port = 8888

INTERNAL PACKET
IP address = 10.0.0.6
Port = 80

then hit the external IP you get from 'whatismyip.com' (trying to leave dynDNS out of this for now)
I did that but when I enter [http://10.0.0.6:8888](http://10.0.0.6:8888) I don't get anything though when I use only [http://10.0.0.6](http://10.0.0.6) it still shows the "It works!" page.

When I ping my dns domain I get the same IP I get from [http://whatismyip.com](http://whatismyip.com)

What now?

Edit:
Oh and I still get the same result when entering my IP (from [http://whatismyip.com](http://whatismyip.com)) - the login to my router..

---

### Post by Master_God on 2009-01-19
I just checked and to my surprise [http://canyouseeme.org](http://canyouseeme.org) :
Success: I can see your service on 79.183.14.155 on port (8888)
Your ISP is not blocking port 8888

---

### Post by aaron.d on 2009-01-19
nah you dont understand, port 8888 is not accessible INTERNALLY. it will be available externally only because you are telling the router to make port 8888 open, but really redirect all traffic to 10.0.0.6:80. If you try to hit 10.0.0.6 while you are already INSIDE the LAN, you dont go through the router at all, and of course, port 8888 isnt open for real on your server. 

all that to say, the forwarding works for a non standard port.

```
$ wget http://pimpmyhouse.kicks-***.net:8888/
--15:14:03--  http://pimpmyhouse.kicks-***.net:8888/
           => `index.html'
Resolving pimpmyhouse.kicks-***.net... 79.183.14.155
Connecting to pimpmyhouse.kicks-***.net|79.183.14.155|:8888... connected.
HTTP request sent, awaiting response... 200 OK
Length: 45 [text/html]

100%[=====================================================================================================================================================================>] 45            --.--K/s             

15:14:03 (3.31 MB/s) - `index.html' saved [45/45]

$ cat index.html
<html><body><h1>It works!</h1></body></html>
$ 
```


or in laymans terms, hit:

[http://pimpmyhouse.kicks-***.net:8888/](http://pimpmyhouse.kicks-***.net:8888/)

and it will work. congrats.

---

### Post by Master_God on 2009-01-19
**[http://10.0.0.6](http://10.0.0.6)**
"It works!" page.

**[http://10.0.0.6:8888](http://10.0.0.6:8888)**
Page Load Error.

**[http://79.183.14.155:8888](http://79.183.14.155:8888)**
Page Load Error.

**[http://79.183.14.155](http://79.183.14.155)**
Router Login.

**[http://canyouseeme.org](http://canyouseeme.org)**
**On port 8888** - Success (finally one success..)

**Ports forwarding**
from ANY:8888 to 10.0.0.6:80

Just a little summery.

Edit: Posted that before seeing your (aaron.d) post ;)

---

### Post by Master_God on 2009-01-19
Thanks!!!

---

### Post by Master_God on 2009-01-19
Thanks!!

I just can't believe it's working!!

I want to thank you all for helping me all the way!!

You have no idea how much I appreciate it!

Hooray!

Long Live the Open Source Community!

---

### Post by Master_God on 2009-01-19
How can I edit the topic to add [Solved]?

---

