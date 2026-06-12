---
title: "Wifi Security???"
date: 2006-03-06
forum: Server Platforms
---

### Post by mikedtemple on 2006-03-06
Ok- I'm not sure if this is the place to post- and it has nothing to do with Ubuntu in particular, but I was hoping a few people can weigh in on this for me...

I'm a big open souce advocate- but now, I'm being torn in two.  I currently pay about $55/month for broadband internet.  I host a small site for my own use on a ClarkConnect Linux box, which serves as a local fileserver and access portal for my MythTv box and some Home Automation Equipment I run at home, as well as a photo server for family and friends.  I run Ubuntu on my MythTv box, and dual boot Ubuntu and WinXP on my desktop (My work uses Microsoft VPN, and I haven't figured out a clean routing table, else I'd be all Linux).  All is good, I run lots of open source stuff.  :-D 

Problem is, I also have a Linksys WRT54G runnning as an AP for my home.  I started notices some serious QoS issues, when I found some neighbors piggybacking on my connection.  Once again, I'm an open source guy-  No big deal.  Let's share!!  Yeah right- it's getting to be a bit too much at this point.  I've noticed a 40-45% reduction in Bandwith at times.

Now, I'm a reasonable guy, and I like the fact that I have an open AP to share, but this is getting to be a bit too much.  Things are locked down, the AP is on it's own Subnet- so Im not super concerned about being hacked- I just want some of my bandwith back!!!  I've heard about using openWRT and the like to dial some people back using filtering- does anyone have experience with this?  How would you handle?  Is it worth going to knock on my neighbors doors or should I just lock it all down entirely?

---

### Post by soce_32 on 2006-03-06
Please do not confuse Open Source with open security policies. You should not allow other people (especially strangers) to use your WAP regardless of your feelings about software licensing.  Even if you are not concerned about your computing resources, you need to understand that if one of your neighbors is downloading copyrighted/illegal content, you will be legally responsible for those actions.  You should check with your ISP and see if they have any policies regarding running an open AP if you choose to trust your neighbors and continue with this setup.

I doubt that "It wasn't me, I was running an open AP" will float as a good excuse in the event that any questions arise regarding downloaded content.  Your ISP will clearly be able to pin down times and IP's and account names and trace your neighbors' actions back to you.  Are you keeping logs of MAC addresses that could possibly exhonerate you in the event of an abuse investigation?

You should lock your WAP down with the strongest encryption it has available, and use a good password to protect it.  It would also be better to hide the SSID so that it's not broadcasting to the neighborhood about its presence.

---

### Post by mikedtemple on 2006-03-06
Thanks for the reply-  although I do not confuse open source with open security- I do see a benefit of sharing wether its code or bandwith- and yes, I do log MAC addresses as well as connection info.  My guess is that someone is running a game server or downloading via bittorrent.

Its too bad that if you're trying to benefit others you end up getting screwed in the long run- looks like I'm going to end up locking everything down tonight- it's a damn shame too, but you're right about illegal content and such.  Thanks for weighing in.

---

### Post by Endwin on 2006-03-06
Another thought is if you do want to have an open AP is to just set up some rules and limit the bandwidth.

For instance since your AP is on its own subnet you could throttle the amount of bandwidth it uses with some program (I think IPTables can do this) You could then block all ports the AP uses but 80 for web and 23 for mail. Or some other combo you are comfortable with. That way they can browse the net, and the use of other programs for illegal purposes is greatly reduced. (Mind if someone is sufficiently skilled and wants to take the time they will just patch whatever traffic they want through the ports you do allow) However it is a thought and might be worth playing around with.

---

