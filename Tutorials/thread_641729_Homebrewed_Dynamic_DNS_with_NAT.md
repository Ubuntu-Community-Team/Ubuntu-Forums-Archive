---
title: "Homebrewed Dynamic DNS with NAT"
date: 2007-12-15
forum: Tutorials
---

### Post by MrFSL on 2007-12-15
****EDIT**** - bad news, the people over at angelfire have notified me that using their site in this respect is somehow in violation of their user agreement :( -- I will leave this thread here though, as a proof of concept. It can be modified to suit another free web service.

***_The Situation_***
You are trying to run a service like a web server from your home but your ISP does not give you a static IP address. You have heard of services like [http://www.no-ip.com/](http://www.no-ip.com/) and [https://www.dyndns.com/](https://www.dyndns.com/) but you want to use your own domain name and you aren't interested in paying a yearly fee. This little howto will show you how to build your own. It will dynamically update your IP and also send you email notifications and more.

***_The Solution_***
You can use free services to build your own Dynamic DNS service. Specifically, you can sign up for a couple free accounts and build a perl script that runs using cron that does all the work for you. (It sounds complex but really it is simple.)

***_Howto_***
**Step One: Buy a Domain Name**
There are a few different Domain Registrars that exist out on the world wide web. I don't promote one over another. I personally use GoDaddy ([http://www.godaddy.com/](http://www.godaddy.com/)). This howto is not exclusive to GoDaddy though. It should work with any registrar.

**Step Two: Set Nameservers**
Using the tools provided by your registrar update your nameservers to point to everydns.net . In GoDaddy it looks like this:
[IMG]http://www.frontiernet.net/~hwdiminished/dns.png[/IMG]
A list of nameservers can be found at: [http://www.everydns.net/](http://www.everydns.net/)

**Step Three: Register and Setup at EveryDNS**
Go to [http://www.everydns.net/](http://www.everydns.net/) and sign up for a free account. Sign in and add your new Domain Name as a dynamic domain:
[IMG]http://frontiernet.net/~hwdiminished/AddDomain.png[/IMG]

You can check out this link: [http://www.everydns.net/dynamic.php](http://www.everydns.net/dynamic.php) to download some free clients to help keep your DNS records up to date. The problem is that these tools do not help you if you are on a NAT network. The rest of this howto involves us building the script that will allow us to update from behind a NAT.

**Step Four: Register At Angelfire**
Angelfire ([http://angelfire.com](http://angelfire.com)) is a free web hosting service. We are going to use it for some free webspace. **_When registering for an angelfire account make sure that your username and password are the same as they were for EveryDNS!_**

**Step Five: Get Dependencies And Edit Script**
Here I will go over the update script section by section. Feel free to update the code if you don't like it. Attached will be the final product.

First we set some get all out dependencies:
```
sudo apt-get install libwww-perl libnet-smtpauth-perl libnet-ip-perl libnet-dns-perl 
```
Next download the attached script: fsl.IPUpdate.pl


These will be the only things you need to edit in the script:
> 
$username = 	"**username**";
$password = 	"**password**";
$domain_name =	"**NewDomainName.com**";
$smtp_server = 	"**YourSMTPServer.com**";
$to = 		'**YourEmailUsername@YourEmail.com**';
$from = 	"**SERVER@NewDomainName.com**';

*username* should be the username you used to setup BOTH angelfire and everydns.

*password* should be the password you used to setup BOTH angelfire and everydns.

*NewDomainName.com* should be the Domain Name you registered in step one.

*YourSMTPServer.com*] should by your mail server. This is so the script can send you email notifications. Odds are your ISP supplies you with an SMTP server you can use.

*YourEmailUsername@YourEmail.com* should be your valid email address where you want notifications sent.

*SERVER@NewDomainName.com* can be any email address you would like. It does not really matter if it is valid or not. This email address will show up as the sender in your email notifications. You can set this the same as above if you would like.

**Step Six: Schedule The Script To Run**
I suggest using gnome-schedule for ease of scheduling. If it is not installed:
```
sudo apt-get install gnome-schedule
```

Thats it! Your Homebrew Dynamic DNS should now update your IP address records, send you email notifications, and as an added bonus create an angelfire page to redirect you while the DNS updates are propagating.

Hope this helps someone.

---

### Post by semaiyen on 2012-05-03
Sorry for pushing this old topic UP. I found it in google and will give it a try

---

