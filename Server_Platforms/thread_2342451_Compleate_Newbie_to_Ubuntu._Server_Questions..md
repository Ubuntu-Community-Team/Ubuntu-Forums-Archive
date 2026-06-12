---
title: "Compleate Newbie to Ubuntu. Server Questions."
date: 2016-11-06
forum: Server Platforms
---

### Post by daniel228 on 2016-11-06
Hello to all and thanks for taking the time to read my post.

I have a server hear being an 8 Core Xeon, 12GiB and x6 HDD's what I can set up using a RAID layout. I do believe the server is very powerful but thats just based on what I have seen over the years with other people and what they are running. The Server is a Rack I bought from a company that was getting shot of its old Hardware so I snapped it up at £65 hear in the U.K . 

Like I said in my thread title. I am completely new to Ubuntu and I don't know squat. Installation I think I could get threw with reading up ect. but have no idea how I would use the Software.

I was curious to know what I could use the Server for if anyone could point me in the rite direction and help me set it up to use the correct software and learn hear at home how to fully utilize it to the best of its abilities.

I was also curious to know would you have to pay for Ubuntu in a home environment. I have watched Videos were as I watched that when installing the likes of Server or Enterprise software you have to pay. The gye on the video said it has the ability to be very cheap to very expensive very quickly.

Any help would be great if anyone can.

---

### Post by cariboo on 2016-11-06
See [here]("https://wiki.ubuntu.com/MarkShuttleworth"), Jump to Will Ubuntu ever demand licence fees or royalties?

You can use your server, for whatever you want. I use my server as a file server, streaming video server and for a personal wiki. My server runs on a consumer motherboard here are the specifications:

```
inxi -b
System:    Host: willy Kernel: 4.4.0-45-generic x86_64 (64 bit) Console: tty 0
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: MICRO-STAR model: G31TM-P21 (MS-7529) v: 1.0
           Bios: American Megatrends v: V4.4 date: 11/25/2009
CPU:       Dual core Pentium E5400 (-MCP-) speed/max: 2003/2700 MHz
Graphics:  Card: Intel 82G33/G31 Express Integrated Graphics Controller
           Display Server: N/A driver: N/A
           tty size: 80x24 Advanced Data: N/A out of X
Network:   Card: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169
Drives:    HDD Total Size: 3960.8GB (62.5% used)
Info:      Processes: 213 Uptime: 1 day Memory: 420.0/1990.7MB
           Init: systemd runlevel: 5 Client: Shell (bash) inxi: 2.2.35 
```

---

### Post by mastablasta on 2016-11-07
wow very powerful machine for only 65. maybe it sucks the power or something. i mean this is very very cheap. get the server image, decide what you want to do with this server (for only a file server this is an overkill), install the OS and then start installing applications. you will need ot use terminal at some point anyway, so start reading into that.

i think this would be an awesome minceraft or other games server.

---

### Post by dudumomo on 2016-11-07
Nice machine Daniel,

Well, you can do plenty of thing with it and probably all at the same time. I have done quite a lot of tutorials on testing many applications ==> freedif.org, you can have a look.
But of course, it depends on what you want to do...

For example, you could use it as:
- a NAS, to save all your files, access them remotely, etc.. (You can use some nice web interface like Pydio)
- a music streaming server, to allow you, your family, your friends, to listen in the cloud, all the music you/they want, with Subsonic for example
- a video streaming server, where you connect all your home devices (TV, PC, Smartphones,..) to have a sync home theater, with Plex for example
- a seedbox, where you can access to a nice web interface and add all the torrents you want, with Deluge-torrent for example
- Running a mailserver to host your own email and ensure privacy
- Hosting a blog, with wordpress for example or a photo gallery with Piwigo, for example


But you can even have some more specific applications:
- Running BOINC, a open infrastructure using the computing power of the community to help science simulation (Done by universities, public institutions,... for many different type of application, in biology, astronomy,..)
- Running a decentralized search engine, connected with others peers and help the community, with Yacy for example
- Installing a RSS web client (Like Google Reader), with FreshRSS for example
- If you have a good internet connection, you could host a mirror of some small projects that needs support in bandwidth/disk space
- Running a TOR node,
- Running a game server (Like Minecraft or other)

And the list goes on.

---

### Post by daniel228 on 2016-11-07
> **mastablasta said:**
> wow very powerful machine for only 65. maybe it sucks the power or something. i mean this is very very cheap. get the server image, decide what you want to do with this server (for only a file server this is an overkill), install the OS and then start installing applications. you will need ot use terminal at some point anyway, so start reading into that.

i think this would be an awesome minceraft or other games server.

I bought the machine for £65, I asked if the gye would take it because originally it was advertised at £100 . Then two days later it was dropped to £75. I offered £65 if he could do delivery as well and he said yes. I bought this off my local trader web site.

