---
title: "computer can't get on server after connection lose"
date: 2012-05-01
forum: Server Platforms
---

### Post by JAZ1976 on 2012-05-01
Hey Everyone,

I was wondering if there was a way to clear a connection from a specific computer or IP address. A remote location lost its connection to our main Linux server and now some of those computers can not log back into the server. Users who were using those computers can log in from other computers that were not effected. 

Thanks,
JAZ

---

### Post by SeijiSensei on 2012-05-02
This sounds like a networking problem to me.  Can machines in the remote location ping the server but somehow not connect?  What are they connecting to?  

The situation you describe is one I've never encountered, and I've used a lot of different clients and servers over my career.  TCP/IP was designed to be fault-tolerant so that connection failures, once repaired, should work once again.

---

### Post by JAZ1976 on 2012-05-02
The users are connecting from a Windows 7 computer, using a Telnet client to a BBX shell on the Linux server. When the computers come back online from loosing their connections they are able to get to every other network resource; printers, fileservers, databases, but they can't connect to the Linux server through their Telnet client. I'm not sure if they are able to ping the server after their connection comes back. I would have to wait and see the next time this happens. They are able to get on after some time, so I assume their old connection may timeout at some point. My boss was wondering if we could get them back on quicker.

---

### Post by SeijiSensei on 2012-05-02
Are they connecting to the server's IP address or using DNS?  If the latter, see if using the IP address is more robust.

---

