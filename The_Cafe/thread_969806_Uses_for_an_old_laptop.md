---
title: "Uses for an old laptop?"
date: 2008-11-03
forum: The Cafe
---

### Post by rhcm123 on 2008-11-03
I have a bunch of old, still functioning laptops lying around that i want to put to use in some form of server application.

Machine 1: Toshiba, 2 ghz processor, 1 gb ram
Machine 2: Toshiba, 1.50 ghs processor, 256 mb ram
Machine 3: IBM, acient, 250 mhz processor, 125 mb ram

Does anybody have any good ideas for these? There still in good shape, all work fine (with the exception of the IBM, but that's pretty useless anyways)
-All have ethernet (i got a pcimcia card for the ibm)
-All have power adapters
-2 out of 3 have batteries (machine 1 does not)
-All screens are readable (occasionally 1 goes all funky but it still works)
-I did not mention the HDD because we have a 250 gb file server that they connect to

I would just like some good ideas to put these things to work in a server application setting.

---

### Post by hessiess on 2008-11-03
torrent server
renderfarm
http server
firewall

---

### Post by Daveski on 2008-11-03
> **rhcm123 said:**
> 
Machine 1: Toshiba, 2 ghz processor, 1 gb ram


Wow, that one is better spec'ed than my main machine. Ubuntu will run wonderfully on this one.

---

### Post by rhcm123 on 2008-11-03
> **Daveski said:**
> Wow, that one is better spec'ed than my main machine. Ubuntu will run wonderfully on this one.

It is running ubuntu and it runs wonderfully. It even has ATI graphics.
The problem is, i got it from my uncle (no joke) who broke the **** out of it.

-Power button is busted
-No battery
-Had to scrounge for power supply at radio shack
-grey bars appear through screen, forcing image to move downwards past the bottom of the screen

It's great hard ware
just the user interface is junk
i usually VNC to it, cause it lives in my closet under my pritner

---

### Post by rhcm123 on 2008-11-03
> **Daveski said:**
> Wow, that one is better spec'ed than my main machine. Ubuntu will run wonderfully on this one.

And yes, it is also better speced than my main laptop (a toshiba, again, 1.75 ghz, 759 mb ram, 80 gb hdd)

---

### Post by rhcm123 on 2008-11-03
> **hessiess said:**
> torrent server
renderfarm
http server
firewall

To adress your ideas:
Torrent Server - This sounds interesting. How do i do it
Renderfarm - what is a render farm
http server - i know of the idea, i just have no desire for one
firewall - already got one

:)

---

### Post by hessiess on 2008-11-03
> Torrent Server - This sounds interesting. How do i do it
install a CLI torrent client and controal it via SSH, theres probably better ways.

> Renderfarm - what is a render farm
a collection of computers used for 3D rendering.

---

### Post by rhcm123 on 2008-11-03
i see
i have no use for the render farm
but a tornent host would be a good idea... transmission is eating up a lot of my computer space right now:p

---

### Post by Daveski on 2008-11-03
> **rhcm123 said:**
> 
-Power button is busted
-No battery
-Had to scrounge for power supply at radio shack
-grey bars appear through screen, forcing image to move downwards past the bottom of the screen

It's great hard ware
just the user interface is junk
i usually VNC to it, cause it lives in my closet under my pritner

That is a shame. You could build a wooden cabinet, and use a CRT (loads around now), proper Quickshot type joystick and buttons and have yourself a nice retro arcade machine. Use it to run emulators (Mame, PSX, SNES etc.) and re-live those classic gaming moments.

---

### Post by rhcm123 on 2008-11-03
Actually, i own a nes, n64 and dreamcast, so i really have no use for that, soory... but the VGA port still works, so i'll look into that.

---

### Post by AndyCooll on 2008-11-03
For your torrents you can use rTorrent. It's an excellent low resource torrent client, heck even your lowest spec laptop could run that. Works great with ssh and screen.

I have a couple of NSLU2's running a basic headless version of Debian. I think they have 32mb RAM and they act as my file server and backup server, I also have rTorrent running on the file server.  

You can also use one as a file server and print server, and possibly one as a media server, and possibly one as a backup server, and if you want to get more technical have one of them running as a router/firewall or mail server or even a dhcp server.

The choice is yours, there's loads of things you can use them for!

:cool:

---

### Post by rhcm123 on 2008-11-03
> **AndyCooll said:**
> For your torrents you can use rTorrent. It's an excellent low resource torrent client, heck even your lowest spec laptop could run that. Works great with ssh and screen.

I have a couple of NSLU2's running a basic headless version of Debian. I think they have 32mb RAM and they act as my file server and backup server, I also have rTorrent running on the file server.  

You can also use one as a file server and print server, and possibly one as a media server, and possibly one as a backup server, and if you want to get more technical have one of them running as a router/firewall or mail server or even a dhcp server.

