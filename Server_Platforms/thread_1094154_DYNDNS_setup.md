---
title: "DYNDNS setup"
date: 2009-03-12
forum: Server Platforms
---

### Post by happyhacker on 2009-03-12
It is not clear to me how to do this. I have partly setup a DYDNS account but am a bit confused as to the next steps. AT the DYDNS page the instructions are:

1. I have set my dn to <myserver>.dydns.org. Is that right? The IP address is not fixed.

2. The help at dydns site says:
[COLOR="Blue"]Wildcard 
Allows any fourth-level (and deeper) hostnames to be resolved. If wildcard is disabled, names like [www.yourname.example.org](www.yourname.example.org) will not work.
Service Type 
Sets host to one of three possible states. 
&#8211; Host With IP address would allow visitors to access services at your network by IP address; 
&#8211; WebHop Redirect would redirect web-requests from address [http://www.yourname.example.org](http://www.yourname.example.org) to URL that you would provide below; 
&#8211; Offline Hostname will hide your host IP or URL redirection settings (useful for temporary maintenance).[/COLOR]

Which one of these should I use?

3. Based on the above choice how do I configure the next bit:

IP Parameters (invisible for WebHop Hostnames) OR
WebHop Parameters (shown only for WebHop Hostnames) OR
Mail Routing Parameters. Do I need these?

4. Then I think I should perform these but please confirm:
$ sudo apt-get install libio-socket-ssl-perl (I already have SSH server running)
$ sudo apt-get install ddclient (does the command line ask for certains parameters during install - I do not have a GUI?).

5. Then use this tutorial to configure ddclient:

