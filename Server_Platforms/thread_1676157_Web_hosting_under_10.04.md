---
title: "Web hosting under 10.04"
date: 2011-01-26
forum: Server Platforms
---

### Post by dieselpwr4life on 2011-01-26
I've decided to start a new project/second business.  Namely, I want to create my own website hosting/design service and I need to know where to start.  I've been reading up on some topics related to this, but as far as implementing my idea, I still have some questions.  Should note here that previously, my only experience with hosting was putting a page up for a friend via godaddy.com....
 
I've gotten my hands on a Poweredge 6800, 4 processors 2.8 gHz, (currently) 4 73 gb u320 hard drives.  I know that I want to run a RAID setup that allows for redundancy (not sure if I should just set up the 4 drives as 2 disks with mirroring or not).  I also for the forseeable future will have to run everything off of one server.  With the server came Windows Server 2003 disks and license.
 
From what I've seen/read, it seems a LAMP server would be the way to go.  My main question is this: Since I am running everything off of one server for now, am I right in thinking that Ubuntu Server would be the better way to go for ease of use, and reduced resource usage?  Also, is it simpler to use a static IP address from my ISP or the dynamic IP addresses they give you?  The final question is this: while I like the idea of H-sphere, are there better all in one hosting apps/control panels that don't have as high a learning curve/hardware requirements?
 
Any other suggestions, links, FAQs are greatly appreciated.  Also want to apologize in advance if I missed postings where this was already covered.
 
Thanks in advance guys.

---

### Post by gordintoronto on 2011-01-26
Ubuntu Server is a good choice, until a potential client demands that you support a Microsoft technology. (I have a friend who has an immense web site using Microsoft Front Page...) Your computer is fine until a client loads up his site with videos. If the business takes off, you can deal with those issues.

Static IP is the right answer. Dynamic IP can be made to work, but it's a kludge that will eventually break. Do your ISP's Terms of Service allow you to host web sites? Some ISPs have punitive pricing for web site hosting.

Some people like Kompozer for simple web site development. If you're making an online brochure, it's fine.

---

### Post by sh1ny on 2011-01-27
For a control panel i'd recommend ISPConfig 3. It's good and it works :D My hosting is entirely on 10.04 and i've yet to encounter any problems related to the OS itself ( excluding human errors :D ).

---

### Post by dieselpwr4life on 2011-01-27
Thanks for the replies, I was thinking of using ISPconfig3, but was hoping to find something all in one - even if I had to pay a little bit for it.  Though it seems that most of the CPs that offer this, usually require redhat, centOS.  I've used Ubuntu before as a workstation and loved it immensely.
 
Hopefully I can grow to the point of needing more than a couple servers and using Microsoft to attract more customers.  Though I doubt that it will happen in the short term.  If they do, I am probably not that well equipped hardware wise to meet their needs.  Besides, I love free!  :P
 
I have Comcast here at my house and when I talked to the rep, I specifically told him what I was going to use their business class service for.  I know Comcast isn't the best, but I couldn't get a hold of ATT at all for 4 days to talk to them about their services.  For the price right now, I can't really justify spending the couple hundred per month to get a dedicated line.  Though if I can manage to get ahold of 7-10 clients, I should be able to justify the expense.
 
I've heard some back and forth about the different ftp programs to use, sftp, proftp (pureftp, can't remember which), etc.  Is there truely one better than the other as far as security, or are they about the same?

---

### Post by abhinavkumar940 on 2011-01-27
You can also give WebMin a try. Its free & comes bundled with a huge list of add ons including the proxy, email etc.

Best of luck using Ubuntu! :)

---

### Post by BQAggie2006 on 2011-01-27
Not quite sure what you mean by "all in one", but this is a pretty good tutorial for getting ISPConfig 3 set up and running on Ubuntu Server 10.04 LTS:

[http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3)

As far as FTP servers, the above tutorial suggests using PureFTPd, but I myself am a vsftpd fan as it's pretty easy to set up and configure, and is recommended in the Ubuntu Server Guide: [https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html).

---

### Post by dieselpwr4life on 2011-01-27
By all in one, I was referring to being able to invoice/bill right from the control panel.  Kind of like CPanel or H-sphere, where there is an accounting feature built in to the panel itself.
 
I'll probably just use ISPConfig and make sure that I am closely monitoring who's paid up and who's behind.

---

