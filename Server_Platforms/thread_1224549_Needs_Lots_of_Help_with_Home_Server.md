---
title: "Needs Lots of Help with Home Server"
date: 2009-07-27
forum: Server Platforms
---

### Post by blsmit on 2009-07-27
Fellow Ubuntu users and experts, I am having a few isues setting up the server I want to set up. 
I purchased a MSI Wind Nettop 100 with a 320 GB HDD, 2 GB RAM, NO CD-ROM.
I work on my Macbook Pro with VBox Ubuntu 9.04, my girlfriends Acer Laptop with Vista Home Premium, and my desktop pc with Vista Home Basic.
I can install both Ubuntu 9.04 Server and Desktop.
I CANNOT install Ubuntu 8.04LTS Desktop and Server, or FreeNAS Server.

My connection is Cable Modem--wired-->Linksys WRT54GS--wired-->MSI Ubuntu Server

My requirements are: 
1. Web server 
    1.1. Adobe Flash Compatible 
2. Print Server 
    2.1. Ability to print from outside network
3. Music server 
    3.1. Song Download compatible
    3.2. Stream file download (.m3u) 
    3.3. Music listening from browser (ie pandora.com like) 
4. OpenSSH (server) or VNC (desktop) 
5. Dynamic DNS 
    5.1 ddclient
6. folding@home (or is this a terrible idea?)

What I've gotten to work on Ubuntu Server 9.04: 
1. Webserver:  Using the LAMP install Apache, MySQL, and PHP have always worked.
2. Music Server:  I worked on jinzora and got song downloading to work and stream file download to work.
3. OpenSSH:  This has always with OpenSSH install.
4. Dynamic DNS: ddclient has always worked with editing the /etc/networking/interfaces.

