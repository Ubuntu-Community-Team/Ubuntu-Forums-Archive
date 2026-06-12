---
title: "A Ubuntu Powered Internet Cafe"
date: 2007-11-23
forum: Testimonials &amp; Experiences
---

### Post by gdi2k on 2007-11-23
At the beginning of this month, I went to the Philippines (my wife's home country) to set up an Ubuntu powered Internet Cafe. Now that it's all up and running, I thought I'd share what I did, what worked, and what did not. 
[URL="http://www.flickr.com/photos/33359003@N00/sets/72157602974457983/"]
[IMG]http://farm3.static.flickr.com/2092/1941119136_3d1511bb1a.jpg?v=0[/IMG]
**I kept track of its progress over the week on flickr (click here)**. [/URL]


**Hardware: **
[LIST]
[*]The server is a medium spec AMD Athlon X2 with 2 GB RAM and 4 x 500 GB HDD arranged as a software RAID 5. 
[*]The switch is a run of the mill 10/100 Mbit 24-port 3Com Office switch, with 2 Gigabit uplink ports, one of which I used to connect the server to. 
[*]The workstations are all 2GHz AMD Athlon X2s with 1 GB of RAM, no HDDs. They also feature Nvidia Geforce 7300 GTs for a decent gaming experience. 
[*]We also have a midrange HP all-in-one Printer / Scanner.
[/LIST]

**Software: **
[LIST]
[*]Ubuntu of course!
[*]Plenty of freebie games and programs, mostly from the standard Repos. 
[*]A custom programmed web-based internet cafe management application. 
[*][DRBL]("http://drbl.sourceforge.net/")
[/LIST]

**How it works: **
[LIST]
[*]Once the server is booted, the workstations boot over the network using DRBL. 
[*]Each customer gets a dedicated customer account with 200 MB storage space. It automatically gets deleted if the user doesn't log in for 30 days. 
[*]Users prepay for access - much like a prepaid phone card.
[*]All users' home directories are stored on the server.
[*]The web-based management application keeps track of who's logged into which machine and bills accordingly.
[/LIST]


**Cool Stuff**
[LIST]
[*]We charge by the minute - all accounting is automated, so users can log in to check their email for a couple of minutes while waiting for the bus. 
[*]Users are automatically logged out once their credit is used up, and can't log back in until they've recharged their accounts. 
[*]Users get their own personal desktop with their files, settings, game high scores etc., regardless of which workstation they log into. 
[*]The operator can start up and shut down machines based on demand from the management interface (electricity is expensive in the Philippines). 
[*]Most users aren't bothered by it being non-Windows. They quickly find the Applications menu and it's smooth sailing from there.
[*]Installing new applications / games is just a matter of running apt-get on the server. It then magically appears on the Application menus of all the workstations without the user even having to log out. 
[/LIST]


**Issues**
[LIST]
[*]Webcams in the Philippines are highly sought after, and Pidgin's lack of webcam support is very disappointing - the developers have some strange attitudes towards them. Had to resort to Gyache, which works, but is a little on the ugly side. 
[*]Compiz being enabled by default caused a lot of issues and it took me a while to figure out how to disable it by default. It doesn't play nice with games, and also does it's "white-screen" thing quite frequently. Users don't appreciate the visual effects anyway. 
[*]I'm having mysterious quota issues that I haven't been able to figure out yet. 
[*]The ISP doesn't provide an external IP address, so I've had to create a script which automatically creates a reverse SSH tunnel via a public server to be able to access the server for management purposes. It works reliably though. 
[*]The normal electricity outlets in the Philippines don't have earth / ground. An effect of this is that you get a low-voltage shock when touching the rear panel of the server - can anyone shed some light on why this might be?
[*]Some users miss not being able to play their MMORPPROGRG (or whatever) of choice. I did try Wine, but it's a no go. The Linux alternatives seem pretty weak on this front. 
[*]Linux has about 20 decent FPS games, but not a single decent racing game! 
[/LIST]


**Lessons:**
[LIST]
[*]If you buy cheap keyboards / mice, they come with SHORT cables - this caused a cabling nightmare as the PCs were too far away from the keyboards / mice; a major headache, especially as the nearest computer shops were 3 hours drive in a bus that was likely built before the last world war! 
[*]If you make network cables yourself, get a decent cable tester! 
[*]Power fluctuations are plentiful, the UPS was worth its weight in gold! 
[*]Test everything before installation day - I found dozens of issues during the testing phase which would have been a nightmare to fix on site.
[*]Gaming and social networking sites seem to be the most common passtimes. School work (in OpenOffice no less) is common as well. 
[*]I only had just over a week to do it all, which really wasn't enough.
[/LIST]

It was a hell of a lot of fun, but seriously knackering! 

:guitar:

---

### Post by mellowd on 2007-11-23
Awesome!

About the electricity thing though, if the plug isn't grounded you could possibly ground it yourself by soldering a cable to the main metal part and somehow getting it into the ground.

---

### Post by Dark Hornet on 2007-11-23
WOW!!  Thats great--Is business good?

---

### Post by houstonbofh on 2007-11-23
> **gdi2k said:**
> 
**Software: **
[LIST]
[*]Ubuntu of course!
[*]Plenty of freebie games and programs, mostly from the standard Repos. 
[*]**A custom programmed web-based internet cafe management application.** 
[*][DRBL]("http://drbl.sourceforge.net/")
[/LIST]

Are you interested in sharing that custom app?

---

### Post by Whiffle on 2007-11-23
No electricity providers provide ground, they only provide the two wires required to transmit AC power.  The ground is provided by an 8 ft copper spike driven into the ground near the distribution panel, which is wired to the third prong on outlets.  At least thats how it is over here.

Anyhow, you shouldn't be getting a shock when you touch the case during normal operation, even without a properly wired ground.  Something else is fishy.  What kind of power is in the phillipines anyway, 120 or 240?

---

### Post by erlyrisa on 2007-11-23
Old Australian homes are setup with ground the same way (fat iron spike stuck into the ground near the junction box of the house.

I agree that even without ground you shouldn't be getting a Jolt of E...

I have a theoryy.... and it's more to do with static electricity.

1. PC's aren't designed for tropical climates. Humidity can play havoc on your PC. Consider encasing your PC in a box with a dehumidifier system., or if practical (i Heard electricity prices are high) then closed the doors on the cafe and de-humidify the entire room - dunno hoe that would pan with the locals though.

2 Static shocks off the case can be caused by:
-a. moving part that is stripping electrons (consider the fans)
-b. moving air that is stripping electrons (consider the placement of the case - is placed somewhere the air is constantly rising/falling creating friction around the case)

Solution:
Stop air and mechanical movement. Or ground the bugger. Sadly Static Electricity don't flow like normal Electrcity so grounding maybe difficult... what you need to do is provide a source of electrons to even out the difference.
Take the rubber feet off the case and 'ground it' - if the ground isn't of static quality (wood vs. carpet), consider putting a carpet matt of sutiable potential under the case. (PS. Test the static qualities of the matt by rubbing it with a hair comb, that also worked when you rubbed it in your hair... if it raises paper than it works)

If it's your fans that are passing highly chargeable air, than consider coating the blades on your fans. and the air passages (the metal grills) with a low static material... which would be a pain... but another solution is to put streamers onto the outlets of your main fan. The streamers fly around in the air, eminating the potential charge built up on the case into the air.

---

### Post by gdi2k on 2007-11-24
Thanks for the comments! 

Regarding the grounding:  
Yes, I agree that there really shouldn't be shocks originating from the case, regardless of whether it is grounded or not. It doesn't feel like static though - you get constantly zapped if you continue to touch it - static by contrast would give you a single shock, but once it's discharged, you would be able to touch the surface without further shocks. 

I also thought it must be something to do with the humidity at first, but once we got the AC up and running, the shocks didn't subside despite the cool dry air. 

The workstations do not exhibit this behaviour, but there's only a motherboard, graphics card and PSU in those, wheras the server is fully loaded with 4 HDDs, a DVD burner, plenty of fans etc. 

I have encountered other PCs also in the Philippines that shock from the rear panel, and even the electrician said that his PC does the same. I even have a friend whose aged Asus laptop emits shocks from its metal hinges connecting the screen to the base, so I don't think it's very uncommon, but I can't find much on Google about it. 

I could organize grounding myself, but it would be tricky - the area in front of the shop is fully paved, and it's only rented, so any damage I do must later be undone, and any expensive modifications I do will be harvested by the landlord when we leave. 

For now the solution seems to be to not touch the rear panel until the machine is off...

Patient: "Doctor, it hurts when I do this" [shakes head widly].
Doctor: "Don't do it then."

Quite shocking really... :-?

Regarding sharing the management application: 
It's still very much in the early stages and usability is quirky, but I am already working on the next version. Maybe one day it'll reach a stage where I would like to share it. It's also completely geared to work with the DRBL set up, so probably won't be useful to most people.

[QUOTE=Dark Hornet]WOW!! Thats great--Is business good?[/QUOTE]
Yes, weekdays are busy in the afternoons / evenings, and it's always jam packed at weekends. But because of the economics of the Philippines, I would have to operate 10 Cafes to earn what I earn at my day job abroad - maybe I will one day ;-)

---

### Post by jackflap on 2007-11-24
In regards to no good racing games.. There're a couple of options that I've come across:

- TORCS (use package manager)
- Need for Speed works nicely in Wine. It's also officially supported in Cedega, which has a VERY cheap monthly subscription.
- Ballistics by the LGP. It's a classic Windows game which can also be bought for Linux. [http://www.linuxgamepublishing.com/info.php?id=13&](http://www.linuxgamepublishing.com/info.php?id=13&)

---

### Post by mellowd on 2007-11-24
Unrealt Tournament 2004 has a native linux install. Give that a try. It's not the newest which means they'll run pretty well on those cards

---

### Post by bobbocanfly on 2007-11-24
Very nice :D

This is where Ubuntu shines really isnt it? Bringing inexpensive computing to *everyone*. Like the name ("Cyber Penguin" :D) and the custom management program looks very good. Loved the photo of the guy playing Nexuiz.

---

### Post by tadcan on 2007-11-24
Funnily enough I was thinking what it would like to set up a cafe with ubuntu machines. I had thought a big obstacle would be people adapting from msn/yahoo etc to pidgen. Not having known about the service I was surprised about the webcam.

I presumed the main browsing/documents would be simple enough for people to adapt to. How would you compare the knowledge in the Philippines compared to Europe or the US. I imagine it would be harder in Europe since people have used MS for longer. 

I had been wondering about having people be able to keep an account for customer loyalty. Does it keep up return business. I also prefer the credit system. I hate the €1 euro minuim charge if your there for an 20 mins or an hour.

Do you also have snacks and other services to boost your sales. 

I hope works out. And maybe having a chain is the way forward!:)

---

### Post by mellowd on 2007-11-24
> **tadcan said:**
> Funnily enough I was thinking what it would like to set up a cafe with ubuntu machines. I had thought a big obstacle would be people adapting from msn/yahoo etc to pidgen. Not having known about the service I was surprised about the webcam.

I presumed the main browsing/documents would be simple enough for people to adapt to. How would you compare the knowledge in the Philippines compared to Europe or the US. I imagine it would be harder in Europe since people have used MS for longer. 

I had been wondering about having people be able to keep an account for customer loyalty. Does it keep up return business. I also prefer the credit system. I hate the €1 euro minuim charge if your there for an 20 mins or an hour.

Do you also have snacks and other services to boost your sales. 

I hope works out. And maybe having a chain is the way forward!:)

