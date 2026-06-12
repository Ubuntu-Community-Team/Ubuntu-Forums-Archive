---
title: "Kippo Honeypot | Ubuntu 13.04"
date: 2013-09-13
forum: Security
---

### Post by Jetstr3am on 2013-09-13
[COLOR=#000000]Hi i'm hoping someone familar with Kippo can help.

I've it's been racking my brains why kippo honeypot will not log any sort of login attempts against my decoy ssh server.

My real SSH is serving on a high port, Kippo seems to be accepting new  connections but after a few seconds the connection is lost,(see snip  from my kippo log file below) maybe it's just a ping scan I thought but i'm not  convinced because when I put my real SSH server on standard port 22  overnight, I awoke the next morning to various login attempts in a matter  of a few hours as expected.

I left kippo on for 3 straight days and kippo logged no attempts, nothing but new connections and disconnections! 

Everything is correctly set up which I'm now sure is 100% right, I'll break it down very briefly.

Method 1

Added a new user kippo.
Used authbind to bind tcp/22 to user kippo. 
Kippo.cfg set ti listen on port 22
Added authbind --deep in front of start.sh script.
On router I forwarding port 22 to LAN of 192.168.1.66 (honeypot)
Executed start.sh script under user kippo

Kippo starts fine, but doesn't, log attempts

The alternative Method 2

As above but with kippo.cfg on default port 2222 then I used plain old iptables to forward tcp/22 traffic to tcp/2222

Still nada! Dam it....

Now the strange thing is I can directly connect to my honey pot outside  of my local network and kippo will log everything as it should!!, but I  don't understand why it's not being picked up and attacked in the wild,  being the most common port of attack I find it very odd. 

I have no idea other than my network for being wireless adapter being an issue,  I've still to try this through Ethernet and that's why I'm having cables  installed in my cavity walls!

Have you nice people any questions or answers for me?

Many thanks!
Kevin

2013-09-13 00:09:18+0100 [kippo.core.honeypot.HoneyPotSSHFactory] New connection: 203.XX.40.XXX:36502 (192.168.1.66:2222) [session: 3]
2013-09-13 00:09:27+0100 [HoneyPotTransport,3,203.XX.40.XXX] connection lost
2013-09-13 07:37:37+0100 [kippo.core.honeypot.HoneyPotSSHFactory] New connection: 117.XX.127.XX:47580 (192.168.1.66:2222) [session: 4]
2013-09-13 07:37:45+0100 [HoneyPotTransport,4,172.XX.127.XX] connection lost
2013-09-13 11:38:56+0100 [kippo.core.honeypot.HoneyPotSSHFactory] New connection: 46.XXX.221.XXX:54272 (192.168.1.66:2222) [session: 5]
2013-09-13 11:38:57+0100 [HoneyPotTransport,5,46.XXX.221.XXX] connection lost
2013-09-13 11:47:42+0100 [kippo.core.honeypot.HoneyPotSSHFactory] New connection: 183.XXX.32.XX:46421 (192.168.1.66:2222) [session: 6]
2013-09-13 11:47:52+0100 [HoneyPotTransport,6,183.XXX.32.XX] connection lost[/COLOR]

---

### Post by cariboo on 2013-09-13
Moved to Security Discussion, as you probably get an answer here, quicker than where it was.

---

