---
title: "Remote connection on port 6001"
date: 2007-01-05
forum: Server Platforms
---

### Post by Biggus on 2007-01-05
Hi there. I've just had a little look at the list of active connections in firestarter, and I've noticed that I appear to have a connection from a remote box, which has connected to a service which is apparently running on my box on port 6001.

A little bit of investigative work has led me to find that this 'service' is called x windows, and I think (although I'm by no means certain) that this is some sort of GUI?

Any thoughts on the matter would be muchly appreciated.

---

### Post by rth on 2007-01-05
Where is the connection coming from? Are you blocking ports with iptables (through FireStarter)? If it's coming from 127.0.0.1, that's you. If it's coming from 192.168.x.x that could be someone on your network (including you). There's also 172, but that's far less common, plus 10.x.x.x... If it's coming from something other than those (see here for more info: [http://en.wikipedia.org/wiki/Private_network)](http://en.wikipedia.org/wiki/Private_network)), then that means someone is connecting to X (yes, it's for GUI) from the Internet.

---

### Post by kebes on 2007-01-05
Yes port 6001 is X-windows, which is the subsystem that runs your GUI. (Both GNOME and KDE rely on X-windows).

Double check that 'connection' and make sure it is local and not remote. Having a local connection is fine... that just means you're logged into your desktop! However if someone actually has a remote connection to your GUI (that you didn't allow), that's not a good thing.

---

### Post by kebes on 2007-01-05
Do you have a VNC server running? Do you use VNC? Sometimes it can activate port 6001...

---

### Post by Biggus on 2007-01-06
Hi chaps, thanks for the swift replies.

Sadly, it isn't a local connection, but originates from an entirely different box altogether (at 81.x.x.x)

The mention of VNC interested me, because I used to use a little program of that name when I used M$ windows, many moons ago, and that was a remote desktop access client.

I dont recall ever installing a VNC service, but I'm never exactly one hundred percent certain, mainly because I'm still at the stage of typing in pretty much anything that anyone tells me to into the terminal.

I shall go and have a look and see if I have a VNC server running firstly.

---

### Post by kebes on 2007-01-06
Yes VNC is a remote desktiop sharing/access system. If you have a VNC server running but you don't need/want it, then you should certainly turn it off. You can go:
pgrep vnc

To see if any programs with "vnc" in the name are running. Then you can go
kill ####
To kill that program based on the process number reported by pgrep.



Another thing: do you have a hardware firewall? (Router, etc.) If so, make sure that port 6001 is blocked! Also, why not reboot your computer and see if the connection disappears or whether it reappears...?

---

### Post by Biggus on 2007-01-06
Well, a 'pgrep vnc' doesn't return anything, so theres no VNC server running.

I don't have a hardware firewall, and only a passing acquaintance with firestarter.

I've rebooted the machine, and the connection is lost now.

One possibility, I suppose, is that the Skype client I use could have randomly picked that port, as I understand it uses anything from 1024 upwards.

---

### Post by rth on 2007-01-06
Go to grc.com and do the ShieldsUp! test that he has there. Scan the common ports and then put in a custom port of 6001. Ideally everything will be stealth or closed. Whatever is open means that it is something that can be connected to...

---

### Post by Biggus on 2007-01-06
> All attempts to get any information from your computer have FAILED. **(This is very uncommon for a Windows networking-based PC.)**

:D

Oh well, all ports from 1-1056, and 6001, are 'stealthed' so I'm guessing that one of the programs I allow to access the net has used this port. I had a connection on port 50505 a little while ago, which worried me until I realised that it was just Skype, and not the windows based trojan which uses that port.

---

### Post by rth on 2007-01-06
So, you should be fine then. No one can initiate a connection to you if all the ports are blocked and drop incoming packets.

---

