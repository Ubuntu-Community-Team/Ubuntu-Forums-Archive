---
title: "Ubuntu 6.06.1 LAMP server"
date: 2006-10-16
forum: Server Platforms
---

### Post by londonhelper on 2006-10-16
Hey all:
This noob is needing a little advice.

I love Ubuntu so though I would stick with it on this one - but need some advice on configuring it.
Here are my objectives. 
I have got a domain name and want to host a mail server, webserver, ftp server etc on this domain name at home on my broadband line.

I ideally want to receive email and have a web interface to the email as well - [email]anymailsentto@mynewdomain.com[/email]
any mail that is not in the userlist will end up in the postmast box and the rest to the actual set up users. the users can access their email say at webmail.mynewdomain.com

ftp.mynewdmain.com will work and have user accounts as well.

I am having difficulty getting my head around Bind and dnsing for this site - here are the details on the server end.

internal ip - 192.168.1.10 - external ip - 87.245.69.85 (for eg) all ports for 8080, 23,21,25 etc etc - pointing to 192.168.1.10

My confusion is setting up hostname and dns on the server as well as the domain control panel - what do i need to set -
I would like the server to be called server1 for eg. so the whole name is server1.mydomain.com
as for the ip address's and dns records I get well confused - could anyone point me in the right direction - I will be willing to give any information needed as i would really like to learn these things - Once i have it all working I will then see HOW it works and be able to do it again later.

eventually I want to take it a few more steps futher and have either 2 different domains pointing to the same server but different webpages. Or have my wife have a webpage on a subdomain like mywife.mynewdomain.com and she has her webpage there. and my main one on [www.mynewdomain.com](www.mynewdomain.com)

Any help will be much appreciated.
ta

---

### Post by londonhelper on 2006-10-17
Anybody out there? Any advice on dns and the steps I need to take at the Domain end - router end and server end?
please help
thanks

---

### Post by londonhelper on 2006-10-18
Well I have been all over - read all there is about DNS and bind - Read Howto forums etc - but still seem to be stumbling on something - but cant put my finger on it.

Here are my objectives but not sure if i am taking things further than i need and would really appreciate some help.

I have got a 123-reg domain - mywebspace.co.uk (here i am allowed to change everything on dns, nameservers, A records CNAME's etc.

I have a Ubuntu -server installation on my personal home machine (running at the moment as a virtual machine Until i get things right)

I have pointed my domain name to the external (static) Ip address of my router - 888.888.888.888 (for eg)
I have configure my router to forward ports on 8080, 80, 23, 21, 110, 10000 etc etc to the internal ip address (static)  192.168.1.10

My true intentions are : to have multiple webpages under my domain name : like - me.mywebspace.co.uk and mymate.mywebspace.co.uk and once i have email set up for [email]EVERYTHING@mywebspace.co.uk[/email] to goto a web login at say webmail.mywebspace.co.uk . (obviosly will have all the mail stuff set up according to the howtoforge guid on 6.06 perfect setup)

Now I am not sure if i need it but I looked and attempted to use ISPconfig but this seems to confuse me more.

The front end to it all - I would love to use the Joomla system (as i know how to ue it for a single web system) but not sure what i need to do to manage more than one webpage.

What is getting to me the most is DNS and nameservers etc. I have tried so many different things - but not sure how involved i need to be with the configs.

Do i need to have my own nameserver? ns.mywebspace.co.uk and configure the control panel at 123-reg to point my name server to this ns.mywebspace.co.uk and the (external or internal) ip address of it?

when i edit the /etv/hosts file - server1.mywebspace.co.uk - do i use 192.168.1.10 or the external ip address of my router?

do i need to edit or creater /etc/resolv.conf ? what do i need to put in there?

If i need to create a nameserver - what should i do? (they mention 2 name server are needed) but i have one server - what do i point to as the second server?

If i want to create a subdomain - webmail.mywebspace.co.uk - how do i go about doing it?

Once this has been fully explained and installed and working - It will then be able to look into it to understand it better.

Any help will be muchly apreciated -
cheers

---

### Post by tomBorgia on 2006-10-18
"eventually I want to take it a few more steps futher and have either 2 different domains pointing to the same server but different webpages. Or have my wife have a webpage on a subdomain like mywife.mynewdomain.com and she has her webpage there. and my main one on www.mynewdomain.com"

Not too sure about this mate but you could look into the virtualhost bits of apache... it seems you can direct various 'alias's to different subdirs of /var/www... 

Your DNS hosting (123-reg) will need to point ftp.mynedomain.com to youripaddress:21 and I suspect any other things such as mywife.mydomain.com would need to point to youripaddress/mywife (then using the virutal hosts bit of apache point it somewhere else... or just put the site in /var/www/mywife... )

As I understand it its the nameserver that points to your IP address, not the other way around "I have pointed my domain name to the external (static) Ip address of my router - 888.888.888.888 (for eg)" so this should work! do you get your webpage if you connect to your domainname?

---

### Post by sitedesign on 2006-11-25
Just to confuse you a little bit.

YOU WILL NOT BE ABLE TO SEE THE WEB SITES FROM INSIDE THE BRAODBAND NETWORK AT HOME. Not without extra configuration. This is because when you request [www.mydomain.com](www.mydomain.com) it goes out through your broadband connection to the internet then tries to come back again (head up butt job).

In 123-reg you would create an ´A´ record which points to your broadband public IP (go to whatsmyip.org to find) that IP must be static (never changes even if your braodband reconnects). Call the ´A´ record ´homenet´ then you can set the www and * and wife and any more host names to have a ´CNAME´ to ´homenet´.
Next you need to set the ´MX´ record (only one, delete the extra) pointing to ´homenet.domainname.com.´ NOTICE THE DOT AT THE END! That points it to an absolute name, you can just put homenet then it would be for the currently configured domain, but causes problems when configuring other domain names to point to the same mail server.

Hope that helps getting the domain set-up. Next you need to set-up your LAMP services.

Openwebmail is nice for the web based email system.

---

