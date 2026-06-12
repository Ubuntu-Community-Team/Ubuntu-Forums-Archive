---
title: "My dream server - Where should I start?"
date: 2006-02-01
forum: Server Platforms
---

### Post by RAZZ on 2006-02-01
Hi, I'm new! :)

Please don't kill me if I made some kind of obvious mistake.


About me:

I am new to Linux, but not computers. I have been playing around with them for about 20 years. Sadly, I suck at anything related to networking. I mean really, really suck. Like, I kind of know what an IP is - kind of. Thats about it.
I am one of those windows users that tend to complain about windows alot.
I am not afraid of learning. Command promts don't scare me one bit.
I don't have money.


This is what I have:

1 blazing fast celeron 300MHz, that *can* run 450MHz if needed.
1 nice BX board from Abit.
A whooping 384 MB of RAM.
a 4GB hard disk.
DVD drive/burner.
nVidia TNT2 graphics card.
2 D-Link 10/100 net cards.
All installed with Ubuntu 5.10, AND connected to the internet (I am so proud of myself :) ).
1 Switch.
A poor internet connection (1Mb downstream/128Kb up. Up to 2 dynamic IPs).
Time.

curent network:
2 windows xp workstations, that are always connected.
1-2 laptops that come and go.
1 future linux labtop.


OK, for starters, I intend to connect 1 net card to the internet, and the other to the switch.


This is what I would like it to become:

1: A server that could manage my poor internet connection, so I could connect more than 2 computers to the internet. I would like it to be able to automatically hand out IPs (and/or what else is needed) to any computer (and any number of computers) I might plug in to the switch.

2: I would like the server to run emule (and probably other internet-intensive software), but prioritize trafic to and from the clients higher. So one could for instance play battlefield without problems. I would also like the server to act as a firewall, so I wouldn't need to run software firewalls on the xp workstations.

3: I'd like a "secure" LAN.

Future Plan X: Get the thing to run PHP and MySQL, so I could test web pages and related technology, without having to upload it to an external server via the slow internet connection.


OK - so what do I hope to gain from this thread? 

Well, knowledge. For instance
- are all of these things even possible?
- are some of them really contradictions?
- are some of these ideas not advisable, maybe stupid even?
- how could it be acomplished?
- what other things should I consider?
- where should I begin?
- is ubuntu really wrong for me?
- is this project insane?

Also, when a labtop needs to connect (or this new ubuntu machine I am typing on now), I have to disconnect a workstation and wait, some times ½-1 hour, for my service provider to hand out an IP... Not cool. Not cool at all.


I would like to thank anyone who answers in advance. Thank you!:)

---

### Post by Iowan on 2006-02-01
The 4 gig may get used up in a hurry... (Imagine that - 70 MEG used to be considered huge).  I have a small '486 running a single-floppy router/firewall program "watching the door", but I suspect the server could do that as well or better.  I still like having the guard dog dedicated as a first line of defense.  I have a blazing 56K dialup, so when I get a couple of XP boxes downloading and playing mp3's across the 10M network, it slows down - a lot. DHCP server should be fairly easy to set up.  Good luck... bring issues back to the forum.
I just stumbled across [THIS]("http://doc.gwos.org/index.php/BreezyCust"), you should have a look!

---

### Post by RAZZ on 2006-02-01
Great! Looking at it now.

A 486, huh? I know I have one of those somewhere...

And - thanks for replying!

---

### Post by eviltwin on 2006-02-01
[QUOTE=RAZZ]Great! Looking at it now.

A 486, huh? I know I have one of those somewhere...

And - thanks for replying![/QUOTE]
I know this might not be what you are after, but if you are scared of the command line then perhaps use a prebuilt distro designed specifically to be a router? Something like [IPCop]("http://www.ipcop.org/") or [Devil Linux]("http://www.devil-linux.org/home/index.php")? Maybe these aren't for you, I have used IPCop but I plan to replace it for my own purposes, however I know it has trafic prioritisation. Maybe you could have a look at their sites and see if they offer everything you want, they both have their advantages.

If you want to go with an Ubuntu server then it is possible, I just can't remember the commands off the top of my head and can't test them because I am at school and don't have access to the apt repositories (DAMN YOU WEBSENSE!! ;)). I can help you out with them, just post what you would like to go ahead with - I am about to try and do something extremely similar with ubuntu when I get home in two weeks, so I will be more than willing to talk you through this now so that I have a better idea when I go home ;)