What I have not gotten to work on either Ubuntu Server 9.04 or Ubuntu Desktop 9.04:
1. Adobe Flash Compatible:  I haven't attempted this but I forsee this being an issue in the future.
2. Print Server: My HP 4180C is connected via usb, and I have the correct .ppd file but it refuses to work.
3. Music Server: I am completely lost on how to setup the music listening from browser.
    3.1 I've tried using:
        3.1.1: Jinzora [http://rubbervir.us/projects/ubuntu_media_server/](http://rubbervir.us/projects/ubuntu_media_server/)
        3.1.2: Sockso [http://www.smokinglinux.com/linux-media/start-your-own-music-personal-server-with-sockso-on-ubuntu-gutsy-710-linux](http://www.smokinglinux.com/linux-media/start-your-own-music-personal-server-with-sockso-on-ubuntu-gutsy-710-linux)
        3.1.3: Gnump3d [http://onlyubuntu.blogspot.com/2007/04/streaming-media-server-in-ubuntu.html](http://onlyubuntu.blogspot.com/2007/04/streaming-media-server-in-ubuntu.html)
        3.1.4: Ampahce [http://nousessence.com/node/1260](http://nousessence.com/node/1260)
        3.1.5: Subsonic [http://blog.lundscape.com/2009/05/install-subsonic-on-ubuntu-server/](http://blog.lundscape.com/2009/05/install-subsonic-on-ubuntu-server/)
        3.1.7: Rhythmbox
        3.1.8: MPD
        3.1.9: Firefly: [http://www.ubuntugeek.com/howto-setup-itunes-compatible-media-server-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-itunes-compatible-media-server-in-ubuntu.html)

Questions:
1. Are there any howto's for running a flash website on ubuntu server?
2. Is it even possible to print from a printer outside the network?
    2.1 I enjoy doing work during my college classes, and if I could print documents to my printer at home it would be a great help.
3. What am I supposed to do with this music server, Nothing seems to work!?! HELP!?!
4. Folding@Home, I would love to help out with folding at home, but the only computer I have on all the time is my server. I figure since the server isn't going to be used all that much, I could devote some if not all of the CPU to Folding.
    4.1 Is this possible?
    4.2 Is it wise to do?
    
Sorry for making this so long, but i've been working on this server for 3-4 weeks for 2-10hours per day.

Thanks to anyone who helps, and sorry if I double post on a topic.

blsmit

---

### Post by tgalati4 on 2009-07-27
This is a good list for you to print out.

You may get better reponses by chipping away at one problem at a time and posting each problem in it's appropriate subforum.

As far as printing across the web.  Sure, it's possible.  Poke a hole (port 631) in your firewall or router.  If you have a DSL or cable modem, go into the setup web page and set port forwarding for 631 and assign it to the local IP (it should be a static IP to avoid headaches) that the printer hangs off of.  

For the music servers, I tried several in your list and they work out of the box from within your LAN.  To stream outside of your LAN you will again have to poke some holes.  Look at the documentation for each server to determine the port(s) that need to be left open to stream.

I don't know the spec's on the MSI Wind nettop, but you can always run Folding, just not sure if it will measureably interfere will all of the other server functions you want to get running.

Folding won't help your printing or music streaming, so focus on getting things to work first.  Although linux is multitasking, your problem-solving skills are better served one-at-a-time.

---

### Post by blsmit on 2009-07-27
Tgalati4-- Thanks for the response.  As far as opening the ports, I accomplished that and was able to set up ampache, jinzora, and i think sockso, but was never able to get any of them to work in the browser, I also opened the ports for the printing but once again was unable to print from outside the network yet alone inside.

The list of requirements are in order of importance.  So folding would be my last step.

Thanks for your help, but more information would have been helpful.

---

### Post by tgalati4 on 2009-07-28
What specific ports are you using for each music streaming service?

For instance, I have gnump3d running on port 9000.

I can see the gnump3d front page when I put [http://192.168.1.114:9000](http://192.168.1.114:9000) in the browser.

What do you get for each service when you put in the correct [http://IP: PORT?](http://IP: PORT?)

You will have to be more specific about each error that you are getting with each music server.

Also, how is your server attached to the rest or your network?  Do you have a 4-port hub that it is hung off of?

Of course you need to be able to access the server from your LAN to make sure it works before opening ports to the outside world.

---

### Post by blsmit on 2009-07-28
I'm working on Ubuntu 9.04 Desktop Version with SSH, Apache, and SFTP working
> What specific ports are you using for each music streaming service?

I have open: ssh 22, sftp 21, http 80 , https 8080, mysql 3306, CUPS 631 , and 6600 for Jinzora.

> You will have to be more specific about each error that you are getting with each music server.

My Issue now Is that Jinzora won't play nice with MPD or VLC for jukebox control.

> Also, how is your server attached to the rest or your network?

My connection is Cable Modem-->Linksys WRT54GS--Wired-->Server; --Wireless-->Laptops.

> Of course you need to be able to access the server from your LAN to make sure it works before opening ports to the outside world.

I'm not sure what this means. I am able to view the index.php from apache on both my laptop and the "server".  I will post in the morning if I am able to view this outside the network. 

> or instance, I have gnump3d running on port 9000.
Is gnump3d running with a jukebox, (are you able to listen to music in a web browser outside the network?

Hope this information was helpful.

blsmit

---

### Post by tgalati4 on 2009-07-29
I'm not familiar interfacing Jinzora and either MPD or VLC.  That will require some research.  I use mt-daap (firefly) and mediatomb for my general media sharing.  I use gnump3d to feed a church website.

Does Jinzora default to port 6600?  If yes, then you should be OK.  If you chose 6600, then it may conflict with another service.  In that case you should select a port greater than 10000 since most ports below 10000 are reserved for existing services.

As for gnump3d:

See if you can play any files from:

[http://wofmusic.homelinux.org:9000/](http://wofmusic.homelinux.org:9000/)

My comment about running a service locally means that you should be able to run a service on your locally-connected machine first (via direct cable connection to the router), then check wireless connection--sometimes wired connections work but wireless can be problematic due to different router rules being applied to the wireless versus the direct-connect ethernet cable.

If your service works as desired in both cabled and wireless mode locally, then try it outside the network.  From a friend's house for instance, or use the external IP address to access the service.

---

### Post by blsmit on 2009-07-29
I visited the site you listed, I am unable to play directly from the browser, I must download the .m3u to be played from iTunes.  I'm looking to play directly from the browser.

> Does Jinzora default to port 6600?
When I finally set everything up with Jinzora, it called an error that MPD could not connect to the jinzora on port 6600, so I opened it up.  Still didn't work.

Also I am able to view my site from outside the network.

Still very confused with playing media in the browser.  Ill try picking a port number above 10000, although I don't think its going to work.

blsmit

---

### Post by tgalati4 on 2009-07-29
I can play media from my church music server in Firefox 3.0.12.  I'm running Linux Mint 7 (Gloria) based on Jaunty.  It plays right in the browser with whatever embedded player Firefox comes with.  If on a mac, it will also play on safari using the embedded quicktime player.  Using Control(or Option)-U in iTunes, it will also play the *.m3u files.  It's really streaming, but the *.m3u file is needed to play a list of files--an entire church service for example.

As far as MPD is concerned, my understanding is that MPD is music player daemon.  It resides on your server and will only play music that resides on that server.  The music could be anywhere, but mpd only plays on the server it's installed on.  To control mpd you need a client such as mpc.  mpc can be run on the same machine or any remote machine.

apt-cache search mpd

will find packages related to mpd.

Since jinzora is a web-based music server and mpd is a server music player, I'm not sure how they work together.

---

### Post by blsmit on 2009-07-29
> I can play media from my church music server in Firefox 3.0.12 

I am unable to play your music from my firefox, or safari (haven't opened that program since I last installed OS X).  Am I missing something?

> It resides on your server and will only play music that resides on that server
But I do have it on the server, and my music is on the server, so it should work?
Ill try to set up both mpc and mpd, maybe it will work?

blsmit

---

### Post by tgalati4 on 2009-07-30
Linux Mint configures firefox to play media out-of-the-box.  Ubuntu may require some configuration.  Sounds like you need a media player plugin for both firefox and safari.

mpc controls mpd.  It's a simple but reliable protocol.

---

### Post by blsmit on 2009-08-02
Sorry for the really late post back, I was away for the weekend (starts thursday for me)

I'm officially giving up on ubuntu for my server. I'm shooting for using [Mac OS X]("http://www.uselessninjas.com/guides/msiwindosx/") and[ pulpTunes]("http://pulptunes.com") to sync up with itunes, and link it to my dynamic dns ([as per]("http://www.macinstruct.com/node/112")).  

I'm thinking of using ubuntu as my main system with virtual box running windows home basic.
My computer stats are 320GB HDD, AMD dual core CPU at 3.1Ghz (stock), 4GB 800 DDR2.  
How well do you think that will work (New thread??)

Thanks for the help
Blsmit

---

