---
title: "Building a basic web store"
date: 2006-09-22
forum: Server Platforms
---

### Post by dkline on 2006-09-22
Ok I'm pretty much a windows guy, but my first look and try with ubuntu is really positive. I'm loving it so far. I installed ubuntu server and am looking at a command line....  Now what?  My goal is to build a basic website and incorporate a store into that site.  Could someone please point me in a direction on where to start?  Lets start with apache and web design.  Is there some good web design software in the Linux world? and is there some basic apache setup links to get me started?

---

### Post by jISh on 2006-09-22
sudo apt-get install ubuntu-desktop for GNOME
sudo apt-get install kubuntu-desktop for KDE
sudo apt-get install xubuntu-desktop for XFCE

Out of those three desktop environments it's your choice really.

Look at Bluefish/NVU for web design software.

---

### Post by dkline on 2006-09-22
Wow thank you for the quick responce.  When I try to do the sudo for KDE desktop I get package not found?  Is there any type of configuration I have to do on the server?  My server install is straight "out of the box"  I've logged in twice... That's it.

---

### Post by dkline on 2006-09-22
I looked at the web design software, and I should add I'm new to web design as well. Looks like bluefish is to advanced and NVU is pure HTML which is old school as I understand it.

---

### Post by chrisfay on 2006-09-22
> Now what? My goal is to build a basic website and incorporate a store into that site. Could someone please point me in a direction on where to start?

It really depends on how you plan on hosting your site. 

I would recommend checking out some howtos regarding your situation. Something like [this]("http://www.howtoforge.com/lamp_installation_ubuntu6.06") may help you get started. 

You will need to invest some time learning how to run Bind9 if you plan on hosting your own DNS or use a DNS service such as zoneedit.com. Make sure you understand the networking requirements regarding routing and portforwarding if you use a router. 

Security is obviously important so look into securing Apache through their online docs. They have some pretty good references to do so. 

Just some thoughts....

---

### Post by dkline on 2006-09-22
Amazing the link provided was just waht I needed. Thank you.

---

### Post by lonce on 2006-09-23
The absolute best commerce software out there is free.  Its called OScommerce.  Put that into google to go to the website.  It installs itself after you upload it to your server.  Asks you a couple questions and sets itself up.  Very easy.  Check out my site in my signature.  It was all OScommerce.  And its open source.

---

### Post by compunuts on 2006-09-23
Depending on what type of web store you want to run. I have been happy with Zencart . Google for it.

---

