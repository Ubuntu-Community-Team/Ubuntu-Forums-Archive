---
title: "domain name problem with server"
date: 2011-03-27
forum: Server Platforms
---

### Post by Robert the Kat on 2011-03-27
[SIZE=2]Well, I registered a domain name with GoDaddy which was in a "parked" state. I managed to forward it to the IP of my server. The only problem it goes to the login of my router and not the server. GoDaddy tech stated there is nothing they can do when it comes to getting to a certain port on your router. So how is that problem corrected?
RK
 
[/SIZE]

---

### Post by soulresin on 2011-03-27
> **Robert the Kat said:**
> [SIZE=2]Well, I registered a domain name with GoDaddy which was in a "parked" state. I managed to forward it to the IP of my server. The only problem it goes to the login of my router and not the server. GoDaddy tech stated there is nothing they can do when it comes to getting to a certain port on your router. So how is that problem corrected?
RK
 
[/SIZE]

Depends on the router.  You'll likely need to set up port forwarding for port 80.

---

### Post by Robert the Kat on 2011-03-27
> **soulresin said:**
> Depends on the router. You'll likely need to set up port forwarding for port 80.
 
Well, I have the port the server is set to forwarded.  It makes me think the server MUST be on 80 ?
 
RK

---

### Post by arvevans on 2011-03-27
Your web server software has configuration options for what port it will be watching for inbound HTTP requests.  By default this is usually portmapper port-80, but it can be changed in server configurations.

Your router has a firewall that blocks inbound connections from the Internet to any of your locally connected computers.  In order for outsiders (those out in Internet land) to connect to your local web server you will need to poke a hole in the firewall for a specific portmapper port number (usually port 80 for web servers).  This process is called "port forwarding" and is configured in your router.  You will need to select a computer by LAN IP address, a service "HTTP" and a port "80" in your router configuration and activate it.

Some ISP's do not allow their subscribers to receive inbound [HTTP://*URL](HTTP://*URL)*:80 requests.  This is to prevent you from running a local web server via their interconnect facilities.  If you run into this problem, the work-around is to configure your server to use some other port number, and use a DNS translation service (like dyndns.com) to map port-80 requests to your actual portmapper port number.  Of course if you do this you really don't need the GoDaddy URL because a suitable, usually free, URL can be provided by the DNS translation company.

---

### Post by Robert the Kat on 2011-03-28
> **arvevans said:**
> Your web server software has configuration options for what port it will be watching for inbound HTTP requests. By default this is usually portmapper port-80, but it can be changed in server configurations.
 
Your router has a firewall that blocks inbound connections from the Internet to any of your locally connected computers. In order for outsiders (those out in Internet land) to connect to your local web server you will need to poke a hole in the firewall for a specific portmapper port number (usually port 80 for web servers). This process is called "port forwarding" and is configured in your router. You will need to select a computer by LAN IP address, a service "HTTP" and a port "80" in your router configuration and activate it.
 
Some ISP's do not allow their subscribers to receive inbound [HTTP://*URL*]("HTTP://<i>URL</i>"):80 requests. This is to prevent you from running a local web server via their interconnect facilities. If you run into this problem, the work-around is to configure your server to use some other port number, and use a DNS translation service (like dyndns.com) to map port-80 requests to your actual portmapper port number. Of course if you do this you really don't need the GoDaddy URL because a suitable, usually free, URL can be provided by the DNS translation company.
 
Thanks for all the info on port fowarding.  But that is one subject that I am very familiar with.  I port forward security camera servers all the time.  Not a problem.  I think what I did not state here correctly is this server is set up for incoming mail.  If it was just say a server to collect or store files, getting to it would not be a problem.  I use "no-ip.com" very often for getting to a file server.  Because this is an Email server I need the registered domain name as has been stated in many tutorials.
 
RK

---

### Post by BkkBonanza on 2011-03-28
As long as your ISP isn't blocking relevant ports the only steps are to port forward the correct SMTP (25) and POP3 (110) ports (or IMAP if you use that) from your router to your server on the LAN, and make sure you have added a correct MX record to your DNS at GoDaddy. Port 80 is irrelevant for email.

It's a good idea to add an spf record too in your DNS.

---

### Post by Robert the Kat on 2011-03-28
> **BkkBonanza said:**
> As long as your ISP isn't blocking relevant ports the only steps are to port forward the correct SMTP (25) and POP3 (110) ports (or IMAP if you use that) from your router to your server on the LAN, and make sure you have added a correct MX record to your DNS at GoDaddy. Port 80 is irrelevant for email.
 
It's a good idea to add an spf record too in your DNS.
 
Great info.  Recently found out that my ISP does block port 25 to keep you from creating and Email server.  Bummer.
 
RK

---

### Post by BkkBonanza on 2011-03-28
You can create a free gmail account that uses your domain name as the address. I've used this for a few years and it works great. [See here]("https://www.google.com/a/cpanel/domain/new"). This looks and works like a normal email server for your domain but you don't need to bother running the server. You can use the web interface or it also fully supports pop3s (ssl) , smtp and imap too.

I've used this since my domain registrar name.com has it free and built in to their control panel but it can be setup manually too. You just add suitable DNS records to point to gmail servers (once signed up).

---