In the UK its usually 50p for 30 min, £1 for an hour. ridiculous...

---

### Post by sajro on 2007-11-24
> **mellowd said:**
> In the UK its usually 50p for 30 min, £1 for an hour. ridiculous...

It's around $6 US (even when the US dollar was worth anything) per hour in my area. Internet cafes can be ripoffs but I love that charge-by-the-minute idea.

Also, I support the idea stated earlier. You should share that internet cafe software. It could be useful in other applications (eg the computer lab my school is wanting to set up) and people could improve it. It's only right to open-source software made for linux for a special application. There's really no excuse since sourceforge hosts for free.

If you published it I bet someone would make it Win/Mac/BSD compatible in addition to Linux. A universal, free (as in beer and speech) internet cafe/public computer system software. That owuld help open-source adoption.

---

### Post by SouthernPott on 2007-11-25
My electrical background is limited to work I do for myself around the house but I don't see this as a ground problem.

Power to the computer is 120 or 240 volts which connects to the power supply.  The power supply steps it down to 12 volts(or whatever your's is)  plus or minus a little bit for most things.   By your description, something or some wire  is touching the frame of the computer and continuing the path of the electricity.  

My guess is the problem is happening after the power supply steps the power down, otherwise it would be a bigger jolt when you are touching the frame. 

It could be any individual unit, i.e., the power supply has a 12+ connection hitting inside the power supply enclosure(which is attached to the frame), or any of the hard drives or the motherboard have 12+ connections touching the frame somewhere.   One of the hard drives might even have a bad connection inside which is touching its housing, then attached to the frame so you might not see it.  

The next step would be safer to do with a multimeter but if the electrical shock you have been feeling hasn't been super strong you can do the following(if it was strong use a multimeter).

Take the power supply out and plug it in.  Touch the power supply enclosure.  If you get the same tingling unplug it and replace it.  Test the new one the same way before you install it. 

If you didn't get shocked by the power supply enclosure it is one of the other items in the server which you can check by taking one out at a time until you get to the motherboard.    Of course unplug the server  before you remove or reconnect anything.

My guess would be the power supply.  These seem to be the weakest links for quality most times. 

You didn't really qualify the type of shock you are getting and I don't know what your experience is but when my brother and I were kids we used to take a 9 volt battery (the little rectangular block batteries with a positive and negative terminal on the top) and touch it to our tongues.  You get a little continuous jolt/shock/tingle from this.  Too much to do for very long but not enough to scare you from doing it again.  You grab a live 120 volt house wire by accident and it is a much heavier feeling shock that definitely makes you afraid to try that again.  The kind of shock that you feel running through your whole body.

---

### Post by Whiffle on 2007-11-25
What bugs me about the shock thing is that any decent power supply should shutdown if there is a short to ground anywhere inside the computer (ie a loose wire hitting the case).  Also, 12 volts isn't really enough to give much of a jolt on dry un-cut skin (try touching the two terminals of a car battery, no shock there, do it again with wet hands and it may get a little more interesting).  

Still not sure what to think yet...

---

### Post by SouthernPott on 2007-11-25
I agree it shouldn't happen to a quality grounded power supply but this one isn't grounded. I can't speak for certain if the voltage is high enough to cause this.   

What worries me most is the "electrician" says the same  thing happens to his computer and he thinks it is normal.

---

### Post by Whiffle on 2007-11-25
> **SouthernPott said:**
> 
What worries me most is the "electrician" says the same  thing happens to his computer and he thinks it is normal.

yeaaah, that is worriesome.  And the fact that other guys laptop does it too.  If only I could fly over there with an oscilloscope and a meter...sounds like all kinds of fun.

---

### Post by SouthernPott on 2007-11-26
My youngest brother lived in the P.I. for a couple of years and recommends it for vacationing.  Pack up your meters and just show up uninvited.

My brother lived in Angeles City but I think he traveled throughout.  Lots of world travelers there. Several ex-pat Americans own small night clubs and bars.   Lots of retired service people.

---

### Post by mykeldg on 2007-11-27
amazing idea. I live in the Philippines, and this is the first i've heard running opensource alltheway. Just curious on the whereabouts of that Internet Shop. I might drop by if its veritably close from my place. :D

as for the charging rates here in the country, it usually goes for about 0.30-0.50C (US $) per hour. Premium ones (per minute, in-mall cafes) go for a dollar to a dollar fifty tops. Dirt cheap. That is, however, usually ran by a 1mbit-4mbit connection. People here never really complain about the speed so long as it can run their mail clients, youtube and their LAN games. heheh. 


On to the static e- issues, I have experiences of this grounding even when the computer is all plugged out of the socket. I hold that this is a powersupply issue. There are occurances that i plug-out the monitor's signal cable from the unit, and its all gone. But seeing as your shop uses LCD monitors, i have no idea. My best best is to attach a wire from the grounding devices which goes to a ground or any conducting area on which it could dump off these ill effects.


cheers! first post! :D:D:D

---

### Post by houstonbofh on 2007-11-27
About opening the software...  If you want to improve it, opening it is the fastest way to go.  However, I do not feel that you are obligated in any way just because it is built on Linux.  It is a personal choice, and we can still be friends either way. :)

