---
title: "Moving over to Ubunt? Help please"
date: 2007-11-26
forum: Testimonials &amp; Experiences
---

### Post by philmossuk on 2007-11-26
Hi, be gentle with me; this is my first ever post.

I've recently started working with an environmental charity who are to put it mildy..poor as church mice. They have about 30 very old pc (mine only has 128k RAM and is also a print server) running various forms of windows as clients (98 through to 2000) and everything driven by a windows NT server...aaaaaargh.

We are keen green environmentalists and  have a policy of only using old kit; a  pretty good policy given that we don't have any money. 

My instincts and some experience of working with education ICT non profits tell me that Linux would be better for us in terms of reliability and getting the best out of low spec old pc and servers. 

Our ICT support suppliers are kind people, but Microsoft neanderthal in their thinking e.g. I had to unilaterally load Firefox because they thought it might destroy the integrity of the network.

I want to make the case for Linux, so therefore your help appreciated

Questions:

1. Can I use ubuntu as a desktop system and connect fully to Win NT server, and if so any techniques for achieving this? I would like to use one pc as an example to our non techie people who are otherwise intimidated by our microsoft techie undead.

2. Anyone experienced in Microoft to Ubuntu server migrate who can give me a rudimentary (ball park) cost for transfering 30 pc and the usual servers and storage, and point me in the direction of any white papers or other docs that can give me a simpletons understanding of the issues involves?

As I said at the beggining we're pretty poor, but committed and in the end it's your environment as well.  

Thanks for you time...

Check out our web site [www.wildsheffield.com](www.wildsheffield.com)

philmossuk

---

### Post by azimuth on 2007-11-26
Time to do some reading. A good place to start is the results of a Google search for "thin client ubuntu". This may give you some ideas where to start.

---

### Post by Sqwishy on 2007-11-26
> **philmossuk said:**
> 
They have about 30 very old pc (mine only has 128k RAM and is also a print server) running various forms of windows...

I'm going to pretend you said 128MB of RAM because i'm pretty sure you can't run windows on 128kb :S

> **philmossuk said:**
> 
Our ICT support suppliers are kind people, but Microsoft neanderthal in their thinking e.g. I had to unilaterally load Firefox because they thought it might destroy the integrity of the network.
 o.0 eek!

> **philmossuk said:**
> 
1. Can I use ubuntu as a desktop system and connect fully to Win NT server, and if so any techniques for achieving this? I would like to use one pc as an example to our non techie people who are otherwise intimidated by our microsoft techie undead.

How do you mean connect? Like if your Win NT server is just a webserver then ubuntu can use http to "connect" to the winbox, if it's hosting files ubuntu can use samba to transfer files to/from the winbox. However, I've heard that some windows computers -perticularly server edition- will try to "take over the network" as the Domain Controller and it'll mess up ubuntu if it's trying to host files with samba. I'm not quite sure how that works though :S

It all sorta depends on what your dealing with, do you want to use ubuntu to log on to a Winblows Server Domain network thingy? ...With samba when you try to access a folder on a network you might get asked to login cause of permissions, and at that point you can specify your username and password and domain, and I've tried it at school and it works like an ordinary windows login but limited only to browsing the network. At least I think I know what I'm talking about.

---

### Post by philmossuk on 2007-11-26
mea culpa...of course Mb. Tho I didn't even think that 128mb would do it. twas a shock that such still existed. I have loads of spare RAM at home but our tech service suppliers would require the threat of serious hurt being applied to them for them to let me fit it.

I'm seeing this in two stages....the first is a machine that can do some basic stuff, run something like Open Office,  access printers and internet. I simply want to make people realise that there is a world outside of Microsoft...the second phase is moving the whole system over to Ubuntu/Linux. Thanks for the Samba tip.

---

### Post by azimuth on 2007-11-26
Phil, For one machine to try out, just install Xubuntu. 128MB is within it's specs. It has a GUI and many preloaded programs. You'll have fun with it and it is so much nicer than win98.

---

### Post by Sqwishy on 2007-11-26
Yeah you should have a minimum of 320MB of ram i think if your trying to install ordinary Ubuntu with gnome. Xubuntu, in case you didn't know, is the same thing as Ubuntu but with a different desktop enviroment designed to be faster and use less RAM. Setting up a printer should be pretty easy from Ubuntu to a windows shared, and I was gonna give a few tips but I'm not sure how Xubuntu's GUI is layed out exactly so I can't >.<

---

