---
title: "GUI Based vs Command Line Based Server"
date: 2010-06-25
forum: Server Platforms
---

### Post by SecretLegend on 2010-06-25
Hey guys lately I have been using Ubuntu Desktop 10.04 with LAMP server installed to run my wordpress blog (Currently Offline) It Runs GREAT!, But recently I heard that running a GUI based server affects the servers performance, so a friend recommended that I should switch to Ubuntu Server. I just wanted to know if there is a really big speed difference that I should move over to Ubuntu Server. I do REALLY! I love the GUI interface but if there is a big speed difference I will consider moving over to Ubuntu Server as I don't fear the command line :p So what do you guys think, I want to get my site up as soon as possible so I really need an answer :) Any replies are greatly aprreciated. Btw this is my first time on the forums ):P


Specs of my server:
pentium 4 at 1.8 ghz
1 gig of ram 
Integrated Graphics 
Connected Through 10/100/1000 Ethernet 
(Thats all I guess you need to know)


Internet Connection: Cable with 25 Mb/s Download and 10 Mb/s Upload

---

### Post by Bachstelze on 2010-06-25
> **SecretLegend said:**
> But recently I heard that running a GUI based server affects the servers performance,

Sometimes it does, sometimes it does not. In your case, unless you have over 9000 visitors per day, it probably does not.

---

### Post by SecretLegend on 2010-06-25
> **Bachstelze said:**
> Sometimes it does, sometimes it does not. In your case, unless you have over 9000 visitors per day, it probably does not.