The choice is yours, there's loads of things you can use them for!

:cool:

Good ideas, here's my take:
Torrent server: Working on that one. Gonna be a fun project!
File Server: Built and running. Also integrated with media server.
Print Server: Attached to my aging HP deskjet, prints all computers in the house.
Backup Server: How would I do that automatically?
Firewall: Got one already
Mail Server: An stmp or a POP3? That would be a pain in the *** to configure and there is no real reason (to my mind) to do it.
DHCP: I'm statically configured... but what would this do?

Thanks, i've got a little inspiration now...

---

### Post by CJ Master on 2008-11-03
Set the insides on fire, then imediately close the case and RUN! It'll be a nice fireworks show until the fire reaches the battary.... BOOOOOOOOOOM!

Oh... serious?

I'd recomend using it as an external drive for backup programs, keeps your data safe as long as your not using windows with its viruses.

---

### Post by AndyCooll on 2008-11-03
> **rhcm123 said:**
> Good ideas, here's my take:
Torrent server: Working on that one. Gonna be a fun project!
File Server: Built and running. Also integrated with media server.
Print Server: Attached to my aging HP deskjet, prints all computers in the house.
Backup Server: How would I do that automatically?
Firewall: Got one already
Mail Server: An stmp or a POP3? That would be a pain in the *** to configure and there is no real reason (to my mind) to do it.
DHCP: I'm statically configured... but what would this do?

Thanks, i've got a little inspiration now...
For rTorrent there's an excellent guide here: [Howto: Use rtorrent like a pro]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/")

I only mentioned the last two as possible advanced projects, why? ..."just because you can". I'm not sure how much value they would be since typically (for instance) your router automatically acts as a dhcp server.

For automatic backing up you need to have a look at rsync and using the cron.

:cool:

---

### Post by Compucore on 2008-11-03
Also considered this as another explanation. To crunch numbers or mass enough information like a supercomputer. A render farm can deal with almos anything you want it to do depending on what you want the render farm to do a beowulf system. I think I had seen something on youtube where they had about 1000 DUal G4 systems maxed out on ram. And all that did was to crunch numbers I believe. 

Compucore


> **hessiess said:**
> install a CLI torrent client and controal it via SSH, theres probably better ways.


a collection of computers used for 3D rendering.

---

### Post by steveneddy on 2008-11-03
Beowulf cluster of laptops!

---

### Post by Daveski on 2008-11-04
> **AndyCooll said:**
> 
You can also use one as a file server and print server, and possibly one as a media server, and possibly one as a backup server, and if you want to get more technical have one of them running as a router/firewall or mail server or even a dhcp server.


A media server is a great idea if you have a PS3 or XBOX connected to your telly. Put all your music, photos and videos on a main file server, and stream them out to the console for consumption without looking too much like a geek.

---

### Post by mips on 2008-11-04
> **rhcm123 said:**
> It is running ubuntu and it runs wonderfully. It even has ATI graphics.
The problem is, i got it from my uncle (no joke) who broke the **** out of it.

-Power button is busted
-No battery
-Had to scrounge for power supply at radio shack
-grey bars appear through screen, forcing image to move downwards past the bottom of the screen


Have you tried scrounging places like ebay for second hand parts. Might be worthwhile to fix.

---

### Post by TwiceOver on 2008-11-04
Strip one of them and make a digital picture frame.

---

### Post by manicman on 2008-11-04
If your thinking about using one as a Torrent server its worth looking into torrentflux. I run it on my server and it means you dont have to use a CLI interface everytime you download a torrent.

---

### Post by bigbrovar on 2008-11-04
> **Daveski said:**
> A media server is a great idea if you have a PS3 or XBOX connected to your telly. Put all your music, photos and videos on a main file server, and stream them out to the console for consumption without looking too much like a geek.

i have been trying to do that but i havent found the right tool .. any ideas

---

### Post by civillian on 2008-11-04
An idea I had was to maybe get a larger hard drive and use the laptop as a jukebox (there are some that have been made online if you google them) whihc seems to be a cool idea, although it would be a waste of your computers specs, if I'm honest.

Although you could use madplay and control it via ssh if you wanted a bit more out of it...

---

### Post by Twitch6000 on 2008-11-04
you could take parts from each and make one.

like take ram from number 1 put in in number three.

---

### Post by Daveski on 2008-11-04
> **bigbrovar said:**
> i have been trying to do that but i havent found the right tool .. any ideas

