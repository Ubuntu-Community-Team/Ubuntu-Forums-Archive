---
title: "Ubuntu ignores RST packets with unexpected SEQ number."
date: 2016-01-24
forum: Server Platforms
---

### Post by Seiji_Kobayashi on 2016-01-24
Hi Everyone,

Problem is here. Ubuntu is used as Web server, and there is an another network appliance between Ubuntu and Client. The appliance try to disconnect with RST packet, which SEQ number is NOT a series of previous packets.  
Web Server then ignores this RST and still being Established. I suppose this is preventing from RST attacks but not sure. I'm asking how I can configure Ubuntu to receive RST packet.

This was captured on Web server(Ubuntu).
...
 --> Client Hello(70 bytes) 
<-- Server Hello 
---> RST (Seq:411,Ack:1591)   <<<<<  this is ignores on Ubuntu.

In contrast, when seq number is 71 as expected, Ubuntu accepts RST packet.
 
14.04 desktop + Apache2.7. 

Thanks,
seij

---

### Post by matt_symes on 2016-01-24
Thread moved to **Server Platforms**

This is a better forum for your query.

---

### Post by CharlesA on 2016-01-24
A better question to ask is why this other appliance is messing with the sequence numbers in the first place?

I do not believe this is a problem with Ubuntu.

---

### Post by Seiji_Kobayashi on 2016-01-25
Thanks for the response. I understood your point, but even if the appliance is wrong, ubuntu should accept the RST packet with that sequence number because RFC793 says ..

P36, Reset Processing
all reset (RST) segments are validated by checking their SEQ-fields.  A reset is valid if its sequence number is in the window.

The document I read up is too old?

---

### Post by Seiji_Kobayashi on 2016-01-25
[Resolved]

The appliance doesn't follow RFC 5961, Ubuntu does.

---

