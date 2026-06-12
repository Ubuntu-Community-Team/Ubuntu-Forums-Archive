---
title: "Outgoing SMTP"
date: 2009-11-03
forum: Server Platforms
---

### Post by shoaibi on 2009-11-03
Whenever i configure a VPS a common task is to set it up so that i can email its crons, logwatch and other output to an email address instead of saving it in local box. Previously i achieved this by combining postfix+sasl and using gmail account, however that seems not an option as gmail blocks such accounts. 
I read some documentation and i would still need a smtp server to act as my relay_host to send out email. I googled but couldn't find any free SMTP server, and those which were found doesn't work anymore. What do i need to do? Please provide links if possible.

PS:
This is a null client, just needs outgoing SMTP, nothing else, which can also be done by ssmtp but again what should be relayhost? My ISP/VPS Provider doesn't give me one.

---

### Post by rfreedman on 2009-11-03
ssmtp
see [http://greybeardedgeek.net/?p=17](http://greybeardedgeek.net/?p=17)

---

### Post by shoaibi on 2009-11-04
thats being blocked by gmail, i have tried and my account gets locked everytime...

---

