---
title: "Listening Telnet Daemon"
date: 2005-04-13
forum: Server Platforms
---

### Post by mbeach on 2005-04-13
Hi,
I'm loving Ubuntu so far, so much so I'd like to do some stuff from home.

I currently access my work machines by connecting to a server at work which has a public IP address (connA).  From there I VNC to my personal machine at work (connB), then ensure my home machine is running a Listening VNC Viewer, and connect to home from my work machine (WinXP) (connC).  I then terminate connA and connB and work happily on my work pc from home.  I have been telneting to my new work Ubuntu test box (from my work WinXP machine).  Whew, I know craziness, but necessary (I don't control the firewall).

VNC is ok but I would like to know if there exists a 'listening telnet daemon' that I could run on a Windows XP box (at home), that I could establish a connection to from work.  I would then end up with a single telnet connection to home (initiated from work but the client would be the home XP machine).

NAT to the Ubuntu server is out of the question at this time.  

Hope this makes some sense.  Apologies if this has been answered already -  I did some searching without success.  I posted here because this seems like the crowd that would know the answer.  

Using Ubuntu 5.04 with Telnet-ssl running.

mb

---

### Post by dataw0lf on 2005-04-13
[http://kpym.sourceforge.net/en/Overview.htm](http://kpym.sourceforge.net/en/Overview.htm)

Is this what you're looking for ?

---

### Post by mbeach on 2005-04-13
I'll look into it further, but I don't think so.  I have the Telnet server (telnet-ssl) is running on Ubuntu at work, and I need to "Add a client" (my home machine) from the server. 

VNC does this by allowing you to run a listening viewer (client) at home.  The server then 'adds a client' where you would put in the IP address of the client (home machine).  Its your typical client server model, except that the connection is initiated from the server (so not typical at all).  In my particular case it allows me to connect to my home machine through my work's firewall.

No worries, I'll keep looking (I was just looking for an alternative to VNC).  I'm trying to prove to the folks that make the decisions that buying into the whole Novell/SuSE concept is not necessary.  I'm immersed in a crowd that feels that if they didn't pay for it - it must be junk.  I'm trying to convince them otherwise with a litte open source demo using Ubuntu, PHP, MySQL to show off a couple of PHP applications like dotProject and Mambo.

thanks datawOlf.

---

