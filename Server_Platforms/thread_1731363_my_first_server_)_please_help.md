---
title: "my first server :) please help"
date: 2011-04-17
forum: Server Platforms
---

### Post by root486 on 2011-04-17
Hi All,
  I'm pretty new to linux, and i want to set up my first server on an old dell pc.  i would like to install ubuntu server edition 10.04.  

i've been looking around online and in the forums, and it seems that there is a lot of info around for people who want really robust servers with lots of functionality.  i don't want any of that, just a very slimmed down media server

here is what i'd like the server to do:
hold all of my music and video files,
provide a reasonably easy way to move files on and off of it from any of my other computer (mostly laptops),
act as a media server to an xbox 360

here is what i don't want my server to do:
provide remote access outside of my home network,
provide e-mail service
support web hosting

thorough instructions would be preferred, but a link to a site would be welcome as well.  

thank you for your time, i look forward to any help or advice that can be offered

---

### Post by thecamelcoder on 2011-04-17
Hey mate, sounds like a great little project. 

Check out my server build guide and let me know how you get on: [http://www.linux-geek.co.nz/2011/04/17/perfect-ubuntu-10-10-server-installation/](http://www.linux-geek.co.nz/2011/04/17/perfect-ubuntu-10-10-server-installation/)

Basically tis tutorial will provide you with a server that will:

[LIST]
[*]Keep network time
[*]Be accessable locally via a shell
[*]Retain a static IP
[*]Work as a network files server
[*]Have a database
[*]Have a web server
[*]and a couple of management apps
[/LIST]

The LAMP portions is not necessary but its something that given time you'll get stuck into i'm sure. 

Let me know if you need any more help. 
):P

---

### Post by MattBD on 2011-04-17
Sounds like you want Samba for the file server - at least if you want to be able to share files with machines running Windows. There's a few guides at [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba) that may be of use. If you don't need to share files with Windows, then NFS might be a better choice.

Regarding streaming content, there's a couple of UPnP media servers that may do what you want - check out [https://help.ubuntu.com/community/MediaTomb](https://help.ubuntu.com/community/MediaTomb) and [https://help.ubuntu.com/community/Ps3MediaServer](https://help.ubuntu.com/community/Ps3MediaServer) for more details.

I would also install an OpenSSH server so you can log in and administer the server without having to go to the bother of attaching a monitor to it. If you aren't comfortable using the command line for everything, you could check out Webmin, which is a browser-based configuration tool which you may find more convenient.

Finally, considering that this is intended to be a file/media server, may I suggest a couple of other things you might want to consider including? A BitTorrent client with either a command-line or web interface might come in handy, and maybe some kind of CD ripper too?

---

### Post by root486 on 2011-04-17
Hi thecamel and matt, thanks for your suggestions, i'll be starting my project later today, i'll let you know how it goes.

i would like to run the server headless, but if i install an openSSH, does that mean that it can be accessed over the internet, or just when i'm physically at home on my home network?  i'd prefer the latter.

as far as torrents are concerned, is this possible:
i have bittorent on my linux laptop already, when i download a file, can i just have that download go straight into a folder on the server, or does it need to go into my laptop and then transferred to the server

the whole reason for this desire to have a media server is because everyone in the house downloads cool and different music for themselves, and we're constantly saying to each other, 'did you hear such and such... oh i just downloaded it, i'll put it on disk/flash for you later.'  problem is, we always forget to get around to it, so having somewhere central to dump it all makes sense.  

so is this possible:
we'd all like to plug in our external hard drives and put our current libraries on the server, can this be as simple as drag and drop?  and do we plug our drives to our laptops and put them on over the network, or do we plug straight into the server? 

thanks again for reading this, i can hardly wait to get home to try all of this!

---

### Post by usatonycuba on 2011-04-17
Openssh server, gives you the opportunity to connect to your server safely, for the purpose of administration via "command line" where you can install packages and updates.... Now, with the purpose of installing a Web server to your needs .. I would recommend LAMP, based on open source and with a wide and very good community forums.

And ;) without wishing to discredit the @thecamelcoder tutorial, I would also recommend that you take a look at >> howtoforge for [ The Perfect Server - Ubuntu Maverick Meerkat (Ubuntu 10.10) [ISPConfig 2]]("http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-2")

---

