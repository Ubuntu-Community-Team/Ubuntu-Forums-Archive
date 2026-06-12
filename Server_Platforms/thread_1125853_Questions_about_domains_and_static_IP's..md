---
title: "Questions about domains and static IP's."
date: 2009-04-14
forum: Server Platforms
---

### Post by cmwslw on 2009-04-14
I have already purchased a domain and set up an Ubuntu server. The server is working great, but I have no idea if it is using a static IP. In /etc/network/interfaces, I have set it up as a static IP, but I don't know if Comcast is actually providing a static IP (I have a basic home plan - not business class). Is there any way to tell? And if I do end up having a dynamic IP. Is it possible to map a domain name to a dynamic IP? I have heard that you can use a service called DynDNS. Is this what the service is for?

Thanks in advance, (I am a server noob :))
Cory Walker

---

### Post by doas777 on 2009-04-14
I use a firefox extension called [external IP]("http://www.ermodev.se/visa_firefoxExtensions.htm") that shows me my public address. 

Most ISPs cache the mac address of your Modem and serve up the same ip address to it each time, but I have noticed that if you replace the modem, or reset it a few times, it may give you a new one.

I've never set up ddns but you can do it with services like dydns:
[http://www.dyndns.com/](http://www.dyndns.com/)

good luck,
franklin

---

### Post by BDNiner on 2009-04-14
[http://www.no-ip.com/](http://www.no-ip.com/)

That is another service that will help keep your dynamic IP pointing to your hostname, with their free version they give you a hostname to use. I believe that you have to pay to use your own hostname.

---

### Post by BkkBonanza on 2009-04-14
Whether you have static ip depends on your ISP. Mine changes my ip 1-2 times per day. Others take longer and some may re-assign the same address always until one day they change their system and suddenly you don't know why your ip has changed. It is typical for home class service to be dynamic. If you're not sure then there isn't any harm in configuring dyndns type service. It would ensure your domain name is updated if it did change but not affect anything if it stays the same. Configuring your interfaces file as static doesn't mean that your service is static but it will work until sometime they change your ip. 

When you signed up for your ISP account they should have provided some details/instructions that would make it clear if you had a dynamic ip. If they gave instructions for Windows where they tell you to select "automatic" for settings then that implies you have a dynamic ip. Otherwise they would give you an ip to use during setup - which implies it is static. They won't likely have Linux instructions but generally with dynamic ips you want to have a dhcp client running and then run ddclient for the domain name updating.

---

### Post by windependence on 2009-04-15
Comcast does not sell static IPs to their residential customers so you will either have to use dynamic DNS or get a business account. They are not my favorite ISP for sure as they routinely block many ports and throttle network traffic. 

Be aware that although you can certainly run a web site from a dynamic IP, that is not the "proper" way to run a commercial site and will probably violate Comcast's terms of service. Also, when I ran a server using dynamic DNS there were quite a few people who could not view my web site from certain places like their work or public computers because their company firewalls blocked all known dynamic IP services or redirected addresses. If you don't think that people view your site from work, think again :) Most of my traffic comes from people's companies during their work day.

-Tim

---

### Post by spynappels on 2009-04-15
Just as a general point, it is normally safer to place a server behind a router/firewall and only forward the required ports from your public IP to whatever the local LAN IP of the server is. Many routers come setup to update various DDNS services, my Linksys has 3 presets, one of which is DynDNS which I use.

---

### Post by cmwslw on 2009-04-15
> **windependence said:**
> Comcast does not sell static IPs to their residential customers so you will either have to use dynamic DNS or get a business account. They are not my favorite ISP for sure as they routinely block many ports and throttle network traffic. 

Be aware that although you can certainly run a web site from a dynamic IP, that is not the "proper" way to run a commercial site and will probably violate Comcast's terms of service. Also, when I ran a server using dynamic DNS there were quite a few people who could not view my web site from certain places like their work or public computers because their company firewalls blocked all known dynamic IP services or redirected addresses. If you don't think that people view your site from work, think again :) Most of my traffic comes from people's companies during their work day.

-Tim

