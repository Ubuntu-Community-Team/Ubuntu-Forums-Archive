---
title: "Server for Internet  Logging and Filtering"
date: 2010-06-16
forum: Server Platforms
---

### Post by junkman51 on 2010-06-16
I hope I am posting this in the correct area. If not, I hope a staff member will move this to a more appropriate area.

I'm in charge of a church computer lab which is open to children ages 6 to 16 for about 3 hours a week. We try to have adult supervision but don't have 100% coverage.

The lab has a maximum of 8 computers, a mixture of MACs, Windows XP, and Linux machines, depending on their state of repair.

The church's current internet connection is Verizon residential speed DSL to a 4 port wired plus wireless router in a locked office which also houses our Windows XP office computer and is adjacent to our locked pastor's office.

Internet access for the lab is by a single CAT5 cable passing through a small hole in a wall to a network switch on the other side. All of the lab computers are connected to the switch by CAT5 cable.

I would like to add a server in the locked office to log internet usage and block access to certain websites as needed. I think logging internet activity will be a good antidote in case one of the older ones wants to try to get sneaky and cover their tracks.

I envision building a computer from donated parts, including 2 NICs.

I have never done things from the server end, but think the server edition of Ubuntu would be a good starting point.

My goal is to be able to manage internet access with an easy to use GUI system so I could teach the basics to a couple of youth leaders to use it when I'm not there.

I welcome all suggestions and comments.

---

### Post by hictio on 2010-06-16
What you need is a proxy, a piece of software, a program that seats between what the clients -using the web browsers- requests and the internet at large offers.
If I can recommend one to you, I would say that you should get your hands on a Linux distribution already setup for that purpose, and free.
For easy of setup and management, I would say the community edition of the Endian firewall, yes, it is not an Ubuntu solution :)
Once installed (you'll need the 2 NICs on this machine), you place it between the internet connection and your switch, and enable the internet filtering, there are filters for all type of content.

[Endian Community Edition](http://www.endian.com/en/community/)

---

### Post by HermanAB on 2010-06-16
Howdy,

Read up on Squid and Dansguardian.

---

### Post by junkman51 on 2010-06-17
Hictio and HermanAB,

Thank you both for your suggestions. I did a quick look at your links and will look more closely after get the hardware ready from my junkpiles.

My computer career included mainframe and VAX system administration, DEC terminal server administration, and PC rebuilding/deployment before I retired a little over 4 years ago after 30 years at the same place.

I'm used to checking documentation, etc. to learn to get things done, of course with suggestions from more experienced helpful people like you and other forum members.

I have done a little distro hopping, but for desktop use I like Ubuntu and some of its derivatives.

For now, it seems that Linux Mint is the desktop distro that kids used to Windows seem to get used to most quickly.

My goals are to set up a computer management system for this computer lab, be able to show other people how to maintain it, then after I am comfortable it is working well, assist other churches set up computer labs.

Thank you again for pointing me in the right direction.

---

