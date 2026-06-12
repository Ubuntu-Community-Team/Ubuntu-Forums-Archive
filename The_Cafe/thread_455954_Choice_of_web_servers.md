---
title: "Choice of web servers"
date: 2007-05-27
forum: The Cafe
---

### Post by samjh on 2007-05-27
Feeling a little bored tonight, I did some random searches of websites to see just what kind of OS and Web Server they run.  Your can look these up at [http://www.netcraft.com](http://www.netcraft.com)

[www.microsoft.com](www.microsoft.com)
Windows Server 2003	Microsoft-IIS/6.0  (predictably :) )

[www.yahoo.com](www.yahoo.com)
FreeBSD	unknown  (secret web server?! :p )

[www.australia.gov.au](www.australia.gov.au) (Australian federal gov)
Linux	Apache (our government has actually made a good choice!)

[www.telstra.com](www.telstra.com) (Australia's national telecom carrier)
Windows 2000	Microsoft-IIS/5.0

[www.ubuntuforums.org](www.ubuntuforums.org) (need I explain?)
Linux	Apache/2.0.55 Ubuntu PHP/5.1.2

[www.ubuntu.com](www.ubuntu.com)
Linux	Apache/2.2.3 Ubuntu (predictably!)

[www.novell.com](www.novell.com)
NetWare	Apache (interesting...)

[www.sun.com](www.sun.com)
Solaris 9/10	Sun-Java-System-Web-Server/6.1 (interesting but predictable)

[www.ibm.com](www.ibm.com)
unknown	IBM_HTTP_Server (perhaps AIX as the OS?)

[www.google.com](www.google.com)
Linux	GWS/2.1 (most definitely an in-house web server)

[www.news.com.au](www.news.com.au) (Rupert Murdoch's Australian newspaper portal)
Linux	AkamaiGHost (interesting choice of web server)

[www.police.qld.gov.au](www.police.qld.gov.au) (my state's police service)
Windows Server 2003	unknown (hmmm... secret police-brewed web server :p )

[www.auscert.org.au](www.auscert.org.au) (Australia's own CERT)
FreeBSD	Apache (good choice! :) )

[www.uq.edu.au](www.uq.edu.au) (my alma mater)
unknown	Apache/2.2.3 Unix mod_ssl/2.2.3 OpenSSL/0.9.8a DAV/2 PHP/5.1.6 (that's a very complicated set up!)

[www.youtube.com](www.youtube.com)
unknown	Apache (I thought they might use the same as Google's, but apparently not)

[www.gnu.org](www.gnu.org) (we know who these guys are! :) )
Linux	Apache/1.3.34 Ubuntu mod_python/2.7.10 Python/2.3.5 (they use Ubuntu! :D )

[www.nasa.gov](www.nasa.gov) (yes folks, let's see what the rocket scientists use)
Linux	Apache/2.0.45 Unix mod_perl/1.99_09-dev Perl/v5.6.1 covalent_auth/2.3 DAV/2 CovalentSSL/2.3.3 RSA/SSLC mod_jk/1.2.2-beta-1 (good glorious stars, they like to make things complicated!)

[www.boeing.com](www.boeing.com) (Boeing, the world's #1 commercial aircraft maker)
Solaris 9/10	Sun-ONE-Web-Server/6.1 (interesting but good choice)

[www.raytheon.com](www.raytheon.com) (another prominent aerospace company, most famous for its missile systems)
Solaris 9/10	Raytheon Company (hmmm... a home-brewed web server)

[www.defence.gov.au](www.defence.gov.au) (Australia's Dept of Defence)
Solaris 9/10	Microsoft-IIS/4.0 (what an odd arrangement, is there something wrong?)

:D

---

### Post by MrHorus on 2007-05-27
> **samjh said:**
> 
[www.news.com.au](www.news.com.au) (Rupert Murdoch's Australian newspaper portal)
Linux	AkamaiGHost (interesting choice of web server)

Not all that interesting - if I remember correctly Akamai are a content delivery network and they deliver content to the client by selecting the nearest media server based on geolocating their IP address, so it would make sense for NewsCorp to be a client.

> 
[www.defence.gov.au](www.defence.gov.au) (Australia's Dept of Defence)
Solaris 9/10	Microsoft-IIS/4.0 (what an odd arrangement, is there something wrong?)


That is quite strange, yeah.

I would hope for your sake that your Defence Department really isn't running IIS4 ;)

---

### Post by samjh on 2007-05-27
> **MrHorus said:**
> That is quite strange, yeah.

I would hope for your sake that your Defence Department really isn't running IIS4 ;)

Well, it is only their web server, after all.  I don't think it is connected to anything really sensitive... at least I hope not. :)

But really, Windows servers have gone from strength to strength.  They are not really any more or less vulnerable than *nix-based servers.  At least no object test has conclusively decided which one is more secure.

---

### Post by MrHorus on 2007-05-27
> **samjh said:**
> 
But really, Windows servers have gone from strength to strength.  They are not really any more or less vulnerable than *nix-based servers.  At least no object test has conclusively decided which one is more secure.

There are several issues there that i'm not going to go into, but the probe clearly raised the question of the Defence Department running IIS4 - this predates any advances or improvements inbetween IIS4 being common and IIS6 being standard.

---

### Post by samjh on 2007-05-27
That's true.

I wonder if they're faking it?  Solaris and IIS just doesn't add up in my mind.

---

