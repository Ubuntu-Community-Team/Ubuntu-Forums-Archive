---
title: "Ads know my zip code?"
date: 2007-08-12
forum: The Cafe
---

### Post by speirint on 2007-08-12
I've noticed for a while that some advertisements (especially for personals sites) know what city I live in and my zip code.  Is there any way to hide or block this information?  Has anyone found anything about it before, I googled it but I still haven't found anything useful.  I this rather discomforting.

---

### Post by jeremy on 2007-08-12
They must get it from your IP, so I guess the only thing you can do is spoof that.

---

### Post by bwtranch on 2007-08-12
They get it from google.

---

### Post by jeremy1138 on 2007-08-12
cookies...  You must have entered your zip code somewhere...  try deleting your cookies and clearing your cache.

---

### Post by bwtranch on 2007-08-12
It's too late google's already got it. If you don't beleive it. Just google it. That's a strange irony isn't it?

---

### Post by tcpip4lyfe on 2007-08-12
They have your ip and use 'whois'

For a proof of concept, open a terminal and type:

```
 whois* youripadress* 
```

I wish other sites (like papajohns.com) would use this instead of just porn and personal sites.

---

### Post by prizrak on 2007-08-12
Like most other's said it goes by IP address. If you want you can go to [www.ip-adress.com](www.ip-adress.com) and it will show you on Google maps where you are located.

---

### Post by Darkhack on 2007-08-12
Thankfully they don't know exactly where you live, but yeah it is pretty scary.  It worried me the first time I glanced at one of those ads and it knew where I was.  Took me a few minutes before I figured out that it was via my IP.  My paranoia can sometimes take over and make me think that they are watching me.  There is a lot of information one can get online just by visiting a webpage including...

**Referrer URL:** What page you came from to get to where you are now.  If you were to click a link on this page to visit another site then your referrer URL would be [http://ubuntuforums.org/showthread.php?523560](http://ubuntuforums.org/showthread.php?523560) and that new site would know where you came from.
**IP Address:** Unique number that identifies you online.
**Location:** Country and usually city or zip code.
**ISP:** Who provides your internet access.
**System:** Your browser, operating system, screen resolution, CPU architecture, language, and probably a few other things I can't think of at the moment.  [IP Chicken]("http://ipchicken.com") knew that I was using Ubuntu Feisty with an en-us keyboard.  So yeah, they can even get specific version information too.

---

### Post by jgrabham on 2007-08-12
> **jeremy said:**
> They must get it from your IP, so I guess the only thing you can do is spoof that.

My IP address says I live 50 miles away from where I actually live : D

---

### Post by xpod on 2007-08-12
> My IP address says I live 50 miles away from where I actually live : D

 7 miles away here:)

---

### Post by darksidedude on 2007-08-12
do web proxys help to protect your information?

I was thinking of [https://vtunnel.com]("https://vtunnel.com")

---

### Post by sunexplodes on 2007-08-12
You think that's weird?

When I enter my IP address as mentioned above (whois myip) in a terminal, it displays this:

person:       Jane Gatfield
address:      Connect Systems
address:      51 Woodside Road
address:      Amersham
address:      HP6 6AA
address:      UK
phone:        +44 01494 434900
e-mail:       [email]janeg@connectsys.co.uk[/email]




Now, this is weird, because I live just outside of Toronto, Ontario.

---

### Post by jgrabham on 2007-08-12
This is the RIPE Whois query server #1.
% The objects are in RPSL format.
%
% Rights restricted by copyright.
% See [http://www.ripe.net/db/copyright.html](http://www.ripe.net/db/copyright.html)

% Note: This output has been filtered.
%       To receive output for a database update, use the "-B" flag.

% Information related to '84.13.0.0 - 84.13.127.255'

inetnum:      84.13.0.0 - 84.13.127.255
netname:      OPAL-DSL
descr:        Opal Telecom DSL Network
country:      GB
admin-c:      PM58-RIPE
admin-c:      GD1052-RIPE
tech-c:       PM58-RIPE
tech-c:       GD1052-RIPE
status:       ASSIGNED PA
mnt-by:       OPAL-MNT
source:       RIPE # Filtered

person:       Phill Magill
address:      Opal Telecommunications Plc
address:      Northbank Industrial Estate
address:      Irlam
address:      Manchester
address:      M44 5BL
address:      United Kingdom
phone:        +44 161 222-2000
fax-no:       +44 161 222-2008
e-mail:       [email]pmagill@opaltelecom.co.uk[/email]
nic-hdl:      PM58-RIPE
mnt-by:       OPAL-MNT
source:       RIPE # Filtered

person:         Gavin Ditchfield
address:        Opal Telecommunications Plc
address:        Northbank Industrial Estate
address:        Irlam
address:        Manchester
address:        M44 5BL
address:        United Kingdom
phone:          +44 161 222-2000
fax-no:         +44 161 222-2008
e-mail:         [email]gditchfield@opaltelecom.co.uk[/email]
nic-hdl:        GD1052-RIPE
mnt-by:         OPAL-MNT
source:         RIPE # Filtered

% Information related to '84.13.0.0/16AS13285'

route:        84.13.0.0/16
descr:        Opal-Net Autonomous System
origin:       AS13285
mnt-by:       OPAL-MNT
source:       RIPE # Filtered


in hatismyipaddress.com it says I live in Hetton in the yorkshire dales

---

### Post by BlackAnthrax on 2007-08-12
For you paranoid people out there......
Take a look into TOR and Privoxy. 
It helps you sleep at night....
([-(

---

### Post by init1 on 2007-08-12
> **BlackAnthrax said:**
> For you paranoid people out there...... Take a look into TOR and Privoxy. It helps you sleep at night.... ([-( Can't the proxy then record your history? It's only secure if you trust the site.

---

