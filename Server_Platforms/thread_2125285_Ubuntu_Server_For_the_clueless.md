---
title: "Ubuntu Server For the clueless"
date: 2013-03-13
forum: Server Platforms
---

### Post by ally_uk on 2013-03-13
Howdy all I am a life long user of Windows tying to make the transition into the wonderful world of Ubuntu I have a dual Core AMD shuttle that is sitting there currently doing nothing so I figured I would setup up a Server and actually have it doing something productive. 

Skillwise I am ok with the CLI have a good understanding of how to use vim, file navigation understand concepts such as piping, redirection and can can use utilities such as Grep

I basically want to setup to start with a Media server which will handle streaming, downloading of torrents, I also want to setup a ftp and share out a few samba shares with windows 7 clients. I also want to learn about basic security of the server real basic foundation level stuff I don't want to jump into the deep end and bite off more than I can chew. I preferably don't want anonymous access to the samba shares and want some kind of security in place.

Has anybody set up something similar or have access to good easy to follow tutorials I am willing to get my hands dirty just having a got a clue about where to start I usually install the O/S and then that's about as far as I go I need to break everything down into small chunks to achieve the goal.

With your help I can move onto phase two of the project which will mean I will document my journey with Ubuntu server setup a blog and give something back to people who are new to Ubuntu and are in a similar position as myself need clear easy advice.

Please somebody give me some encouragement and help me get this project off the ground if you have access to any tutorials or guides I would appreciate it :)

The plan is to build this server build a foundation of knowledge and give back to the community that is my dream please help me achieve this I want to educate people about Ubuntu Server :)

---

### Post by ranger12 on 2013-03-13
Take a look at this link and see if this may help:
[http://www.danbishop.org/2012/06/02/ubuntu-12-04-ultimate-server-guide/](http://www.danbishop.org/2012/06/02/ubuntu-12-04-ultimate-server-guide/)
I did not setup my server exactly like this because my needs were a little different but alot of it is similar to mine - see if this would meet your needs.

I posted a tutorial on the way I setup my ftp service on my server:
[http://ubuntuforums.org/showthread.php?t=2121931](http://ubuntuforums.org/showthread.php?t=2121931)
Hopefully it may help.

---

### Post by papibe on 2013-03-13
Hi ally_uk.

All possible. I would try to solve one problem at a time (one thread per task).

Here's a few tips:
[LIST]
[*]You don't "have" to use a command line interface. You can set up any 'server' service on a desktop edition. If the command line slows you down, by all means install a light desktop version like Xubuntu or Lubuntu.
[*]Evaluate your need for streaming. Unless you have devices with limited capabilities (console game for instance), most of the time you'll need sharing instead of streaming. In case you do, take a look at [MediaTomb]("http://mediatomb.cc/") (in the repos btw).
[*]There are 2 options for network sharing: samba and nfs. Unless your Windows machines support nfs (they have to be either pro or ultimate editions), the simplest way is to install samba.
[*]I recommend taking a look at[ transmission-dameon]("http://www.evilcodingmonkey.com/2012/07/16/installing-a-transmission-daemon-on-ubuntu/") as your torrent client. It works on the server as a service, and can be accessed through  a web interface from every computer on the house (if you want to).
[*]Although ftp would be OK on a LAN, I would recommend using sftp instead. It is installed by default when you install ssh server. It works right out of the box. From Windows you can use several clients: WinSCP, Filezilla or fireFTP (Firefox plugin).
[*]
[/LIST]
I hope that helps. Let us know how it goes.
Regards.

---

### Post by grunge09 on 2013-03-13
Here is a step by step guide that may help.  I worked thru most of that.  I chose Webmin, Mdadm Raid5, Samba.  

[http://www.havetheknowhow.com/default.htm]("http://www.havetheknowhow.com/default.htm")

Hope this helps.

---

### Post by ally_uk on 2013-03-13
Thanks for the replies very insightful :) I thought if you were using a Server platform the GUI was a no no and it is always best to go hardcore and do everything through the CLI I have avoided tools like Webmin in the past because I had this stupid mentality where I thought that if I was working in a professional environment it would be best to learn the harder way of doing things and not to take shortcuts. 

I think I will install a GUI hell I may even just run the normal version of Ubuntu as my server platform is there a easy way of turning of Uinity and having a classic GUI such as Gnome 2 or a more lightweight based GUI.

When I do eventually manage to get the blog up and running I will remember to give a shout out to you guys because it is you who have inspired me and have given the motivation to get something working lol :)

The Blog will be geared for newcomers like myself to Ubuntu and will contain tutorials etc.

How long have you guys used Ubuntu Server? What were the first projects you worked on? What are some good tips to learn more about it? 

Sorry about all the questions I am just interested in your experiences :) as I find it helps to motivate myself

---

### Post by ranger12 on 2013-03-13
I have been using 12.04 Server for 9 months or so. i have a private home lan setup. i run ftp, dns, mDNS, ldap, nfs, samba and who knows what else. It is not recommended to run a GUI on top it for 2 reasons: performance and security - that is why Canonical does not ship the server edition with a GUI. I do not have one on mine and have no desire to put one on but you do what you think would best fit your needs. Good luck with it.

---

### Post by Doug S on 2013-03-14
I don't think the [Ubuntu serverguide ]("https://help.ubuntu.com/12.10/serverguide/index.html")([pdf]("https://help.ubuntu.com/12.10/serverguide/serverguide.pdf")) was mentioned as a good reference. When the 13.04 serverguide is released, there will be a new "Worpress" sub-section under the "Lamp Applications" chapter.

