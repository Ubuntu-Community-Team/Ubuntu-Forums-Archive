---
title: "Need Help Installing VNCSERVER on Ubuntu 9.04, for 2users"
date: 2009-11-04
forum: Server Platforms
---

### Post by husskii on 2009-11-04
Hi Im learning how to setup ubuntu servers, and have installed a test server at home, using Ubuntu 9.04.
I have 2users on the server, 1 being my self and the 2nd user account is for a friend, so he can login remotley.

I followed a tutorial which didn't help much, as some of the commands wouldnt work, & at the moment I can connect thru vnc on my notebook, to the ubuntu server, but all I get is a gey checkered window, with terminal.

Can I pls get help to setup vns so it works properly & shows the desktop, and I also need help to setup vnc for the 2nd user account, which doesnt have admin credentials. I dnt know how to connect to his account as root, so I can setup vnc on his account.

Thanks in advance
Husskii:)

---

### Post by windependence on 2009-11-04
Use FreeNX or Team Viewer. VNC is not very secure at all.

-Tim

---

### Post by husskii on 2009-11-04
Hi windependence thanks mate I will use that as an option for my server, but my friends are always asking for vnc viewer to connect to there servers, so I still need to find a good tutorial that helps with it...

I followed a tutorial earlier but I got as far as 
#sudo apt-get install ssh


#sudo apt-get install vnc4server

After it is installed you should be logged as normal user and not root.
#vncserver :1 -geometry 1024x768 -depth 16

the I killed the process using
#vncserver -kill :1 

**then I tried the following but command wouldn't work.

The configuration is kept in the file /home/userxx/.vnc/xstartup I edited this file so that I can start the server with gnome. My file looks exactly like below.

#!/bin/sh

**I also didnt know were to enter the following...

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

gnome-session &

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
# xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
twm &


(by the way your also helping me with my webserver, Its just on hold at the moment while I work this out. Im trying to learn how to set HDD quota for 2user accounts & vnc access, for a friends server) :)

---

### Post by windependence on 2009-11-05
You're welcome mate. 

I don't ever remember messing with the configuration file when I set up VNC server. Let me see what I can find in my notes here.

You really should check out NoMachine. Extra fast and free, and there are binaries for many different platforms.

Here is the link:    [http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)

There's no Windows server, but there IS a free Windows client. Perfect for what you are doing. Give it a try mate, it's so much faster than VNC and tunnels over ssh so security is so much better.

-Tim

---

### Post by husskii on 2009-11-05
sure think Ill give it a try now.. :)
Oh that's right right. The problem with nx is that 2users can't connect to the same user account at once. So that's why they want NX. that way 2users can login to the same window & one user can show them how to find there way around the screen...

they pretty much have my mind set on vnc, as do my mates. so need to figure out how to install it properly.

---

### Post by husskii on 2009-11-05
I decided to go ahead with freenx, and afetr installing nxclient nxnode and nxserver, I tried to connect thru nx on my notebppk and I got the following error,

NX> 203 NXSSH running with pid: 988
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
ssh: connect to host 58.106.220.65 port 22: Connection refused

---

### Post by husskii on 2009-11-07
hi guys I managed to get vnc to work, but im having trouble connection from a remote location.

I can connect on the local network & everything looks and work as it should, but wen I try from a remote location, I get a [unable to connect to host: connection timeout (10060)] error

and wen I try from inside my network, but using the remote IP, I get [unable to connect to host: connection refused (10061)] error

I also tried opening port 59000 & 5900 in my router, but that didnt work..

just incase Im using the wrong port, can anyone tell me how to find out wat port vnc is on pls...

Also if anyone know what the problem could be, that would help alot.

---

### Post by windependence on 2009-11-08
You need to FORWARD port 5900 (not 59000) back to the box you want to be able to log on to. Look in your router for port forwarding.

You cannot reach an external IP you assign to your interface on this box from within your local LAN because for that you would need a router that supports NAT reflection. Most all home routers do not support reflection.

-Tim

---

### Post by husskii on 2009-11-08
Hi windependence, if u mean "NAT (Network Address Translation)" I have that enabled in my router, Ive also opened the port 5900 and still have it open to the server. I had it set to udp/tcp & then tried tcp on its own, but still didnt work. 
wen I had set remote desktop the normal way thru system>> prefrences>> remote desktop, I was able to connect  via vnc, but i also cant connect this time.. I reset my router just b4 the instal, so mmaybe another port needs to be open, or a package needs to be installed, Im not too sure. It also says in remotedesktop that im only reachable of the local network, this time, where as before It said I was reachable over both local and remote.

---

### Post by peppino on 2009-11-08
> **husskii said:**
> Hi windependence, if u mean "NAT (Network Address Translation)" I have that enabled in my router, Ive also opened the port 5900 and still have it open to the server. I had it set to udp/tcp & then tried tcp on its own, but still didnt work. 
wen I had set remote desktop the normal way thru system>> prefrences>> remote desktop, I was able to connect  via vnc, but i also cant connect this time.. I reset my router just b4 the instal, so mmaybe another port needs to be open, or a package needs to be installed, Im not too sure. It also says in remotedesktop that im only reachable of the local network, this time, where as before It said I was reachable over both local and remote.

look at [https://help.ubuntu.com/community/FreeNX):P](https://help.ubuntu.com/community/FreeNX):P)

---

### Post by husskii on 2009-11-08
its all good guys I finally got vnc working for mulitple users.. now I start my next project, which is learning how to create hdd quotas for each user, so they cant exceed there hdd limits..


any advice is appreciated.. 
& a BIG thanks to those who help me, and showed patients, with my slow learning... I think after hdd quotas I should have linux under control :)

well the basics anyways ;)

Much appreciated :D

---

