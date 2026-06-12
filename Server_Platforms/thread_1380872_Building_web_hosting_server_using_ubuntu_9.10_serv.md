---
title: "Building web hosting server using ubuntu 9.10 server edtion at home"
date: 2010-01-14
forum: Server Platforms
---

### Post by programming.name on 2010-01-14
Hi.

Before I can actually build my webserver with ubuntu server 9.10, I want to see a big picture of the process of building a web server. I can implement a web page using XHTML/CSS, JavaScript, FLASH, PHP and so on, but I have no idea how to creat a web hosting server at home. 

First of all, 
**Question 1:** What do I need to prepare in order to build a web server with ubuntu 9.10 server edtion at home? 

So far, I have

**-** **FTTH cable installed** (IP address not static),

**- ipTIME G304 router**, 

**- one (wired) desktop computer with ubuntu 9.10 server edition installed**,  <- I am going to use this PC only for the server.

*** **one (wireless) desktop (Windows), 
*** **one (wired) laptop (Windows), 
*** **one (wireless) laptop (Windows) 

Note: I guess the last 3 asterisked computers are not significant, but in case it matters, I just stated. Also note that all computers above are accessing the Internet through the ipTIME G304 router both wired and wireless.[B]

- Domain [/B]purchased from a domain company and with 
**Master DNS Address**(ns.xxxxx.xxx) and **Secondary DNS Address(**(ns1.xxxxx.xxx)provided by the company (x indicates a specific character)

What else do I need more? 


**Question 2:** If it is needed to configure the router what would it be?

**Question 3:** My IP address is not static and I heard even if the IP address is dynamic it still works fine as a sever. I also heard some chages are needed as a difeerent IP address is assigned for my computer. Although I think it might be a bit frustrated, I will go with this. Becuase I'm not familliar with ubuntu server yet and don't have much knowledge about networking. Anyway could you tell me how to do this please?

**Question 4:** What do I do with the DNS addresses provided by the domain company?

As far as I know DNS stands for Domain Name Server and this is a role of chaging IPs to domain names like ubuntuforum.org so we can remember easliy. For instance, if I enter [http://abcdefg.com](http://abcdefg.com) in Firefox then the DNS looks for the ns.xxxx.xxx and if the IP associated to abcdefg.com is found then it returns the page to the browser.

Do I need to modify to another or just leave as it was?


**Question 5:** Please illustate about the process of the building web hosting server globally. I mean just like this:

1. get  internet connection, ubuntu 9.10 server edition installed on desktop. 
2. configure router about this and that.
                                     .
                                     .
                                     .

Sorry for asking so many questions and thanks.

---

### Post by neoanderthal on 2010-01-14
first and foremost, you're either going to need a static IP address, a DNS registrar that supports dynamic DNS, of you'll have to update your DNS entries by hand every time your IP address changes. The distributed database that DNS uses needs to have the current IP address for your server in order to direct queries for [www.yourdomain.com](www.yourdomain.com) to [www.xxx.yyy.zzz](www.xxx.yyy.zzz), which is your IP address.

second, presuming your router has some sort of firewall, you'll need to map your ports on the firewall to your internal server. port 80 at the very least - if you're using SSL you'll need 443, plus any custom ports you want to have service directed to.

There are a number of HOWTOs that illustrate in excruciating detail what is needed to set up a webserver on Ubuntu.

---

### Post by Iowan on 2010-01-14
[Links]("http://ubuntuforums.org/showpost.php?p=8599983&postcount=3") to a couple of Dynamic DNS suppliers.

---

