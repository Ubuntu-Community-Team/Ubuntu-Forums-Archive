---
title: "My Ubuntu Server Build"
date: 2010-04-14
forum: Server Platforms
---

### Post by imbty on 2010-04-14
I've installed Ubuntu 8.04 (Desktop Edition) on an old PC from 2001 (1.1 Ghz, 512 MB DDR1) to try out because I want to the basic things:

Share photos/videos/music with my main laptop (mac) and 2 windows laptop
Stream photos (no, not really) and videos to ps3
Automatic backup of documents (.doc, .pdf, etc) and selected media folders of laptops to server
Automatic backup of important media on server to an external hard drive via usb
Remote access the server and 2 windows laptop with my main laptop
FTP (somewhere down the road for when I travel out of the country so I can upload my photos on the go)
Torrent - i kinda want a GUI and access remotely locally, but it'd be nice if I can use SSH to download without GUI. I'm not sure if it's possible.

I've managed to:
share photos/videos/music to said 3 laptops
Stream to ps3
Remote access the server

I have yet to set up the FTP, but I can probably manage. My problem is I can't automatically backup selected folders. I want to also be able to remotely access the home server via internet (not just locally), but i don't know where to start.

Like I said, I'm only trying out Ubuntu 8.04. I've used it before, but not server purposes. Once I purchase a new mobo/cpu/memory, I plan on using Ubuntu Server Edition and hope I can manage it without a GUI.

Since this PC is from 2001, I hope to get away with mobo/cpu/memory for under $200. I already have a case, 1 500GB SATA hard drive; 2x 2.5" hard drive (which i'll need to buy an enclosure for). 

I'm actually not sure how to setup the hard drives. The 2.5" are obviously 5400, but I was thinking of installing the OS on one of the 2.5" and have the 500GB strictly for storage along with the other 2.5". Would I be able to RAID the 500GB + 160GB together while the 100GB is for OS?

edit: also, i've used ftp before, but never through a router. if my server is 192.168.1.xxx, how can i connect to the ftp? i guess the server's IP address (not the static ip) and it'l be good to go without any portforwarding?

---

### Post by dudumomo on 2010-04-14
Hello imbty,
For a FTP, which kind of FTP do you need ? I mean, there are basically 2 and half choice. Using FTP/FTPS and SFTP (Based on SSH).
I rather prefer SFTP than FTP.

But you can also only use a Web file explorer if you like it.
Check the demo here: [http://www.ajaxplorer.info/wordpress/demo/](http://www.ajaxplorer.info/wordpress/demo/)
(Login and password = demo)
And how to install it: [http://www.freelydifferent.com/self-hosting/ajaxplorer-file-explorer/](http://www.freelydifferent.com/self-hosting/ajaxplorer-file-explorer/)

Also, a torrent, I suggest you using deluge torrent. It runs as a daemon, can access remotely to the daemon by installing another instance of deluge on your main computer (Then just connecting the GUI to the daemon) or using directly the WEB UI: [http://www.freelydifferent.com/self-hosting/deluge-torrent-daemon-webui/](http://www.freelydifferent.com/self-hosting/deluge-torrent-daemon-webui/)

To have access to your computer not only locally but also remotely, you can simply use SSH (If you are fine with it).

You will need to know your IP (Not your local IP) and to open the port 22 or any other port according to your conf.

For the FTP, it will be the same, you will need to open some ports and to access remotely with your real IP.

To backup all your data, you can simply create a partition on your 500 hard drive of 100go or a bit more to be sure, to make a ghost of your 100GB OS. (Ie, every thursday night at 2am, CRON can launch the command to copy your entire disk to your 500gb.

Oh, and if you want to share photos with a gallery, I suggest you Piwigo. (Again, you can find a tuto on my self hosted blog: [www.freelydifferent.com](www.freelydifferent.com))

---

### Post by imbty on 2010-04-14
I think SFTP will work, since I just plan to upload JPEGs so when I travel, I can upload my pictures there. This is me assuming I can use Terminal (Mac) or Command Prompt (Windows).

I'm actually having trouble with SSH right now. I'd like to turn on Ubuntu's Mediatomb (to stream to PS3) using my Mac's Terminal, which I succeed, but once I turn off the Terminal (Mac), the Mediatomb shuts down.

What's the advantage of making a backup of my OS? Ill only be using it to run a home server. All DATA will be in another storage. I plan to use a 2.5" 100 GB 5400 as my OS btw.

And thanks for the help. I'll be looking into this Deluge torrent.

---

### Post by gordintoronto on 2010-04-14
You definitely want to be able to do port forwarding from your router to the server.

---

### Post by jhollinger on 2010-04-16
Aye, you'll need port forwarding for ssh/sftp access from the outside world. All router's are different, so I can't give you exact advice, but you'll want to forward port 22 (or the "ssh service") to your computer's IP.

Most consumer-level routers will allow you to set a few static IPs based on your machine's MAC address. But again, they're all very different and use weird terms and horrible UIs, so you'll have to tool around a bit. ('ifconfig' will show you your MAC address if your router's mean and won't show you somewhere).

If your router's a tool and doesn't allow static IPs, you'll just have to keep up with your IP in the port forwarding settings. It shouldn't change more than once a month, if that. And you might be able to set that, too.

And of course to access your machine from The Outside, you'll need to know your router's external or "WAN" IP. If you want a free domain name instead, you can sign up at [http://www.dyndns.com/](http://www.dyndns.com/). Most routers can hook up your account there, keeping everything working when your WAN IP changes.

---

### Post by buntunoob on 2010-04-19
start mediatomb with 
mediatomb -d
that starts it as a daemon

---

