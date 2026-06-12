---
title: "Running tasks on a server instead of on a local machine"
date: 2006-03-18
forum: Server Platforms
---

### Post by wookieman on 2006-03-18
Hi

What I really want to do is run tasks like frostwire (p2p-client) on my server rather than on my main machine so I can switch my main machine off at night, is this possible ?

So far I've tried connecting via VNC to my server but that isn't working correctly (I get a blank screen), because Xserver doesn't like the graphics card in my server. Is there a way of running the Xserver purely for a VNCserver regardless of the local graphics capabilities ? I.e. at 800x600 even if the graphics card in the server is only good for cga/vga text/graphics ?

I've also tried FreeNX with similar results :( 

Cheers Wookie.

---

### Post by MJSOnline on 2006-03-20
Hi all.  I too would like to do the same as Wookieman, but using Azures too.  Is this possible?  Thankx M

---

### Post by MJSOnline on 2006-03-21
[QUOTE=MJSOnline]Hi all.  I too would like to do the same as Wookieman, but using Azures too.  Is this possible?  Thankx M[/QUOTE]
Anyone got any ideas? It must be possible..... M

---

### Post by colo on 2006-03-21
Use ssh and screen for CLI-applications.

---

### Post by MJSOnline on 2006-03-21
[QUOTE=colo]Use ssh and screen for CLI-applications.[/QUOTE] Hi Colo.  How does that work?  Sorry I am new to all this "server" stuff.  I am trying it for the first time ever.  Thanks. M

---

### Post by nocturn on 2006-03-21
Are these graphical applications that you want to run?

---

### Post by herrpoon on 2006-03-21
For torrents, I use [http://www.torrentflux.com/]("http://www.torrentflux.com/") which works really well.  

From the site:"*TorrentFlux is a FREE PHP based Torrent client that runs on a web server. Manage all of your Torrent downloads through a convenient web interface from anywhere. *

It's not as feature-full as azureus by any means, but it has the basics which is fine for me.

---

### Post by MJSOnline on 2006-03-21
[QUOTE=nocturn]Are these graphical applications that you want to run?[/QUOTE]
Some maybe..  As the above poster said use"TorrentFlux" but I do like the conreol of azures and maybe frostwire etc... I also want to keep most of my mp3 or ogg format music files on the 2nd harddrive in the server box for this reason... Any ideas or am I thinking of something that does not exiet? Thanks. Matthew

---

### Post by MJSOnline on 2006-03-21
[QUOTE=herrpoon]For torrents, I use [http://www.torrentflux.com/]("http://www.torrentflux.com/") which works really well.  

From the site:"*TorrentFlux is a FREE PHP based Torrent client that runs on a web server. Manage all of your Torrent downloads through a convenient web interface from anywhere. *

It's not as feature-full as azureus by any means, but it has the basics which is fine for me.[/QUOTE]
Hi.  Can I control the down/up speed using this app? How do I go about firewalls with is type of app?M

---

### Post by nocturn on 2006-03-21
[QUOTE=MJSOnline]Some maybe..  As the above poster said use"TorrentFlux" but I do like the conreol of azures and maybe frostwire etc... I also want to keep most of my mp3 or ogg format music files on the 2nd harddrive in the server box for this reason... Any ideas or am I thinking of something that does not exiet? Thanks. Matthew[/QUOTE]


The thing is that you can schedule console programs to run in the background or on specific times.

You can also have a graphical program run on one machine while displaying it on another, but it still exists if you shut down the machine with the display.

I guess what would suit you best is something like VNC, so you can keep the session on the server and connect/disconnect to it from a client.

---

### Post by herrpoon on 2006-03-21
[QUOTE=MJSOnline]Hi.  Can I control the down/up speed using this app? How do I go about firewalls with is type of app?M[/QUOTE]

Just to confirm, torrentflux is a frontend to the bittorrent client bittornado, i.e instead of controlling your torrents through a commandline (which is possible) you get a nice, easy-to-use graphical interface.

Yes, you can control the speed of each torrent, much like other clients, although to control the overall speed of all your torrents, you'll need to use an external app such as trickle.  With regards to the port forwarding, all you have to do is forward the necessary ports in your router as you would do normally.

Although, to be honest, if you are currently running an X server, i.e., gnome or whatever then your best bet is to use something like VNC as it will make life a lot easier :)  If you want to be adminster stuff externally you can use the following guide to set things up: [http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

@wookieman - I'm not too sure why VNC'ing isn't working for you, but you are probably better off posting in the beginners lounge as more people are likely to see it then.

---

### Post by MJSOnline on 2006-03-21
Hi nocturn & herrpoon. VNC sound just the ticket.  Can I use this app to do other things apart from torrents and p2p downloads? What about backups etc?  I love Linux for it's many apps! M

---

### Post by nocturn on 2006-03-21
[QUOTE=MJSOnline]Hi nocturn & herrpoon. VNC sound just the ticket.  Can I use this app to do other things apart from torrents and p2p downloads? What about backups etc?  I love Linux for it's many apps! M[/QUOTE]

With VNC, you can connect to a desktop on your server remotely (doesn't have to be real I think).  So you could run anything you wanted there...

---

### Post by MJSOnline on 2006-03-21
Hi nocturn.  So I could easily have, lets say a report open in openoffice and a 2nd window open running VNC looking at and setting up a torrent file to download or transfaring files from the downloaded folder of the torrents to say /media/2nd Drive/Backups  ?  What apps can I put on the server to do all this?  Is it just a server install of Ubuntu? Thanks. Matthew

---

### Post by nocturn on 2006-03-21
[QUOTE=MJSOnline]Hi nocturn.  So I could easily have, lets say a report open in openoffice and a 2nd window open running VNC looking at and setting up a torrent file to download or transfaring files from the downloaded folder of the torrents to say /media/2nd Drive/Backups  ?  What apps can I put on the server to do all this?  Is it just a server install of Ubuntu? Thanks. Matthew[/QUOTE]

The apps are all in the Ubuntu repositories.  You can install them via synaptic

---

### Post by MJSOnline on 2006-03-21
Magic!!  Thanks nocturn. Am right about the window sernerio? Thanks again. Matthew

---

### Post by nocturn on 2006-03-21
[QUOTE=MJSOnline]Magic!!  Thanks nocturn. Am right about the window sernerio? Thanks again. Matthew[/QUOTE]

Yes, you can do that.  You'll have a window in which the desktop on your server is displayed, you can do anything on there you could on a local machine.

---

### Post by MJSOnline on 2006-03-21
Fantastic...  Thats why I love Linux.  I was a Window$ user for 15years, but now I wont go back.  I may dual boot from it to time but fully Ubuntu Linux now.  Thanks again. Matthew

---

### Post by Jose Catre-Vandis on 2006-05-13
I found the answers on this voyage of discovery and learning here:

[http://www.ubuntuforums.org/showthread.php?p=1011516#post1011516](http://www.ubuntuforums.org/showthread.php?p=1011516#post1011516)

---

