---
title: "UFW -- host &amp; OpenVZ VE's: UFW or Shorewall?"
date: 2011-11-04
forum: Server Platforms
---

### Post by held7over on 2011-11-04
I need your expertise to guide me. I used to be a programmer in BASIC a very long time ago. I have been running Linux desktops for 5 years, but I feel I am really at the beginner level on the command line, although I have used it. This is my first server, a business server I am creating for a business idea to hopefully keep me from starving in this economic disaster, and if successful I need it to have a heavy load capacity without adding too much complication...as I am learning as I go. Using HowToForge stuff...I have set up my host and implemented OpenVZ to allow many different VE's. Amazing as it seems, everything works! 

A linux web server professional I bumped into was kind enough to give  me a quick outline of how he set's his own pro systems up which fits exactly what I want. But, being a novice and needing to cut my learning curve/time, I am wondering if UFW wouldn't be easier to implement for me, than Shorewall.

**My question is:**  Does UFW have the ability to do what I need it to do in the layout described below? I will be quoting my notes from the professional and perhaps this little description will also help someone else set up in this manner:

Building this at home, all external domains will, for now, point to my single home IP address. The host node will have a "rough" firewall which is not really meant to protect the host node. Instead the host's rough firewall is to be set to direct ALL port 80 and 443 traffic to OpenVZ's VE container 101 which is to contain a "sophisticated" firewall. (UFW or Shorewall?) 

This "sophisticated" firewall in VE container 101, which recognises port numbers and has them mapped to their respective various VE container's own IP addresses, then routes IP number traffic directly to the proper VE containers.

AND this "sophisticated" firewall in VE 101 also directs all domain name based http traffic to VE container 102 which is setting within VE 101's firewall's DMZ.

Container VE 102 contains an Apache server (which will be another big hurtle for me) which is running in VIRTUAL HOST MODE and which then handles all the external incoming and internal outgoing domain name based http(s) traffic by passing it to the respective and proper virtual containers I create for my business operations, etc., and receiving it back from the same.

Each of these other VE containers which I will create as I need them, will also have their own firewall and Apache server operating in SINGLE SERVER MODE and listening on their own high port numbers, such as 8800, 9123, etc.

Can UFW handle this and still be simple for me to learn and implement compared to Shorewall?

Any additional suggestions or things I should be aware of or that would make my task easier while still being able to handle heavy traffic, in implementing the firewall and web server, etc., would be welcome also!

Thanks! :)

---

