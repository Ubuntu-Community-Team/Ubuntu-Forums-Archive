---
title: "packet replay tools"
date: 2008-01-20
forum: Server Platforms
---

### Post by shahin on 2008-01-20
Greetings-
     I may need to replay some captured packets for testing purpose, and tried to download Tomahawk, but it is only available for RedHat.  Just wondering what other tools I can use please that is available for Ubuntu please?

---

### Post by compiledkernel on 2008-01-20
Depends on what format the captured packets are in. 

I guess if its a libpcap dump you could use wireshark to exmaine the packet stream.

---

### Post by shahin on 2008-01-20
I want to examing the traffic, but it is more important for me to replay a capture that someone else might send me.  I may not be able to arrange for the platform that generates the trraffic quickly.  So I want to be able to replay a capture that someone else generated.  Any help is greatly appreciated.

---

### Post by ohioboy757 on 2008-01-21
tcpreplay

---

