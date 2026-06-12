---
title: "Setting WebServer on Hardy"
date: 2008-12-05
forum: Server Platforms
---

### Post by gvanto on 2008-12-05
I would like to get ssh, vnc and a webserver set up on my Linux Hardy (Ubuntu 8.04) machine.

I've obtained a static ip from my ISP, but trying to figure out how to get the whole networking thing set up (port forwarding, etc) so I can ssh into my box from anywhere, run a webserver on it, vnc into it, etc.

I know there's some static (internal) ip's I need to configure but a good step-by-step tutorial on getting this set up in Hardy would be so awesome. I've google a fair bit but no luck. Got a good tutorial on networking but for Fedora linux and alot of the examples are Fedora-specific.

Any help / advice appreciated a million on this!

Gerry
Networking noob :-)

---

### Post by cybergalvez on 2008-12-05
1) if you have a static IP set up your machine with that ip address, you'll most likely have to edit /etc/network/interfaces with some like:

auto eth0
iface eth0 inet static
address 192.168.1.60
netmask 255.255.255.0
gateway 192.168.1.1

or what ever your appropriate address are

2) install ssh
sudo apt-get install ssh
3) install apache
sudo apt-get apache2

reboot after install both

you can test apache using your browser and pointing it to [http://locahost](http://locahost)

you can test ssh by opening a terminal window and typing "ssh <username>@localhost" 
this should ask you for a password.  

if your not already logged into the machine with a gui I find vnc difficult, if you have the gui already and your logged just use System->Preferences->Remote desktop and turn that on. otherwise just use ssh to get a command shell.  You can also download and install nomachie which works really well and is my personal favorite way to log in remotely to my home machine

As for port forwarding and the rest, it kind of depends on how things are set up, do you have a router? will the router get the static ip from your ISP or will your home computer get it?

Assuming that you have a router and it will get the static IP you'll have to set your router to forward port 80 and port 22 to your home computer.  Google exactly how to do that with your router its a little different with every maker and model

Hope this helps, 
Jose




> **gvanto said:**
> I would like to get ssh, vnc and a webserver set up on my Linux Hardy (Ubuntu 8.04) machine.

I've obtained a static ip from my ISP, but trying to figure out how to get the whole networking thing set up (port forwarding, etc) so I can ssh into my box from anywhere, run a webserver on it, vnc into it, etc.

I know there's some static (internal) ip's I need to configure but a good step-by-step tutorial on getting this set up in Hardy would be so awesome. I've google a fair bit but no luck. Got a good tutorial on networking but for Fedora linux and alot of the examples are Fedora-specific.

Any help / advice appreciated a million on this!

Gerry
Networking noob :-)

---

### Post by hyper_ch on 2008-12-05
(1) are you behind a router?

(2) ssh server:
```

sudo apt-get install openssh-server

```

(3) webserver
I'd say you'll also need a dns server if you want to operate your home webserver... as you have a static IP, you could also run a mailserver... I'd suggest to have a look at the perfect server howtos at [http://www.howtoforge.com](http://www.howtoforge.com)

---

### Post by wkitty42 on 2008-12-06
i would be ***extremely*** wary of doing everything on one box... there's just too many irons in the fire to worry about and sooner or later, you will get burned... 30+ years playing with these toys has shown me that murphy is still alive, well, and very active ;)

my personal recommendation is to get and set up at least two more boxes and keep your workstation clean, lean and mean... the other two boxes would be a good customizable firewall (i use smoothwall express on an old 800mhz 256M RAM box with a 6Gig HD) that would handle the static address and the connection to the internet... the other box would be a LAMP server for your server activities...

with a good customizable firewall, you can easily port forwarding to provide the webserver's services to the wild world outside your protected network... you can also easily allow port forwarding of a specific port to your local workstation for your SSH needs... the same with another port for you to SSH into your LAMP server for whatever you may want to do on it from remote, too ;)

---

### Post by gvanto on 2008-12-11
Hey thanks alot guys for all the help.

I am still wrestling with this and learning about networking ... when I disable the DHCP (after manually setting the IP on my PC using KNetworkManager, the internet stops working)...

Just studying up my router's user manual now, to try and figure out how to set up port forwarding wiht the (interal) static IPs...

Was wondering: there seems to be something mentioned about a Virtual Server (where port forwarding is mentioned, page 
99 in the manual ) - its either this or Packet Filtering which I need to enable to be able to access SSH and webserver and SVN access to my PC at home
(which is sharing the network with 2 other laptops)

If anyone has done this sort of setup and has a tip it would be good to hear about.

Gerry

---

### Post by Iowan on 2008-12-11
[help.ubuntu.com]("https://help.ubuntu.com/") is my first stop for information. There's even a section on the [server edition]("http://www.ubuntu.com/products/whatisubuntu/serveredition"). I have bookmarks for VNC, LAMP, and ICS to name a few.  Of course, I like [http://www.howtoforge.com/]("http://www.howtoforge.com/") well enough to include it in my sig.

---

### Post by gvanto on 2008-12-11
Awesome I've got the SSH working !!!!!!!!

thanks everyone for your help, much appreciated!!

---