About the ground...  You probably have a pipe somewhere going into the ground.  I would prefer a mounting pipe (Lamp post, or similar) first, a sewer pipe second, and not a fresh water pipe.  All you need is to light up someone while washing there hands!  Lastly, a thin blade of metal could go between the slab and the sidewalk if you have any gap at all.

About the shock...  Sounds like a PS to me as well.  Get a PS tester, [http://www.google.com/products?q=ATX+power+supply+tester](http://www.google.com/products?q=ATX+power+supply+tester) and test some top brands.  It would not surprise me to know that cheap Chinese knockoffs are what is widely available there.

---

### Post by SouthernPott on 2007-11-27
I didn't look at all the pictures before.  You did a great job setting that up and it looks like the customers are happy to have it.  

What city are you in?

---

### Post by W. Irving on 2007-11-27
The issue of getting shocked can happen on any appliance with a metal casing and transformer that is meant to be grounded. As far as I have understood it, the voltage across the chassie and ground should be half of that of the input voltage - either 115 or 55V. I presume this is due to a small leakage through the capacitors just after the rectifiers. But it's never more than a few mere milliamps.
It's more noticeable if you grab something that is grounded while touching the chassis, or touch the chassis with a body part where the skin is thin (which conducts the current through nerves, rather than thru the skin).. such as the underside of your wrist. ;)

I certainly would not recommend a DIY grounding. Contact a licensed electrician, or forget about it. Or.. rotate the mains plug 180 degrees - this might help by connecting the neutral to the chassis instead (which is practically ground).

Well done on spreading the word! :)

