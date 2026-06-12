---
title: "headless file/print server and x11vnc?"
date: 2008-09-18
forum: Server Platforms
---

### Post by donbenjy on 2008-09-18
Hi, I'm a bit of a linux n00b, so I apologise if any of these questions have been answered before/are stupid.  I have searched, and can't find anything that really helps me or gives a definitive answer!

Ok, so I've currently got a ubuntu server setup to share files/act as a time machine backup with my household of macs via netatalk, and I've also got vnc to work across the network, and be advertised by avahi.  However, the idea is to run the ubuntu box as a headless server, and as such, I want to be running the least amount of unnecessary services as possible.

Currently I can only run x11vnc when logged in (I haven't attempted to solve this problem yet, as the other issue is more important).  It appears that I need to be running xserver for x11vnc to actually display anything (duh!)...Is there any way to either make x11vnc return just the CLI/text-based interface so that gdm can be started AFTER the user has connected to the vnc server, or remotely start x11vnc  only when the user requires.  The second option seems less useful, as I won't be able to troubleshoot as easily if there is an error.

Oh yeah, the main (only?) reason for running vnc is to be able to access/control the server in case of emergency, so you can see why I don't need to be running gdm all the time.

This'll be my first headless server, so any help would be appreciated.  I've not actually configured the startup items yet (and don't yet know how, so any pointers to a file would be cool!), so I'm not sure what to include...I think avahi and netatalk run automatically, so the only service I'm currently running manually is x11vnc.  I was thinking (and read somewhere) that it'd be cool to use the internal speaker to beep a sequence once the server is up and running, so that it'll be easy to tell if everything is running properly...where would I stick the script for that?


Sorry about all the questions...I'm learning slowly from just following various howtos, and trying to do anything that the authors didn't do themselves is extremely hard!

Thanks in advance for any advice I can glean from you guys!

Ben

---

### Post by donbenjy on 2008-09-19
anyone?  Am I asking the wrong questions?!  this is the right forum right?

Sorry, I don't normally bump, but I thought I'd have a reply by now!

---

### Post by Pamir on 2008-09-19
For controling the headleass server, you can use WEBMIN from any pc connect to your network and any web-browser!

---

### Post by HermanAB on 2008-09-19
With Linux, VNC is almost always the wrong answer.  VNC is good for Windows XP Home Edition only.  For Windows XP Pro, Remote Desktop is best.

The only time VNC on Linux makes sense, is for remote assistance, where you want the user to connect through his NAT firewall and connect to your helpdesk using reverse VNC.  Google for "one click VNC" or "single click VNC" for that situation.

You should use SSH or Webmin for server administration:
$ ssh root@server "gedit /etc/fstab"

or for Webmin:
$ firefox [http://server:10000](http://server:10000)

Cheers,

Herman

---