The machine is a x3650 IBM Rack Mount M1 . I looked at this server when I bought it off the gye and just agreed as I knew I had a absolute bargain. I'll be 100% honest I haven't a clue half of the stuff inside. Its got all the optional extras. Full array of Hot Swap fans and the connectivity on the back is unreal. I'm pretty good with computers but you folk on this forum would put me to shame. It's even got a redundant PSU. This machine is the 2GHZ Model @x2 Socket @x4 per Socket Xeon with 12 GiB Volatile Memory. Put it this way I didn't hang around when they gye took it out the car out side my house being a private sale. I gave him the Money and left.


> **dudumomo said:**
> Nice machine Daniel,

Well, you can do plenty of thing with it and probably all at the same time. I have done quite a lot of tutorials on testing many applications ==> freedif.org, you can have a look.
But of course, it depends on what you want to do...

For example, you could use it as:
- a NAS, to save all your files, access them remotely, etc.. (You can use some nice web interface like Pydio)
- a music streaming server, to allow you, your family, your friends, to listen in the cloud, all the music you/they want, with Subsonic for example
- a video streaming server, where you connect all your home devices (TV, PC, Smartphones,..) to have a sync home theater, with Plex for example
- a seedbox, where you can access to a nice web interface and add all the torrents you want, with Deluge-torrent for example
- Running a mailserver to host your own email and ensure privacy
- Hosting a blog, with wordpress for example or a photo gallery with Piwigo, for example


But you can even have some more specific applications:
- Running BOINC, a open infrastructure using the computing power of the community to help science simulation (Done by universities, public institutions,... for many different type of application, in biology, astronomy,..)
- Running a decentralized search engine, connected with others peers and help the community, with Yacy for example
- Installing a RSS web client (Like Google Reader), with FreshRSS for example
- If you have a good internet connection, you could host a mirror of some small projects that needs support in bandwidth/disk space
- Running a TOR node,
- Running a game server (Like Minecraft or other)

And the list goes on.

Their are a lot of options even in just those few examples. I have ran previous systems running BOINC Software and the likes of F@H . I'm going to struggle with the CLI in a major way. Thats the only thing I'm worried about. I've got an up too date image of Ubuntu and will install it. What are your recommendations for a RAID Set Up. Would this depend on what I were doing with the server.

---

