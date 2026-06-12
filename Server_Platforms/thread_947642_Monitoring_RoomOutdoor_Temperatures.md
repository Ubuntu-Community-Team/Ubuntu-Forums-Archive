---
title: "Monitoring Room/Outdoor Temperatures"
date: 2008-10-14
forum: Server Platforms
---

### Post by teqsun on 2008-10-14
Hello all,

I am not sure if this is the right place or not but here goes anyways.

I want to monitor the room temperature that the server is located in as well as monitor the outdoor temperature.

What I am looking for is a simple command line interface to monitor these temperatures in real time, perhaps even supporting logging.

I have googled for hours and not found anything.  Does anyone know if there is an interface like this available?

---

### Post by mbeach on 2008-10-14
do you have a digital thermometer of some sort?  How do you plan on connecting the thermometer to your machine?  For devices I've used (a looonng time ago) the documentation provided the method to read the raw data from the device measuring the temperature/humidity/salinity etc and convert to the appropriate units - it was using rs232 and we had a little utility that could read the data on a regular interval and write to a log file - I imagine that should be simple enough to program these days.

doing a quick search on a popular search engine for 'usb thermometer' provides a wide range on thermometers - find one that works for you and buy it.

---

### Post by mbeach on 2008-10-14
similar question here - might provide a model for you to start with:
[http://ubuntuforums.org/showthread.php?t=205251](http://ubuntuforums.org/showthread.php?t=205251)

the links at the bottom of:
[http://www.linuxquestions.org/questions/general-10/usb-thermometer-that-works-w-linux-286752/](http://www.linuxquestions.org/questions/general-10/usb-thermometer-that-works-w-linux-286752/)
may also provide you some insights.

---

### Post by teqsun on 2008-10-15
cool guys, Thanks for the links and info.

Just incase anyone is interested, I found two products that have done all the work for me (kind of takes all the fun out of it)

They are ethernet thermometers, basically they run a small web server and relay temperature data through http, ftp, smtp, and more.

Here are two links that I found.

[http://www.wut.de/e-57606-ww-daus-000.php](http://www.wut.de/e-57606-ww-daus-000.php)
[http://www.equalsgreaterthan.com.au/Products.html](http://www.equalsgreaterthan.com.au/Products.html)

:guitar:

---

### Post by MJN on 2008-10-15
At those prices I'm assuming this is a business expenditure.

For those that are looking at doing this from a home/hobby perspective check out [http://martybugs.net/electronics/tempsensor/](http://martybugs.net/electronics/tempsensor/) which discusses using the '1-wire' DS1820 thermometer from Maxim - available for the cost of a couple of pints of beer (I'm trying to be country-agnostic!).

The site covers construction/interfacing as well as the all-important software (for both Linux and Windows).

I've been meaning to give it a go myself for a while but never got round to it... maybe now is as good a time as any!

Mathew

---

### Post by teqsun on 2008-10-15
MJN,  Currently I am on a tight budget, I want to do this for under $200-300 including the cost of the server  under $100 preferably for the supplies.

I am doing this as a personal project, so unfortunately, I do not have corporate backing :(


If I have to, I will spend the $$ for the ethernet system, but I would rather do this myself.

---

### Post by MJN on 2008-10-15
In that case get yourself some DS1820's and a soldering iron. For $10 + a server you'll be all set...

(and do let me/us know how it goes!)

Mathew

---

### Post by teqsun on 2008-10-15
> **MJN said:**
> In that case get yourself some DS1820's and a soldering iron. For $10 + a server you'll be all set...

(and do let me/us know how it goes!)

Mathew

I'll have to do that! 

Oh and by the way, When I mention server cost, I am not planning on making a powerhouse server by any means.  The pure purpose and functionality of the server will be to monitor temperatures and control relays. (edit: heck I could probably use a 486 for this lol)

---

### Post by teqsun on 2008-10-15
> **MJN said:**
> In that case get yourself some DS1820's and a soldering iron. For $10 + a server you'll be all set...

(and do let me/us know how it goes!)

Mathew

Sry about the double post to my own thread... I just got done reading the link you sent me... You hit the nail RIGHT on the head, this is exactly what I am looking for! 

THANK YOU!8)

---