---

### Post by Photonic Nature on 2007-11-27
> **gdi2k said:**
> 
Regarding the grounding:  
Yes, I agree that there really shouldn't be shocks originating from the case, regardless of whether it is grounded or not. ...

The workstations do not exhibit this behaviour, but... 

I have encountered other PCs also in the Philippines that shock from the rear panel, and even the electrician said that his PC does the same. I even have a friend whose aged Asus laptop emits shocks from its metal hinges connecting the screen to the base, so I don't think it's very uncommon, ...

I could organize grounding myself, but it would be tricky - the area in front of the shop is fully paved, and it's only rented, so any damage I do must later be undone, and any expensive modifications I do will be harvested by the landlord when we leave. 


U.S. electronics are polarized with a larger blade on one side of the plug. - Most electronics are polarized by proper design regardless of origin and destination.
Chances are that the particular units emitting shocks are connected to outlets that are wired wrong (backwards) - 1 side of the outlet is a return or a neutral while the other is hot.
Thus sending hot current through the circuits that are normally cold or neutral, resulting in current travelling through your body to ground. (a weak ground luckily, otherwise you might be lit up and smoking.)
In building circuit panels that do have grounding you will find that many neutral circuits are also connected to ground locally.

Cheap PSUs are, cheap for a reason and most PSUs that ship with cases or OEM units are of the cheap variety... sorry grounding and a lot of bleeding issues are usually a direct result of inferior parts, especially under heavy loads such as your server... multiple drives being the most power hungry.

As for your conundrum,
1. I would suggest to first check the wiring polarity of the outlet compared to that of the of the other outlets - if same, then the whole building could be reversed and the low power requirements of the clients or possible better quality of their power supplies may not be revealing your shocking experience there. Also, that particular branch could be reversed at the breaker panel.

2. I would try replacing the PSU with the best you can afford and overshoot the wattage requirements of your server (get a 600w or higher PSU)
Power problems cause anomalies which cause certain program / software problems too.

3. How hard, tricky and/or expensive would it be to hammer drill a 3/4" hole in the concrete or blacktop and drive a copper rod in the ground? ...
 And how much would it cost to fill in a small hole like that? - Peanuts!

I'd rather bear that minute expense than have to replace and service my server and possibly everything on the network every time failures occur due to rampant voltage travelling through your server and everything it is hardwired to or random failures of equipment plugged in to that sorry electrical system.
We have electrical codes and standards in place here in the US for reasons just like your are experiencing there. Not to mention the liability issues.