[http://mexpolk.blogspot.com/2008/01/ubuntu-gutsy-dyndns-client-setup.html](http://mexpolk.blogspot.com/2008/01/ubuntu-gutsy-dyndns-client-setup.html)

If someone could comment on the validity of the above steps I could confidently go ahead on my system.

---

### Post by drummingpariah on 2009-03-12
It's a pretty straightforward install.  Some routers can also update dyndns automatically, which is slightly easier.

---

### Post by happyhacker on 2009-03-12
Thanks, still hoping someone can answer the Qs above.

---

### Post by hyper_ch on 2009-03-12
what router have you got? if the router is not too old it may have dyndns or no-ip or some other dyn ip server integrated. that makes things a lot simpler.

---

### Post by happyhacker on 2009-03-12
DG834. Does seem to have a facility but does it every 5mins as far as I can see. Does anyone have the command line for it? I still need to configure the server though, don't I?

---

### Post by BkkBonanza on 2009-03-12
If your router can do dyndns then it should update the dns server with it's new ip every time it gets changed by your isp. If it handles that for you then there is no need to do it again from anywhere else - it would be redundant and just change what was already changed by the router. This is the simplest way to do it. If your router can't do it then you can install and use something like ddclient. It will detect ip changes and then update dyndns (or other dns servers) as needed.

---

### Post by hyper_ch on 2009-03-12
throught the web interface you should just be required to enter your name and password for the dyndns account.

---

### Post by happyhacker on 2009-03-12
OK I will explore the router option. But how do I configure ssl (I assume I need an encrypted connection) so logon with a password is necessary?

When I have that and I logon what/how do I set what appears in the browser - is a command line or something else?

---

### Post by hyper_ch on 2009-03-12
it should be a web user interface... enter the IP of the router in your browser.

---

### Post by BkkBonanza on 2009-03-12
You may want to read this thread as well. It contains a bit of info related to using DynDNS with your router model (in particular last post).

[http://mybroadband.co.za/vb/showthread.php?t=12478](http://mybroadband.co.za/vb/showthread.php?t=12478)

BTW when you do login into your router via your browser (the address would be something along the lines of 192.168.0.10 - check the manual for defaults) also be sure that you change the admin password while your'e in there. Double so if your'e using wifi. You'd be suprised at how many local wifi users leave their routers configured with default admin passwords - just silly as any passer by can login and reconfigure their router for them. I had an SMC router once that even allowed WAN side telnet access with a default password. Terrible.

---

### Post by happyhacker on 2009-03-24
If I type in [http://myIpAddress:8080](http://myIpAddress:8080) the IP that my router is giving me after setting it up to collect the (IP) from DYNDNS then the access fails in the browser. If I just put in IP then I get the router logon screen and can access my router. So it would appear that DYNDNS is working, yes?

If I try to access webmin on my server [http://myIpAddress:10000](http://myIpAddress:10000) it fails "Internet Explorer cannot display the webpage".

I get the same if I type [http://www.myDomainName.dyndns.com/](http://www.myDomainName.dyndns.com/).

Advice appreciated.

---

### Post by BkkBonanza on 2009-03-24
If you are using your public (dynamic) ip or domain name to get to your router and getting the admin page then you should consider disabling "remote admin" from the router admin panel. It allows the public to see and potentially hack your router. If you really need to access the router from outside your lan (public internet) then ok, do it. But if you only need to access your router from inside the lan (typical) then not allowing outside access is a security improvement.

Regarding port 8080 - if it is blocked that then it means you need to forward a port in your router to your local machine. So go to the router admin and look for port forwarding or NAT and add an entry that tells the router to forward from port 8080 to the suitable ip and port within your lan. 

It sounds like your isp doesn't block port 80 since you can see your router admin panel so why not use port 80 for your web server? That's ths norm for web pages. You can forward it the same way. You can also forward to different ports eg. forward from port 80 publicly to port 8080 on your inside machine.

---

### Post by BkkBonanza on 2009-03-24
BTW - same issue for your webmin panel. Need to open port 10000 and forward to local server ip at port 10000. So the router passes that traffic as well.

Having ports closed/blocked is what makes the router good for your LAN security. Only open and forward the ports you need the public to get in through.

---

### Post by Bachstelze on 2009-03-24
@cantthinkofanickname: are you trying to connect to your server from *inside* your LAN using youe public IP address? If so, your router most likely doesn't allow this, which is why you are redirected to the admin page. Try to connect to it from outside your LAN.

---

### Post by happyhacker on 2009-03-24
Thanks. Firstly I am trying to get in from my LAN but the browser just does not connect. I don't get a refusal message. So maybe the external address working is a red herring here. I have now disallowed external access (turned remote management off which was using 8080 so I assume it's available for others now) to my router (for the moment).

I have configured access to my server by stating its LAN IP for http(80) for any WAN users. Same refusal result. But I notice that the router has 8080 set for remote management (see above) but that should be bypassed now.

I cannot test from outside until I get home. So tell me if I'm wasting my time here and I'll come back later.

---

### Post by Bachstelze on 2009-03-24
So right now you are on the same LAN as the server, right? Can you connect to the server using its LAN IP?

---

### Post by Joeb454 on 2009-03-24
First off, putting your public IP probably isn't the best idea.

Nevertheless - your port forwarding seems to be working correctly, because visiting the IP address in your previous posts gives me the default apache2 "It Works!" page :)

Port 8080 however - doesn't appear to be working

---

### Post by happyhacker on 2009-03-24
Yes, right now I'm on my LAN. So Joeb454 what did you type in? If I type in something I put earlier it does not work, in fact I get a logon form for my router!!. I only get "It works" if I type port 80 on the internal IP. I am now worried I've given people the wrong access!

---

### Post by MrWES on 2009-03-24
> **BkkBonaza said:**
> BTW - same issue for your webmin panel. Need to open port 10000 and forward to local server ip at port 10000. So the router passes that traffic as well.

Having ports closed/blocked is what makes the router good for your LAN security. Only open and forward the ports you need the public to get in through.

With port 10000 being forwarded and running DenyHosts; any need to make changes in the config?

Bill

---

### Post by BkkBonanza on 2009-03-24
As of this moment your public ip given above works fine. I get the "It Works" page.
It's just when you use your public ip within your own lan that it doesn't work. Routers do often block public ips used from within.

If you want to see it work from within then go to a public proxy page and type your ip in there. Or use your domain address if that is functioning.

For proxy page try one like: hidemyass.com (which places an ad at top of pages)
But many others out there. Google.

---

### Post by happyhacker on 2009-03-25
[SOLVED} I have now tried remotely and it works as joeb454 said, thanks for your help.

---

