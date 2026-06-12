---
title: "Do I need a hardware firewall?"
date: 2012-05-06
forum: Server Platforms
---

### Post by cyncicle on 2012-05-06
This might not be a Linux question per se, but I'm in the process of replacing our old Windows server with a newer Dell PowerEdge R410, probably running 12.04LTS.  This is a small office (<15 stations) environment, and we haven't had a huge amount of problems other than the usual crap the users get themselves into.

The server will be used pretty much exclusively as a fileserver, as our web and email is externally hosted.  I would like to add VPN access at some point.

One of my IT buddies, who knows a lot more about this than I (I'm our company's IT guy by default), told me I should be looking for a hardware firewall/router like SonicWall.  My original plan was to load DD-WRT onto a $100 router and configure firewall, etc. from there.

I guess I don't mind spending the money if it's necessary, but aren't there adequate software solutions available in Linux for a small operation like ours?

---

### Post by HermanAB on 2012-05-06
Well, first of all, make regular backups.

Since it is a very small office, I would just get a $100 Linksys (Linux based) router and be done with it.  The low bandwidth of a cheap router also provides a lot of protection actually.

VPN access is actually risky, since it opens you up to whatever lurks on the LAN where the remote person is connecting from.  So, don't see a VPN as an infallible solution.

Then, you should also think why you are getting a Windows server.  Maybe a Samba server on Linux would be good enough - and certainly more secure.

---

### Post by Lars Noodén on 2012-05-06
+1 to everything that HermanAB said.

For basic use, you'll be able to load DD-WRT onto a $100 router and go from there.  A point of information about firewalls: it's all software underneath.

---

### Post by cyncicle on 2012-05-06
> **HermanAB said:**
> Well, first of all, make regular backups.

Yes, I'm thinking about the various options for doing this once the new server is online.  No backup program at present - bad I know!

> Since it is a very small office, I would just get a $100 Linksys (Linux based) router and be done with it.  The low bandwidth of a cheap router also provides a lot of protection actually.

That was my thinking.  My plan was to just upgrade the router we have so that wireless users (cell phones and a few non-regulars) can get N speeds.

> VPN access is actually risky, since it opens you up to whatever lurks on the LAN where the remote person is connecting from.  So, don't see a VPN as an infallible solution.

Yeah, I'm trying to figure out a way to minimize the risk, while implementing something user-friendly.  I'm definitely open to suggestions!

> Then, you should also think why you are getting a Windows server.  Maybe a Samba server on Linux would be good enough - and certainly more secure.

Sorry, guess my post wasn't too clear - I'm getting rid of the Windows server.

Thanks for the reply!

---

### Post by linuxmatt7 on 2012-05-06
If you will be connected to a network than the answer will always be yes. If not you really do not need one.

---

### Post by techyjt on 2012-05-06
> **linuxmatt7 said:**
> If you will be connected to a network than the answer will always be yes. If not you really do not need one.

I have the same sort of setup in my office.  I found a unused or old pc workstation with say 50 gb HDD, 512K of RAM, need 2 or 3 NICs, but nothing special.  I then installed IPCop 1.4.x.  I can set all the necessary firewall configuration, allow aliases so you can have static IP behind the firewall.  IPCop has the ability to use 3 NICs one for the DSL, one for the Green Network which is the local land and 1 called Blue for Wireless adapter or it can be orange for a DMZ zone.  A setup like that would need 4 NICs but you get the point.  I have been running this firewall for over 8 years without any problems.  It allows to back local settings on the HDD, to a floppy or to create local backups that can be downloaded to any machine with a browser.

Just an opinion and my setup.  And as mentioned before YOU ALWAYS NEED A FIREWALL.  I am not pushing IPCop just giving an example of a simple setup.

---

### Post by sammiev on 2012-05-06
> **HermanAB said:**
> Well, first of all, make regular backups.

Since it is a very small office, I would just get a $100 Linksys (Linux based) router and be done with it.  The low bandwidth of a cheap router also provides a lot of protection actually.

VPN access is actually risky, since it opens you up to whatever lurks on the LAN where the remote person is connecting from.  So, don't see a VPN as an infallible solution.

Then, you should also think why you are getting a Windows server.  Maybe a Samba server on Linux would be good enough - and certainly more secure.

+1 again.

---

### Post by cyncicle on 2012-05-07
Thanks for the advice everyone.  Nice to know I had the right idea all along.

I'll take a look at IPCop.

---

### Post by Jonathan L on 2012-05-08
Hi cyncicle
> 12.04LTS.  ... small office ... fileserver...  add VPN access at some point ... hardware firewall/router lJust another point of view: if you have accessibility from ordinary users, and you are considering VPN for later, you are most at risk from unintended actions from your authorised users.  And as such, I recommend you consider putting the emphasis on the security of your _server_, and less on the security of your _network_.  Of course the two go hand-in-hand and you work on them together.  But I'm just cautioning explicitly against the notion that "insde = safe".

What I'm suggesting is a router with good port and address filtering (like most have).  But do your antivirus and whatever on the server and the users'  machines.  And don't forget -- really, really -- protecting the users  against each other, with good groups and permission settings on your  Samba config and the server in general.

Concretely: for small offices like yours I've mostly used Cisco 800-series, but have good success with M0n0wall and would expect DD-WRT to also be excellent.  I've had less success with budget equipment from Netgear and Linksys.

Hope that's helpful.

Kind regards,
Jonathan.

---

