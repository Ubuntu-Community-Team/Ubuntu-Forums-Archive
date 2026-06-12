---
title: "Apache/SSL Issue"
date: 2007-11-02
forum: Server Platforms
---

### Post by Diggit2001 on 2007-11-02
Hello everyone.  First, I would like to say that this site has helped me immensely with my introduction to Linux.  Everyone on this forum seems to be very helpful and I don’t see a lot of the “attitude” that is normally seen in an internet forum.  I have been a lurker for a month or two now and I finally have a problem that I have been unable to find a solution to here.

I had been running Fiesty desktop version with XAMPP to run an open source help desk application I found.  I decided that I wanted to give Gutsy server a try and move my application over to it so I loaded up a fresh server and instead of going with XAMPP, I thought I would individually install each component so I might learn a little more about them.  I’ve gotten pretty much everything working so far except for Apache.  It seems that I have a bit of an unexplainable SSL problem.  I installed Webmin to manage the server and it connects with SSL no problem.  I unpacked my help desk application into the /var/www folder and I can successfully hit [http://www.helpdesk.mydomainame.com](http://www.helpdesk.mydomainame.com).  There is a setting in the help desk application that tells it to use SSL only and when I turn it on, I receive a strange error in Firefox:  > Firefox can’t connect securely to helpdesk.mydomainame.com because the site uses an older, insecure version of the SSL protocol.

I have tweaked several different things in the Apache Webmin config but nothing has helped to resolve this so far.  I find it odd that Webmin connects fine with SSL but my help desk site does not.  I take this to mean that it is something site specific and not server specific but I am not sure how to fix it.  Can anyone point me in the direction toward a solution?  I appreciate any assistance that can be lent.

Thanks
-Chris

---

### Post by dantrevino on 2007-11-02
Webmin uses its own server, not apache, by default, so unless you've manually configured webmin to use apache, when you access webmin, you're accessing the miniserv.pl process.

I assume you've set up your certs for apache, so what do your log files (/var/log/apache2/) say when you try to connect via https?


dan

---

### Post by Diggit2001 on 2007-11-05
> Webmin uses its own server, not apache, by default, so unless you've manually configured webmin to use apache, when you access webmin, you're accessing the miniserv.pl process

Ah, I didn't know that.  That makes sense.

Yeah, I have set up a Cert for this site.  When I attempt to access the site, I see this in my /var/log/apache2/access.log file:

> 192.168.0.30 - - [05/Nov/2007:08:30:51 -0500] "\x16\x03\x01" 200 5899 "-" "-"
192.168.0.30 - - [05/Nov/2007:08:30:51 -0500] "\x80=\x01\x03" 200 5899 "-" "-"

Not sure what exactly this means....


I appreciate the help.
-Chris

---

### Post by Diggit2001 on 2007-11-05
Never mind.  I generated a new cert from an online trusted CA and all seems to be well now.  I had been using one I generated locally temporarily and I guess I musta done something wrong somewhere.

Good to go now.  Thanks.

---