Let me know what you want to do.

And for the record: I have a P2 400mhz comp with 256MB ram that I use on a day to day basis, it runs fine with a heavy gnome UI (although I am going to change to XFCE in the future) and so running what you have on the command line as a headless box is quite easy, I have a 100mhz system at home doing my broadband with a 1gig hdd, I never experience downtime and it is never under heavy load :mrgreen:

---

### Post by RAZZ on 2006-02-01
OK - I have tried [THIS]("http://doc.gwos.org/index.php/DHCPServer") and all I get is "* Starting DHCP server... [fail]" when I "sudo /etc/init.d/dhcp3-server start".
But then again, I have no idea what I am doing...

EDIT: YAY! DHCP problem fixed! I needed to set a static IP withing range...

@eviltwin - both your sugestions sound interesting. As for what is best, eh, I really don't know.

I might just like your talking me through this thing, and if it helps you too, that just makes it better.
Also - nope, command line doesn't scare me. Not too much anyway;)

---

### Post by majikstreet on 2006-02-01
also. there is smoothwall, m0n0wall, pfsense and more for dedicated firewall distros..

---

### Post by RAZZ on 2006-02-01
Thank you for replying.

Question: Would it really be best to use a dedicated firewall distro, with all the stuff I want this server to do? Do you think it is a bad idea to go with Ubuntu for this purpose?

And now - I got the DHCP server thingy to start now, but the XP machine can't retrieve an IP automatically. I did get an IP within the range I specified (192.168.0.100 - 192.168.0.200) when I entered the server's IP into it. Still, I was unable to ping from any of the machines. Any suggestions?

Thanks again!

---

### Post by Crimguy on 2006-02-01
Regarding the dedicated firewall distros:  the (big) plus is that they're generally bug-free, and work as advertised.  Getting support can be good b/c each user is doing the same thing (i.e. running a firewall!).

However, you can get the same security and functionality with any linux distro if you do it right.  I recommend reading a bit on the subject of iptables to familiarize yourself, and go from there.

---

### Post by eviltwin on 2006-02-02
[QUOTE=RAZZ]Thank you for replying.

Question: Would it really be best to use a dedicated firewall distro, with all the stuff I want this server to do? Do you think it is a bad idea to go with Ubuntu for this purpose?

And now - I got the DHCP server thingy to start now, but the XP machine can't retrieve an IP automatically. I did get an IP within the range I specified (192.168.0.100 - 192.168.0.200) when I entered the server's IP into it. Still, I was unable to ping from any of the machines. Any suggestions?

Thanks again![/QUOTE]
Well, building it from Ubuntu gives you MUCH more flexibility... I have a huge problem where I don't like the firewall distros because they are restrictive, and in my case never seem to work... I'm planning out packages I need to install on my machine to get it to work now, as you keep going let me know. The one thing that I will say is that Ubuntu by default forgets your IPTable settings, but this can be solved with a quick script (which I have nicked from Fedora and am editing tyo fit Ubuntu). I'll post the script up somewhere when it is done, if you are interested...

---

### Post by RAZZ on 2006-02-02
Update: Horray! I can now succesfully ping from both sides, while the ubuntu machine is connected to the internet (typing on it now). Still no internet on the XP machine, though.
Also, I installed firestarter and ran through the wizard, but that didn't make any difference.

On the upside, the XP machine *does* get an IP within the range I specified, so it would seem that DHCP *is* working.

I decided to stick with ubuntu for now, at least untill someone convinces me that it is really a bad idea. Switching to another distro just seems like a de-tour. Besides, I have no idea weather it will be insanely difficult, or just plain impossible to run emule, php, or MySQL, when I get to that point.

