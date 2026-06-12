---
title: "Static IP / Domain name"
date: 2008-04-15
forum: Server Platforms
---

### Post by Diana Rogger on 2008-04-15
Hi Ubuntu family,

In this month I want to complete my webserver and make it accessible. I installed everything and it is working. I also have a static Ip now and a own domain name. In this month I hope I can publish my website.

**But I have some problems now.**

I know there are some experts on this forum and thats why I am here.

- My ISP give me a static Ip: (For example: 200.2.173.205)
- I also have a registered domain name (For example: [www.diana.sr](www.diana.sr) )


The ISP installed a ADSL/ROUTER in my house.
--------------------------------------------------------------------------------------------------
The WAN IP is 200.2.173.205. / The LAN IP is 192.168.1.1


I setup my own Linksys ROUTER
--------------------------------------------------------------------------------------------------
The IP is 192.168.1.2 / My Lan is 192.168.50.10

THE IP OF MY WEBSERVER IS : 192.168.50.200

When you enter my static IP (200.2.173.205) in a web browser the Linksys Router is forwarding this address to my Web server so you can see the home page on my webserver.


-------------------------------------------------------------------------------------------------
When I enter my domain name in a web browser on a computer outside my network the browser is displaying the content of the www folder in the webserver of the ISP. The content of the WWW folder is a CGI folder. When I ping my domain name ([www.diana.sr](www.diana.sr)) I am getting this address: 190.98.5.50.

**First Step**
--------------------------------------------------------------------------------------------------
1) I Logged into the home folder they made for me on the ISP server /usr/home/diana/www and I put a index.php file with a php script in to it to redirect the index.php page to my Static IP: 200.2.173.205 to display the home page on my own web server. It is working nice


**Problem:**
--------------------------------------------------------------------------------------------------
When I enter [www.diana.sr](www.diana.sr) in the web browser I am getting my home page on my webserver but the web browser is displaying my static Ip address. I don't want the web browser to do that.


Questions:
--------------------------------------------------------------------------------------------------
1) 
How can I configure my server to display my domain name in stead of my IP?

I want that if any body type [www.diana.sr](www.diana.sr) in their browser they must see my home page on my own web server without displaying my static IP.

2) 
Is this a good configuration by my self to redirect the index page on the ISP Server to my static IP to display my home page on my own web server?

3) 
Should the ISP not have configured the ip address 190.98.5.50 from [www.diana.com](www.diana.com) on their server to rediret to my static IP?

I hope someone can help me with these questions.

Thank you in advanced

---

### Post by cdenley on 2008-04-15
Your domain should be configured so it resolves to 200.2.173.205. This needs to be done through your ISP. The only way to force your domain to stay as the url with your current setup would be to setup a frames page on the site your ISP is hosting for you, then put your real site in the only visible frame. This would be really annoying, though.

---

### Post by hyper_ch on 2008-04-15
the place where you registered your domain you should also be able to manage the "dns" for it. It needs to point to your static ip address as cdenley has already said.

---

### Post by Deathrend on 2008-04-15
I use GoDaddy for mine.  It's really simple, and you don't have to host your own name servers (Which isn't hard if you know what you're doing, but I'm lazy).  It let's me have full DNS control over my domain, as though I hosted the name server myself, without having to worry about poking more holes through my firewall than I have to.  Makes for an easy test of webpages I plan to put into production, as well as very easy VPN access.

[http://exodusguild.net/](http://exodusguild.net/)

---

### Post by Diana Rogger on 2008-04-15
Hi Guys,

Thank you for your reply.

I will do that.

I would want to know how I should configure a webserver to display the home page using the domain name instead of a Ip address. How can I configure the sever?

Is there someone who want to help me?

Thank you in advanced.

Diana

---

### Post by hyper_ch on 2008-04-16
if you have registered a domain name (or use a dyndns service) and if that domain name points to your ip then you can browse a webpage there by entering the domain name into the browser's location bar.

---

### Post by haryoh on 2008-04-16
Hyper:
I set up my DNS but I have not clue what am doing or to set the BIND9. I've tried setting it up twice but I just don't get how or where my domain DNS will go or what. HELP!

---

### Post by hyper_ch on 2008-04-17
well, if you setup your DNS then it should work... otherwise you have to explain what you did.

---

### Post by Diana Rogger on 2008-04-19
He guys,

Thank you all for your reply.

I explained to my ISP what my problem is. They told me that I must pay 50 USD If I want them to set it up for me. So they know that it is a DNS story. I will do that ik I have the money.

Thank you all.

Regards,

Diana

---

### Post by haryoh on 2008-04-22
[http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)

Follow steps in this tutorial, and you'll be fine. you don't have to by a static IP address from your ISP before you can setup a web server.

identify you ISP's IP either from your router or from your TCP status. Just make sure you add your ISP DNS to your server in your NS(name server): make one primary DNS and enter a second one. don't mind the 192.168.0.x

just identify 192.168.0.x as your server static dynamic IP.

let me know...

---

