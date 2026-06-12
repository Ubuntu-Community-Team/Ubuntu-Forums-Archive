---
title: "Setting up server"
date: 2008-11-23
forum: Server Platforms
---

### Post by caralyh on 2008-11-23
I'm thinking about setting up server at home, and I'd like some advise for doing it.

Network would be like this:

[IMG]http://img155.imageshack.us/img155/8804/setupqi3.gif[/IMG]

Box 1: Server
Box 2: My linux/vista computer
Box 3: Other vista computer
Box 4: Linux mediacenter


I'd like to have the server to be firewall and router, and possibly LAMP+samba also, and maybe even mailserver.

I have played with webserver thingys few years, had apache+mysql+php running in my first computer when I was 14 etc. But I've never really had possibility for having any networks as I've only had one computer, so'm kinda networking newbie and I don't know so much about all security things. 

So what I'm asking is that should I have the server run just firewall and routing, or the other things too, and how. Other option would be to get some other computer for doing that LAMP+SMB+mail, but I dont have a spare machine right now.
The supposed server has 1,5Ghz/1GB/160GB if i remember correctly.

---

### Post by Lars Noodén on 2008-11-23
For the setup described, you'll need two network interfaces in the server and need to get familiar with IPTables:  
[INDENT][http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)[/INDENT]

FW Builder is useful for some beginners, you may look at that.  The cookbook gives ideas of what can be done:

[INDENT][http://www.fwbuilder.org/guides/firewall_builder_cookbook.html](http://www.fwbuilder.org/guides/firewall_builder_cookbook.html)[/INDENT]

However, if you become serious, then you would find it well worth your time to learn how to use the shell and write the shell scripts without a GUI.  Shell is **always** there, even when the GUI is broken, or the connection is too slow for VNC.  

The one Windows computer might be upgraded to XP or, better, (Flux|X|K)ubuntu with WINE.  WINE does a good job on any apps that might be holding you back on the legacy systems.

---

### Post by caralyh on 2008-11-24
Thank you for the links! Well the server is going to be headless, I'm comfortable with CLI, have installed gentoo like five times so it's not new thing for me :)  I don't have much experience with shell scripts but I'd like to learn.
Can't really have that other windoze comp upgraded to linux, I've tried but the user isn't very willing :P

I'd like to have opinion about what services to set in the server, would too much services make it less secure, harder to maintain etc. And I'm pretty much lost with the network configuration, IP-settings, gateways, netmasks etc.

I know that I need installed ssh, iptables, apache, mysql, php, perl, samba and mailing stuff. Just need to know if I need something more and how to config all these things.

---

### Post by txtiger on 2008-11-24
Hi,
I have done exactly what you describe and it has been running fine for about a year.  Perhaps I am just lucky, but I used the NAT router firewall as the main "stopper" and only opened a specific port for SSH (which I moved to avoid at least some of the port 22 hammering).  Most recently I have been investigating what firewalls to use on the server box and so far my favorites have been IPcop, Smoothwall, and Untangle.  They are very secure and can handle the openVPN that I want to try next.

If you want to stay safe but limit yourself to just the NAT router and the server I would suggest that you use Firestarter on Ubuntu Server 8.04 LTS and go through and try shutting down services that do not look necessary one at a time.  What Firestarter does is create its own set of IPtables rules via a nice GUI.  What I like the best about it is that it will allow me to see an exception (like my Denon AV receiver trying to get uPnP) and then I can just click on the IP of the exception and it will allow that for future access.

All that said, the reason I am here on the forums today is the drive crashed on my server and while I can ssh into the network, all else is dead (but note the Ubuntu survived even with the drive dead-I just hope the UPS holds out).  So seriously consider a software Raid 1 for the server box.

Hope this helps

---

### Post by caralyh on 2008-11-24
I'm starting to get idea what I need to do, but before I install I'd like to know how to configure the server as router, so I don't need to plug the internet cable on and off all the time to read internet :)

So from the modem comes the wire and goes into eth1, and from eth0 goes wire to hub, from hub goes wires to other computers. What do I need to do to be able to ssh into the server from my computer behind the hub for doing rest of the stuff? Preferably with CLI, so I don't have to install GUI.

And yeah raid would be great, but I only have 2 old spare hdd's, 160gb and 40gb, and no extra money for buying more right now, so this will have to do for now. And this is just my toy project, so probably there wouldn't be much harm done if the hdd were to crash some day.


EDIT//
I just installed ubuntu server 8.10, /etc/network/interfaces looks like this:
auto eth1
iface eth1 inet dhcp
iface eth0 inet static
	address 192.168.0.2
	netmask 255.255.255.0
        network 192.168.0.0
	gateway 192.168.0.1
        broadcast 192.168.0.255

"ssh localhost" seems to work, but I'm lost about what to do next. Tried putty in vista but as I expected it didn't connect. 

EDIT2//
I't looks like I got even port 22 to be listened, but still no luck. As I'm no expert in these kinda things, I'm starting to wonder if it's even possible to ssh into the server from comp behing the hub, somebody tell me is it possible or not? :P

---

### Post by caralyh on 2008-11-24
I'm starting to doubt the possibility of my project lol. So I'd really like to have a confirmation if it is doable or not when my server is located between modem and hub/switch/whatever.
I guess the normal setup would be server behind a router with port forwarding etc, but I don't have separate router but just a normal hub for sharing internet for 2 or 3 computers.


EDIT//
GOT IT WORKING !!!
Used this howto: [http://ubuntuforums.org/showthread.php?t=713874]("http://ubuntuforums.org/showthread.php?t=713874")

Next I need to configure the system more secure, and all other things I want it to do... :P

---

### Post by txtiger on 2008-11-24
Yes your project is very do-able :).  You had the right concept in your drawing and description.  Here are the steps I would do:
[LIST=1]
[*]Get your "server" box running the way you want in "stand alone" mode.
[*]Hook it to the internet and use the install software part to ensure that Firestarter and SSH are installed
[*]Open Firestarter and under preferences configure your eth1 and eth0 devices.  Then go to policies and allow ssh from your local area addresses (192.168. whatever)
[*]from the command line find the ssh config (sorry I don't remember where it is) and change the file to disallow root logins.  That does not prevent you from using sudo when you log in, it just prevents someone from logging in using the default root password
[*]Now hook another machine to the switch and plug the switch into the new server as you described.
[*]Test for an internet connection.  If you don't see one, then go back to your server and Firestarter and look at the exceptions tab to see if the effort showed up.  If it did then change the policies to allow that outbound access.
[/LIST]

I think that will do it.  You should then be able to ssh into the server from anywhere on your internal network (just remember to use the exact server ip since you will not have a name server to handle addressing it by name).

The only part of all that I am not sure of is the NAT part -- my DSL modem does that part for me so I am not sure how the server box needs to be set to handle a direct internet connection.  Basically I have the same setup that you drew in your diagram, but I have a DSL modem/router between me and the internet.  That meant that I had to open the ssh port on the router.

I am pretty much a self-educated newbie, but if I missed anything obvious hopefully someone else on the forum will let us know.

Good luck.  By the way, I sure would consider the US $40-ish investment for an inexpensive router to put between you and the internet as a first line of defense.

---

### Post by caralyh on 2008-11-24
Now I got it pretty much working :)
I have SSH, dhcp, nat, samba, apache, dyndns+ddclient, webmin and probably mysql and php too working atm, I just need to study iptables more to make the box more secure. 

But anyway, YAY it's working! :grin:

---