### Post by James78 on 2011-01-27
Not to sound like I'm one upping anyone here, but I really recommend Webmin over ISPConfig. I've used both, and ISPConfig doesn't really have much features like Webmin does. Webmin has a ton of features for mostly everything, it's really handy, and you can create advanced setups with it. It's ultimately up to you, but I want you to know about what you're missing. In the end, I'd suggest you try both of them out, that way you'll be able to use the one you end up liking (it's best to be informed; since you may spend a lot of wasted time in ISPConfig and find out you like Webmin more, or even vise versa). Virtualmachine time. ;)

P.S. [http://ubuntuforums.org/showthread.php?t=1197883](http://ubuntuforums.org/showthread.php?t=1197883)

---

### Post by amish_geek on 2011-01-27
If you're going to be hosting websites for others as a business, then please take your business seriously and do not use a cable or DSL connection.

If you want to use your own server that you bought, there are plenty of colocation proivders that you can use for about the same price as a commercial cable connection.  Then you'll get a solid internet connection with proper SLA's to guarantee network uptime.


H-Sphere is a good control panel.  I had a 16 server H-Sphere cluster several years ago which was primarily powered by FreeBSD.  Unfortunately, H-sphere was sold to swsoft which is now Parallels (who also owns Plesk/Ensim and a bunch of other hosting control panels).  They buy up control panels and then stop developing them, forcing hosts to switch to their flagship panel, Plesk.


CPanel and DirectAdmin are really your only two choices for running a web hosting BUSINESS.  You're going to want a billing solution like modernbill or WHMCS.   ISPConfig and Webmin are merely tools for managing users, and services on a server, and are not designed to be web hosting control panels for customers.  They can be used that way, but they were not designed for that purpose.


I advise checking out [www.webhostingtalk.com](www.webhostingtalk.com) and asking in the "running a web hosting business" section.


If you really want to start a hosting business, I would strongly recommend starting out on a reseller account with another host, and growing your customer base before jumping in with both feet on a full fledged server.  If you're just looking to host your own websites, and perhaps a couple for some friends, then by all means, use ISPConfig or webmin.  But if you set up shop and expect your average internet user to sign up for your service and pay you money, please take it seriously and do things the right way.  There are enough people out there already who set up shop as a hobby and leave honest paying customers out to dry when their hobby gets old and they disappear.


Remember, when running a hosting company, you are:
- Hosting Websites with Apache
- Hosting Databases with MySQL and/or Postgresql
- Hosting Email (you're going to need a mail server)
- Eternally fighting spam (your mailserver is going to be a spam magnet, since all of your customers have email addresses and sign up for stupid mailing lists etc)
- Hosting DNS
- Maintaining and security a control panel
- Dealing with customers/users who have a plethora of different sites, wants, needs, and desires.

Any one of those services (web,mail,mysql,control panel,etc) can bring your server to its knees, especially when you have customers who install things like drupal and wordpress, and then get lucky and are listed on the frontpage of Digg.

---

### Post by James78 on 2011-01-28
> **amish_geek said:**
> If you're going to be hosting websites for others as a business, then please take your business seriously and do not use a cable or DSL connection.

If you want to use your own server that you bought, there are plenty of colocation proivders that you can use for about the same price as a commercial cable connection.  Then you'll get a solid internet connection with proper SLA's to guarantee network uptime.


H-Sphere is a good control panel.  I had a 16 server H-Sphere cluster several years ago which was primarily powered by FreeBSD.  Unfortunately, H-sphere was sold to swsoft which is now Parallels (who also owns Plesk/Ensim and a bunch of other hosting control panels).  They buy up control panels and then stop developing them, forcing hosts to switch to their flagship panel, Plesk.


CPanel and DirectAdmin are really your only two choices for running a web hosting BUSINESS.  You're going to want a billing solution like modernbill or WHMCS.   **ISPConfig and Webmin are merely tools for managing users, and services on a server, and are not designed to be web hosting control panels for customers.  They can be used that way, but they were not designed for that purpose.**


I advise checking out [www.webhostingtalk.com](www.webhostingtalk.com) and asking in the "running a web hosting business" section.


If you really want to start a hosting business, I would strongly recommend starting out on a reseller account with another host, and growing your customer base before jumping in with both feet on a full fledged server.  If you're just looking to host your own websites, and perhaps a couple for some friends, then by all means, use ISPConfig or webmin.  But if you set up shop and expect your average internet user to sign up for your service and pay you money, please take it seriously and do things the right way.  There are enough people out there already who set up shop as a hobby and leave honest paying customers out to dry when their hobby gets old and they disappear.


Remember, when running a hosting company, you are:
- Hosting Websites with Apache
- Hosting Databases with MySQL and/or Postgresql
- Hosting Email (you're going to need a mail server)
- Eternally fighting spam (your mailserver is going to be a spam magnet, since all of your customers have email addresses and sign up for stupid mailing lists etc)
- Hosting DNS
- Maintaining and security a control panel
- Dealing with customers/users who have a plethora of different sites, wants, needs, and desires.

Any one of those services (web,mail,mysql,control panel,etc) can bring your server to its knees, especially when you have customers who install things like drupal and wordpress, and then get lucky and are listed on the frontpage of Digg.
There's no doubt about that. Webmin is definitely more of a tool for managing things. But were you also including Virtualmin in that argument? Because Virtualmin is more of the one for the customers. I've used it and have 0 complaints, especially for the free price.

And ya, I completely agree with you about making a hobby while it's fun, then leaving your customers out when it gets old. That's just not right.

---

### Post by sh1ny on 2011-01-28
> **amish_geek said:**
> If you're going to be hosting websites for others as a business, then please take your business seriously and do not use a cable or DSL connection.

If you want to use your own server that you bought, there are plenty of colocation proivders that you can use for about the same price as a commercial cable connection.  Then you'll get a solid internet connection with proper SLA's to guarantee network uptime.


H-Sphere is a good control panel.  I had a 16 server H-Sphere cluster several years ago which was primarily powered by FreeBSD.  Unfortunately, H-sphere was sold to swsoft which is now Parallels (who also owns Plesk/Ensim and a bunch of other hosting control panels).  They buy up control panels and then stop developing them, forcing hosts to switch to their flagship panel, Plesk.


CPanel and DirectAdmin are really your only two choices for running a web hosting BUSINESS.  You're going to want a billing solution like modernbill or WHMCS.   ISPConfig and Webmin are merely tools for managing users, and services on a server, and are not designed to be web hosting control panels for customers.  They can be used that way, but they were not designed for that purpose.


I advise checking out [www.webhostingtalk.com](www.webhostingtalk.com) and asking in the "running a web hosting business" section.


If you really want to start a hosting business, I would strongly recommend starting out on a reseller account with another host, and growing your customer base before jumping in with both feet on a full fledged server.  If you're just looking to host your own websites, and perhaps a couple for some friends, then by all means, use ISPConfig or webmin.  But if you set up shop and expect your average internet user to sign up for your service and pay you money, please take it seriously and do things the right way.  There are enough people out there already who set up shop as a hobby and leave honest paying customers out to dry when their hobby gets old and they disappear.


Remember, when running a hosting company, you are:
- Hosting Websites with Apache
- Hosting Databases with MySQL and/or Postgresql
- Hosting Email (you're going to need a mail server)
- Eternally fighting spam (your mailserver is going to be a spam magnet, since all of your customers have email addresses and sign up for stupid mailing lists etc)
- Hosting DNS
- Maintaining and security a control panel
- Dealing with customers/users who have a plethora of different sites, wants, needs, and desires.

Any one of those services (web,mail,mysql,control panel,etc) can bring your server to its knees, especially when you have customers who install things like drupal and wordpress, and then get lucky and are listed on the frontpage of Digg.

Sorry to burst your bubble, but ISPConfig IS designed for web hosting for BUSINESS. Just because it's not paid, doesn't mean it can't handle it.

You are right about the billing part tho -> i would not go with something less than WHMCS, HostBill or something of the sorts. Also because no open source solution exists for managing virtual servers, my personal choice was SolusVM.

But back on topic - ispconfig handles web hosting just fine, i strongly urge you to take a look ( a deeper one ) at it. Webmin IS a tool for managing services, but ISPConfig is made to handle web hosting from the start.

P.S. There's also a recent release of a plugin that connects WHMCS < - > ISPConfig, making it damn easy to connect it to your billing service. Look at the WHMCS forums for more info.

---

### Post by dieselpwr4life on 2011-01-28
> **amish_geek said:**
> If you're going to be hosting websites for others as a business, then please take your business seriously and do not use a cable or DSL connection.
 
If you want to use your own server that you bought, there are plenty of colocation proivders that you can use for about the same price as a commercial cable connection. Then you'll get a solid internet connection with proper SLA's to guarantee network uptime.
 
 
H-Sphere is a good control panel. I had a 16 server H-Sphere cluster several years ago which was primarily powered by FreeBSD. Unfortunately, H-sphere was sold to swsoft which is now Parallels (who also owns Plesk/Ensim and a bunch of other hosting control panels). They buy up control panels and then stop developing them, forcing hosts to switch to their flagship panel, Plesk.
 
 
CPanel and DirectAdmin are really your only two choices for running a web hosting BUSINESS. You're going to want a billing solution like modernbill or WHMCS. ISPConfig and Webmin are merely tools for managing users, and services on a server, and are not designed to be web hosting control panels for customers. They can be used that way, but they were not designed for that purpose.
 
 
I advise checking out [www.webhostingtalk.com]("http://www.webhostingtalk.com") and asking in the "running a web hosting business" section.
 
 
If you really want to start a hosting business, I would strongly recommend starting out on a reseller account with another host, and growing your customer base before jumping in with both feet on a full fledged server. If you're just looking to host your own websites, and perhaps a couple for some friends, then by all means, use ISPConfig or webmin. But if you set up shop and expect your average internet user to sign up for your service and pay you money, please take it seriously and do things the right way. There are enough people out there already who set up shop as a hobby and leave honest paying customers out to dry when their hobby gets old and they disappear.
 
 
Remember, when running a hosting company, you are:
- Hosting Websites with Apache
- Hosting Databases with MySQL and/or Postgresql
- Hosting Email (you're going to need a mail server)
- Eternally fighting spam (your mailserver is going to be a spam magnet, since all of your customers have email addresses and sign up for stupid mailing lists etc)
- Hosting DNS
- Maintaining and security a control panel
- Dealing with customers/users who have a plethora of different sites, wants, needs, and desires.
 
Any one of those services (web,mail,mysql,control panel,etc) can bring your server to its knees, especially when you have customers who install things like drupal and wordpress, and then get lucky and are listed on the frontpage of Digg.
 
Thanks for the insight, and I completely understand what you're getting across here.  I don't intend to leave people hanging high and dry, its not the way I work.  I'm trying to get myself slowly out from under another business venture that I am in right now, and would like to have something to dive right into after the fact.  As far as customers, I will not actively pursue any for at least a little while, as I need to learn more about this.  I know cable is not the best alternative to a dedicated line, such as T1 or above, but the way I am starting things up (my fiance's parents site) will keep me plenty busy during my learning period.  Once I'm past this point, yes I intend to invest in several other servers, and a "real" hosting line and location of my own.  
 
Thanks again for everything guys. :P

---

### Post by acc61287 on 2011-09-23
I want to host my own website using ISPConfig 3, I already installed ISPConfig 3 in Ubuntu 10.04. Then I have static ip address, then I'm using joomla in creating website.

How I host my website?? I'm really noob in web hosting :(

---

### Post by Rahul Kulkarni on 2011-09-29
Please read tutorials on setting up a LAMP server. 

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

If I am not wrong you are not yet running apache. Without Apache you can't host a website. To have a full fledged server you need the complete LAMP (**L**inux **A**pache **M**ySQL **P**HP) package.

---

### Post by Jonathan L on 2011-09-29
> **dieselpwr4life said:**
> I've decided to start a new project/second business.  Namely, I want to create my own website hosting/design service and I need to know where to start.  I've been reading up on some topics related to this, but as far as implementing my idea, I still have some questions.  Should note here that previously, my only experience with hosting was putting a page up for a friend via godaddy.com....
 
I've gotten my hands on a Poweredge 6800, 4 processors 2.8 gHz, (currently) 4 73 gb u320 hard drives.  I know that I want to run a RAID setup that allows for redundancy (not sure if I should just set up the 4 drives as 2 disks with mirroring or not).  I also for the forseeable future will have to run everything off of one server.  With the server came Windows Server 2003 disks and license.
 
From what I've seen/read, it seems a LAMP server would be the way to go.  My main question is this: Since I am running everything off of one server for now, am I right in thinking that Ubuntu Server would be the better way to go for ease of use, and reduced resource usage?  Also, is it simpler to use a static IP address from my ISP or the dynamic IP addresses they give you?  The final question is this: while I like the idea of H-sphere, are there better all in one hosting apps/control panels that don't have as high a learning curve/hardware requirements?
 
Any other suggestions, links, FAQs are greatly appreciated.  Also want to apologize in advance if I missed postings where this was already covered.
 
Thanks in advance guys.

Dear Diesel

On the hardware platform and scalability issue, I'd really recommend you take a good look at both Amazon Web Services and Canonical's cloud offer (and indeed the others too).  Both are fabulous in various ways.

But the ability to completely outsource your physical environment to such enormous players is a huge advantage.  For example: what would you do if you had a major power cut?  Or needed lots more CPU for a given client?  Or lots more disk space for a given client?   I use AWS for my client-facing things and have found it really excellent.  The main thing about AWS is that everything is priced in very small increments, typically about USD 0.10, so you scale everything to the right size.  I run web servers on the cheapest CPU at about USD 0.02/hour and image renders on the biggest at USD 2.00/hour.  The biggest advantage I'd say though is the ability to experiment: if you want to do some major change you can replicate everything easily, install your new changes, and test them without any risk to the running production systems.  That gets very expensive if you do it with real hardware.

On the downside, if you haven't planned for a problem, when it comes it can be big.  I was affected by the recent lightning strike and fire at Amazon's facility in Ireland; my smaller systems without good replication were taken out.  The good news is how well Amazon provided backup images of my running systems; the bad news is it took them three days.  It has to be said, if I was running my own equipment it would have been much worse: for example, how long would it take your ISP to move your static IP addresses to a new site if you needed them to?  Moral: replicate across availability zones and/or continents, because it's so easy.  Definitely my architecture was the culprit here.

Ask yourself this question: which is better for your business, you spending time learning how to manage your own facility and using your own capital on hardware, or spending time talking with clients and giving them better service?  What do you do about cashflow when you find yourself needing more or newer equipment?  A micropriced cloud infrastructure turns your equipment into a variable cost in your business, taking out the fixed costs of installed plant and the capital costs of new plant.

Having been responsible in the past for about 100 servers spread across continents, it's pretty difficult to imagine how I would do it now without using someone's cloud offer, and I wouldn't even consider using my own servers for a small business.

On software: I switched all my client things to Ubuntu for two reasons: 1) The long-term support versions, 2) so I could run identical things in the cloud and on private servers if required (it does happen occasionally!)  And indeed on laptops.  So I'd recommend running 10.04 LTS at the time being, with review of 12.04 LTS when it comes out; and run it across everything so you don't get surprises.

Anyways, just some thoughts on that topic which I hope are helpful to you.

Kind regards,
Jonathan.


_Links_

Building your own cloud with Ubuntu: [https://help.ubuntu.com/community/UEC](https://help.ubuntu.com/community/UEC)
 
Amazon

[LIST]
[*]General  [https://aws.amazon.com/ec2/](https://aws.amazon.com/ec2/)
[*]Pricing: [https://aws.amazon.com/ec2/pricing/](https://aws.amazon.com/ec2/pricing/)
[*]note free tier for experiments/training
[/LIST]
  Canonical

[LIST]
[*]General [http://www.ubuntu.com/business/cloud/deploy-anywhere](http://www.ubuntu.com/business/cloud/deploy-anywhere)
[*] pricing: [http://www.ubuntu.com/business/services/cloud](http://www.ubuntu.com/business/services/cloud)
[*] free service for experiments: [https://10.cloud.ubuntu.com/](https://10.cloud.ubuntu.com/)
[/LIST]
  They aren't the only game in town of course: here's more.

[LIST]
[*] Rackspace Cloud services: [http://www.rackspace.com/cloud/](http://www.rackspace.com/cloud/)
[*] Red Hat Cloud: [http://www.redhat.com/solutions/cloud/](http://www.redhat.com/solutions/cloud/)
[*]The excellent (but mysterious): [http://www.johncompanies.com/](http://www.johncompanies.com/)
[/LIST]

---

### Post by ingramproductions on 2012-10-22
This might help some of you. Here are the top 10 open-source web hosting panels:

[http://itswapshop.com/reviews/top-10-free-and-open-source-web-hosting-control-panels-linux-or-windows-demos]("http://itswapshop.com/reviews/top-10-free-and-open-source-web-hosting-control-panels-linux-or-windows-demos")

It has a feature comparison chart also

---

