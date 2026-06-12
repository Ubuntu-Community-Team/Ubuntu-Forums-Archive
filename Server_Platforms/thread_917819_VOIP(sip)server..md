---
title: "VOIP(sip)server."
date: 2008-09-12
forum: Server Platforms
---

### Post by amai on 2008-09-12
VOIP(sip)server.
any guides, tips on settings up a home server for VOIP??

here is what I want to do

-Have a podcast and listeners/friends can call in using X-lite
-configure it so that I can give listeners/friends EXTs numbers
to be able to talk...

Any ideas on how to go about this!!

---

### Post by jamesb73 on 2008-09-12
I can't really help you with the podcasts / live streaming bit but I can help you out with the SIP server.

You probably want Asterisk.

The only issue is that there is quite a bit of understanding to do and configuring.

Asterisk do a liveCD version called AsteriskNOW which has a really good interface and sorts out all the configuration files.

There are a couple of packages that i've heard about floating around for the 1.2 branch but all my experience and running has been self-compiling the 1.4 branches and up.

Can you explain to me exactly what you want to do and I can think through the configuration and try and help you.

Start by downloading the sources for asterisk-1.4.x and zaptel-1.4.x

You may need the autobuild package (sudo apt-get install autobuild) to be able to build the application.

Regards
James

---

### Post by amai on 2008-09-13
Thanks Jamesb73..

In simple terms what I want to achieve is as follows..

-Have a SIP server where users have to register.
-After they register I will give them EXT numbers.
-Users can then call each other using EXT numbers which I will have supplied.
-Users can also call me and I can call users.

HOW user will get to know each other EXT
By PM(private message) each-other and ask one another there EXT number.

I want to have a bit of control on what will be taking place

---

### Post by ayllu on 2008-09-13
I usually use yahoo for make phone calls to movil phones and normal phones, but I want to use it in my ubuntu, you have any ideas to configurateit in some software for voip

---

### Post by erwall on 2008-09-13
> **amai said:**
> Thanks Jamesb73..

In simple terms what I want to achieve is as follows..

-Have a SIP server where users have to register.
-After they register I will give them EXT numbers.
-Users can then call each other using EXT numbers which I will have supplied.
-Users can also call me and I can call users.

HOW user will get to know each other EXT
By PM(private message) each-other and ask one another there EXT number.

I want to have a bit of control on what will be taking place

Check out [trixbox]("http://www.trixbox.com")

---

### Post by jamesb73 on 2008-09-15
Trixbox isn't a bad solution, i've not used it myself so i'm not sure if it's a full install of one product or you can overlay it onto an existing setup.

As far as your other questions, basically what you're doing is creating an office style phone system, you have to advertise by some means a directory of extension numbers.  You could do this with an intranet web page as a company directory if it's a case of publishing all parties numbers, if not then you'll have to figure out some way of advertising a partial directory to those that need it.

Most hardware and software phones have a directory download facility and with a bit of clever software coding you can get it to dish out a directory based on an extension number requesting it.

Hope this helps.

- James

---

### Post by maidei on 2008-09-17
y

---

### Post by amai on 2008-09-18
I am more looking for something hands on...
This is for educational purpose, so i need to be putting it together...

Just like putting/building a webserver

---

### Post by chrispottrell on 2008-09-18
Freepbx is a good alternative. It basically takes the important 1/4 of Trixbox.

Asterisk/Flash operator Panel/Web administration.

---

