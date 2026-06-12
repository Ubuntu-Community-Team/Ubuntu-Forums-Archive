---
title: "Help me: Apache error : (EAI 2) Name or Service Not Known:"
date: 2008-10-19
forum: Server Platforms
---

### Post by nimes on 2008-10-19
hi, i add some virtualhost, /etc/apache2/sites-enabled/default
and apache restart: bump

(EAI 2) Name or Service Not Known: could not resolve hostname [www.example.com](www.example.com) -ignoring
(EAI 2) Name or Service Not Known: could not resolve hostname [www.example1.com](www.example1.com) -ignoring
(EAI 2) Name or Service Not Known: could not resolve hostname [www.example2.com](www.example2.com) -ignoring

i need urgent help..

thanks

---

### Post by floydwilde on 2009-02-21
I saw this same error today.  And googled it, and this forum post came up.  It was the second thing that came up actually, the first thing that came up didn't really have the resolution to this mostly self explanatory error. I mean you know its a dns thing because its talking about resolving a name. 

This page which came up first in google: 

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch20_:_The_Apache_Web_Server](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch20_:_The_Apache_Web_Server)

Says something about putting localhost in the VirtualHost directive.  I thought that was weird.  The problem I encoutered was that someone setup ip based virtual hosts when they really wanted name based, and one of the domains wasn't in dns.  Just looking at this sorted it out: 

[http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html)

And I stuck the domain in /etc/hosts a line something like: 

ip.ad.ddr.ess example.com

The actuall ip address of the server, so this way it doesn't query for the address externally.  Anyhow just thought I'd mention it, maybe it will help someone else searching for this.

---

### Post by nyaswanth on 2010-11-02
Thanks, It helped me :-)

---

