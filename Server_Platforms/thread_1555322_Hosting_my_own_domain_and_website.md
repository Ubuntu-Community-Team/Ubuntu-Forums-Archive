---
title: "Hosting my own domain and website"
date: 2010-08-17
forum: Server Platforms
---

### Post by physic.dude on 2010-08-17
I'm looking toward making and hosting a website AND domain of my own. I don't need it to hold up to many users. I will be using my standard home Internet (AT&T U-Verse) witch is pretty reliable and fast. I have a few modern and up to date computers I can use for the server.

I just have a few questions before I start. 

-How can I host both a domain and a website. (Point me to a simple guide.)
-How this?
-How that?
-How?
-What program(s) should I use to build my web pages (simple web pages with text, links, and graphics)
-Will it cost a VERY VERY DRAMATIC loss in bandwidth in my home network?


I don't have much experience in this exact subject, some, but not much.
I do have a "Networking |All-In-One Desk Reference| For Dummies" book if it helps. ("ISBN: 978-0-470-17915-4")

---

### Post by bodhi.zazen on 2010-08-18
For the cost you are almost always better off with a VPS.

Next, check with your ip provider, some may have space you can use or will give you space for personal web pages. Others may block port 80 ...

To register a domain name, use a service such as godaddy, there are several options.

Install a server @ home, install apache, forward port 80, update your public IP on your Domain name.

To make web pages learn html, css, javascript, php, mysql, etc. Probably start with html and css, tons of online guides.

You can start with a WYSIWYG editor, but I prefer bluefish.

Good luck

---

### Post by graphius on 2010-08-19
i run my website off a ubuntu server at home. Some of the advantages are relatively unlimited storage space (I can buy hard drives cheaper than buying online storage) full control of my system, and of course it is a great way to learn about linux.

For my domain name, I just got a free redirect from [dyndns.com]("http://dyndns.com")
(one of these days I will get a "real" domain name...)
For hardware I just have an old P4 with 2 GB ram and 500 GB storage in a raid
For a website, I would recommend one of the many open-source CMS such as Drupal or Joomla. Since I am a photographer, I went with Gallery2 as most suitable to my needs. 
I agree that you still need to learn a bit of html, css, etc to customize your site.

I originally started my server project to see how cheaply I could put up a website. My original cost was $0 including an old donated computer, and about a month of my spare time learning how to make it all work. Since then I have put a few dollars into new hard drives, and I replaced the older tower with a "newer" discarded machine.

If you want to tinker, set up a server. If you just want a website, it is probably easier to go with a hosting company.

PS, my [website]("http://klughammer.dnsalias.com")

---

