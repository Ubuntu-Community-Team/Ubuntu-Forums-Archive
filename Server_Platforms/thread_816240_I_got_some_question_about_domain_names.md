---
title: "I got some question about domain names"
date: 2008-06-02
forum: Server Platforms
---

### Post by serverCrazy on 2008-06-02
hi, 

i built a server which will serve web applications, such as, email, web sites, ftp, etc. I will be using ISPconfig as my control panel. However, i dont understand one thing. In order to have a email server will need the MX and A record, but i am not sure where i need this records. Is it on my internet connection or on my domain?

if i buy a domain on godady.com, will it come with this records? which will enable my self to set up my server.

thanks very much, it is a silly question, but i could not find noone who could respond me this doubt.

---

### Post by dmond on 2008-06-02
im not familiar with godaddy.com, but normally, when you buy a domain from a registrar, you'll be given the option to add / edit the DNS entries for your mx and a records to point to a static IP.

---

### Post by serverCrazy on 2008-06-02
so that mean that the records are a domain settigns that can be edited and modified.

There is any how to become a registrar?

---

### Post by windependence on 2008-06-02
> **serverCrazy said:**
> so that mean that the records are a domain settigns that can be edited and modified.

There is any how to become a registrar?

GoDaddy would be your registrar. You will get a domain control panel where you can do all that you need to set up your domain. Also, their phone support is free and very good. Get the guys on the line and get them to walk you through it and explain it to you, it's not that hard.

-Tim

---

### Post by molotov00 on 2008-06-02
> **windependence said:**
> GoDaddy would be your registrar. You will get a domain control panel where you can do all that you need to set up your domain. Also, their phone support is free and very good. Get the guys on the line and get them to walk you through it and explain it to you, it's not that hard.

-Tim

I've used Godaddy before and can confir m that you can edit the MX and A records.

One thing I HATE about godaddy is their customer support though. Their basic fees are cheap, but additions are expensive and the only free customer service is over email, which can take up to 24 hours per response. Sometime they are idiots and it takes more than a few emails to resolve an issue, so that takes days. They don't have a 1-800 number.

---

### Post by serverCrazy on 2008-06-02
thanks for the replies. I really understood about the records and i can not become a registrar because it is quite expensive, about $2,500. And you have to proof  a lot of stuff.

Anyway, sorry for the silly questions.

Now the only thing i need to decide is the name of my businness, which will be hosting service.

Thanks

---

### Post by windependence on 2008-06-03
> **molotov00 said:**
> I've used Godaddy before and can confir m that you can edit the MX and A records.

One thing I HATE about godaddy is their customer support though. Their basic fees are cheap, but additions are expensive and the only free customer service is over email, which can take up to 24 hours per response. Sometime they are idiots and it takes more than a few emails to resolve an issue, so that takes days. They don't have a 1-800 number.

Sorry but I have to disagree. Sure, they don't have toll free numbers but who needs them when most cell phone long distance is free nowadays? And they DO have free phone support. I have had real good luck with them and I own 18 domains. i have never used their e-mail support though, no need if I can just call them even at 2 am.

-Tim

---

### Post by windependence on 2008-06-03
> **serverCrazy said:**
> thanks for the replies. I really understood about the records and i can not become a registrar because it is quite expensive, about $2,500. And you have to proof  a lot of stuff.

Anyway, sorry for the silly questions.

Now the only thing i need to decide is the name of my businness, which will be hosting service.

Thanks

Don't take this the wrong way but if you are going to run a hosting service, you really need to know this stuff inside and out. Run a few servers on your own first and get your feet wet until you are comfortable. Also, do you have redundant power? Redundant connections? Backup servers and extra parts like cooling fans? When a server breaks at 3 am on a Saturday you need to be able to fix it or get running on a backup server. People tend to get just a little pissed if their site is down. I run several of my own sites and I have spent over $5,000 just getting the things in place I have mentioned. Do a little more research before you jump in with both feet on this.

-Tim

---

### Post by rickyjones on 2008-06-03
> **windependence said:**
> Sorry but I have to disagree. Sure, they don't have toll free numbers but who needs them when most cell phone long distance is free nowadays? And they DO have free phone support. I have had real good luck with them and I own 18 domains. i have never used their e-mail support though, no need if I can just call them even at 2 am.

-Tim

I am in total agreement with you. I've been with Godaddy for several years now and I have no complaints. They even call me when I purchase a new product to ensure that everything was nice and smooth on my end. 

I can confirm that their email support is superb. Usually I get a response in only a few hours and the issue is usually resolved immediately.

Thanks,
Richard

---

### Post by serverCrazy on 2008-06-03
ok, windependence, i really understood your point, however i am ready to do those steps. I have 6 servers. Im going into research about back-ups and how to set up all the servers together. However, is quite difficult to find some help in these area or someone that is willing to spend some time explaining me few things. As result, getting wet is not a problem for me, as long i have my aspirin and my paracetamol with me all the time.

Dont forget that nobody born knowing everything in life. Everybody need to learn and keeping improving. So that would be my learning stage. In addition, will be a free hosting services for a limited numbers of users and for my clients (I also pretend to open a Web development businness).

Also, i dont expect to get right in the first place, however this would be a experience through out my IT carier and maybe, Who knows?, if everything goes right, it can grow.