If there was 9000 Visitors a day by how far would you think it would affect the server? (Lol I'll probably never get that much)

---

### Post by amauk on 2010-06-26
There's really no way to say (without actively running benchmarks)

You have 1Gb ram
A GUI will eat 200-300Mb of that (assuming Gnome)
so, approx. 700Mb to play with
(for server software, cache & other bits & bobs)

RAM is used to cache frequently used files, and to cache database query results

less RAM = reduced cache
Reduced cache = more CPU usage + more I/O needed to serve clients

Plus, there's differences under-the-hood between the Desktop & Server editions of Ubuntu
different kernel configs, and such

I do have a thing about people putting GUIs on servers - I really don't see the sense
server admin is all about editing config files, reviewing logs, and service management
All of which are more of a hassle within a GUI environment

but in all honesty, if it works and you're happy with it, stick with it
If it ain't broke...

---

### Post by tgalati4 on 2010-06-26
I've been running a Dapper Drake desktop with several server functions since 6.06. It's a 1 GHz, Celeron--basically crap.  I find the desktop uses about 9% of the CPU cycles.  Of course, you don't have to boot to the Desktop GUI.  You can simply boot to the command line and not invoke the desktop.

The server kernel is optimized for server workloads.  Once you learn a few command-line techniques for managing the server, the rest can be done through web page administration.  Search through the forums and the wiki's.  There's a lot of server admin stuff out there.

Don't forget to put an UPS on the server.  It will dramatically increase the uptime and life of the machine.

---

### Post by MartinHansell on 2010-06-26
Amauk  :  > **amauk said:**
> Plus, there's differences under-the-hood between the Desktop & Server editions of Ubuntu
different kernel configs, and such

I do have a thing about people putting GUIs on servers - I really don't see the sense
server admin is all about editing config files, reviewing logs, and service management
All of which are more of a hassle within a GUI environment

Do you happen to know what those differences are?  I am trying to learn servers in a command-line environment, but fell over at the first hurdle coz the server version couldn't handle my wireless (whilst the desktop version can).  I am trying to find out what's different between the two so I can fix my problem and stay true to that sentiment on server admin.

---

### Post by amauk on 2010-06-26
> **MartinHansell said:**
> Amauk  :  

Do you happen to know what those differences are?  I am trying to learn servers in a command-line environment, but fell over at the first hurdle coz the server version couldn't handle my wireless (whilst the desktop version can).  I am trying to find out what's different between the two so I can fix my problem and stay true to that sentiment on server admin.Chances are you're wireless needs a non-free driver that's included by default on Desktop, but not server
Just find which package provides the driver, and install it

plus the management of network stuff is different on server
using /etc/networking/interfaces instead of networkmanager

See iwconfig man page for the wireless options available for /etc/networking/interfaces

---

### Post by MartinHansell on 2010-06-26
> **amauk said:**
> ...Just find which package provides the driver, and install it
How would I do that exactly?  I think my device uses rt73usb driver, but I can't work out what's different on the server setup that prevents it from being used.  It seemed to be installed, but just not able to use it.  If you search for another thread using my name in "Networking & Wireless" you will see the technical details relating to this.

> **amauk said:**
> ...using /etc/networking/interfaces instead of networkmanager

I just used a standard config, to keep the complications to a minimum, but it may be that the WEP key presented me a "silent" problem.  I also tried to set this in the interfaces file, but to no avail.

Simple settings were:
wlan0 auto
iface wlan0 inet dhcp

I will take a look at the options page - thanks.

---

### Post by SecretLegend on 2010-06-26
> **tgalati4 said:**
> I've been running a Dapper Drake desktop with several server functions since 6.06. It's a 1 GHz, Celeron--basically crap.  I find the desktop uses about 9% of the CPU cycles.  Of course, you don't have to boot to the Desktop GUI.  You can simply boot to the command line and not invoke the desktop.

The server kernel is optimized for server workloads.  Once you learn a few command-line techniques for managing the server, the rest can be done through web page administration.  Search through the forums and the wiki's.  There's a lot of server admin stuff out there.

Don't forget to put an UPS on the server.  It will dramatically increase the uptime and life of the machine.

Hey Guys I think I may try Ubuntu Server and see how it goes, I guess Ubuntu Server is better in the long term.

---

### Post by MartinHansell on 2010-06-26
I think Ubuntu is great, generally.  I recently tried to try out Debian, which has solid track record, but it wouldn't even format my hard drive with ext3 (goodness knows why), so what could I do?  It's Ubuntu all the way (so far at least!).  That's why I'm so keen to resolve existing issues in the server setup.  I think it's worth it!

---

### Post by HermanAB on 2010-06-26
Running a GUI was an issue many years ago when RAM was expensive.  Nowadays, with gigabytes of RAM in a machine, having X installed makes no difference and in any case, if it does nothing then it will get swapped out.  So, from a performance point of view, go ahead and use a GUI if you want to.

From a security point of view, it is better to not to run the GUI.  Here, one solution is to simply shut X down when you are not using it.

---

### Post by SecretLegend on 2010-06-26
> **amauk said:**
> There's really no way to say (without actively running benchmarks)

You have 1Gb ram
A GUI will eat 200-300Mb of that (assuming Gnome)
so, approx. 700Mb to play with
(for server software, cache & other bits & bobs)

RAM is used to cache frequently used files, and to cache database query results

less RAM = reduced cache
Reduced cache = more CPU usage + more I/O needed to serve clients

Plus, there's differences under-the-hood between the Desktop & Server editions of Ubuntu
different kernel configs, and such

I do have a thing about people putting GUIs on servers - I really don't see the sense
server admin is all about editing config files, reviewing logs, and service management
All of which are more of a hassle within a GUI environment

but in all honesty, if it works and you're happy with it, stick with it
If it ain't broke...

Well I tried Ubuntu Server but I am having some trouble installing samba on it and accessing it form another computer. I guess I may stick with Ubuntu Desktop since it works perfectly fine, also I upgraded the computer to 6gigs of ram a core 2 duo at 3.0ghz and a 1 terabyte hard drive <-----  So that hopefully should cover for the performance if gnome is using many resources :)

---

### Post by SecretLegend on 2010-06-26
> **HermanAB said:**
> Running a GUI was an issue many years ago when RAM was expensive.  Nowadays, with gigabytes of RAM in a machine, having X installed makes no difference and in any case, if it does nothing then it will get swapped out.  So, from a performance point of view, go ahead and use a GUI if you want to.

From a security point of view, it is better to not to run the GUI.  Here, one solution is to simply shut X down when you are not using it.

Hey Man Thanks!!! :) I guess I will do that with Ubuntu Desktop I have 6gigs of ram on the machine so I bet it doesnt matter too much, but I will be shutting down X. Thanks for the great advice. UbuntuForums are great when you need help :KS

---

