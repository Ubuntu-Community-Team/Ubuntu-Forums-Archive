---
title: "Server wireless Setup"
date: 2009-08-31
forum: Server Platforms
---

### Post by lestat6205 on 2009-08-31
I am in the process of turing 5 old computers into 2 desktop machines and 1 wireless server. I have the Desktops running and they are running well; the server and the desktops are in a seperate room from the router and I want to set the server with a wireless connection and share the connection with the 2 desktops and 1 windows xp desktop the server will also be a place to hold files to share between the computers.
 
I have been searching the forum for the wireless network setup stuff and I cant get it to work.
 
The wireless usb is a linksys wireless-g network adapter It works under the desktop edition. when I type iwconfig the file says its under wlan0
 
IEEE 802.11BG ESSID: "MAWAP1
Mode: Managed Frequency: 2.412 GHZ Acces Point: Not-Associated
Tx-Power=20 Dbm
Retry min limit:7 RTS thr:off Fragment thr=2352 B
Power Management:off
Link Quality:0 signal Level:0 Noise:0
Rx invalad nwid:0 Rx invalad crypt:0 Rx invalad frag:0
Tx excessive retries:0 Invalad misc:0 Missed beacon:0
 
 
 
I tried to setup the sudo gedit /etc/network/interfaces
and it tells me that i dont have gedit I try to sud apt-get it and it cant find it
 
Thanks for everyone that replys and I like the Ubuntu Desktop edition it has brought life back to my old computers and my son like the edubuntu version he plays it all the time.

---

### Post by hessiess on 2009-08-31
Best option: run a cat5 cable between the rooms, wireless networks are notoriously unreliable and have a tendency to drop out occasionally, which is not something you want when you are running a server.

Something else you will want to do is ditch X11, it is a resource hog and a complete waste of memory on a server.

---

### Post by lestat6205 on 2009-08-31
what do you mean x11 i didnt mean to install that so how can i get rid of it if its bad?

---

### Post by hessiess on 2009-08-31
> **lestat6205 said:**
> what do you mean x11 i didnt mean to install that so how can i get rid of it if its bad?

X11 is the graphical display server on Linux, and it comes as-default on the desktop version, Just running a command line is much more resource efficient on a server, as they are headless(no monitor) 99% of the time.

---

### Post by lestat6205 on 2009-09-01
i have just the server version for my server and i have two seperate desktops. So the server one will just have the server from the 9.04 release with the command line. I am starting to get used to using command line and I decided to move my server closer to the router so I can just directly connect to it. I agree that it will be easier.

---