Grounding holes and rods can be driven through Anywhere - inside or outside by drilling through the top surface covering the earth... 
Better to be safe than sorry.  
Drive a rod to a minimum depth of 3 feet for your situation. 

Grounding also tends to hide just how cheap some electronics are by diverting the rampant voltages to ground so you never notice that zap.

Good luck - hope my 2 cents helps ya...  please let me know when you get it fixed and what you found. :)

---

### Post by dnns123 on 2007-12-05
I'm not an expert, but heres my theory...

The one getting shocked is statically charged. Most probably coming from the socks.

---

### Post by kalingking on 2007-12-09
sir good morning. we are an internet cafe that just swicthed to ubuntu os. we are very much new to this linux thing. we would like to ask your help on how to set up an internet cafe manager or pos system. thank you very much. we are located in negros occidental.

---

### Post by ubuntu27 on 2007-12-10
It's really awesome that you opened-up a Internet cafe with GNU/Linux :)
I always dream on doing that.

---

### Post by matthewcraig on 2007-12-11
"Linux has about 20 decent FPS games, but not a single decent racing game!"

Check out Ballistics.  And of course, Supertuxcart and Tux Racer.

---

### Post by gdi2k on 2007-12-11
Thanks for all the responses! Sorry about the slow reply, I've been hellishly busy (at work sadly, not at the Internet Cafe!). 

[QUOTE=tadcan]How would you compare the knowledge in the Philippines compared to Europe or the US. I imagine it would be harder in Europe since people have used MS for longer. 

I had been wondering about having people be able to keep an account for customer loyalty. Does it keep up return business. I also prefer the credit system. I hate the €1 euro minuim charge if your there for an 20 mins or an hour.

Do you also have snacks and other services to boost your sales. [/QUOTE]
I would say people have less computing knowledge than Europeans and Americans, which means they're not as set in their Windows ways yet. Most people didn't seem bothered by the different looking interface. Barely any customers I talked to had ever heard of Linux!

I think charging by the minute does increase loyalty for a number of reasons: 
[LIST]
[*]People don't feel they're being ripped off.
[*]People log off when they're finished, not when their credit is up. If they need a couple more minutes, they can just add a bit more credit - it's not wasted.
[*]Because users often have some leftover credit at the end of their session, they're more likely to return to use up their credit next time they want to go online rather than to go to another Internet cafe.
[/LIST]

**Snacks & Other Services: **
We'll start serving soft drinks soon, maybe snacks at a later date. Apart from that, just the usual printing, scanning, burning, etc.

**Power: **
Wow, lots of wise discussion about power. I'd completely forgotten about plugs being polarized since Physics classes a few moons ago. I'll try spinning the plug around and see if it makes a difference. Will report back!


[QUOTE=mykeldg]amazing idea. I live in the Philippines, and this is the first i've heard running opensource alltheway. Just curious on the whereabouts of that Internet Shop. I might drop by if its veritably close from my place.[/QUOTE]

[QUOTE=kalingking]sir good morning. we are an internet cafe that just swicthed to ubuntu os. we are very much new to this linux thing. we would like to ask your help on how to set up an internet cafe manager or pos system. thank you very much. we are located in negros occidental.[/QUOTE]

We are in Negros Oriental, which is the opposite side of Negros Island to Negros Occidental, so not too far from you, kalingking. We're in Guihulngan to be precise. 

Regarding the application:  It's custom made to work specifically with DRBL, so it won't work with normal Ubuntu PCs booting off their internal harddrives. 

In terms of POS, the operator just creates a new account with however much credit the customer wants on it. The system spits out an account number and password. Internally, the web application sends a command to the server (on the same machine) to create a new account, create a random password and set quotas. It stores the credit level in a MySQL database. 

Each minute, the server "pings" each workstation to see if it's on, and if so, which user is logged in. It then deducts credit until there is no more, at which time it disables the user account and sends a command to the workstation to ["slay"]("http://freshmeat.net/projects/slay/") the currently logged in user. 

**To Open or not to Open? That is the Question...**
I'd rather not open source the management application just yet as I'm not sure what direction the project is going to take. If I decided to open source it, I wouldn't have much of a competitive advantage should I decide to pursue it commercially with more seriousness. 

Most software-based business do the same: Canonical (the commercial sponsor of Ubuntu) for example supports Open Source fully, but needs to retain some closed source bits to remain in business over the long run, such as its Launchpad and Landscape offerings. Google is another example - it contributes massively to open source both in terms of code and money, but certainly wouldn't open source its internal server management applications, Google File System or search algorithms. They're critical to Google's competitive advantage and existence. 

What's better: a company that supports open source, but has some bits of closed source software of its own, or a company that open sources everything and then goes bust? I think open and closed source software of all kinds will continue to coexist for the time being, which is probably healthy. 

Hopefully this won't cause too much heated discussion, but if so, keep it clean! :popcorn:

---

### Post by cocoyriv on 2008-02-21
This is with regard to the shock you are experiencing from the back panel. I did not read through all the replies so im not sure if somebody has come up with my suggestions. If you touch your panel and any bare part of your body touches the floor or wall, say your feet, and you experience shock then that's a grounding problem. Otherwise, its static electricity. Humidity is static friendly. If its humid then you experience less of the static electricity. Dry air is static electricity's friend. Anyway, your electricity meter should be grounded. You can wire up your grounding to that. But if its connected to a water pipe then I should say not to do it. That's rampant in the Phils. I should know ;). You wouldn't want to shock your neighbor while he's bathing. :lolflag: Regarding your whole setup, it rocks! :guitar: Its always been my dream to setup one "open" cafe. Finances seem to point to a different direction. :D Well, goodluck!