Try GNUMP3d or fuppes
[http://www.howtoforge.com/set-up-a-linux-playstation-3-media-server-with-ubuntu8.04](http://www.howtoforge.com/set-up-a-linux-playstation-3-media-server-with-ubuntu8.04)

---

### Post by K.Mandla on 2008-11-04
(Ahem.)

[http://kmandla.wordpress.com/2007/03/16/ten-things-you-can-do-keep-an-old-computer-useful/](http://kmandla.wordpress.com/2007/03/16/ten-things-you-can-do-keep-an-old-computer-useful/)
[http://kmandla.wordpress.com/2008/10/28/ten-reasons-not-to-buy-a-new-computer/](http://kmandla.wordpress.com/2008/10/28/ten-reasons-not-to-buy-a-new-computer/)
[http://kmandla.wordpress.com/2007/09/14/things-to-do-with-an-old-computer/](http://kmandla.wordpress.com/2007/09/14/things-to-do-with-an-old-computer/)

---

### Post by fedex1993 on 2008-11-04
> **Daveski said:**
> A media server is a great idea if you have a PS3 or XBOX connected to your telly. Put all your music, photos and videos on a main file server, and stream them out to the console for consumption without looking too much like a geek.

yeah is there a guide to this somewhere

---

### Post by EdThaSlayer on 2008-11-04
Put them in a personal museum of yours. :popcorn:
Those laptops should gain some dust, and 20 years later you could go look back and say,"these were the days when computers were slow and bulky".

---

### Post by Frak on 2008-11-04
> **EdThaSlayer said:**
> Put them in a personal museum of yours. :popcorn:
Those laptops should gain some dust, and 20 years later you could go look back and say,"these were the days when computers were slow and bulky".
And had broken power buttons by default...

---

### Post by rhcm123 on 2008-11-05
Oh, lord you guys write far too much :).
Ok, quotes and responses, one at a time:

> **steveneddy said:**
> Beowulf cluster of laptops!
Yeah... ELECTRICITY BILL > Money i have. :) Thanks, maybe later.

> **Daveski said:**
> A media server is a great idea if you have a PS3 or XBOX connected to your telly. Put all your music, photos and videos on a main file server, and stream them out to the console for consumption without looking too much like a geek.
I've heard of this, but I can't get my 360 to connect to the file server. I heard there was a program to do it, but I cant find one..GRR. :mad:

> **TwiceOver said:**
> Strip one of them and make a digital picture frame.
Oh... I could do that.. the problem is.. I have no pictures I particulary want to display to people...

> **C!V!NT said:**
> An idea I had was to maybe get a larger hard drive and use the laptop as a jukebox (there are some that have been made online if you google them) whihc seems to be a cool idea, although it would be a waste of your computers specs, if I'm honest.

Although you could use madplay and control it via ssh if you wanted a bit more out of it...
I've heard of this jukebox idea, and I could do it if my parents so approved (I have all of my dad's records as mp3's so perhaps I could get them on the information superhighway. :)

> **Twitch6000 said:**
> you could take parts from each and make one.

like take ram from number 1 put in in number three.
Some of the RAM from number 2 is in my main laptop. :)

> **Frak said:**
> And had broken power buttons by default...
:lolflag:


Ok, so here are my current set of ideas:
Setup my print server (just eating energy waiting for me to print somthing) as a media server as well. I can now share media with the 360.
Set up one of the machines as a number cruncher. I heard google was doing somthing like that where you could donate processing time to a good cause.
Setup another one to backup stuff to the file server.
Place machine three in a musemue.

:KS

---

### Post by rhcm123 on 2008-11-05
> **rhcm123 said:**
> 
Ok, so here are my current set of ideas:
Setup my print server (just eating energy waiting for me to print somthing) as a media server as well. I can now share media with the 360.
Set up one of the machines as a number cruncher. I heard google was doing somthing like that where you could donate processing time to a good cause.
Setup another one to backup stuff to the file server.
Place machine three in a musemue.


Or, I could setup the IBM as the picture frame.. does anybody know of a good command-line based (it dosent actually run 'buntu) picture frame program?:confused:

---

### Post by rhcm123 on 2008-11-05
> **K.Mandla said:**
> (Ahem.)

[http://kmandla.wordpress.com/2007/03/16/ten-things-you-can-do-keep-an-old-computer-useful/](http://kmandla.wordpress.com/2007/03/16/ten-things-you-can-do-keep-an-old-computer-useful/)
[http://kmandla.wordpress.com/2008/10/28/ten-reasons-not-to-buy-a-new-computer/](http://kmandla.wordpress.com/2008/10/28/ten-reasons-not-to-buy-a-new-computer/)
[http://kmandla.wordpress.com/2007/09/14/things-to-do-with-an-old-computer/](http://kmandla.wordpress.com/2007/09/14/things-to-do-with-an-old-computer/)

Actually, I have already read these articles! I was particularly interested in the bottom one.
I want to use one of my machines as a web server (already changing ideas!) so that I can access my file server across the web? I've got apache on it, got any ideas on how to access it? (I also have apache on my file server)

---

