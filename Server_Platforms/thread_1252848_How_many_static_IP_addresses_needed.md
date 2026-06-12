---
title: "How many static IP addresses needed"
date: 2009-08-29
forum: Server Platforms
---

### Post by Strictly on 2009-08-29
Hi

I would really appreciate some questions that will probably sound stupid but I'm pretty confused at the moment.
 
 I currently use a web host company for three websites. All three use MySQL and PHP but for a number of reasons I want to host them on a server that I control. I am in the process of changing my ISP to a provider that will give a static IP but since starting, I have since read somewhere that I should have two DNS severs and each will require its own static IP in addition to the static IP for the web server.  
 
 My questions are:
 
 Does 'bind 9' provide all that I require for DNS servers?
 Do I really need three static IP's?
 Can everything be contained within the same computer?
 
 Thanks. The more I read the more confused I become.

S

---

### Post by hessiess on 2009-08-29
> **Strictly said:**
> Hi

I would really appreciate some questions that will probably sound stupid but I'm pretty confused at the moment.
 
 I currently use a web host company for three websites. All three use MySQL and PHP but for a number of reasons I want to host them on a server that I control. I am in the process of changing my ISP to a provider that will give a static IP but since starting, I have since read somewhere that I should have two DNS severs and each will require its own static IP in addition to the static IP for the web server.  
 
 My questions are:
 
 Does 'bind 9' provide all that I require for DNS servers?
 Do I really need three static IP's?
 Can everything be contained within the same computer?
 
 Thanks. The more I read the more confused I become.

S

You need to buy domain names from a domain name registrar, running a DNS server locally will only make the domain names valid within your local network as external clients have no idea your DNS server exists. Listen to sccurty now episode 155 for a overview of how DNS works: [http://www.grc.com/securitynow.htm](http://www.grc.com/securitynow.htm).


You only need ONE IP adress, and then set up Apache with name-based virtual hosts for all of the sites. The only reason why you would need one IP per site is if you were using TLS(SSL) encryption for all 3 sites, as this dousent work with name-based vhosting. Howeaver this is unlickly unless you are doing E-commerce from all 3.

You will need to read up on server security, as you seam to be unexperianced with server configuration it is quite lickly that you will end up with a server that is less sccure than your web hosting provider.

And yes, you can easely have everything on one physical server.

---

### Post by Strictly on 2009-08-29
Thanks H for your reply I much appreciate it and I gratefully accept your advice concerning security.
 
 I already have the Domain names (.co.uk) and have been using them for a couple of years now. I assumed it is a simple matter of informing Nominet when I start using the new server.
 
 The server is working with MySQL, apache and PHP and can see the outside world from behind a simple Netgear router which I do not believe can be configured to allow incoming server requests and will need to be replaced.
 
 It will be at least a month before I have the fixed IP in place and when it is I will install Bind 9. In the meantime I will follow your advice and research the security issues
 
 Thanks again - S

---

### Post by wojox on 2009-08-29
You need to configure port forwarding on your Netgear router for incoming requests.

---

### Post by hessiess on 2009-08-29
You already have the domain names, all you need to do is update them to point to your static IP. Running a DNS server is unsesoserry.

---

### Post by phantasmik on 2009-08-29
Forward port 80 (default) on your router. then point your domain to your static IP address.

---

### Post by DGortze380 on 2009-08-30
> **Strictly said:**
>  behind a simple Netgear router which I do not believe can be 

I really suggest ditching the home router for a Small Business Class Device from Cisco or the like. Though Netgear is good, if you handling any real traffic load it will likely overheat and lock up fairly often. (at least that's been my experience).

---

### Post by Strictly on 2009-08-30
[SIZE=2]This is an amazing forum.[/SIZE]
 [SIZE=2]Thanks for all of the help and advice. It is really appreciated. I am currently wading through episode 155, as suggested by hessiess, to try and start understanding DNS and the related security issues. Actually, unless I'm missing something, the principals seem quite simple. You can be sure that I will come back and ask further questions.[/SIZE]
 
 [SIZE=2]Thanks for the tip on the router. I have found how I can configure the port forwarding on my Netgear WGR614v7 and it appears to work. If it can be used securely, I don't believe it will be overworked because my websites rarely receive more than 100 page requests per day.[/SIZE]
 
 [SIZE=2]Thanks again everyone.[/SIZE]
 [SIZE=2]S[/SIZE]

---