### Post by Corvillus on 2006-03-06
Also, with the WRT54G (providing it's one of the Linux based ones, not the new V5 which is crippled), you can install custom firmware on it that will give you extensive QoS controls, such as packet shaping by service, or packet shaping by MAC address (so you could give all the mac addresses of your devices and people you trust high QoS and everyone else low QoS). OpenWRT is probably the most powerful one, but you have to configure everything via a shell, if you prefer a web based interface, DD-WRT is probably the best one to use

---

### Post by mikedtemple on 2006-03-07
Thanks all!

In the meantime- I locked everything down- it's a v3 router I purchased 2 years ago, so it's Linux based- I'm a little worried about bricking it though by installing new firmware.  The warnings on the sites are quite serious for both DD-WRT and OpenWRT.  Have you had any experience with installing them?

---

### Post by towsonu2003 on 2006-03-07
instead of bothering with firmware, why not get a very old computer and install [http://distrowatch.com/table.php?distribution=ipcop](http://distrowatch.com/table.php?distribution=ipcop) ipcop on it? than, of course, read read read and configure configure configure... but at least it's not firmware you're messing with, just an old computer.

---

### Post by SBFC on 2006-03-08
[QUOTE=Corvillus]Also, with the WRT54G (providing it's one of the Linux based ones, not the new V5 which is crippled)...[/QUOTE]

What do you mean crippled? I just got one of these routers and it's a v5...

---

### Post by mikedtemple on 2006-03-08
[QUOTE=SBFC]What do you mean crippled? I just got one of these routers and it's a v5...[/QUOTE]

the new Linksys Routers don't use a Linux Kernel inside them any more and are, from my understanding unable to be modified like the older ones.  To get the "hackable" Router I think you need a WRT54GL and not the WRT54GS v5.
I'm sure the GL is more expensive too, because it's a "hobbyist" router.

My ClarkConnect Box acts as a gateway- that's why the Wireless Router acts as an access point, I suppost I gould start messing with iptables and really shaping access resctrictions and such.

---

### Post by seekyrr on 2006-03-08
I installed WRT, and it was my first time messing with firmware.  Follow the directions and make sure u enable Boot-Wait.

I have a V4 and set it up as a Kismet Drone ..I love it.

While haveing an "open" AP is friendly to your neighboors, its is a pretty big pain and security risk.  They can be useing your connection to make attacks, and it will trace back to your Modem/DSL account..makeing u responsible.

Seek

---

### Post by sadjack on 2006-03-08
You want to share your connection with others! Are you mad? Do you understand the implications? What if they are downloading illegal images and storing them on YOUR hard drive without your knowledge? Its a minefiled. Lock it down as much as you can and change encryption & passwords on a regular basis. Am I paranoid? you betcha, the Internet is like the wild west!

Seriously, protect yourself as much as you can. There are some scary people out there who may not just be your neighbours!

---

### Post by towsonu2003 on 2006-03-08
[QUOTE=sadjack]Are you mad? Do you understand the implications? What if they are downloading illegal images and storing them on YOUR hard drive without your knowledge?[/QUOTE]
I think you just went off the board there... If someone out there has the itention to get into your wifi network and do stuff, he'll do it, regardless of encyption etc. Encryption will only function as "now you know I don't want you here" message. 
if he has the ability to crack the network + get into the hard drive from that network, the encryption won't help a bit. 
the OP wants to open his/her wifi, that's his/her decision. you don't have the right to go like "are you mad" etc. not being rude and respecting others' decision is usually a good idea. Being constructive, on the other hand, is priceless...

@OP: IMO, an opened up network is a nice gesture, however it brings responsability. you need to set up a firewall so that they don't eat your bandwith (ipcop), and sniff your own network (ethereal) to make sure illegal activities do not occur. If you think you sniffed an illegal activity on your network using ethereal, make sure to notify legal auhorities and save the file. Ethereal should help with that. other than that, I like your concept of sharing...

---

### Post by mikedtemple on 2006-03-09
Thanks for the info, I really appreciate it-right now I locked everything down, I'm going to revisit things with some more security measures and bandwith shaping/QoS shortly.  Thanks for everyone's input.

---

### Post by sadjack on 2006-03-11
MMM, interesting concept this. Open networks are good.

About as good as leaving your car open with the keys in the ignition whilst you went shopping. It would be a nice gesture.

Yes encryption can be broken. Doors can be jemmied and locks picked.

I do believe that we have a responsibilty to keep ourselves as safe as possible, especially if we keep sensitive data on our machines.

Simple sensible precautions in our everyday life keep us safe. Computers and networks are becoming everyday life for a lot of people. Simple sensible precautions to protect our data should be as normal as in every other facet of life.

If using the phrase 'are you mad' upset anyone I unreservedly apologise. However it was used, I thought, tongue in cheek as one would over a pint with your mates.

---

### Post by JoWilly on 2006-03-14
[QUOTE=sadjack]MMM, interesting concept this. Open networks are good.

About as good as leaving your car open with the keys in the ignition whilst you went shopping. It would be a nice gesture.

[/QUOTE]

lol, :mrgreen: :mrgreen: :mrgreen:

Jeeezzz sadjack, you made my day !

---

