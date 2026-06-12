---
title: "Software Firewall equiv of Zonealarm"
date: 2006-11-06
forum: Server Platforms
---

### Post by jamesr on 2006-11-06
Hi,

I have setup a Ubuntu 6.10 system on my home network mainly for internet browsing and personal emails. It was before the 'upgrade", a W98SE system with a software firewall ZoneAlarm, spyware/adware programme called Adwaer from Lavasoft and a virus programme:- Norton.

The system is on a home intranet with a router with embedded firewall, ie hardware, as the gateway, but I have always used an additional software firewall. A belt and braces approach I suppose. 

Could you please make any suggestions if :-

1) these are necessary ? 
I believe yes but I could be misinformed.

2) suggestions of replacement programmes.
After googling for the firewall, the responses seemed to windows based or if Linux based a dedicated firewall pc eg coyote linux or using iptables.

---

### Post by happy-and-lost on 2006-11-06
Linux uses iptables to firewall by default. If you're after a GUI *sudo apt-get install firestarter*

---

### Post by jamesr on 2006-11-06
Hi Happy-and-lost

Thanks for the suggestion  > Linux uses iptables to firewall by default. If you're after a GUI sudo apt-get install firestarter but I had already realised that iptables was a default but the way that I understood that it worked and I could be wrong, iptables is more of a host-based firewall ie one selects the address that is blocked. What I was really was looking for, was an application based firewall like zonealarm to complement the one currently in the router. Another use, is that one see what programmes are trying to call out and one can block that programme. The converse can apply and that is the normal way that I use them and that is that only certain programmes are allowed to call out. Some to the local intranet and a selected few to the internet. Perhaps Ubuntu does not need that type of protection because there are not many trojans, worms and spyware for Linux but I sure that in the future as Ubuntu becomes more popular that more malware will be written for Ubuntu systems. I cannot believe that spyware that tracks your surfing habits will not be available soon.

As a general comment, I believe the terms host-based firewall and application based firewall are the correct names for the different forms. But I know on a windows system that is connected to the internet I would have available both forms of firewall available along with a anti-virus programme whose signatures are updated regularly and a couple of spyware/spybot programmes.

---

### Post by Pri0n on 2006-11-06
Application based firewall is the correct term for "ZoneAlarm type" firewall behavior.

Take a look at TuxGuardian ( [http://tuxguardian.sourceforge.net/]("http://tuxguardian.sourceforge.net/") ) Program Guard ( [http://pgrd.sourceforge.net/]("http://pgrd.sourceforge.net/") ) and Systrace ( [http://www.citi.umich.edu/u/provos/systrace/]("http://www.citi.umich.edu/u/provos/systrace/") )

I don't believe there are any Ubuntu packages for either application yet, so you'll need to compile from source.

---

### Post by jamesr on 2006-11-07
Thanks for the suggestions. Have you tried any of these?

Any suggestions for the spyware finder and anti-virus?

---

### Post by Pri0n on 2006-11-08
I haven't had the chance to try any of those application based firewalls, so I can't comment on them.

In terms of viruses, I believe that most anti-virus software for Linux is more geared towards scanning against Windows viruses, not Linux viruses.  For example, if your Linux box is running a mail server, and is being used by Windows clients (for their e-mail), you may want to scan all incoming and outgoing e-mails for viruses.  Likewise, if you are hosting a File Server or a public FTP server on a Linux box, you may also want to scan the files uploaded to see if any of them contain viruses (Windows viruses).  I believe there ARE some Linux viruses out there, but they are more conceptual than anything else.  Note that I am making a distinction here between viruses and worms. (A virus you need to execute in order for it to infect your system, a worm spreads around automatically through the network by exploiting some security hole).  The first Internet worm (Morris worm) spread around Unix servers using sendmail.  To protect yourself against worms, use a firewall, keep up to date with security patches, and only run the services that you need. 

In terms of spyware, so far I don't believe there is any Linux-specific spyware.  Most Linux applications are open-source, so it would be easy for other people to detect an application that has spyware behavior.  If you stick with open-sourced applications downloaded from the Ubuntu repositories, you should be safe.  Mind you, if the software that you're downloading is closed source, from some obscure web site, and very few people have actually tested it out (i.e. you're the 10th downloader), then who knows what it may harbor.  Either way, you should always check the md5sum (or sha1sum) of a file that you've downloaded, to confirm its integrity (i.e. whether it was corrupted, or whether the version that you have was deliberately modified by somebody else).  Often I try to confirm the md5sum on a different site than the one that I downloaded the application from, just in case both the file and the md5sum were changed.

---

