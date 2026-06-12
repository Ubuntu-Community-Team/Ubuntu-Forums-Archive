---
title: "Home Automation / Alarm System ?"
date: 2007-06-08
forum: The Cafe
---

### Post by matthinckley on 2007-06-08
I am interesting in building a home automation / Alarm system for my house out of ubuntu.. What I need is some sort of interface (hardware) that I can connect to my computer that would give me inputs for sensors and a block of outputs that I could use to activate relays.. pretty much an alarm panel that I could tie into my computer.. does anyone know of something like this that is affordable? 

I've looked at smarthome.com and they have some cool stuff but most of it is out of the box turn-key solutions and I would like to build something myself.

EDIT: I just found [this]("http://www.ipio.nu/") and it is probably the closest thing I've found but I would like to find something cheaper than 300 EURO.. also I don't need the IP stuff I just want to connect directly to my box.. either with serial or USB

EDIT2: I also found [this]("http://www.truetex.com/poolcontrol.htm") which looks very promising for giving me ideas on how to put something together

---

### Post by ZeroXR on 2007-06-08
I would check out the Linux MCE project for some ideas... Their integration of home automation and home security is pretty slick. The best example is the Bluetooth phone as a remote for the system, as it can also broadcast video imaging of the front door. That way, you could have the Bluetooth applet send you an image/video of who is at the door.

---

### Post by ramjet_1953 on 2007-06-09
There ar two packages in Synaptic for controlling X-10 devices:

x10
x10-automate

If you fire-up Synaptic, the x10 package talks about the [COLOR="Blue"]CP290 serial port controller[/COLOR], available from Radio Shack.

I haven't seen any home-build information about a controller, but it would also require some sort of imbedded controller on-board with the necessary firmware.

Hope this helps.

Regards,
Roger :cool:

---

### Post by reidms on 2007-06-09
But if your computer were to get compromised- so would your house

Make sure you have secured the box :P

---

### Post by matthinckley on 2007-06-09
> **ramjet_1953 said:**
> There ar two packages in Synaptic for controlling X-10 devices:

x10
x10-automate

If you fire-up Synaptic, the x10 package talks about the [COLOR="Blue"]CP290 serial port controller[/COLOR], available from Radio Shack.

I haven't seen any home-build information about a controller, but it would also require some sort of imbedded controller on-board with the necessary firmware.

Hope this helps.

Regards,
Roger :cool:

Thanks for the reply.. I am trying to stay away from X10.. I've had a lot of experience with it.. It's nice and all but doesn't give device status to the controller.. like the computer has no way of knowing what the state of a device is.. whether a lamp is on or off or whatnot.. but what I'm really looking for is something that I can use to control multiple relays, for controlling things such as lights, drapes, solenoid dead bolts, etc..  and basic inputs.. just on/off inputs like an alarm panel.. so I could connect door/window/motion sensors to them..  Once I find something like this I will write the program myself to control everything.. probably going to be web based.. that way I can control it from any computer in the house..

> **reidms said:**
> But if your computer were to get compromised- so would your house

Make sure you have secured the box :P

Oh yes.. although I don't really think I have to worry about it that much.. I live in a small town of about 50k people.. we don't have much for crime here.. :) I mainly want to build it for the automation, but adding on sensors for doors and windows I can create interfaces that will alert me when any of them are open say when I go to bed, or whatever. Just a project for hobby I guess.

---

### Post by reclusivemonkey on 2007-06-09
You might find this interesting;

[http://plutohome.com/](http://plutohome.com/)

They sell hardware, but they use Linux in that hardware, and they clearly state if you want to download their software and build your own hardware they are perfectly ok with this. I believe they use Debian as a base, so you might even be able to get the debs to work on an Ubuntu install.

The Wiki is probably the best source of information for you;

[http://plutohome.com/wiki/index.php/Main_Page](http://plutohome.com/wiki/index.php/Main_Page)

Unfortunately I think they rely on x10 for most things :-S

HTH

---

### Post by jennifer8055 on 2009-01-10
Hi,
If you're looking for a home security system comparison you should check out **[http://usalarmcompanies.info](http://usalarmcompanies.info)** . They give you a free complete comparison of the various home alarm system providers in the US and you can choose one based on the size of your home, your requirements, budget etc.

---

### Post by user123454321 on 2010-05-24
I found [here]("http://www.homesystem.com") some interesting home automation systems .

---