### Post by dudumomo on 2016-11-07
Depending on what you want to do, you could install some web interface to administrate your server, like with [Webmin]("http://www.webmin.com/").
Or you could install some fancy self-hosting environnement like [CozyCloud ]("https://cozy.io/en/")or [Yunohost]("https://yunohost.org"), which let you install in few clics many applications and do most of the configuration. You might want to start there !
Here is a demo of Cozycloud: [https://demo.cozycloud.cc/](https://demo.cozycloud.cc/)
And here is the demo of Yunohost: [https://yunohost.org/#/try](https://yunohost.org/#/try)

For the RAID, it will depends on what you want to achieve. Reliability vs performance
[https://www.prepressure.com/library/technology/raid](https://www.prepressure.com/library/technology/raid)
RAID 1 is probably the most simple one (Just a copy of all your files from Disk 1 to Disk 2). But if your configuration, you should be able to do much more.

---

### Post by daniel228 on 2016-11-07
> **dudumomo said:**
> Depending on what you want to do, you could install some web interface to administrate your server, like with [Webmin]("http://www.webmin.com/").
Or you could install some fancy self-hosting environnement like [CozyCloud ]("https://cozy.io/en/")or [Yunohost]("https://yunohost.org"), which let you install in few clics many applications and do most of the configuration. You might want to start there !
Here is a demo of Cozycloud: [https://demo.cozycloud.cc/](https://demo.cozycloud.cc/)
And here is the demo of Yunohost: [https://yunohost.org/#/try](https://yunohost.org/#/try)

For the RAID, it will depends on what you want to achieve. Reliability vs performance
[https://www.prepressure.com/library/technology/raid](https://www.prepressure.com/library/technology/raid)
RAID 1 is probably the most simple one (Just a copy of all your files from Disk 1 to Disk 2). But if your configuration, you should be able to do much more.

Depending on what I decide to do with the Server. I will I'm guessing have to install Ubuntu first obviously. It goes with out saying you can't have something like a Mail Server, a File Server or what I choose to do with it with out having an OS. 

My point being because this is a Server and Server class hardware. Would I install some sort of scripting or framework to get the desired purpose of the Server up and running. I'm not sure if that question is an exact science but how could you have say a Mail Server or a SeedBox with out installing some sort of scripting.

I will delve in too this soon, over the next few days but my point being I will have to learn the CLI as I have no knowledge on it.

---

### Post by cariboo on 2016-11-07
Near the end of the server installation process you will see a window asking you which servers to install, make sure you at least select openssh server, so you can access the server remotely, then once the install is finished you can stuff the server away in a corner, and access it from the computer  you use daily for any administration tasks. As far as scripting goes, you don't need to install anything extra. There are many server howto guides out there, so I'd suggest you find one that suits your needs and follow it.

Have a look [here]("https://www.howtoforge.com/tutorial/perfect-server-ubuntu-16.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/3/") for an example.

---

### Post by daniel228 on 2016-11-08
> **cariboo said:**
> Near the end of the server installation process you will see a window asking you which servers to install, make sure you at least select openssh server, so you can access the server remotely, then once the install is finished you can stuff the server away in a corner, and access it from the computer  you use daily for any administration tasks. As far as scripting goes, you don't need to install anything extra. There are many server howto guides out there, so I'd suggest you find one that suits your needs and follow it.

Have a look [here]("https://www.howtoforge.com/tutorial/perfect-server-ubuntu-16.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/3/") for an example.

I'm going to be straight up hear. When I logged in to my account with Ubuntu Forums I knew absolutely nothing about Ubuntu or Linux in General. I have been in front of my computer all night and my *** is killing because I have wanted to do this for so long. I have been reading up on UNIX \ LINUX and Linux Like OS's . I even just had to Google.co.uk SSH being Secure SHell.

This is the answer I got back.

> SSH stands for **Secure SHell**. It is a  program designed to allow users to log into another computer over a  network, to execute commands on that computer and to move files to and  from that computer. It effectively replaces telnet, ftp and the  rcp/rsh/remsh programs.

My point being I know very little but I'm going to give this a shot. I have all ready been learning so much about Linux \ Linux Like and UNIX OS's that I want to get my Server up and running because I don't want to waste it. I really liked you comment on stuffing it in the corner and forgetting about it when reading what SSH meant. I'm quite worried if I cant master the CLI I'm going to have waisted a lot of time and effort.

Am I rite in thinking if I were to install a script I would be missing the point of learning how to use the server directly as this would take out the learning and simply execute given commands.

At this point I'm debating between, File Server, On-line Streaming (say my Smart Phone or a friend or family members given device) , or a E Mail Server.   Would I be able to do just one or a multitude of these things could you tell me. E Mail Server and On line Streaming are the most appealing.

---

### Post by mastablasta on 2016-11-08
> **daniel228 said:**
> I bought the machine for £65, I asked if the gye would take it because originally it was advertised at £100 . Then two days later it was dropped to £75. I offered £65 if he could do delivery as well and he said yes. I bought this off my local trader web site.

The machine is a x3650 IBM Rack Mount M1 . I looked at this server when I bought it off the gye and just agreed as I knew I had a absolute bargain. I'll be 100% honest I haven't a clue half of the stuff inside. Its got all the optional extras. Full array of Hot Swap fans and the connectivity on the back is unreal. I'm pretty good with computers but you folk on this forum would put me to shame. It's even got a redundant PSU. This machine is the 2GHZ Model @x2 Socket @x4 per Socket Xeon with 12 GiB Volatile Memory. Put it this way I didn't hang around when they gye took it out the car out side my house being a private sale. I gave him the Money and left..

very good choice! such power for so little. 
\\:D/

> 
Their are a lot of options even in just those few examples. I have ran previous systems running BOINC Software and the likes of F@H . I'm going to struggle with the CLI in a major way. Thats the only thing I'm worried about. I've got an up too date image of Ubuntu and will install it. What are your recommendations for a RAID Set Up. Would this depend on what I were doing with the server.

you can try Ajenti web interface.

Anothe roption is Zentyal, but this is aimed really towards business (it used ot be better at catering home user). 

if you are not limited with Ubuntu the Openmediavault (debian based) web interfce is easy to use. you then add plugins for services you would like to have. 

Outside of Debian based distros there are two more nice web interfaces that deserve the mention: ClearOS and Nethserver - both are based on cenOS which is made form Red Hat linux's open source code.

Have a look online, you can try some online demo on many of these to see how they look like and feel.


as for RAID software raid (mdadm) might be a better way to go.


there are good tutorial online, people here will help as well, it just you need to decide what you want to do with the beast. then people will be able to offer advice on configuration, point you to good and easy to follow tutorial as well as help you achieve the goal.

---

### Post by dudumomo on 2016-11-08
Hi Daniel,

Either you are interested in learning CLI, in such case, the best is to install Ubuntu Server on your machine and follow some tutorials + document yourself.
Or you just want to have it running without too much hassle (or at least a minimum) and in this case, you should go for something like Cozy Cloud or Yunohost. You basically only have to install the distributions (Quite easy to do, no CLI, just selections) and all the rest will be through a web interface.

But CLI is cool ;)

---