---

### Post by gdi2k on 2008-03-08
Just thought I'd post back about the earthing issue (touching the back metal panel of the server results in an electric shock). 

I tried rotating the plug around to change the polarisation, but it made no difference, still the same issue. I'm not in the market for installing a proper earthing solution, so I'll just have to live with it. 

Interestingly, I've moved flats recently (I'm in the Middle East), and now I've got the same issue intermittently with my normal desktop. What I've found out: 

[LIST]
[*]The shocks come from the monitors, not the PC's PSU - if the PC is unplugged, I still get a shock if either of my screens is plugged in, and if both are plugged in, I get twice the shock.
[*]I'm using UK -> European Adapters that say they're made in the UK, but are probably made in China. I suspect this is where the earthing issue lies.
[*]It's particularly annoying as my whole case is metalic, including the power button. I've taken to turning on my machine with a tissue.
[*]If I touch metal bits of the screens, I get a shock too (only on certain parts of the casing)
[/LIST]

I think I can solve my issues by using proper 3-pin UK plugs without converters, through high quality extension boxes - I imagine the sockets are properly earthed here - it's a brand new building.

---

### Post by BatsotO on 2008-03-23
Bad grounding is bad for any electric devices live time, We once installed vsat with complete cpu and the company demanded that the grounding must be below 0.3 (ohm I suppose). For that reason we have to drill 2 holes in the ground to reach water (artesian well, short like that), plant copper bars in those holes, connect with grounding cables to an arrester and the main circuit breaker.
 I get electric shock from the pcs in that building , but not from my installation.
I don't know if this suit you, but you can dig a hole in the paveway and covered it with cement.

---

### Post by yoshimira80 on 2008-04-07
I too am *planning* to open a cyber cafe in the Fils. I plan, also, to use Ubuntu because of its security and overall AWESOMENESS (LoL)

I'm printing and saving your post for future refference. but I'm wondering if you have any more specific advice on setting up the network. (e.g. that custom software you mentioned)

---

### Post by earthpigg on 2008-12-30
shameless bump for an awesome thread. hope no one minds ;)

---

### Post by hyperdude111 on 2008-12-31
Good luck, you will be saving quite a lot of money on ubuntu and hopefully your customers like it.

---

