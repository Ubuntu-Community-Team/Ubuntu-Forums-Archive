---
title: "Best way to add wi-fi to Wild Dog Pro?"
date: 2016-11-14
forum: System76 Support
---

### Post by ShowMeGrrl on 2016-11-14
Hello - I have a System76 Wild Dog Pro bought in August 2016 running Ubuntu 16.04LTS. It's got plenty of RAM and chip power.  I foolishly decided not to order internal wireless with this machine, since I connect it to the router via an ethernet cable and that seems to work well. 

However, the problem is this. I have TWO wi-fi networks in my home. One is the cable TV provider's wi-fi network and the other is the wi-fi on my router. My TV set is hooked up via ethernet cable to the cable provider router/modem, which is connected by ethernet cable to my router. My husband's Mac desktop is also hooked into my router via ethernet cable. The wi-fi is basically used only by our cellphones, laptop and tablet.

I recently installed Plex on my desktop, hoping I would be able to display photos from my desktop in my study on my TV in the living room. But while Plex allows me to display the photos on the laptop and on cellphones, as long as they are all on the same network, I cannot get the TV and the desktop communicating. Neither TV nor desktop has wireless functionality. My TV, by the way, has a TiVo DVR with a Plex app on it. I'm thinking that if I added wi-fi capability to my desktop, it would allow the desktop to communicate with the TV. If nothing else, I could use Google Cast (formerly called Chromecast, then Google Cast and now called Google Home) to cast stuff from my desktop to the TV. 

So my first question is what is the best way to make my desktop wi-fi compatible. As far as I know, there are three solutions:
1) Add wi-fi internally. (This scares me a little since I'd have to open up the box. Also wouldn't I have to configure the card? And which card should I get?)
2) Add a USB wi-fi dongle to my desktop (I'd have to figure out a compatible dongle and configure it properly)
3) Do a wi-fi to ethernet bridge in the router (This sounds good to me since I wouldn't have the problems I'd have with 1) and 2), but I don't know the first thing about how to do this bridge thing).

The interesting thing is that my TV's Plex app did recognize my Wild Dog Pro. I went through the steps of logging in and was told by Plex that I was "all set" as regards linking the TV to my desktop. However, I could never get beyond that step, instead receiving an error message that there was some unspecified problem with the connection. Our view is that the problem was that the desktop was on my router network and the TV was on the cable provider network. However, I should say that my desktop is able to transfer stuff via ftp (Filezilla) to my cellphone when my cellphone is on the cable provider network. At first I thought the reason Plex on my TV couldn't get photos from my desktop was a permissions problem, but the fact my laptop and cellphones had no problem using Plex to display my desktop photos I think indicates there was no permissions problem.

So my second question is: Do you think adding wi-fi capability to my desktop will solve this problem?

A side note: I actually was able to move photos to Google Photos on the web and then use the Google Home (aka Chromecast) to cast them to my TV on the TV's network (the cable provider network).  However, I'd rather get the photos directly from my PC to the TV and not have to go through Google Photos.

---

### Post by untrustytahr on 2016-11-16
Ok, so first things first...

Unplug the Mac.  Both the network and and AC power.  Put it in a box and hike to the top of Rainier and toss it over the edge.  The world has problems and we all need to do our part to make it a better place.:wink:

Now that that's out of the way... I was reluctant to respond because it can really be a can of worms...

Let me start by asking why you have two routers in the first place?

I'm guessing you have the LAN side of the cable router/switch plugged into WAN side of your router/switch.  There's nothing 'illegal' about this but it does create separate subnets within your home.  I'm not familiar with Plex, but most applications like it use what are called 'broadcast packets' to discover other devices on the network.  Routers by definition stop broadcast packets from propagating through themselves.  The good news is:  if you don't really need two routers, you most likely could just reconfigure what you have and all devices would be on the same network(subnet).

---

### Post by ShowMeGrrl on 2016-11-28
Hello untrustytahr! We have two routers because two desktop PCs connect by ethernet cable to one router, while the cable router, TV and TiVo are in a different part of the house. Our phones and laptop can use the wi-fi on either router depending where we are in the house. I don't know if having two routers is necessary, but it's worked well for us -- EXCEPT for trying to get the Plex app on our TiVo to connect to the Plex server on one of the PCs.

Your guess about the cable router being on a different subnet from the PC router is right on and was very helpful to us. Using that information, we have made quite a bit of progress. We still haven't quite gotten there, but we understand our networking much better and I think we will get to a solution soon. Thanks for the help.

---

### Post by untrustytahr on 2016-11-28
Glad to hear you're making progress.  In a nutshell, you want to use your second device (your personal router/switch) as a switch and forget about the router functionality since you don't need it.  You do that by plugging the wire FROM the cable modem LAN into the LAN side of your device (the side with the 4 ports) not the WAN port.  You then configure your device with the same network information as the cable modem (most likely 192.168.0.0 mask 255.255.255.0).  Make sure the second device has a different IP address than the cable gateway The cable gateway will probably be 192.168.0.1 so you can make it 192.168.0.2 (assuming that it's not already being used)...If you fail to do that we'll be reading about you in the morning papers as authorities haul you away to the local asylum.  If you have AP isolation, make sure it's turned off.  That'll ruin your day too.  Be sure to turn off DHCP on the second device as well because you don't want duplicate addresses being handed out.  

This guide should get you through it: [http://www.labnol.org/software/add-router-to-wireless-network/19716/](http://www.labnol.org/software/add-router-to-wireless-network/19716/)
Nothing special, just the first one I clicked on and looked correct.  You can google your own "Extending wifi with old router".

After you have that setup, force your devices (TV's, computers, phones, etc) to get new addresses.  This is just to make sure that there are no duplicate addresses.  All of your devices should now be on the same subnet and should be visible/pingable.

One caveat about mixing hardware: If you have different aged hardware, your system won't perform at peek performance.  Usually the older stuff is slower so it could be a bottleneck, but since you weren't complaining about speed the way it was before, it most likely won't be an issue.  You probably won't notice by browsing, but if you start pushing large GB files around the network to different computers, you might.

If all else fails, find the local neighborhood geek and give him/her a few bucks to set it up.  It has the dual benefit of teaching a good work ethic as well as showing that their knowledge has value in the world.

---

### Post by ShowMeGrrl on 2016-11-28
We actually did everything that you suggested here: we configured the router to be a switch, and it worked! We got TiVo's Plex app communicating with the Plex server on one of our PCs. However, a friend of ours strongly urged us not to take this approach, because we would lose the security of having our PCs behind a second router. She now is proposing to install a NIC in my PC, which hosts the Plex server. System76 Support has assured me that installing the NIC should be a trouble-free, simple process. Thanks for your help, untrusty tahr! And let's hope that this thread may help others at some point with their networking questions.

---

