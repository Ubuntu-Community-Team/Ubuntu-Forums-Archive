---
title: "ISPConfig, thoughts,opinions &amp; problems"
date: 2012-06-19
forum: Server Platforms
---

### Post by poolet on 2012-06-19
Ok, This is my last chance to be able to fixed the problem with my server.... I have several post on different kinds of forums and they are not able to fixed my problem..... So hopefully you have an idea of what's going on and give me some hints that may help me to continue..

First of all, am running dual cpu's xeon with 16GB of ram and CentOS 6.2 64bit..

I have already success build a lot of things on server such as:: 
ISPconfig, nginx web server, Postfix mail server, MySQL, phpmyadmin, BIND nameserver, PureFTPd, SpamAssassin, ClamAV, Mailman, and many more....
I have also a UPS that can handle a possible power off of 5-8 min the server and the router.. Now, what am asking is if there is any way on the server, when gets the notification from UPS that it should shutting down in conjunction with router to re-forward my DNS nameserver back in the default domain/hostname of my website.com... The purpose of this is when the power is off (probably one day will off am not a company or some kind of organisation to handle that )  the server & router will re-forward the DNS (registrars) back to the domain, so website will running proper without any problem until the power is back.. 

Until now I have conclude that I **must** have a backup of database users.. For example if some client register into the website mysql will store the details in 2 different database but with the same records and tables.. e.g: one save on the server and one domain... The problem here is what?? 

Even if it's possible to re-forward that what's going on when the the power is on ?? the users that may register at the time that the power is off will not be have access on website since fail2ban will ban ip address of user and locked out since they will not get the ssl/tls certificate..... 

To be more clear of what am asking is:: 
1st is anyway to re-forward the registrars back into domain of hostname?? 
if the answer is yes..
2nd what about the users that register into the site when the site runs outside of server?? basically on the domain/hostname of the company that I will bought ???? Is any possibility fail2ban to ban the ip address?? 

It took me 24 hours of work to build a lot of process on server and I have already banned myself by the ssl key for another 24 hours to see if it's works.. Fortunately is was works because if it wasn't then I must format the whole partitions of ext4 since quota will block the root so my only permission  on server was on read only, in addition, if am right and my conclusion are correct, then I will have serious problem on any user included me since the key will not successful confirm..

---

