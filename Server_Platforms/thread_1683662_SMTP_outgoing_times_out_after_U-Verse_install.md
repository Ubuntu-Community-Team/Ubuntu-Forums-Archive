---
title: "SMTP outgoing times out after U-Verse install"
date: 2011-02-07
forum: Server Platforms
---

### Post by seanmccaskey on 2011-02-07
I am stumped.  I changed over to U-Verse which means I have a new router, gateway and IPs.  Took some doing but everything is working on my server with one exception.  Outgoing SMTP mail.  I get CONNECTION TIMEOUT when ever something from inside my network tries to hit an SMTP server outside.  Any computer within my network does a Telnet (hostname or IP) 25 and I get a time out.  Port 25 is open on the router.  What am I missing??

---

### Post by wormyblackburny on 2011-02-08
U-verse (much like any residential ISP) blocks outgoing SMTP as well as http/https traffic (probably, I know Cox does). Why you may ask? Money. I'm sure if you call them and ask them to unblock it, they can "upgrade" you to a business class connection for 3X the money. Looking over a few forums it "appears" that they can unblock it for free if you call techsupport, but the posts I found about it are a couple years old, so no promises. Hey, it never hurts to ask :) Call their tech support (chances are you will need a Tier-2, since having worked in an ISP callcenter before, I can guarantee you most Tier1's are idiots and will rather tell you "no" than find out for sure...)

---

### Post by elico on 2011-02-08
or ... use a mail relay server cause most of the dynamic IPs are blocked on the web.
and also it can be a DNS issue.

---

### Post by seanmccaskey on 2011-06-14
Outgoing SMTP port was blocked by Uverse.  Have to ask for it to be change, but that resolved the issue.

---

