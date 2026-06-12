---
title: "Server and remote desktop login Q's, i know nothing of servers at all..."
date: 2009-02-27
forum: Server Platforms
---

### Post by Snow Keld on 2009-02-27
ok, well say i get a nice server for very cheep, dual 2.0gighz processors and 4 gigs of ram say.

now, i'm not looking to use a server as web hosting, i want to use it as a reg comp... well sort of.


i'm looking at getting a server cuz they are cheep, and i'm looking at getting the acer aspire one for the same reason, i'm considering to get both and user laptop to log into the server using one of those USB wireless net things you can buy from phone companies, which i'm pretty sure i saw that you can get compatibility with those.. i hope i can.

then go wherever, and login with the laptop.

i like xubuntu 8.10 so i would want to be loading the xubuntu desktop version into a server and logging into it with a remote desktop connection.



see, i know nothing of servers, so this is my plan, if you could please tell me if it makes sense or any details i should know if i go for this plan.

ah, and just curious, does xubuntu work well with duel processors?

---

### Post by uzi09 on 2009-02-28
Okay, I'm sorry if I didn't totally understand what you said. Let me just make sure this is what you want:

You want to install a server and be able to login remotely huh? (namely xubuntu).

#1 - just install xubuntu (or whatever your favorite distro is). Note that you do not *have* to get the "server" version. It'd probably be easier for you to just stick with the desktop version since it'll give you a GUI to work with.

#2 - Install FreeNX, the free version of No Machine's NX server. You can Google both for more information. Here's the how-to to follow:
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

You'll be able to access your server remotely & login with SUPER-FAST speeds.

---

### Post by TwiceOver on 2009-02-28
Forgive me if I'm wrong, but I just get this feeling you are looking at a 1u server from Geeks.com or some other place as a desktop solution.  I just wanted to let you know that these 1u servers are generally EXTREMELY loud.

Ubuntu should work on dual processors just fine no matter the flavor.

With internet sharing, I assume you want access to your files from anywhere using the cell phone internet you kinda spoke of, look up VPN solutions like OpenVPN or an SSH connection to access your files.

---

### Post by Snow Keld on 2009-02-28
ok, so this isnt an outlandish idea at all.


so if i where to install the xubuntu-desktop cd onto a server it would work fine, then i would put the remote desktop server onto it?

then i would be able to use the remote desktop client that comes with xubuntu (cuz i'd just install xubuntu on the laptop too)

then connect through net and all is good?



question about remote desktop logins in general: which computer runs the graphics? cuz its fairly obvious that the server would run all programs and all that stuff, but does the client run the graphics? if so this is just fine, actually i'd say better, i'd just like to know anyway.

oh, and the other Q i asked before, does xubuntu work fine with duel processors, no extra hassle?


this server just sold on ebay for $95, why i made this topic.

> 
Verari Systems Inc 1U Dual Opteron Server Dual AMD Opteron 2.0Ghz 120Gb IDE 4032Mb ram NO OPTICAL 10/100/1000 Ethernet

This Verari Systems 1U Server is powered by dual AMD Opteron 2.2 GHz processors, 4 GB DDR RAM and a 120 GB IDE hard drive! Video is provided by the ATI Rage XL integrated video while the Broadcom BCM5704 Gigabit Ethernet controller delivers the speed and reliability for your network connectivity!

NO RAILS OR POWER CORD IS INCLUDED IN THIS AUCTION

Features/Specifications:

    * Verari Systems Dual Opteron 2.0 GHz 1U Server

    * General Features:
    * No Server Operating System
    * Dual AMD Opteron 2.0 GHz processors
    * 4 GB DDR RAM 
    * 120 GB IDE hard drive
    * ATI Rage XL integrated video
    * Broadcom Gigabit Ethernet

    * Motherboard Features:
    * AMD chipset
    * One (1) PCI-X riser slot
    * Eight (8) DDR DIMM sockets 
    * I/O Ports:
    * Two (2) PS/2 ports
    * One (1) 15-pin VGA port
    * One (1) 9-pin serial port 
    * Three (3) USB ports (two on back and one at front)
    * Two (2) RJ-45 Ethernet jacks

    * Case Features:
    * 1U server chassis
    * Three (3) 3.5-inch drive bays
    * 350-watt power supply

    * Case Dimensions:
    * 1.75 x 17 x 26-inches (H x W x D, approximate) 


if this info helps, this is what i'd end up getting.

---

### Post by Snow Keld on 2009-02-28
> **TwiceOver said:**
> Forgive me if I'm wrong, but I just get this feeling you are looking at a 1u server from Geeks.com or some other place as a desktop solution.  I just wanted to let you know that these 1u servers are generally EXTREMELY loud.

Ubuntu should work on dual processors just fine no matter the flavor.

With internet sharing, I assume you want access to your files from anywhere using the cell phone internet you kinda spoke of, look up VPN solutions like OpenVPN or an SSH connection to access your files.

ah, you sniped me.

and how loud?

other thing is, this isnt the issue, i have like no $, and i want to get a good setup without spending allot, i'm gana be selling my buddys car for him and making a couple hundred, then another buddys old sword for him, prolly get $50 for selling it more him, possibly more, and i've been asked by 2 diff people to build them cheep desktop comps, which i can do no prob and i'll get like $50 out of each of them.

so, i'll have about $500 and want to have a GOOD comp, and be able to use it anywhere, to get a laptop as nice as i want it would be way to much $, and a desktop i could do for $500 but then i wouldnt have the laptop to log into it remotely as i would have used up all my $, i saw the servers selling for next to nothing and i got this idea.

---

### Post by TwiceOver on 2009-02-28
Graphics is handled by the server end.  

By loud, I mean you don't want to be sitting next to it, be in the room, or hang out outside the closed door of the room it is in.

I think you should look at this as a real server setup rather than a remote desktop terminal.  You have an Aspire which is an excellent netbook.

Look into using this server as a file share, VPN, web server.  I think you'll find a lot of fun things to do with it.

Here's what I do with mine, similar setup:

Stream music accross web
Share Pictures
Share files and folders (including web sharing)
run my personal website

Just a few examples.

---

### Post by Snow Keld on 2009-02-28
ok, so what if i put it in insulation in a closet?

i dont have an aspire yet, but its what i would be getting for a laptop.



my desktop has slightly less than the aspire has for hardware, so i have a good idea of how well the aspire will run, it will run well, but i want something a bit better, i have a good buddy who's got his own comp biss and told me remote desktop logins was a very good idea, and it makes sense.


idk, exactly if i should get the server or not, thats why i posted here, lots of smart people on this forum :D




my normal use of my comp is lots of torrent downloads, firefox + lots of tabs, rhythembox, pidgin, and GIMP cuz i do lots of graphics editing, i make forum sigs and do SMF forum customization and hosting for people.

my desktop can run all that, but slow.



should i try for building a good desktop instead of getting the server? it would cost more but is that a better idea?

---

