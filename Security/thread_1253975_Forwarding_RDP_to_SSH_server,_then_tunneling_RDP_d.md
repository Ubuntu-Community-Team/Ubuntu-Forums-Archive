---
title: "Forwarding RDP to SSH server, then tunneling RDP data to remote machine"
date: 2009-08-30
forum: Security
---

### Post by nerr on 2009-08-30
Hey everyone, I know this job would be better suited for a VPN, but I leave for college tomorrow and that'll have to be a project for another day.  Basically what I want to do is set a Windows machine up as an RDP server, forward that data through the LAN to my Ubuntu server, then use SSH from the Ubuntu server to forward the data to myself on a remote network.

Here's a quick map:

RDP server (Windows) ---LAN--> SSH server (Ubuntu) ---Internet---> RDP client (Windows+Putty)

Is this possible just using SSH alone, or will I have to wait and set up a VPN when I get back home?  I'd like to do this so I'm able to work remotely on machines on my home LAN without having to worry about having the data encrypted.  Please help me out if you have any thoughts!  Thanks!

---

### Post by cybergalvez on 2009-08-30
> **nerr said:**
> Hey everyone, I know this job would be better suited for a VPN, but I leave for college tomorrow and that'll have to be a project for another day.  Basically what I want to do is set a Windows machine up as an RDP server, forward that data through the LAN to my Ubuntu server, then use SSH from the Ubuntu server to forward the data to myself on a remote network.

Here's a quick map:

RDP server (Windows) ---LAN--> SSH server (Ubuntu) ---Internet---> RDP client (Windows+Putty)

Is this possible just using SSH alone, or will I have to wait and set up a VPN when I get back home?  I'd like to do this so I'm able to work remotely on machines on my home LAN without having to worry about having the data encrypted.  Please help me out if you have any thoughts!  Thanks!

don't know if you can easily tunnel the wondows rdp through ubuntu the way you want.  I've never done it that way, but you can with Cygwin install an ssh server on your xp box and then just tunnel to it directly so you get:
Windows (cygwin sshd, RDP server) --- Internet ---> RDP client (Windows+Putty)

---

### Post by nerr on 2009-08-30
Ahh I had forgotten about the Cygwin option.  I would prefer to avoid it as it's more of a pain in the neck than it's really worth, especially on a system that I won't be around to fix.

Looks like I might have to go the VPN route.  Thanks anyway!

---

### Post by HermanAB on 2009-09-01
Howdy,

RDP by default uses port 3389/TCP.  However, you need not tunnel it.  It is pretty secure (RDP was not made by Microsoft!) Simply forward port 3389 on your internet router to the box.

Cheers,

H.

---

### Post by kevdog on 2009-09-01
Just my two cents, but I have cygwin installed on all my windows boxes.  There really isnt any maintainence and I would definitely disagree with you that it is difficult.  Run the setup program, select your packages, and then after the install you might need to set up some environment variables -- that's it.  Upgrading is simply running the setup program again periodically -- that's it.  I definitely recommend it if you have the ability to install programs on your windows machine (unlike sometimes at work where you can not).

---

