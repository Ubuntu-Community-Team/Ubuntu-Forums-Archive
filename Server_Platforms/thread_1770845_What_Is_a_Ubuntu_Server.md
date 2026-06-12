---
title: "What Is a Ubuntu Server ?"
date: 2011-05-29
forum: Server Platforms
---

### Post by josephmills on 2011-05-29
Hi there, First I would like to say thank you for taking the time to look at this, That being said. My buddy has a small business and I have been helping him out with his books. As of now I have been using google docs/calender/mail/voice to store all things that have been happening. I am running out of room with google and would like (I think) to use a server out of some of my older pc that I have laying around. I don't know if this is the right or wrong way of thinking about this. Because I have never done anything like this. So these are the things that I need to keep track off.
1) Tickets from customer recipes 
2) This is a landscaping company and he has a boat load of pictures that need to be scanned and filed. 
3) Work times. need to have a calender that says where and how long ect.
4) Resumes that come in off of craigslist and local newspapers 
5) He would like to have a website for the business.
6) And the books 

More Questions 
What are the advantages of having a server? 
What are the costs of having servers 
What is a Ubuntu Server? Is it like vmware? Where it works off of a Hypervisor ? 
Is a server a computer that I have at home, and can log into and also have others log into it too ? How do you upload things from one remote spot to the next? How much time a week do you think that this would take? 

Once again thanks for reading this and look forward to learning!

Joseph

---

### Post by arrrghhh on 2011-05-29
I'll try to answer your questions...

Ubuntu Server is a regular operating system - it has nothing to do with VMWare, but you certainly can run Ubuntu Server in a virtual machine if you choose to do so.

Most of what you mention seems to me like you just need a place to store files.  That is easily done with Ubuntu Server, and what you use kinda depends on who you're sharing files with - other Linux machines on a local network, I use NFS.  Windows clients on a local network, samba.  If you need to share files over the internet, using a VPN or SSH/SFTP are probably best, unless the users are always downloading the same files from the 'net - then you could just host with apache.

Which brings me to the next point, apache - if you want to host a website, look into this service.  If you have a connection that allows it you can certainly host a website off of the server - you'll have to pay for a domain name, unless you want to use a free Dyndns domain - if it's a business, he'll want his own domain.

As for a calendar.. there's ways to get calendar services onto your server, but wouldn't it be easier to just use the calendar built into gmail like you have been, I honestly think the calendar is more trouble than it's worth.

As far as cost, that's entirely up to you - how much storage space do you want, and if you want disk redundancy (to shield against data loss due to disk failure) then that will get more expensive.  You'll obviously want to backup any data as well, in addition to the RAID array.

So a lot of the cost aspects are up to you.  You might want to compare some hosted solution, in combination with a paid-for Google account - you wouldn't need to worry about data loss nearly as much, won't have to worry about hosting an account on a internet connection that doesn't allow it, etc.

---

### Post by Lars Noodén on 2011-05-30
> **josephmills said:**
> H
3) Work times. need to have a calender that says where and how long ect.


Here are some examples of groupware which include calendars.  It would be less work to continue with Google's calendar, though:

Kolab
    [http://www.kolab.org/](http://www.kolab.org/)
Citadel
    [http://www.citadel.org/](http://www.citadel.org/)
Dingo Calendar Server
    [http://andrew.triumf.ca/dingo/](http://andrew.triumf.ca/dingo/)
Bedework
    [http://www.bedework.org/](http://www.bedework.org/)
Zimbra
    [http://www.zimbra.com/](http://www.zimbra.com/)
OpenGroupware
    [http://www.opengroupware.org/](http://www.opengroupware.org/)

---

### Post by Lars Noodén on 2011-05-30
> **josephmills said:**
> 
1) Tickets from customer recipes

Do you mean tickets as in ticketing systems like RT and Trac?

Or do you mean managing receipts?  There is some client software that you don't need a server for:

GnuCash
[http://www.gnucash.org/](http://www.gnucash.org/)

Grisbi
[http://www.grisbi.org/](http://www.grisbi.org/)

KMyMoney
[http://kmymoney2.sourceforge.net/index2.html](http://kmymoney2.sourceforge.net/index2.html)

---

### Post by binkles on 2011-05-30
> Is a server a computer that I have at home, and can log into and also have others log into it too ?

It can be, but make sure your ISP allows hosting home servers, they probably block port 80.

Also you will need a pretty fast upload speed.

---

### Post by Lars Noodén on 2011-05-30
> **binkles said:**
> It can be, but make sure your ISP allows hosting home servers, they probably block port 80.
...

All that's needed is a single port that is not blocked, preferably 22, and then everything can be tunneled.

You can [check](http://www.canyouseeme.org/) with various online utilities to see which ports are blocked, if any.

---

### Post by josephmills on 2011-05-30
Wow you guys thanks for all the info! You guys rock! to get back to some of your questions 
> Do you mean tickets as in ticketing systems like RT and Trac?

Or do you mean managing receipts? There is some client software that you don't need a server for:
 

So he has this book that he keeps receipts in and also a book that he writes out the bill on and saves the yellow ticket behind it(records) dont know if that makes any sense. Then I take all of that scan it with my scanner and put it in with all the docs. It is a pain and I would like to figure something else out as somethimes there can be up to 50 receipts (gas,food,etc) and about 7 to 10 bills(yellow tickets ) here is a pic of a white part of the yellow ticket (kinda) [http://p.office1000.com/vp1/8L800RED.jpg](http://p.office1000.com/vp1/8L800RED.jpg)

> It can be, but make sure your ISP allows hosting home servers, they probably block port 80.
...
All that's needed is a single port that is not blocked, preferably 22, and then everything can be tunneled.

You can check with various online utilities to see which ports are blocked, if any.

how can I tell if my isp allows me to open up ports? just try it and see what happens? They are big old Jerks my isp so I like to stay away from them if possible. (cant wait until that contract is up) 

once again thanks 
Joseph

---

### Post by Lars Noodén on 2011-05-30
> **josephmills said:**
> 
how can I tell if my isp allows me to open up ports? just try it and see what happens? They are big old Jerks my isp so I like to stay away from them if possible. (cant wait until that contract is up)

Just look.  If it's open, it's open.  Also try this tool: [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

---

### Post by Lars Noodén on 2011-05-30
> **josephmills said:**
> 
So he has this book that he keeps receipts in and also a book that he writes out the bill on and saves the yellow ticket behind it(records) dont know if that makes any sense. Then I take all of that scan it with my scanner and put it in with all the docs. It is a pain and I would like to figure something else out as somethimes there can be up to 50 receipts (gas,food,etc) and about 7 to 10 bills(yellow tickets ) here is a pic of a white part of the yellow ticket (kinda) [http://p.office1000.com/vp1/8L800RED.jpg](http://p.office1000.com/vp1/8L800RED.jpg)




Ok.  Those are the kind that [url=http://www.gnucash.org/
]GnuCash[/url], [Grisbi](http://www.grisbi.org/) and [KMyMoney](http://kmymoney2.sourceforge.net/index2.html) are meant to replace: You do your work on them and then if you need a paper copy of the receipt (say for a customer) then you print it out.  

There are fancier ones like Pupesoft and OpenERP, too.  Simple, paper based solutions also have their place, though.

---

### Post by ryanrobinson on 2011-05-30
When it comes to hosting a website on your own equipment there is more risk to your server being attacked as it is exposed to the internet.

I would definitely recommend that you use a hosting service such as hosting24.com or do a Google search for other web hosting companies.

If you want to do everything properly, buy a decent server made by Dell or HP with RAID controllers. Get a good backup regime going with daily backups and offsite backups too.

---

### Post by josephmills on 2011-05-30
> **Lars Noodén said:**
> Just look.  If it's open, it's open.  Also try this tool: [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

do I have to open these ports with my router setting frist? and enable vnc and ssh and so on? by the way thanks for you help you rock. So I think that I am starting to get it. It is a headless keyboard-less computer but with a os that is made to stay on 24/7 and comes with certain things out of the box? What are those things ? Can I run a a linux server in virtual box? Just to test it out. To get to know more about what I am dealing with here.

---

### Post by Joe of loath on 2011-05-30
A server is a computer made to 'serve' content, whether it be web pages, data, or even something like internet radio.

You can run one in virtualbox to test stuff out indeed.

---

### Post by wlraider70 on 2011-05-30
> **josephmills said:**
> do I have to open these ports with my router setting frist? 

If you want to access them externally (from the internet) you need to use port forwarding on your router. If you want to use them internally (computers and phones connected to your router) there is no need to "open" them


To run a a linux server in virtual box Just to test it out is possible, but it might be more work then you need to. 

You can download a "live cd" that boots a version of linux that will run off the CD it makes NO cnanges to your system.

[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

---

### Post by spynappels on 2011-05-31
When you do a Server Edition install (and I strongly recommend the 10.04.02LTS version), you are asked to specify which services you want to install, such as LAMP server for serving static and dynamic webpages and content, SSH server to allow you remote access through the SSH protocol, Mail server functionality etc.

I recommend that you start off by installing only LAMP and SSH first, and get comfortable with those services. Then you can add services by running
```
sudo tasksel
```

If you take it one service at a time, it is a much less daunting prospect to get to grips with.

---

### Post by binkles on 2011-05-31
I have an old dell desktop that i use to test stuff out, its connected to my router and i ssh into it from my main PC.

---

### Post by jramshu on 2011-05-31
I have an Ubuntu Server set up at the house right now, up and broadcasting. If you read carefully on security you won't have any problems with hackers. There are plenty of ways to keep it secure.

If the machine you plan to use is an old spare, I suggest just install the server and tinker with it. The only way to learn it is hands on. Start checking out content management stuff to set up a site, unless you plan to hand code it own your own, and see which of those you like. Drupal isn't too terribly hard to handle, Joomla can be intimidating, but there are plenty of tutorials out there to help you get on your way. 

Then there are these forums.

---

### Post by binkles on 2011-05-31
[IMG]http://binklespup.co.cc/upload/images/48081209952676555701.jpg[/IMG]

[IMG]http://binklespup.co.cc/upload/images/47793216019329232163.jpg[/IMG]

---

### Post by Joe of loath on 2011-05-31
Eww, Ubuntu servers are ugly. My Debian one sits nice and neatly under my set of drawers. It even has a case! :lol:

---

### Post by JPorter on 2011-05-31
> **josephmills said:**
> 1) Tickets from customer recipes 
I assume you mean some type of documents, when you say "recipes"... I'm not familiar with that terminology. If it's a collection of files that you need to store, that can be done in a straightforward way on a file server in-house, or even on Google Docs, which it sounds like you have already.  Upgrade to Google Apps Premier if you need the additional space and functionality.  Premier costs $50 per user per year, and gives you 25GB of space in email as well as a number of other business-specific features.

> **josephmills said:**
> 2) This is a landscaping company and he has a boat load of pictures that need to be scanned and filed. 
Again, a file server would be great for that, but Google Docs wouldn't be. If some of the images are something that he wants to be able to organize and use online in a flexible way for marketing purposes, you can also look at leveraging Flickr or Smugmug for that in certain circumstances.

> **josephmills said:**
> 3) Work times. need to have a calender that says where and how long ect.
You have Google Calendar now...?

> **josephmills said:**
> 4) Resumes that come in off of craigslist and local newspapers 
You can put them on a file server or keep them on his own desktop.  Resumes are a very small space requirement.

> **josephmills said:**
> 5) He would like to have a website for the business.
Don't self-host a website unless you have the knowledge and IT resources to make that a permanent thing.  You're much better off buying a small hosting account with a shared hosting provider for that.  It's completely unrelated to your server in-house.

> **josephmills said:**
> 6) And the books
You need accounting or ERP software for that, again it's unrelated to the server except for the fact that it physically runs on a computer you own (possibly a server).  In a small business where multiple people need to access the books, you would do that with appropriate software loaded on a server, certainly... but if it's just one person (the owner or you) doing the books, you'd likely do the books directly on a desktop PC.

> **josephmills said:**
> More Questions 
What are the advantages of having a server?
A server is just a computer that provides networked services of some type to other computers.  It doesn't "do" anything by default, you have to have an application that uses a client-server model in order to have a need for the server in the first place.  Choose your application, then get a server if you need one to support that application.

> **josephmills said:**
> What are the costs of having servers 
It's a computer, you buy it just like any other computer, it's just a specific type of computer that's designed to be left on all the time. Software costs are additional, depending on the specific software that you want to run.

> **josephmills said:**
> What is a Ubuntu Server? Is it like vmware? Where it works off of a Hypervisor ?
Ubuntu Server is a server-specific version of Ubuntu, it can be run directly on the hardware or it can be installed into a virtual machine like VMware, KVM, etc.  That's not relevant at all to your environment, though.  Basically, it's just a server operating system.

> **josephmills said:**
> Is a server a computer that I have at home, and can log into and also have others log into it too ? How do you upload things from one remote spot to the next? How much time a week do you think that this would take? 
You can theoretically have a server at home, but if it's being used for business you probably wouldn't want to do that.  A home server is for home/personal use, like for music or media.  A business should own their own server, if they have a demonstrated need for one in-house.  If it's not in-house, like for a web site or other web-accessed software, it should be in a datacenter, not in *your* house.  That's what hosting providers are for.


It sounds like you need a local IT provider to assist you with this stuff.  The questions you are asking are huge red flags for future pain and suffering, both for you and for your friend.

---

### Post by josephmills on 2011-05-31
I would like to say thanks to all of you you are all a blessing! I would like to say that I am not mental and that I think that I can handle this. The real  reason I asked these questions is to see what and where other people might be doing or all ready done. You know  a nice way to do some Social engineering. I don't have a server right now and yes I have never had one before but you have to start somewhere. I would also like to say that in the winter time I do I.T work. For about 25 people and 5 to ten business. Yes I may not be the most knowledgeable person but I do have a boat load of references. Also I would like to stress that I am doing this thread more as a engineering kit then anything else. I know that there is always going to be more to learn. That is my plan I want to learn more and I want to see what others are doing. Also I have like 8 to ten extra computers sitting around and I thought I should put them to use. As far as security goes that is a learning curve that I am trying to handle I am really surprised that no one has said any thing about ipcop or pfsense or don't use this port or that port there are spiders out there that love those ports. Also nothing about openvas or other scanning  software. I could use nmap then openvas then Metasploit or fasttrack or gtkhash to gain access. And of course there are more tools that I know how to use (w3af, rkhunter, netrworkscanner, aircrack and the list goes on )I will do these tests myself. But would like to here more about your servers and what you are using in order to combat things like I mentioned above. Also please don't take this the wrong way I am a hacker not a cracker hackers make things while cracker break thing's. I am not looking to get into other peoples servers I just want to know what you use and how you came about using it. Ok now that my rant is over I would like to thank all of you again as I am learning somethings. I don't know everything and dont want to pretend like I do. I just really want to make my life a simple as possible 
>  We've got skyscraper
And it sings a pretty tune
Every band needs skyscraper too

What is a band without skyscraper
Ooh ooh skyscraper is grand

Sim-Bop & Be-Bophone
Sky-Balls & Sax-Scraper

---

### Post by binkles on 2011-06-01
> **josephmills said:**
>  Also I have like 8 to ten extra computers sitting around and I thought I should put them to use.


Thats what you should do, grab [ubuntu server]("http://www.ubuntu.com/download/server/download"), i'm still running 10.04, then install it on one, or more of your extra PCs and play around with it.

You'll need [putty]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/") to ssh into it.

You'll need a router obviously to connect the server too so its got internet access and is visible on the network in putty, as per my photo above.

---

### Post by jramshu on 2011-06-02
You want to know about how other people secure their home server. OK.

I have Ubuntu Server 10.10 on an old HP, AMD Athlon XP, 512RAM.
I used ufw to accept connections via ports 22 and 443.
I generated a self signed certificate for apache to use https.
Set Joomla to use https only for entire site.(Just because I could)

I installed DenyHosts to help slow down and blacklist unauthorized access attempts.

I generated keys to login via ssh.
I edited my /etc/ssh/sshd_conf file to this:
```
PasswordAuthentication no
RSAAuthentication yes
PubkeyAuthentication yes
```

I used NESSUS home edition and tested my server from outside my network.  The only thing it came back with was the security certificate not being  recognized by CA lists. It listed the two ports also.

Haven't had any problems yet.

---

### Post by Lars Noodén on 2011-06-02
> **jramshu said:**
> 
I used NESSUS home edition and tested my server from outside my network.  

(Nessus went closed source a while back.  What was left of the Free Software Nessus became [OpenVAS](http://www.openvas.org/).)

---

### Post by jramshu on 2011-06-02
> **Lars Noodén said:**
> (Nessus went closed source a while back.  What was left of the Free Software Nessus became [OpenVAS]("http://www.openvas.org/").)


Yeah, I read that when I got it. They still allow free use for home only. I removed it, since I would rather have open source. Been thinking about getting OpenVas. Just haven't done it yet.

---