eviltwin, I did have a look at [http://www.netfilter.org/projects/iptables/index.html]("http://www.netfilter.org/projects/iptables/index.html") and [http://www.sns.ias.edu/~jns/wp/iptables/]("http://www.sns.ias.edu/~jns/wp/iptables/") but I still don't feel that confident about using it... Maybe my lacking knowledge about networking in general is to blame - well probably.
I also went through [http://doc.gwos.org/index.php/DHCPServer]("http://doc.gwos.org/index.php/DHCPServer")

If the script you describe would be needed for ubuntu to remember my settings, then sure, I am interested!

Thanks again!

EDIT: YAY! I am typing this on the XP workstation, witch means I have internet through the Ubuntu server!
I deserve a cup of coffee now.
What I needed to do was to set the server's IP as the default gateway in the XP client's TCP/IP protocol. I would really like to avoid that, so I could just plug windows computers in, without having to make any special settings. However, it is working.
Any ideas?

---

### Post by eviltwin on 2006-02-02
[QUOTE=RAZZ]Update: Horray! I can now succesfully ping from both sides, while the ubuntu machine is connected to the internet (typing on it now). Still no internet on the XP machine, though.
Also, I installed firestarter and ran through the wizard, but that didn't make any difference.

On the upside, the XP machine *does* get an IP within the range I specified, so it would seem that DHCP *is* working.

I decided to stick with ubuntu for now, at least untill someone convinces me that it is really a bad idea. Switching to another distro just seems like a de-tour. Besides, I have no idea weather it will be insanely difficult, or just plain impossible to run emule, php, or MySQL, when I get to that point.

eviltwin, I did have a look at [http://www.netfilter.org/projects/iptables/index.html]("http://www.netfilter.org/projects/iptables/index.html") and [http://www.sns.ias.edu/~jns/wp/iptables/]("http://www.sns.ias.edu/~jns/wp/iptables/") but I still don't feel that confident about using it... Maybe my lacking knowledge about networking in general is to blame - well probably.
I also went through [http://doc.gwos.org/index.php/DHCPServer]("http://doc.gwos.org/index.php/DHCPServer")

If the script you describe would be needed for ubuntu to remember my settings, then sure, I am interested!

Thanks again!

EDIT: YAY! I am typing this on the XP workstation, witch means I have internet through the Ubuntu server!
I deserve a cup of coffee now.
What I needed to do was to set the server's IP as the default gateway in the XP client's TCP/IP protocol. I would really like to avoid that, so I could just plug windows computers in, without having to make any special settings. However, it is working.
Any ideas?[/QUOTE]
You can set the default gateway as one of the things that the dhcp gives out, look at your settings...
couple of questions: when you reboot your ubuntu machine, does your firewall config still stay thanks to fire starter? If so, that is fine and you don't need to worry about it. I've found a bunch of problems with ubuntu for my purposes that will probably mean a large amount of editing to get it to do what I want... but nothing I can't do.

---

### Post by RAZZ on 2006-02-02
[QUOTE=eviltwin]You can set the default gateway as one of the things that the dhcp gives out, look at your settings...[/QUOTE]
This is simply amazing. I have a small problem - you give me a pointer in the right direction - I google for five minuttes and - BAM - I have the DHCP server I have needed for years - working exactly the way I only dreamed it could, just a few days ago. Thank you very much!

[QUOTE=eviltwin]couple of questions: when you reboot your ubuntu machine, does your firewall config still stay thanks to fire starter? If so, that is fine and you don't need to worry about it. I've found a bunch of problems with ubuntu for my purposes that will probably mean a large amount of editing to get it to do what I want... but nothing I can't do.[/QUOTE]
Well, I don't really have a custom firewall config yet... But since I installed aMule, and I am getting a low ID, that would seem the sensible thing to do next. aMule will need access to a TCP and a UDP port.
Any idea where to start? Please keep in mind that I utterly suck at anything that has to do with networking... I am used to windows firewalls, like cygate and zonealarm, that simply asks the user wether a program can access the internet when it tries to do so.

Thank you in advance!

---

### Post by deBaas on 2006-02-02
[QUOTE=RAZZ]Well, I don't really have a custom firewall config yet... But since I installed aMule, and I am getting a low ID, that would seem the sensible thing to do next. aMule will need access to a TCP and a UDP port.
Any idea where to start? Please keep in mind that I utterly suck at anything that has to do with networking... I am used to windows firewalls, like cygate and zonealarm, that simply asks the user wether a program can access the internet when it tries to do so.
[/QUOTE]
Just open the correct ports in firestarter and your aMule should work.
by default: 4662, 4665 and 4672

---

### Post by RAZZ on 2006-02-03
[QUOTE=deBaas]Just open the correct ports in firestarter and your aMule should work.
by default: 4662, 4665 and 4672[/QUOTE]
Yeah, well I don't really have a clue about openeing the ports. However I looked at the firestarter documentation, and found out that I could just right-click one of the connection atempts for eDonkey and select "Allow inbound service for everyone". Is that "safe"? I do get a high ID now.

Thanks!

EDIT: I just realized that I already have completed the first part, and I am already into the second, of my 3-point plan. Wow - maybe this project is not insane at all, and "Future plan X" may not be all that far into the future! All I need to do now is:
Remaining part 2:
Figure out if aMule is set up right.
Find how to prioritize traffic to and from the win XP clients higher than aMule.

Final part 3:
Find out if my LAN is "secure", and if not, figure out how to make it so.

Then it's on to plan X!

---

### Post by eviltwin on 2006-02-06
Sorry for my sudden stop of posting, I was hard at work on my server... and I got nowhere :P

I did stumble accross [this]("http://http://thekelleys.org.uk/dnsmasq/doc.html") on my travels though. It might be better for you than the fully fledged dhcp3 server. You may not want to change though, having set up dhcp and got it working. But you may be interested in things to do with the DNS features that it offers, I'm just linking to make you aware and let you make your own mind up. Not sure if it is in the repositories, I went over to debian and took it from their though ;)

I'm very in the dark about the rest of it as you are using firestarter, perhaps someone with more experience can help you there. Until then, post back with anything you can find and I'll see if I can help you decifer it :)

---

### Post by RAZZ on 2006-02-06
> **eviltwin]Sorry for my sudden stop of posting, I was hard at work on my server... and I got nowhere :P[/QUOTE]No problem, man. I'm just gratefull for the help you *do* provide!

[QUOTE=eviltwin]I did stumble accross [this]("http://http://thekelleys.org.uk/dnsmasq/doc.html") on my travels though. It might be better for you than the fully fledged dhcp3 server. You may not want to change though, having set up dhcp and got it working. But you may be interested in things to do with the DNS features that it offers, I'm just linking to make you aware and let you make your own mind up. Not sure if it is in the repositories, I went over to debian and took it from their though  said:**
> Now, here is a funny story: When I clicked the link, I was sent to [http://www.microsoft.com](http://www.microsoft.com) :eek: And I was like "What? Is that supposed to be funny?" (OK, it would have been ;) ). But then I saw the extra "http://" in there. I'm on the XP machine now, but using firefox, so it is kind of strange that I am redirected to [www.microsoft.com](www.microsoft.com), don't you think?
About dhcp3, I have that set up nicely now (I hope!), so I think I will just stick with that now. I actually don't think the configuration was that hard, once I got into it, unless there is something I missed - and there might very well be! :)

[QUOTE=eviltwin]I'm very in the dark about the rest of it as you are using firestarter, perhaps someone with more experience can help you there. Until then, post back with anything you can find and I'll see if I can help you decifer it :)Yeah, I am using firestarter. Is that bad? does it make other things more complicated? Like forwarding ports?
This is what I like about firestarter:
-It has a graphic interface.
-It was extremely easy to give aMule full access to the internet (right-click connection atempt, grant access).
-It never asks annoying questions, like windows firewalls.
-I dont need to have the graphic interface turned on, in fact I shouldn't - it still works.

OK, so what have I been doing the last few days? Traffic shaping. Complicated stuff, I tell ya. At least for me. Do you know something about that?
I have installed wondershaper, which seems like the poor-mans-solution. I don't think it works that well, either. even browsing still feels jerky when I upload on aMule, full speed. So I haven't tried networking games. It does improve my ping times, though.
I would like to try to simply down-prioritize certain ports (1 TCP and 2 UDP, that aMule uses). However, I am having difficulties finding info-for-dummies on that. Then, later, I would like to try some of the more complicated stuff, like prioritizing certain types of packets over others (yes, I AM learning, here!).

---

### Post by Swiss2K on 2006-02-07
Hi Razz, just a thought...

To make it as simple as you posible can. Download Clarkconnect (the free home edition). It's a red hat based distro specificly build for server use. I comes without a gui (like gnome) but with a easy to maintain webbased administrator tool. This means that you can manage your server from any pc in your network with firefox/IE. I've installed it once and i ran everything right from the box. It has HTTP, FTP, Firewall, Samba and more. Allthough this distro it's limited in terms of it's options. It will do a perfect job in your pretty basic setup. there however is one problem... You can't run emule etc on it.

good luck

---

### Post by RAZZ on 2006-02-07
Hi Swiss2k, and thank you for your suggestion.

Clarkconnect looks nice, but not really what I am looking for. Running an edonkey2k/kad client is pretty much a requirement for my project.

As for remote control, I was thinking along the lines of SSH, wich seems like what the big boys are using. I haven't really looked into that yet. Hopefully, I won't need it much though, since I was kind of hoping that the server would pretty much just run without my intervention, once I have set it up right. But maybe that is just a wet dream. ;)

Right. Traffic shaping. I am looking at shorewall right now, witch has built in HTB (Hierarchical Token Bucket) and SFQ (Stochastic Fairness Queuing). I am leaning towards HTB, since I am partial to any technology that has "Bucket" in its name...:-k

---

### Post by eviltwin on 2006-02-08
Well it's not that it is a bad thing, I just have no experience with firestarter :)

I'll read the docs and have a look, meanwhile, anyone else here got experience with firestarter? As for traffic shaping, my server took shape rapidly last night so I am onto that stage now :D (IPTables now restoring rules on startup ^_^)

I suspect eMule is secure, if you want to find out just how secure your network is then you should run the ["Shields Up"]("https://www.grc.com/x/ne.dll?bh0bkyd2") test over at gibson research, it's pretty easy to use.

EDIT: Shorewall is a good bet, but I'm not sure how well it will cooperate with firestarter....

---

### Post by RAZZ on 2006-02-08
Wow - cool link, thanks! I seem to be pretty secure, only problem being that my machine is responding to pings. Also, the tcp port that emule it using is not stealth-mode, only blocked.
About Shorewall, I was thinking of replacing firestarter with that. Not use both. I have a feeling that it is a bad idea to have two softwares fighting over iptables... But really, I have no knowledge to back up this hunch.

---

### Post by eviltwin on 2006-02-08
[QUOTE=RAZZ]Wow - cool link, thanks! I seem to be pretty secure, only problem being that my machine is responding to pings. Also, the tcp port that emule it using is not stealth-mode, only blocked.
About Shorewall, I was thinking of replacing firestarter with that. Not use both. I have a feeling that it is a bad idea to have two softwares fighting over iptables... But really, I have no knowledge to back up this hunch.[/QUOTE]
Aye, your hunch be correct, Sir ;)

