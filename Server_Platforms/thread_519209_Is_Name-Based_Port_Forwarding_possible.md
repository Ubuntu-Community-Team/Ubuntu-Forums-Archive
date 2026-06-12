---
title: "Is Name-Based Port Forwarding possible?"
date: 2007-08-06
forum: Server Platforms
---

### Post by chris.zeman on 2007-08-06
Is it possible to setup name-based port forwarding?

For example...
Internet-Connected Ubuntu Server: domain.com (1 I.P. Address)
LAN Server 1: server1.domain.com
LAN Server 2: server2.domain.com

Could I possibly configure Ubuntu to act appropriately in the following situations:
External client opens [http://server1.domain.com](http://server1.domain.com) in their web browser, and the Ubuntu Server forwards port 80 to Server 1 on the LAN. I'd want the same to occur for Server 2 of course.

I'm open to suggestions if there's a better way to accomplish this. :)

Oh, there is one caveat...
I cannot use multiple ports to do this. These servers are on an internet connection other than the one provided by our company. Other employees need to access these servers from the company's internet connection and can only use port 80. Our I.T. department really has their internet locked down. There is NO way around it.

Thank you,
Chris

---

### Post by Mr. C. on 2007-08-06
You've explained a solution, but haven't indicated what problem you are trying to solve.

MrC

---

### Post by chris.zeman on 2007-08-06
> You've explained a solution, but haven't indicated what problem you are trying to solve.

I guess I'm confused by your statement. :)

I know what I'd like to do, but I'm asking if what I'm trying to accomplish is possible and where I could find information on how to do it. I haven't really been able to find anything other than a few others who would like to do the same thing. That's the problem I'm trying to solve. The only answers I've found is to dedicate a port for each sever (Port 80->Server 1, Port 81->Server 2), and that won't work for my situation.

Thank you,
Chris

---

### Post by Mr. C. on 2007-08-06
I was asking what were you trying to accomplish overall and in general (i.e. your goal vs. your proposal or chosen task to implement that goal).  Often users will ask questions about *how* to do something, when they really mean to ask about the best way to accomplish some other (unstated goal).

This sounds like you want virtual hosts, a proxy, or redirection.  Regardless, this happens at the application layer.

IP and port forwarding is done at a lower level; name based forwarding would require looking into the message data and interpreting the byte stream that represents some host name inside A URI.

MrC

---

### Post by MJN on 2007-08-07
Have a read of the mod_proxy module in Apache - [http://httpd.apache.org/docs/2.0/mod/mod_proxy.html](http://httpd.apache.org/docs/2.0/mod/mod_proxy.html)
 
You can set your Ubuntu server up as a proxy so that external clients can connect to the Ubuntu server for both domains and it would forward the requests on to the appropriate LAN server.
 
A recent thread ([http://ubuntuforums.org/showthread.php?t=514810](http://ubuntuforums.org/showthread.php?t=514810)) covered a similar situation but we never did hear again from the original poster as to whether it solved his problem or not!
 
Mathew

---

