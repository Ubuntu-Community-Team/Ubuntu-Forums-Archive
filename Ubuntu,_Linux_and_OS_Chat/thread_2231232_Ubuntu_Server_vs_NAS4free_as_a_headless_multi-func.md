---
title: "Ubuntu Server vs NAS4free as a headless multi-function media server - an experience"
date: 2014-06-24
forum: Ubuntu, Linux and OS Chat
---

### Post by David_Etcell on 2014-06-24
Hi all,

A few years ago, I set up a media server out of scrap, using an older version of Ubuntu server. Last year it finally came time to upgrade to some REAL home-server hardware, and fix the OS to go with it! Without going into too much detail, I originally decided to go for NAS4free as an operating system, due to its extremely basic setup and interface. I later decided to go with an Ubuntu Server + Webmin combination, but I have a basic blog about the experience HERE: [http://smakmediaserver.blogspot.com/](http://smakmediaserver.blogspot.com/)

A little more detail, which I will move out of my inbox to a forum post in case anyone else is interested, a while ago I received a PM:

[QUOTE=PartisanEntity]Hi there,
I was searching the forum to see what people are writing about NAS4free and came across this post of yours: [http://ubuntuforums.org/showthread.php?t=2208419&p=12945289#post12945289](http://ubuntuforums.org/showthread.php?t=2208419&p=12945289#post12945289) 
I have been personally contemplating setting up a home NAS server using NAS4free, but after reading your post I am wondering if it is a good option to use.
Could you please tell me what you don't like about NAS4free?
Thanks![/QUOTE]

While possibly a little long winded my response was:

[QUOTE=David_Etcell]
No worries!

Basically, while the core itself is just fine, there seems to be very few available packages that install and run properly on NAS4free. I can't speak for other BSD based operating systems, but I gather they would have the same issue. NAS4free does have a few benefits, such as jails - which behave a little like a virtual machine without the application overhead.

Anyway, I wanted my server to do a few things. 
- DHCP server
- DLNA media server
- uTorrent server
- network file sharing via samba
- redundant RAID ability

DHCP is a mature technology which doesnt move much, so there are very mature BSD packages available to do that. It wasn't a problem.
uTorrent server however, has linux packages, but sadly no BSD packages. I attempted to get uTorrent server to install and run in a jail using the linux legacy drivers but for some reason the web ui just refused to start. I decided I could just use a BSD capable alternative to uTorrent, IF this was the only compromise I had to make.
Now, DLNA media servers, this was the killer. I play most videos on the server from either a PS3, or an android box. My old server was running PS3 Media Server, and I wanted the new one to run Universal Media Server (an off-chute of the same application). I managed to get UMS installed and running in a jail, but it was insanely unstable. sometimes it wouldnt start, it had a reliable uptime of about 2 hours, and when it was running, it would frequently crash. I set up a 'crash detector' which ran a script to restart the jail, but I decided this was stupid. This was sort of the final straw with NAS4free to be honest. I did have a look around for native BSD DLNA servers, but could not find anything as customisable and versatile as those available for linux. 

The RAID issue, as far as I'm concerned, was the only downside of not using NAS4free. BSD os' like NAS4free have very mature and reliable ZFS support, though it does require insane quantities of memory (some people say 4gb of ram per gb of hdd space). My server has 16gb of ram, but I was using a 120gb ssd as swap, so really wouldn't have minded giving it 64gb of that as virtual. When I ended up using ubuntu server instead, I used Raid5 instead, which I guess is sort of the same thing, it comes with the read/write speed benefits, as well as the redundancy benefits, but loses some of the ZFS features like self-healing, or its memory swapping.

Its probably not much help, but I blogged about it here: [http://smakmediaserver.blogspot.com/](http://smakmediaserver.blogspot.com/) more for my own piece of mind, like a 'lessons learned' sort of thing.

Anyway, Hope this helped, if you need anything else, let me know :)[/QUOTE]

A few more questions:

[QUOTE=PartisanEntity]
Thanks very much, here some questions after reading your blog (granted they are questions by a newbie):

a) You mentioned that the HP NAS you purchased doesn't support hot-swapping. Why did you go for a model like this if you don't mind me asking?

b) Does Webmin take care of installing packages for services, or does it only allow you to manage installed services? (For example if I want to use AFP, does Webmin take care of that or do I need to install it prior to managing it with Webmin?)

c) Would you recommend Webmin to someone who wants a NAS with minimal tweaking and hassle?

d) How loud is your HP NAS. If it is in a cupboard, and I am standing about 2-3m away, will i still hear the fans?[/QUOTE]

And my response:

[QUOTE=David_Etcell]
a) I've no real need for hot swapping as I don't intend on pulling drives out at any great frequency. I want the server to sit in its cupboard, and its only interactions to be remote over the network. If for some chance I do need to pull one of the drives, I can just turn the machine off first since it takes less than 2 mins for the server to come back up. Removing and replacing drives while the machine is on is all hot swapping is.

b) I personally prefer to use apt-get from the command console (I use PuTTy), but webmin does allow you to install packages directly from it. One of the sidebar options in webmin is 'System'. in System, there is one called Software Packages. in that, there is an option to install from a .deb you might have downloaded, but there is also a button to search apt. The apt window just has a search bar and appears to perform a wildcard search either side of what you enter, but you select what you want to install from the results, and when it returns to the software packages page, you just press install.

c) I strongly prefer webmin and ubuntu server over ubuntu with a gui. The first steps of installing ubuntu server obviously have to be done from the command line, but there are instructions about on how to simply use wget to grab the webmin .deb and install it. Once that is done, you could probably do everything else from webmin, and webmin does have a built in command console so that you don't really need to use anything external unless webmin has an issue. Using ubuntu (not server) with a gui in my opinion just wastes valuable resources loading apis, and drivers, etc, which you are never going to need. Because webmin is web based, the web server only creates that session when you log onto it. the only issues I have had with webmin, are once on my old server, I installed a package which halted the startup sequence, so it didn't make it down to 'W' where the webmin start sctipt lives (when you install webmin, it does the startup scripting itself), and when I first installed it on my current server, the default port of 10000 was used by something else, so I had to change the config from the command line (I changed the port to 20000). If the default port is an issue, I'm pretty sure there was an option to specify the port when webmin was installing.., I just didnt realise 10000 would be an issue.

d) if the door is shut, you wouldn't be able to hear the N54L, it seems to be very quiet indeed. I used to have an underclocked P4 in the cupboard, and the fan on the P4 was so much louder, you could hear it with the cupboard shut for quite a distance. Looking inside the N54L, it doesnt actually have a cpu fan, but a heatsink. The fan is one large fan at the back which blows air from the back of the case through the drive bays and over the motherboard. It is a fairly quiet fan too, for what its worth.[/QUOTE]

Anyway, hopefully I have posted this in the correct forum, and more importantly, I hope it helps someone, at some point. Feel free to inbox me with comments and _constructive_ criticism. Just keep in mind I have read the entire 'Song of Ice and Fire' series of books, and I am not above replying to hatemail with GoT spoilers! ;)

---

