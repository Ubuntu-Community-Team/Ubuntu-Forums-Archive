---
title: "Security using WiFi (Newbe question)"
date: 2008-10-26
forum: Security
---

### Post by AdventurousTux on 2008-10-26
Hello,
first of all I must say that I'm new to the world of Linux.
I know already some simple things like apt-get install / sudo commands.

Here's my concern:
I always hear about the dangers of open hotspots.
WiFi points where anyone can enter the web and a preinstalled
network like e.g. hotspots on starbucks, working spacesm etc.
That anyone would be able to intrude my pc.

Therefor I decided to do the step towards Linux, Ubuntu(because it's newbe-friendly) :guitar:

What do I need to lock-up so that I can use these open hotspots?
The security issue concerning the clock is already solved since
my ubuntu has already disabled the i-net clock_setup thing.

//Edit:
I'm now a bit confused atfer reading the sticky about sudo.
Do I do sth wring by using the sudo command to install a programm? I thought I am only temporal logged with root rights?

Thanks folks for your time!

---

### Post by Dave_Connor on 2008-10-26
If you want secure your own router you can set up encryption with WPA-PSK and passphrase instead of default encryption. You can also set up what is called mirroring so that your wireless single only goes to your house. Securing wireless on your system. If you have a laptop you can install openssh on both machines and then forward a port for ssh on your router and then set up a domain so you can ssh tunnel between your laptop and desktop. So everything that is reaching your laptop is encrypted. Or you can use Tor but it is very slow with having to encrypt your traffic and bounce around several systems to the web site.

---

### Post by AdventurousTux on 2008-10-26
OK,
so for the puplic hotspots that are placed in cafés and 
train stations I can only encrypt my laptop and use tor?
-
My home network is setup with WPA2 PSK (which should be secure enough for home use according to the German Institution for secure IT-technologies short bsi.de)

---

### Post by nubdora on 2008-10-26
> **AdventurousTux said:**
> OK,
so for the puplic hotspots that are placed in cafés and 
train stations I can only encrypt my laptop and use tor?


No. You can also ssh into your home system, as stated above, so the flow of data is encrypted over the public networks.

---

### Post by kevdog on 2008-10-27
I basically agree with the advice above.  What you want to do is to create an encrypted tunnel between the unsecure cafe and your home router or network.  Pass all traffic in between this tunnel.  (I would not advise using tor which creates an encrypted tunnel between the cafe and "other" servers located out on the internet -- its very slow).  In order to establish this tunnel - you could use one of two methods:

1. SSH - The poor man's (but quick) VPN
2. VPN - Specifically OpenVPN -- however other client/server software would be applicable

1. Requires you have an SSH server that is remotely accessible to your own private network.  If you have this setup, then a good set of instructions of how to for example tunnel all firefox traffic(remember when the project was actually called firebird??) is here: [http://ubuntuforums.org/showthread.php?t=723025&highlight=wormser](http://ubuntuforums.org/showthread.php?t=723025&highlight=wormser)

2. OpenVPN installation is more involved, however all traffic can specifically be routed through the tunnel.  I'm in the process of writing a tutorial for this process, and although there are definitely bits and pieces contained in the forums of how to do this (along with a lot of info out on the net), I can't point you to one specific forum post that would be considered "all-encompassing".  This is much more difficult to set up for novices.

---

### Post by ciscosurfer on 2008-10-27
> **kevdog said:**
> I basically agree with the advice above.  What you want to do is to create an encrypted tunnel between the unsecure cafe and your home router or network.  Pass all traffic in between this tunnel.  (I would not advise using tor which creates an encrypted tunnel between the cafe and "other" servers located out on the internet -- its very slow).  In order to establish this tunnel - you could use one of two methods:

1. SSH - The poor man's (but quick) VPN
2. VPN - Specifically OpenVPN -- however other client/server software would be applicable

1. Requires you have an SSH server that is remotely accessible to your own private network.  If you have this setup, then a good set of instructions of how to for example tunnel all firefox (remember when the project was actually called firebird??) is here: [http://ubuntuforums.org/showthread.php?t=723025&highlight=wormser](http://ubuntuforums.org/showthread.php?t=723025&highlight=wormser)

2. OpenVPN installation is more involved, however all traffic can specifically be routed through the tunnel.  I'm in the process of writing a tutorial for this process, and although there are definitely bits and pieces contained in the forums of how to do this (along with a lot of info out on the net), I can't point you to one specific forum post that would be considered "all-encompassing".  This is much more difficult to set up for novices.Well stated, kevdog.  Looking forward to reading your OpenVPN tutorial.

---