Shorewall is pretty cool, very powerful, very extensible. The emule port will tend to not be stealthed because you have it open to allow the traffic in, it's unavoidable I think. Secondly, pings can be stopped by blocking all incoming icmp on your port (you might want to allow echo reply and destination unreachable, though). Once you have smoothwall in place give me a shout - I'll be waiting :P

EDIT: Changed Smoothwall to Shorewall (typoed >_><_<)

---

### Post by RAZZ on 2006-02-08
Eh - are you talking about the [www.smoothwall.org](www.smoothwall.org) smoothwall? But isn't that a whole other distro? The screen shots look cool, though.
If it is a whole new distro, will I be able to run PHP, MySQL, and an emule client (maybe mlDonkey or aMule, Maybe something even better?) on it, without too much grief?

Thanks again for all your help!

---

### Post by eviltwin on 2006-02-08
oops... I meant shorewall... smoothwall is another distro... too much work today >_><_<

So anyway, shorewall, go with shorewall :)

---

### Post by RAZZ on 2006-02-09
Ok eviltwin, I have unistalled firestarter and installed shorewall. Uninstalling firestarter has broken internet connection sharing, even though it was working before I installed firestarter.
I made a panic post about this, and the answer I got indicates that this was to be expected, since uninstalling firestarter resets iptables, or something like that.
I shure am learning something new every day :)

Anyway, I haven't done anything with shorewall, like configuring or even starting it.

---

### Post by eviltwin on 2006-02-15
erm... kinda forgot I was helping you with this *looks ashamed*

Ok, smoothwall. Have you done anything with it, or has my forgetfulness caused your project to collapse?

---

### Post by RAZZ on 2006-02-15
Lol No problem, man. I had a bithday to take care of, anyway.

I haven't done anything with smoothwall.
My project hasn't collapsed, I just put it on pause, since I had a feeling you would check back some time.

Ok- so where do we go from here?

---

### Post by eviltwin on 2006-02-20
Well unfortunately I can't offer much here, a firewall is something you set up on your own for yourself if you see what I mean. I can't TELL you what to do. I can point you heavily in the right direction though :)

[URL="http://www.shorewall.net/"]
Shorewall router setup[/URL] look at the pretty diagram on that page, if it looks like what you want then give that a go, we'll see if we can get your connection sharing before we attempt the traffic shaping (which I think will be trivial, but I am just moving onto learning about at the moment).

Any queries about that and give me a shout.

---

