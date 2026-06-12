---
title: "school webserver help"
date: 2010-03-30
forum: Server Platforms
---

### Post by adgators89 on 2010-03-30
I was told to start a  new thread with one of my posts,so here it is... I would like to add a web server to our existing school server(which is windows 2003 - but 5 years old). I would like to use a seperate computer to do this.  The specs for that computer are -  a regular desktop 2.8ghz intel core2 - 2mb ram with 160gb hard drive. Is this adequate to be a webserver and if possible a mail server as well? This way I can eliminate the fees that we pay to a hosting company for the mail and site hosting that we currently use. I would dedicate this computer to doing these tasks only so that it is not affected by other tasks. Does anyone have any ideas on how I can do this? I saw the LAMP install, is that what I need to do? and if so, how do I use my assigned internal ip address to configure the webserver?

---

### Post by Sporkman on 2010-03-31
> **adgators89 said:**
> I was told to start a  new thread with one of my posts,so here it is... I would like to add a web server to our existing school server(which is windows 2003 - but 5 years old). I would like to use a seperate computer to do this.  The specs for that computer are -  a regular desktop 2.8ghz intel core2 - 2mb ram with 160gb hard drive. Is this adequate to be a webserver and if possible a mail server as well? This way I can eliminate the fees that we pay to a hosting company for the mail and site hosting that we currently use. I would dedicate this computer to doing these tasks only so that it is not affected by other tasks. Does anyone have any ideas on how I can do this? I saw the LAMP install, is that what I need to do? and if so, how do I use my assigned internal ip address to configure the webserver?

The computer you describe is definitely more than adequate for web & mail serving (I assume you mean 2gb of RAM instead of 2mb..?).

Yes - do a LAMP install of ubuntu server, then configure your router to send port 80 tcp traffic to that server (identified by its IP address).

---

### Post by Iowan on 2010-03-31
Hopefully not off-topic - and mostly curiosity: Will your web server be Intranet (local only) or do you plan to expose it to the Internet?

---

### Post by new_tolinux on 2010-03-31
> **adgators89 said:**
> This way I can eliminate the fees that we pay to a hosting company for the mail and site hosting that we currently use.
I guess paying the fees is as cheap/expensive as it is to run a computer 24/7.
Then I'm not even talking about all the time you're going to spent on it (upgrade/other maintenance) and that I'm assuming that the hosting company has a little more experience when it's about securing their servers.
> **Sporkman said:**
> The computer you describe is definitely more than adequate for web & mail serving (I assume you mean 2gb of RAM instead of 2mb..?).
I agree. Even a single core P4 with about 1GB should probably do.

---

### Post by adgators89 on 2010-03-31
Well I guess it would cost more to run, if I have my own lamp server, but the school file server runs 24/7, so I'm sure one more computer running 24/7 isn't that much of a deal.  right now they pay over $3000 for their web and mail server - so anything is cheaper than that. - I figured I would look like a superhero if I ran our own LAMP server compared to that price :)  

I would need this to reach out to the internet.

and yes, I did mean 2gb not 2mb  ha ha

If anyone has any configuration help on how to get it going I would appreciate it

---

### Post by volkswagner on 2010-04-01
[How to forge]("http://www.howtoforge.com/howtos/linux/ubuntu") has many great how-to's.  Look into Citadel and Zimbra for your mail solution for an easy setup with full features on you mail server.

Some advanced research may be in order.  Things to verify before jumping in:
[LIST]
[*]Does your school isp allow you to run a web server and is port 80 blocked or not?
[*]Does your isp provide you with enough bandwidth for the expected traffic?  You'll need good **upload** speeds.
[*]What features will you mail users require or currently using?
[*]Have you considered using Virtual Machines for each, web and mail server?
[/LIST]

---

### Post by adgators89 on 2010-04-01
Some advanced research may be in order. Things to verify before jumping in:

Does your school isp allow you to run a web server and is port 80 blocked or not?
Does your isp provide you with enough bandwidth for the expected traffic? You'll need good upload speeds.
What features will you mail users require or currently using?
Have you considered using Virtual Machines for each, web and mail server?


I'm not sure about the school isp allowing me to run a webserver _ I will be the school tech coordinator next year, so I should have all the access that I want

I do have the bandwidth available

Mail users here just simply require to recieve, read, and send mail.  Have folder options and forwarding serveces.  I would also like to be able to archive the mail if possible

I'm not familiar with virtual machines for each.  I would love to know more about them though! :)  - anyone up for informing me - please do so

---

### Post by adgators89 on 2010-04-01
Yes - do a LAMP install of ubuntu server, then configure your router to send port 80 tcp traffic to that server (identified by its IP address).


can you explain to me how to configure the router to send port 80 tcp traffic to the server?  I am new at this and don't have server knowledge, but a quick learner and willing to keep trying until I get it done :)

---

### Post by new_tolinux on 2010-04-01
That does depend on what router you are using.
Without brand & type (in case of a hardware router) there is no "simple" answer.

---

### Post by Sporkman on 2010-04-01
> **adgators89 said:**
> can you explain to me how to configure the router to send port 80 tcp traffic to the server?  I am new at this and don't have server knowledge, but a quick learner and willing to keep trying until I get it done :)

A lot of consumer home-use routers have a web interface that you can access to configure the router - it's usually on a local IP address like 192.168.0.1, 192.168.1.1, etc. To know for sure, read the instructions that came with the router, or look them up on the internet for that specific make & model of router.

Once you get into the web interface, you can navigate to a section called for example "port forwarding rules" or "firewall settings" or something to that effect. In there, it will let you add rules like "send all tcp port 80 traffic to such-n-such ip address".

---

### Post by adgators89 on 2010-04-01
ok, that sounds good, I'm going to check that out later tonight

---