### Post by Litachao on 2010-08-19
I agree with the previous poster that a VPS might be the most cost-effective solution. You'll use up a lot of electricity when running your own server 24/7, so you should check how much you'll pay per watt/hr ([http://michaelbluejay.com/electricity/computers.html](http://michaelbluejay.com/electricity/computers.html)). You may also have to one-time invest into hardware. 
You can rent a VPS with root access for 15-20$/month, which might be much cheaper (often with a free domain included).

---

### Post by MakOwner on 2010-08-19
Hosting your own domain at the end of your home connection isn't too terribly hard, but you probably want to look into getting at least a business level ISP account.  Some of the larger ISPs are starting to block inbound ports on "personal" accounts to force you into the more expensive business accounts.  The up side of that is you at least get to deal with next level support when troubleshooting network issues.  Sometimes :twisted:

Here's a list of things to get you started:

Set up a firewall to connect to your ISP.  
 
I use IPcop, but to each his own. it works well 
    for low user/low traffic stuff on old hardware.
    Spend some time learning about networking, firewalls, port 
    forwarding and DMZ as that will be critical for you, 
    especially on a home ISP connection.

Set up a server inside your network.  

    I use the Ubuntu minimal CD and do a LAMP install.
    Learn all the odds and ends about running the server
    inside your network and getting traffic to it in the DMZ.

Get your domain.

    Registrar of your choice.

Point your domain to your IP address.

    If you have a business account it's probably static, but if you
    want to do this from a home account there are dynamic DNS services
    out there.  EveryDNS comes to mind, but google is your buddy.


Those are some of the high level steps and there are a billion details I missed. :popcorn:

---

### Post by plusnplus on 2010-08-20
> **bodhi.zazen said:**
> For the cost you are almost always better off with a VPS.

Next, check with your ip provider, some may have space you can use or will give you space for personal web pages. Others may block port 80 ...

To register a domain name, use a service such as godaddy, there are several options.

Install a server @ home, install apache, forward port 80, update your public IP on your Domain name.

To make web pages learn html, css, javascript, php, mysql, etc. Probably start with html and css, tons of online guides.

You can start with a WYSIWYG editor, but I prefer bluefish.

Good luck

Hi..,
can you share more detail, how to :
"forward port 80, update your public IP on your Domain name"?

---

### Post by plusnplus on 2010-08-23
Hi..,
can someone share, how to :
"forward port 80, update your public IP on your Domain name"?

or the easy way to make ubuntu live with static ip ?

---

### Post by jaya28inside on 2010-08-23
> **plusnplus said:**
> Hi..,
can someone share, how to :
"forward port 80, update your public IP on your Domain name"?

or the easy way to make ubuntu live with static ip ?

When we said Forward port 80 it means 'opened by browser.'
Okay, let's think this...

you have a single pc. 
and it's connected through internet,
and your ip was... dynamic. it was 192.168.1.90 (just example)
and then... you install Apache or Tomcat Server.

Don't you know HTML Files opened by Browser? You know of course.

Okay, so then another way to compose HTML files are using 
another language, such as PHP, or JSP (this just example from may other things).

if you use PHP means you could choose Apache.
if you use JSP means you could choose TomCat.

These Web Server or I called it container (Apache or Tomcat)
would deliver the output to any user who access those files 
via browser.

If you just using HTML, thus, no need any Web Server to 
deliver the output. 

Okay, continued...
So, you do have managed yourself making a file either PHP or JSP
and it's located on your PC. on that 192.168.1.90

at the time any user outside 
want to access your file
through their web browser 
of course it would be like this 
at their address bar:

> 
[http://192.168.1.90/yourWebFile.php](http://192.168.1.90/yourWebFile.php)

or 

[http://192.168.1.90/yourWebFile.jsp](http://192.168.1.90/yourWebFile.jsp)


And the result (output) would be presented in the user browser
and would be handled first 
by the WebServer,
and then passed to the user browser.

Those, Tomcat or Apache would usually choose Port 80 as 
your Pc's door to be shown at the user browser.
If we don't choose port 80,
let's say... it's 8080.
thus at the address bar of that user would be like this;


> 
[http://192.168.1.90:8080/yourWebFile.php](http://192.168.1.90:8080/yourWebFile.php)

or 

[http://192.168.1.90:8080/yourWebFile.jsp](http://192.168.1.90:8080/yourWebFile.jsp)


okay?
:lolflag: hope u got it. 

--forgive me for my bad english.

---

### Post by snek on 2010-08-23
You can run

```
sudo tasksel
```Then select LAMP.
It will install apache,php and mysql on your machine.

Then download & install wordpress if you want the easiest to use simple blogging system.
[http://wordpress.org/](http://wordpress.org/)

Bandwidth all depends on how many images etc you use on the website.
My blog current only transfers about 30KB per page-load.
[http://www.robotsystematic.com](http://www.robotsystematic.com)
It uses a very low-bandwidth theme which relies mostly on CSS and not so many images.

---

### Post by plusnplus on 2010-08-23
Hi jaya28inside,

thanks for your time to help me.
after read your explanation, it still make me not clear for some issue.
to make it simple here is my situation:
i have ubuntu 10.4, with LAMP installed. it is working good in lan condition.
now how i can access it from outside my lan.
after i subscribe static ip from service provider, set my router, then what is the next step ? just like that? or my apache/ ubuntu need to do some setting?

i will only subscribe static ip, without any domain name. so how i configure this static ip to my ubuntu?

For static ip setting in router, is not a problem. i can make it ready/ online and ready to surf net :)

---

### Post by BkkBonanza on 2010-08-24
@plusnplus
It's not nice to hijack a thread like this. If you have a question you should post your own thread and not take over another user's question. 

Now, answering your question... that last answer was a bunch of mis-information. You need to login to your router and set the "port forwarding" options so that port 80 on your router is forward to the LAN IP of your server (also port 80 usually). This will make sure that connections to port 80 from the internet get sent thru to your server (otherwise your router would normally drop them).

The exact way you set this port forwarding is different for different routers. So if you can't figure that out then google your router make/model # with the words "port forwarding" and usually a guide can be found. Or read the manual.

---

### Post by snek on 2010-08-25
Just a quick reply from my phone.. Check this site for more port forwarding help, it's great for ppl new to the subject: [http://portforward.com/](http://portforward.com/)

---