I have used Ubuntu server edition for many years. I do not use any GUI.

---

### Post by ally_uk on 2013-03-14
Were you guys new to Linux or made the jump from Windows? I have plenty of documentation the problem I find is that although some of the books say they are geared at beginners it can be a nightmare.

The book I am reading at the moment practical guide to Linux command line by Mark Sorbell starts off ok and is pretty straight forward to follow but then it gets to the section on Bash Programming / writing scripts and I am lost he doesn't show you how to setup a basic script just jumps into flow control, if when and stuff which just goes over my head :)

What were some of the first things you did with Ubuntu Server to learn the system more? what did you setup first? 

:)

---

### Post by nothingspecial on 2013-03-14
For beginning  Bash, I would start here [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by ally_uk on 2013-03-14
Thank you for the guide to Bash :)

---

### Post by ally_uk on 2013-03-14
ranger12 you seem to have accomplished alot with Ubuntu Server were you new to Linux? how did you find the whole process was it easy to learn? :)

---

### Post by lykwydchykyn on 2013-03-14
If you want a server that actually give you a *server GUI* (meaning, GUI configuration utilities for services, not just a desktop on a server OS), you might want to investigate freeNAS, clearOS, or Zentyal.  You can put a desktop on Ubuntu server, but you still need to edit config files and use the terminal to actually do anything.

Not that there's anything wrong with learning the CLI; it's what I use most of the time myself.  Best way to learn is exactly what you're doing now: pick a project, do the research, and implement it.  I got started with a book from O'Reilly press called "Linux server hacks".  Don't know if they've updated that book, but it was a pretty awesome guide to setting up a variety of services back in the day.  I think I paid 5 bucks for it.  Best fiver I ever spent.

---

### Post by nothingspecial on 2013-03-14
> **lykwydchykyn said:**
>  Best way to learn is exactly what you're doing now: pick a project, do the research, and implement it.  

Exactly, you can read all you like, but the best way to learn is to actually do it.

> **ally_uk said:**
> 

I basically want to setup to start with a Media server which will handle streaming, downloading of torrents, I also want to setup a ftp and share out a few samba shares with windows 7 clients. I also want to learn about basic security of the server real basic foundation level stuff

So pick one of those things, read about it, then do it. And go from there.

---

### Post by ally_uk on 2013-03-14
Hey thanks I purposely have avoided tools like Zentyal, Webmin as I had this silly idea of trying to configure everything through the command line. I still haven't configured anything and am still banging my head against the wall :) still am trying to get motivated and to start the process of setting services up. I keep dipping into Linux books and ending up with a headache the information being presented just isn't sinking in :)

To try and stay on track and motivate myself I was thinking of adding stuff I do to this thread on a day to do basis and kind of build up a knowledge base.

Someone really needs to bring out a decent how to setup a server guide or book explaining basic steps from hard disk configuration right up to configuration of services and security but in a easy to understand way I get to stuff like LVM And it just goes over my head. 

:)

---

### Post by ranger12 on 2013-03-14
I actually had been using ubuntu desktop as a regular desktop os since version 10.10. I got another box last summer and thought it would be great if I setup my own network. I downloaded 12.04 server edition, used the server guide and rolled up my sleeves and went to work. My network setup now did not happen overnight but I think I have a pretty good one now if I decide to add more workstations than I can. 1 server, 1 workstation and a network printer - and of course the router/modem for now. I started slow at first. I actually found most of the server guide to be good but it does have some sections that seem some more work done to. I think ubuntu Linux makes a great network platform. I think the desktop version makes a great works tigon coupled with a ubuntu server. I do have it setup with samba if I want to add windows workstations but at the moment I do not have any. I do think the server guide is a great place to start and I have also consulted the man pages on things to help even further with configuring tongs. There is still more though. I need to put in a system to do backups and I might grab another machine to put in secondary masters for ldap and dns just in case the primary decides to go "poof". The cups server does actually have web based interface tool but everything else I do command line; either at the server console or I have the workstation setup so I can ssh over to it. I think after I set it up last summer I played around with just creating regular unix user accounts and than I think it was dns and then openldap. All the other services I setup after that. I then set out to network the desktop system. Just take it slow and after you have the basic server running, just pick a service you want to install and use the server guide first and if that doesn't suffice than try here and some of the other links posted.

---

### Post by ally_uk on 2013-03-14
Ok I will be using Virtual Box to play before I touch a proper system I don't feel comfortable yet apologies if I keep asking questions I really do need a helping hand in getting started the first thing which is bogging me down is the partitioning of my virtual server. I am basically creating 3 10 Gig partitions in Virtual box.

SDA is going to have the main operating system installed 

/boot - 200mb
/ - 2 gig
/home - 6 gig
swap 

The other two drives I want to create a LVM and have it as a data share i.e /data is this a good way of going about the partitioning of the 3 drives or am I being a complete numpty here or do I need raid or some other fancy system in place how would you partition a this kind of layout I am a absolute noob and appreciate the hand holding sorry if I am posting stupid questions we all have to start somewhere and I guess I am on the absolute numpty / noob level whoknows oneday I might a be a guru one step at a time and Rome wasn't built in a day haha 

I must admit this forum compared to the Centos forum is much more pleasant and I appreciate the help I have received so far :) I do intend to give back to the community oneday and help others by devising a blog the absolute idiots guide to Ubuntu Server making the transition from Windows

---