### Post by ebug on 2009-01-03
Found this.
[http://ubuntu.icafebusiness.com/](http://ubuntu.icafebusiness.com/)

and this,
[http://linuxcaffe.ca/node/23981](http://linuxcaffe.ca/node/23981)

How about this,
[https://blueprints.launchpad.net/ubuntu/+spec/cafebuntu](https://blueprints.launchpad.net/ubuntu/+spec/cafebuntu)

---

### Post by jpmelos on 2009-01-03
Congratulations on the iniciative. :D

I don't know if such thing would work here in Brazil. Probably wouldn't. :(

---

### Post by ebug on 2009-01-03
Any idea if thin client will work for internet cafes?

[http://www.linuxdevices.com/news/NS6372429785.html](http://www.linuxdevices.com/news/NS6372429785.html)

[http://www.linuxdevices.com/news/NS6828123924.html](http://www.linuxdevices.com/news/NS6828123924.html)

---

### Post by hyper_ch on 2009-01-16
btw, if you run hardy, have a look at [http://www.playdeb.net](http://www.playdeb.net) - to get a few more games ;)

---

### Post by stchman on 2009-01-16
> **hyper_ch said:**
> btw, if you run hardy, have a look at [http://www.playdeb.net](http://www.playdeb.net) - to get a few more games ;)

Can you download the games directly off playdeb.net like you can off getdeb.net?

---

### Post by hyper_ch on 2009-01-16
you can add playdeb as repository and use synaptic/adept/apt-get/aptitude ;)

---

### Post by badrra on 2009-02-25
You might want to look at this site here. This might be of help to you and all you believers out there. 

[http://pinoygeek.org/forum/index.php/topic,703.0.html](http://pinoygeek.org/forum/index.php/topic,703.0.html)

Its kinda long cause its all contained in one long notes of what I encountered along the way. It basically highlights some of the games I installed on my Ubuntu machine. Maybe you can add more to it. 

Would appreciate that very much.

---

### Post by Thelasko on 2009-02-27
A ground wire should definitely be used.  This is likely the reason for your problems.  [Grounding to a water pipe]("http://en.wikipedia.org/wiki/Ground_(electricity)#AC_power_wiring_installations") should be fine as long as the water pipe is metal, copper is best.  Do not do this with PVC water pipes!  Also, make sure the pipe is metal all the way to the ground, and that at least 10 feet of it runs under ground.

What kind of [plugs do you use?]("http://en.wikipedia.org/wiki/Domestic_AC_power_plugs_and_sockets#Proliferation_of_standards")

P.S. Never mind about the plugs.  Tell me about [these blue pipes.]("http://www.flickr.com/photos/33359003@N00/1902217486/in/set-72157602974457983/")  Are they plastic?  They are usually metal.  The metal provides the ground.  The third prong on the outlet should be connected to the pipes using a screw.

If those pipes are plastic, an extra wire needs to be run through them to provide ground.

Your outlets appear to provide for a ground, but your electrician didn't hook them up.  It's his job to provide one, even if the rest of the country doesn't have it.  All he needs to do is connect that third prong in the outlet to something metal that sticks in the ground.

P.P.S. Congratulations on getting your business up and running!

---

### Post by mkvnmtr on 2009-02-27
An experience I had about 40 years ago might find your shorting problem. I had a travel trailer burn. Before I could rewire it my father jumped in with a friend and did it. I had told him that the polarity had to be the same on each connection but he did not understand. Thus in some places he didn't connect the white wire to the white wire but reversed the polarity and connected to the black wire. With this you would get a shock whenever you touched anything metal. There was no short. It seems if the people that installed the cabels in the shop reversed a wire when hooking up a switch or outlet plug this might give you the problem. Checking this would require cutting the power and using a multimeter with 50 foot long leads. Lots of work. but it amy not be your equipment.

On the other front I then what you have done onyour cyber cafe is great. Best of luck

---

### Post by GrfyGrumpyBear on 2009-03-20
Try SuperTuxKart for racing

---

### Post by motang on 2009-03-22
Wow...that is really cool.  Since it all automated with the billing and stuff it really makes it very easy for you guys and gets the headache of managing it for ourselves.  Congrats on the setup.

---

### Post by punong_bisyonaryo on 2010-10-18
Is the cafe still in operation? Just wondering how things on both the software and business side of things have been developing e.g. Has business gotten any better? What are the top games that people play? Any open MMORPG that you're running now? What new service are you offering now? Do you use only LTS versions or upgrade everytime a new version comes out? Etc.

Great job on the internet cafe. I sincerely hope business couldn't get any better for you.:)

---

### Post by punong_bisyonaryo on 2010-10-18
> **stchman said:**
> Can you download the games directly off playdeb.net like you can off getdeb.net?

Playdeb was created by the guys that did getdeb. They should function basically the same.:)

---

### Post by gdi2k on 2010-10-19
Hi Punong, 

Yes, the cafe is very much still in operation. We relocated down the road next to a school and close to a couple of others some time ago. Business is fine, although quieter during the school holidays. The hardware has aged well - still as snappy as day one, and no complaints about speed compared to those using Windows!

I switched to RAID6 from RAID5 on the server after getting burnt by a failure during a rebuild. The real world failure rates of hard drives has been eye opening. I've started buying the disks locally so I can at least claim on warranty if they fail within a year, which I've been able to do a number of times. Perhaps commercial grade disks are priced higher for good reason. 

All of the original graphics cards have failed, but I suspect I just had a bad batch because none of the replacement cards have ever given me any trouble. Aside from that, just the odd mobo or power supply goes. 

On the software side, I upgrade to the current version whenever I'm over there, not necessarily sticking to LTS releases. Currently it runs 9.04 I think, and things are fine. 

Game-wise, the FPS genre remains popular, especially Urban Terror and the like. There are tons of arcade-style flash games online that are played a lot too, as well as the online-only MMORPGs. I did install a few native Linux ones, but they didn't take off really. A couple of the Linux RTS games are popular though - Glest and one other whose name I can't remember. People don't seem interested in any sort of racing games - odd to me, as that's all I really played growing up aside from Quake and whatnot. 

The rise of Facebook has changed the nature of the place quite a bit - much more facebooking and casual / social facebook gaming (Farmville!) than hardcore gaming. YouTube has also become a lot more popular since we finally got DSL at the beginning of the year (it was simply too slow through the SmartBro wireless service) - not just garbage either, a lot of educational stuff too. 

Sadly the pathetically unreliable power in the area puts a damper on things at times. It's much worse now than it was a couple of years ago; we generally have one outage per day, plus scheduled Sunday outages every couple of weeks. Random full day outages are not unusual. It's dire, but I don't fancy powering it all from a generator. What century are we in!? ;-)

---

### Post by earthpigg on 2010-10-19
> **gdi2k said:**
> It's much worse now than it was a couple of years ago; we generally have one outage per day, plus scheduled Sunday outages every couple of weeks. Random full day outages are not unusual. It's dire, but I don't fancy powering it all from a generator. What century are we in!? ;-)

do you think that getting a generator and charging more (for gas, etc, and because you have a temp monopoly) while city power is out has the potential to pay off?

---

### Post by gdi2k on 2010-10-20
It's a good idea, but not that straightforward; we're on the opposite side of the street to the Barangay (district) Market, which is a building that houses the town market and shops, along with local government admin offices. This building has full generator backup (courtesy tax payer), the power of which is provided to all tenants during blackouts. There are two internet cafes in this building and because they don't have to pay anything extra for the generator power, they don't raise prices during blackouts, and neither could I. But I would have to pay for running my generator, whereas they don't. Life isn't always fair ;-) 

Talking of fair, no Windows-based internet cafes around here pay for licensing for their OS, Office Apps or the hundreds of games they offer. On the other hand, they operate at the risk of being caught, while I can sleep at night.

---

### Post by kangarooks on 2010-10-26
Hi

Congrats on awesome project, I hope business side of it will be just as awesome :)

I created myself from scratch similiar system to yours, ([&#8594; http://pleasanthacking.com/2010/09/29/gaia-system/]("http://pleasanthacking.com/2010/09/29/gaia-system/")) that gives my all windows desktops university a viable linux desktop system. I was wondering, do you by chance know how DRBL handles multi desktops from one source? 

Is it via nfsroot from all nodes? Does DRBL exports all nfsroots as RW from server and all mangling of making one source distro on server appear as one on desktop, being handled by the server? Or maybe there are multiple copies of the same desktop system stored on the server?

When I was building my Gaia system I wasnt aware of this functionality of DRBL, I thought it was mainly for making mass backups of hdd's, so I kinda am now curious, and I didnt find any architectural overview in the documentation on DRBL site.

Once again congrats on the system =D>
Hope you'll like mine too &#8594; [http://art.ubuntuforums.org/showthread.php?t=1605988]("http://art.ubuntuforums.org/showthread.php?t=1605988")

---

### Post by gdi2k on 2010-10-27
Hi kangarooks, 

Sounds like an interesting project you've got going there! 

DRBL can be run in a few different modes - for these sorts of setups, Full DRBL mode and Simple System Image mode are the relevant ones. 

With Full DRBL, each client has its own set of directories similar to how they would appear on a full client locally. This means you can configure each machine differently from the others. If you have some clients with ATI graphics and some with Nvidia for example, you probably want this this. Of course this takes up more space on the server, but it's highly configurable. 

With Single System Image, the system image for all clients is the same (although you can make some small changes to things like /etc without too many issues I think) and as such, takes up only one image worth of space. 

Either way, /home is always on the server, so no matter what machine anyone logs into, their home directory will always be mounted correctly with all their stuff. 

The system differentiates between clients based on MAC address and has a wizard for collecting all the addresses from the systems automatically so you don't have to type them in yourself.

Best just give it a shot and have a play. Instructions are [here]("http://drbl.sourceforge.net/one4all/") and Steven on the mailing list is very helpful.

---

### Post by ubunterooster on 2010-10-28
Very nice!

---

### Post by Omnomnom on 2010-10-29
Haha sweet! How'd you deal with all the old people wondering what an ubuntu is and if it's a kind of chocolate bar?

---

### Post by cabetza1 on 2011-06-10
I have and Internet cafe in cancun, 1 pc for 5 station, with userful multiseat and the other 4 with usb boot and share home with nfs, you can see video in the link  [http://www.youtube.com/watch?v=Fdxy_XW2r0M](http://www.youtube.com/watch?v=Fdxy_XW2r0M) for the control I use a coin collector with usb timer, so I just have to give change, like you, I decide that my customers can insert the minimun time (no 1 but 3 minutes) with the small  coin value. I just  install DRBL SSI unstable with 1 NIC with alias for test, internet is fine but can't play games some facebook games get gray moments (I use for the test old pentium 4) when you say 
> "With Full DRBL, each client has its own set of directories similar to how they would appear on a full client locally." 


¿The user can keep log-in his session in any station and keep his files?
¿you can have different mother board?
Can you say in you installation:
¿how many machines?
¿how many NIC on the server?
¿You use server as station also or is dedicated server?
Thanks in advance.

---

### Post by gdi2k on 2011-06-11
Yes, we generate a unique username / password for each client. This makes sense for us as it is not a tourist area and most business is from regulars who appreciate this feature. As the /home directory is stored on the server with DRBL, it doesn't matter which workstation the user logs into - his / her home directory is always mounted there. 

We do use some different motherboards and some different graphics cards, but all AMD CPUs and all Nvidia GPUs. 

15 machines
2 NICs in the server (one for the DRBL network, one for the web)
Server is dedicated and runs the billing software (new account creation, adding credit etc. - we don't have any automated coin machines). 

Hope that helps!

---

### Post by trekrem on 2011-06-12
I'd like to view the images on Flickr, but access is restricted.

---

### Post by Sef on 2011-06-14
Locked. This thread is old and needs to permanently sleep.

---

### Post by bapoumba on 2011-06-15
Sorry Sef, I reopened.
[http://ubuntuforums.org/showthread.php?t=1783249](http://ubuntuforums.org/showthread.php?t=1783249)

The OP did actually come back to answer, which is quite nice :)

---

### Post by armandh on 2011-06-16
and a final word on those pesky shocks

those computers that do not exhibit schocking behavior likely have good grounds

[and those that do shock likely do not have good grounds]

as for back up [generator] power
one must gauge the lost revenue VS the cost
chances are you are probably well off with just enough ups to shut the servers down

---

### Post by coolnezz on 2012-04-20
Please don't lock this thread.  I for one would like to run my own internet cafe someday.  This thread has a lot of useful information.

---

### Post by tmaranets on 2012-04-20
Epic, awesome, cool, and linuxy. Can you open up some other locations?

---

### Post by sffvba[e0rt on 2012-04-20
> **coolnezz said:**
> Please don't lock this thread.  I for one would like to run my own internet cafe someday.  This thread has a lot of useful information.

The purpose of this area isn't for support.  I am sure you can still read this thread when it is closed and ask support questions in the relevant support areas.

Thread closed.


404

---