What i am doing right now is, setting up the main server where the control panel (ISPconfig) will be installed (only 1 server).

If you can give me some advice on these things. And first i need to have a domain name to test the server and see if is working or not.

So, What do you think? please be honest.

---

### Post by arvevans on 2008-06-03
If one is new to server setup and administration, and wants to play first before investing large amount of time and/or money, you might want to look into one of the IP Address Re-direction Services, such as <http://www.dyndns.com> (there are many more...just do a Google search for them).  Most of these services are free, and only charge if you want to add more advanced features.

An IP Address Re-director Service will let you pick from their already registered group of domain names, and then re-direct incoming http (or other port mapped traffic) to your local server.  This way your server domain name might be something like "ServerCrazy.homelinux.net", where "homelinux.net" is owned by the re-direction service and browser calls to ServerCrazy.homelinux.net would be re-directed to your actual server on your real IP Address.

There are a number of tools such as "ddclient" that can be run on your local server to keep the Re-direction Service advised of your present IP address.  This is handy in case you are using DSL or other ISP access that frequently changes your IP address.

Arv
_._

---

### Post by dmond on 2008-06-04
> **serverCrazy said:**
> Dont forget that nobody born knowing everything in life. Everybody need to learn and keeping improving. So that would be my learning stage. In addition, will be a free hosting services for a limited numbers of users and for my clients (I also pretend to open a Web development businness).

Also, i dont expect to get right in the first place, however this would be a experience through out my IT carier and maybe, Who knows?, if everything goes right, it can grow.

What i am doing right now is, setting up the main server where the control panel (ISPconfig) will be installed (only 1 server).

If you can give me some advice on these things. And first i need to have a domain name to test the server and see if is working or not.

So, What do you think? please be honest.

Ubuntu is an ethic or humanist philosophy focusing on people's allegiances and relations with each other. -wikipedia
We are all here to learn and improve ourselves. No one person knows everything, sharing ideas and knowledge (even saying a kind words of encouragement) with others is why, i think, ubuntu is very successful and popular.

since you're determine to start a web hosting/development company, i strongly suggest you buy a domain from a registrar. do not be afraid to lose money when it comes to business, just charge it to experience and you can also justify it as money used for research and development stage.


> **windependence said:**
> Don't take this the wrong way but if you are going to run a hosting service, you really need to know this stuff inside and out. Run a few servers on your own first and get your feet wet until you are comfortable. Also, do you have redundant power? Redundant connections? Backup servers and extra parts like cooling fans? When a server breaks at 3 am on a Saturday you need to be able to fix it or get running on a backup server. People tend to get just a little pissed if their site is down. I run several of my own sites and I have spent over $5,000 just getting the things in place I have mentioned. Do a little more research before you jump in with both feet on this.

-Tim

i agree, based on my experience, having angry customers call you up is no picnic. but what i think he's trying to say is that researching and marketing your product cannot be done at the same time. marketing should be done after having a 99.9999% reliability service, having less percentage is a disaster, customers are bound to leave you or maybe worst, bad mouth your company to others which is a bad way to start your business.


> **serverCrazy said:**
> ok, windependence, i really understood your point, however i am ready to do those steps. I have 6 servers. Im going into research about back-ups and how to set up all the servers together. However, is quite difficult to find some help in these area or someone that is willing to spend some time explaining me few things. As result, getting wet is not a problem for me, as long i have my aspirin and my paracetamol with me all the time.

just state your specific questions in the forum, someone will answer it. and also, you could always search the forum boards, im sure someone has encountered the same problem you're having. but based on your replies, i suggest you start off with the common softwares like (apache, mysql, drupal, postfix, dovecot, squirrelmail or horde) because there are tons of reference over the net. i have bookmarked plenty of it, tell me if you need help finding some.

pls update me on your research on back-ups, i may need it also due to the fact that i manually back-up some of my files and config. i want to reduce my human-reliability and human-errors. hahaha. :)

---

### Post by windependence on 2008-06-04
Yes, basically what I am saying is you bit off a big bite to digest and you should spend a month or so learning and researching things about what you are going to do. It's a LOT of information to learn in a short period of time.

Look for single points of failure on your setup. If one power supply goes out do you have another one to take over for it? Do you have dual nics in all your boxes and are they all configured to failover. 

I would set up two boxes exactly the same and put two load balancers in front of them. That way, if one box goes down the load balancer will direct all traffic to the other box. Two load balancers are necessary in case one fails. One way to cut operating costs is to use virtualization. On my own netowrk I have two very powerful boxes (daul quad core, 12 gigs RAM) and the host 3 servers each. Less power consumption that way and less space, fewer things that can break.

Like dmond said, ask here and we will help you.

-Tim

---

### Post by serverCrazy on 2008-06-04
ok guys,

first of all, thanks for spending your time with this matter.
Second, i will take your advice and i will start a 3 months research, where i will design, develop and implement my system. However it may not be completed within this time, but at least i will try. Thanks very much for all your advices.

Last thing, any more advices?

What i have in mind is create the main server, where it will hold 2 virtual servers, which will be the load balance (cited by windepence), managing the incoming queries and spliting between 2 others server.

however, im not sure about one thing!! Do i have to make 1 master and the other slave. Because how 2 different servers have the same information?

After that, i will research security, reliability (may need your help on testing it!), maintainability and so on...........

what Do you guys think?

---