### Post by elico on 2011-04-17
i dont recommend to anyone that dont really understand what ISPconfig is to use it.
it's very complicated system that you can get your server loose it's qualities very fast.
if you do want to work with some none  shell based interface use webmin.
and read some before you touch the keyboard.
installing LAMP mail-server ssh and FileSharing for windows  and other OS are built in into the ubuntu server.
just install webmin and you will feel like home in no time.

---

### Post by MattBD on 2011-04-17
> **root486 said:**
> i would like to run the server headless, but if i install an openSSH, does that mean that it can be accessed over the internet, or just when i'm physically at home on my home network?  i'd prefer the latter.

Assuming you already have a router of some kind that allocates IP addresses to computers on the network, then it would only be accessible from the local network. It is, however, a good idea for you to allocate the server a static IP address on the local network rather than allow it to be allocated dynamically.

If you wanted to be able to connect to it from an external network, you'd need to forward the port you were running SSH on from the router to the server.

As for BitTorrent, I know that Transmission and Deluge both have web interfaces. I've just looked at the one for Transmission and it allows you to either upload a .torrent file for download, or enter a URL for the .torrent file to download it, and it will start immediately once it has the .torrent file. It also allows you to specify where you want to download the files to.

Hope that helps!

---

### Post by usatonycuba on 2011-04-17
> **elico said:**
> i dont recommend to anyone that dont really understand what ISPconfig is to use it.
it's very complicated system that you can get your server loose it's qualities very fast.
if you do want to work with some none  shell based interface use webmin.
and read some before you touch the keyboard.
installing LAMP mail-server ssh and FileSharing for windows  and other OS are built in into the ubuntu server.
just install webmin and you will feel like home in no time.

> **root486 said:**
> .....
here is what i don't want my server to do:
provide remote access outside of my home network,
provide e-mail service
**support web hosting**

thorough instructions would be preferred, but a link to a site would be welcome as well....  

> **usatonycuba said:**
> ...I would also recommend that you **take a look** at
@elico.. any server has its own complications and ways around .. so, **take a look**, means to see, understand, experimenting with the code and installations process.. 

**support web hosting**  <<< ...here fit's.. < perfectly > ..a control panel I guess

BTW

ISPConfig <<< is an open source hosting control panel....
Webmin <<<< is a web-based system configuration tool....

Some time we get confuse about.. we can use webmin as (hosting control panel)?.. when we get familiar with (webmin) capabilities (it may help), but webmin is in fact a (system configuration tool) with a powerfull administrate services..

[QUOTE=falko] at [here](http://www.howtoforge.com/forums/showthread.php?t=2680)

ISPConfig is more user-friendly, i.e., you don't need Linux knowledge. And you have 4 levels of administration: admin, resellers, customers, and users.

 With Webmin, you can administrate nearly everything on your server, but you don't have these 4 levels like in ISPConfig, and you must have knowledge about what you do. Webmin isn't a tool I'd give to an end-user.[/QUOTE]

+1

---

### Post by root486 on 2011-04-17
thanks for everything thus far!  i didn't get as much time to fool around as i would have liked today, but i did:
1) install 10.04
2) put in openSSH and samba
3) access nano interfaces to change setting for a static ip address, although i didn't assign it yet, i'll get to that tomorrow.

i also checked from one laptop, and the server does show up.  no files in it yet, but i'll create and test one next time

so, slow but steady progress.  i'm going to try to set the static address, create a file and open it over the network, and install mediatomb first chance i get, hopefully tomorrow, or maybe the day after

any other ideas/suggestions about what else i can do or should consider?

---

### Post by dfreer on 2011-04-17
> **root486 said:**
> 
here is what i'd like the server to do:
hold all of my music and video files,
provide a reasonably easy way to move files on and off of it from any of my other computer (mostly laptops),
act as a media server to an xbox 360


As suggested before, samba will handle the file sharing, and possibly the serving of media to the 360 (pretty sure 360 can browse local network shares).

Since others and yourself were suggesting bittorrent, have you heard of [torrentflux]("http://www.torrentflux.com/") or [torrentflux-b4rt]("http://tf-b4rt.berlios.de/")? Not sure it's supported anymore but it used to work (2-3 years ago) great. It's basically a torrent server, that allows multiple users to download torrents from the server itself (kinda hard to explain but the screenshots should make what it does clear).

Other cool things to do: share music to all your computer's as a iTunes library, called [Firefly/mt-daapd]("http://en.wikipedia.org/wiki/Firefly_Media_Server").

---

