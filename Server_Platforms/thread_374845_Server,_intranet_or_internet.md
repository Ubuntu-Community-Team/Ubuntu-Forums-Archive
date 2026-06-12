---
title: "Server, intranet or internet?"
date: 2007-03-03
forum: Server Platforms
---

### Post by Mytholody on 2007-03-03
Hi. I had a quick (hopefully) question. I set up a lamp server on my network. It's running on an internal ip address, 192.XXX.X.XXX and I was wondering if it may be accessible from the outside somehow. Its connected through a linksys n router (can't remember the model # atm, sorry), and I havn't port forwarded anything, but then again, if its running on a standard port like 80, could it be broadcasting/accessed from the internet? There is no worry at all about security, but I know my ISP does not allow servers and I would not like to violate the user agreement. So any help with this matter would be greatly appreciated! Sorry for the Newby question, and thank you!

---

### Post by Gerard Barberi on 2007-03-03
I actually do the same thing.  My ISP does not like servers, but I don't really use it for anything but development purposes.

As to your question, From my knowledge it should only be accessible if the router is somehow between the server and the modem and it is configured to foward requests on port 80 to that server.

---

### Post by Mr. C. on 2007-03-03
Unless you intentionally configure the linksys appliance to forward external traffic to internal servers, they are not accessible.

ISPs are concerned about bandwidth usage, not names like servers, etc.  As long as you are not using excessive bandwidth, there will be no problems.

MrC

---

### Post by Mytholody on 2007-03-03
Yes, I am aware of the bandwidth issues, and thats another reason I wanted to verify this. I have a very strict bandwidth policy (ISP is licensing wimax technology and/or equipment and I'd hate to lose that, broadband is nice to have in a rural area). I havn't port forwarded my server, so I should be safe then. Thank you both for your help and reassurance!

---

### Post by Mr. C. on 2007-03-03
You should be fine.  Just be sure your server isn't downloading updates or using bandwidth you aren't expecting.

---

