---
title: "Advice on a server"
date: 2009-05-18
forum: Server Platforms
---

### Post by pyromanic123boom on 2009-05-18
Here's what I'm looking to do

- acquire an old desktop that's decently equipped, throw it in my basement and run an ethernet cable up thru the floor to my router

- use the desktop to create a server streaming music, host a personal website (containing files, etc etc)

Now I understand how to stream music, I know how to make a website, and I just have to get the computer. An old tower isn't really that hard to come across for cheap anyway. 

I'd like to run the most basic cui server- isn't it ubuntu server edish? I need to know the basic guidelines for doing this, if anything extra is needed to install, etc. If I get the guidelines then I can find guides and everything. Also, how do I then launch the server online so I can access it from anywhere? I'm thinking something like dndyns, but I really have no idea. 

If possible I'd like to avoid any recurring fees here- as in once I buy a cable I have it, but I don't have to keep paying 15.95 or something every so often. I can build all the sites and everything on a gui desktop and then transfer them over to the harddrive of the server. 

I'd really love to do this since I could just tuck a tower away in my basement corner and listen to music across the country. Like I said, if I get the parameters for doing this, then I can find the specifics on how to delve into something.

I realize this is huge question, but I'm just looking to get started. Thanks

---

### Post by japtar10101 on 2009-05-18
Incidentally, I just setup my server 2 days ago.  What luck!  Here's what I did.

> **pyromanic123boom said:**
> I'd like to run the most basic cui server- isn't it ubuntu server edish? I need to know the basic guidelines for doing this, if anything extra is needed to install, etc.

The Ubuntu server edition, while ideal for servers, may be a bit difficult to handle due to a complete lack of window management.  In another words, all it has is a terminal.

As for having a window manager I would suggest using Xubuntu, which uses a really low-head window manager Xfce.

You have one of the 2 options:

Faster option: burn a Xubuntu CD, then install the distro as normal (it's pretty self-explanatory).  After installation and reboot, login and install ssh, vnc, php5, apache2, and mysql.  The first one installs ssh, for security measures.  The second is a program that allows you to access your server remotely visually (you get to see the desktop and everything!).  The latter 3 is used for hosting a website, and can be installed with just one command: "sudo tasksel install lamp-server".

Slower option: burn a Ubuntu Server CD, then install the distro.  At one point, it will prompt you to install various programs.  Install ssh/openssh and LAMP (php5, apache2, and mysql).  Let the CD download and install the program.  After reboot and login (you'll be on the terminal this time), install vnc and xubuntu-desktop.  Wait...a really long time, then reboot with "reboot".

VNC specifically requires various setup that I, unfortunately, am unknowledgeable about (I stick with the terminal).  The rest should be easy, however.

> **pyromanic123boom said:**
> Also, how do I then launch the server online so I can access it from anywhere? I'm thinking something like dndyns, but I really have no idea.

Well, there's free services such as DynDNS and Afraid.org.  A few more is listed here:
[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

I'm assuming you're going to work with DynDNS.  First, register an account, and create a new hostname (in another words, a url).  I suggest doing this on your server, since it'll prompt for your external ip address (don't worry: the website kindly figures out for you).  Note that the site already has pre-defined ones: those are free.  It's not quite likeable (especially with names like, "is-a-geek.com"), but it's better than nothing.

Once that's setup, you need to install ddclient: "sudo apt-get install ddclient".  I used this website as reference for installation:
[http://mexpolk.blogspot.com/2008/01/ubuntu-gutsy-dyndns-client-setup.html](http://mexpolk.blogspot.com/2008/01/ubuntu-gutsy-dyndns-client-setup.html)

> **pyromanic123boom said:**
> If possible I'd like to avoid any recurring fees here- as in once I buy a cable I have it, but I don't have to keep paying 15.95 or something every so often. I can build all the sites and everything on a gui desktop and then transfer them over to the harddrive of the server.

No kid.  My (admittingly lame) server came up and running with a mere $39.99 total...for the Radioshack network card.  The system itself was picked up from the recycling center, so it's definitely possible to do this all, competely free.

One more note on Web creation: One of the programs you have to install, Apache2, by default displays the webpage from /var/www/index.html.

---

### Post by ugm6hr on 2009-05-19
Not sure it will serve music over the internet, but FreeNAS has lighttpd for basic webserving and Fuppes UPnP for (LAN) media serving as default.  It also has a web-gui interface for ease of use.  It comes pre-configured with these.

DynDNS is a sensible idea if your ISP provides dynamic IP (I use it).

If Fuppes UPnP will serve adequately over the internet, it is worth considering.  Maybe look it up?  In case it isn't clear, I have a home FreeNAS for LAN media serving.  However, accessing UPnP on Linux is not as simple as it sounds, unless you are prepared to use XBMC (which I do).

Otherwise, I keep hearing good things about Jinzora (but never tried).

Hope that might help in decision-making.

EDIT:
A quick google revealed:
[http://musicbrowser.sourceforge.net/](http://musicbrowser.sourceforge.net/)
[http://apps.sourceforge.net/phpbb/freenas/viewtopic.php?f=86&t=117](http://apps.sourceforge.net/phpbb/freenas/viewtopic.php?f=86&t=117)

Looks like Music Browser + FreeNAS will do exactly what you want very easily.

---

### Post by pyromanic123boom on 2009-05-19
Thanks for the replies - I'm sure I'll be fine now with the great advice :)

One more thing confuses me. I've got a wifi router, and before when I tested a dyndns site, it just redirected me to my router main page (verizon). when I tried to mess with the settings I ended up having to reset the router and fix everything up. How can I still use dyndns? Is every outgoing IP different?

Ha and also how'd you get the tower for free again? Just went to the recycling center? I'll have to find out where one is lol

---

### Post by MrWES on 2009-05-19
> **pyromanic123boom said:**
> Here's what I'm looking to do

- acquire an old desktop that's decently equipped, throw it in my basement and run an ethernet cable up thru the floor to my router

- use the desktop to create a server streaming music, host a personal website (containing files, etc etc)

Now I understand how to stream music, I know how to make a website, and I just have to get the computer. An old tower isn't really that hard to come across for cheap anyway. 

I'd like to run the most basic cui server- isn't it ubuntu server edish? I need to know the basic guidelines for doing this, if anything extra is needed to install, etc. If I get the guidelines then I can find guides and everything. Also, how do I then launch the server online so I can access it from anywhere? I'm thinking something like dndyns, but I really have no idea. 

If possible I'd like to avoid any recurring fees here- as in once I buy a cable I have it, but I don't have to keep paying 15.95 or something every so often. I can build all the sites and everything on a gui desktop and then transfer them over to the harddrive of the server. 

I'd really love to do this since I could just tuck a tower away in my basement corner and listen to music across the country. Like I said, if I get the parameters for doing this, then I can find the specifics on how to delve into something.

I realize this is huge question, but I'm just looking to get started. Thanks

I setup a home file, print and mp3 media server just a couple of months ago. I used mt-daap, aka firefly media server to share my mp3's over the network.
[http://www.fireflymediaserver.org/]("http://www.fireflymediaserver.org/")
There is a .deb package in the repositories.

Bill

---

### Post by dmizer on 2009-05-19
I use [gnump3d](http://www.gnu.org/software/gnump3d/). It's VERY simple, and has plenty of options. I set up my music server as an [ssh server](https://wiki.ubuntu.com/AdvancedOpenSSH), and use the -D switch to set up a proxy tunnel. Then I can access the music server from remote over an encrypted proxy without having to make it live on the web.

---

### Post by japtar10101 on 2009-05-19
> **pyromanic123boom said:**
> Thanks for the replies - I'm sure I'll be fine now with the great advice :)

One more thing confuses me. I've got a wifi router, and before when I tested a dyndns site, it just redirected me to my router main page (verizon). when I tried to mess with the settings I ended up having to reset the router and fix everything up. How can I still use dyndns? Is every outgoing IP different?

Ha and also how'd you get the tower for free again? Just went to the recycling center? I'll have to find out where one is lol

*Raises an eyebrow*  That router stuff...is rather strange.  I just made a quick check.  The Verizon DSL modem page ip address is 192.168.1.1.  DynDNS.com's ip address is 204.13.248.107 (hopefully, that's constant).  So there should be no conflicts....

Open up a terminal and run:
```
ping -c 3 www.dyndns.com
```
See if you get anything strange.

As for a free tower, yeah, I got mine from the recycling center for free.  A friend of mine got his server from his grandparents for free.

Computers ages very fast now-a-days, so I'm sure a neighbor or two is willing to give up their PC by now.  Just keep trying.

---

### Post by ugm6hr on 2009-05-20
> **pyromanic123boom said:**
> One more thing confuses me. I've got a wifi router, and before when I tested a dyndns site, it just redirected me to my router main page (verizon). when I tried to mess with the settings I ended up having to reset the router and fix everything up. How can I still use dyndns? Is every outgoing IP different?

If you try the DynDNS url from within your LAN, it won't work (it will just find your router).  You need to ask someone else to check it for you, or check it when away from home.

Also, you need to ensure you forward the relevant ports (80 for html etc) to your server from the router.  If you don't understand how to do that, try [http://www.portforward.com/](http://www.portforward.com/)

---

### Post by slooksterpsv on 2009-05-20
When I ran my web/file/mp3 server here's the programs I had installed:
Web:
Apache2
PHP5
MySQL

File:
FTP - vsftp

MP3:
gnump3d - best media server, I used it to download my music files or it would make a play list to stream it. it was awesome and the best thing I've ever used.

---

### Post by MrWES on 2009-05-20
> **dmizer said:**
> I use [gnump3d](http://www.gnu.org/software/gnump3d/). It's VERY simple, and has plenty of options. I set up my music server as an [ssh server](https://wiki.ubuntu.com/AdvancedOpenSSH), and use the -D switch to set up a proxy tunnel. Then I can access the music server from remote over an encrypted proxy without having to make it live on the web.

gnump3d is command line only for servers? And the access is via web only on the client side? I like mt-daap as it show up in Rhythmbox, iTunes, Songbird, and now the new Amarok.

---

### Post by dmizer on 2009-05-20
> **MrWES said:**
> gnump3d is command line only for servers?

Nope, I have it loaded up on my desktop. It does take a bit of overhead, but most machines these days can handle it. For any of your music players, all you need to do is download the m3u file, load it into whatever your preference is, and off you go. That or just point it at gnump3d's [noparse]url:port[/noparse]

---

### Post by pyromanic123boom on 2009-05-20
> **japtar10101 said:**
> *Raises an eyebrow*  That router stuff...is rather strange.  I just made a quick check.  The Verizon DSL modem page ip address is 192.168.1.1.  DynDNS.com's ip address is 204.13.248.107 (hopefully, that's constant).  So there should be no conflicts....

Open up a terminal and run:
```
ping -c 3 www.dyndns.com
```
See if you get anything strange.

As for a free tower, yeah, I got mine from the recycling center for free.  A friend of mine got his server from his grandparents for free.

Computers ages very fast now-a-days, so I'm sure a neighbor or two is willing to give up their PC by now.  Just keep trying.

The router stuff is strange man...my router's ip is 192.168.1.1, but if you go to the page using that, it says in the info "IP Address: 	
209.158.57.151". 

When I try the 209.158.57.151, it does direct me to my router's main page. So when I try to set up an dns subdomain on the website, it auto detects my ip as 209...

Here's a picture:

[IMG]http://i461.photobucket.com/albums/qq331/pyromanic123boom/dyndns.jpg[/IMG]

Now my router actually has a Dynamic DNS page, but I don't know how to set one up. 

[IMG]http://i461.photobucket.com/albums/qq331/pyromanic123boom/verizondns.jpg[/IMG]

Between the two I'm sure there's some connection so I can set this up once I get a server. I just want to have all the blocks out of the way so I can get everything up and running once I get it.

---

### Post by pyromanic123boom on 2009-05-20
Oh yeah and I love gnump3d. I run it on my computer now so I can stream to laptops

---

### Post by pyromanic123boom on 2009-05-22
Anyone?

---

### Post by dmizer on 2009-05-22
> **pyromanic123boom said:**
> Anyone?
The situation you described above is perfectly normal.

Perhaps a diagram is in order:
```

www <===> (209.158.57.151) modem <---> router (192.168.1.100) ---> computer1
                                              (192.168.1.101) ---> computer2
                                              (192.168.1.102) ---> computer3
                                              (192.168.1.103) ---> computer4
```
Externally (from the web), all 4 computers have the same IP address (209.158.57.151). Routers allow you to use multiple computers on the internet without owning multiple internet connections.

---