So from what I understand my server needs to be able to handle IP address changes since it has a dynamic IP. This can be handled by using services such as No-IP and DynDNS. I guess you would point the domain to them, and from there they redirect the visitor to my current IP. Is this correct? Is any one service cheaper or more reliable based on experience?

Also, [the guide I'm using]("http://www.howtoforge.org/perfect-server-ubuntu8.04-lts") required me to change /etc/network/interfaces to a static address. Is this doing anything since I don't have a static address in the first place? Should I change it back to dynamic since I don't have one?

(Sorry I have tons of questions)

Cory

---

### Post by spynappels on 2009-04-15
Hi Cory,

 First we need to establish how your server connects to the internet. Is there a Cat5 cable from your server direct to a DSL or Cable modem ONLY or does it go through a router? If it goes through a router (often more likely) the static IP you set in the server is a static LAN IP rather than the static Public IP. 

Can you just explain the hardware setup a little more?

Your grasp of how DDNS works is correct. I use DynDNS because it is supported by my Linksys router and it is free. I've had no problems with it.

---

### Post by BkkBonanza on 2009-04-15
Using a dynamic ip is not handled through redirects. What you do is run a program like ddclient either on your server or router - whichever machine is connected to your isp and getting the public ip. ddclient is often built in to routers but if you don't have a router between your server and the net then you run it on the server. It takes care of a periodic checks to see if your ip has changed and then notifies the dns server of the change. Your dns server gives out the most current ip for any name lookups. So users come direct to your server via the updated ip. 

Note that this is not perfect for commerical web sites and not generally recommended. Since there is a time interval for checking the ip that means you can have a few minutes (typically, though could be made less) when the name will not resolve correctly until the ip is updated. The update interval is set in the ddclient config. While dyndns is a popular dns provider there are many, maybe even most, dns providers now that have dynamic update support using the same or similar methods.

Note - I'm talking about dns server being the one run by your registrar or some third party provider (like dyndns). You can't run a dns server for the public on a dynamic ip. Well, you probably could but it's a bit crazy.

---

### Post by ugm6hr on 2009-04-15
Remember, if you have a router, the static IP you set in the /etc/network/interfaces file is for your (local) LAN, not the (web / wide) WAN.

So the static IP is likely to be set as something like 192.168.1.250 (as mine is), whereas your WAN IP will be something more unpredictable, and can be seen at the top right of the open dns site: [http://www.opendns.com/](http://www.opendns.com/)

In order to access your web server from the web (i.e. from somewhere outside your LAN / home network), you can either enter the IP as seen at [http://www.opendns.com/](http://www.opendns.com/) or use DynDNS to give you a more memorable url, which will automatically update to ensure it forwards traffic to the corrent place.

---

### Post by cmwslw on 2009-04-15
> **BkkBonaza said:**
> Using a dynamic ip is not handled through redirects. What you do is run a program like ddclient either on your server or router - whichever machine is connected to your isp and getting the public ip. ddclient is often built in to routers but if you don't have a router between your server and the net then you run it on the server. It takes care of a periodic checks to see if your ip has changed and then notifies the dns server of the change. Your dns server gives out the most current ip for any name lookups. So users come direct to your server via the updated ip. 

Note that this is not perfect for commerical web sites and not generally recommended. Since there is a time interval for checking the ip that means you can have a few minutes (typically, though could be made less) when the name will not resolve correctly until the ip is updated. The update interval is set in the ddclient config. While dyndns is a popular dns provider there are many, maybe even most, dns providers now that have dynamic update support using the same or similar methods.

Note - I'm talking about dns server being the one run by your registrar or some third party provider (like dyndns). You can't run a dns server for the public on a dynamic ip. Well, you probably could but it's a bit crazy.

I guess the company I got my domain from, 1&1, doesn't provide that service. I've looked at companies like DynDNS, but most seem to charge a fee when using a custom domain name, which I'd like to avoid if possible. I've found a site called [XName]("https://www.xname.org"), which seems to be free. Has anyone used this and can confirm that it works?

There seems to be an XName article about Dynanic IP's [here]("http://www.xname.org/dynamic-update.php?language=en").

---

### Post by BkkBonanza on 2009-04-15
I had a look at 1&1 just now. They don't seem to offer any dynamic update functions. I'm not sure what other places charge but I did use sitelutions.com for name serving for a couple years and I think they offered dynamic updates. Their servers were fast and I never had problems but their conttrol panel is a bit clumsy - they are free though. You can use them by registering and adding your dns records and then goto 1&1 and set it to use sitelutions name servers. This holds true for any others you find that offer free dns. Once in the sitelutions control panel they have a help page for dynamic dns. It's a bit messy but the info is there.

Another popular free dns provider is zoneedit.com and I think they have dyndns. I just checked and they have support for quite a few clients too (including ddclient).

[https://www.zoneedit.com/doc/dynamic.html#faq3](https://www.zoneedit.com/doc/dynamic.html#faq3)

---

### Post by cmwslw on 2009-04-15
I believe I've gotten most everything about this figured out. Thank you so much for the awesome help, guys! I do have one final question though, the DDNS service on my router only has a dropdown menu for DynDNS, EasyDNS, and No-IP. Are these the only services I can use? Here is a post on Experts Exchange - I copied it since not everyone can access it:
> create an account at dyndns.org. create a host service using a name like some-name.dyndns.org. log into your router, on the top nav bar click on tools, then click on dynamic dns on the side bar. enable ddns by checking the box. from the drop down menu, select [www.dyndns.org](www.dyndns.org) (free) as the ddns server address. now enter the the name (some-name.dyndns.org), username and password information. leave the last box blank. "save settings."

after your router reboots log into your dyndns account and click on "my hosts." you should see your some-name.dyndns.org entry with an ip address and a "last updated" entry (should be a few seconds ago).

with that done you can go to zoneedit, create a subdomain of webcam1.yourdomain.com and have it forward to some-name.dyndns.org. it will then forward automatically to your router. alternatively you can simply use the some-name.dyndns.org address to get to your cam.
This is not really a great solution due to problems outlined on [this]("http://www.thesitewizard.com/sitepromotion/cloaked-domain-redirection-issues.shtml") website. Are there any alternatives to this method? And by the way, has anyone had experience with EasyDNS for dynamic DNS? I haven't really heard of them, and I might end up having to use a paid service.

---

### Post by BkkBonanza on 2009-04-16
I don't think you want to use cloaked domain redirection. There are problems with it and for a commercial site it would be a bad idea. If the site is for testing/personal use then it may be an easy way out. It's too bad that some routers don't have many options for ddns. What kind of router do you have (mfr/model #)? Some routers are easy to do firmware upgrades on to get better functionality (Linksys, Asus, others). And most give you a terminal (ssh/telnet) access method that may allow low level settings to override the menu choices. The good router firmwares allow a custom option where you can add your own config. A lot of routers have a cron option where you can install your own timed script. This may be doable with zoneedit as they have a very simple update method requiring just an http request. Another option is to run the ddns client behind the firewall on your server. Although not the usual choice there is no reason it can't be done that way.

I haven't used easydns. They are well known and likely fine but why pay if you can arrange a workable free solution. I tried looking at their site and it worked ok until I hit the pricing page. Then they locked up and it still isn't responding even after 5 minutes. Hmmm, something they don't want to share?

---

### Post by windependence on 2009-04-16
> **cmwslw said:**
> I believe I've gotten most everything about this figured out. Thank you so much for the awesome help, guys! I do have one final question though, the DDNS service on my router only has a dropdown menu for DynDNS, EasyDNS, and No-IP. Are these the only services I can use? Here is a post on Experts Exchange - I copied it since not everyone can access it:

This is not really a great solution due to problems outlined on [this]("http://www.thesitewizard.com/sitepromotion/cloaked-domain-redirection-issues.shtml") website. Are there any alternatives to this method? And by the way, has anyone had experience with EasyDNS for dynamic DNS? I haven't really heard of them, and I might end up having to use a paid service.
You would be very correct on this. Using dynamic DNS is really just a hack no matter how you do it. If you have to do this, I would recommend no-ip.com. They have a pay service for just $25 a year. Their free service is good too.

If you really want to do this right, consider dumping Comcast and get someone like speakeasy.net. There, you can get a static IP or several, and a good up speed for a reasonable price, probably less than your Comcast.

-Tim

---

