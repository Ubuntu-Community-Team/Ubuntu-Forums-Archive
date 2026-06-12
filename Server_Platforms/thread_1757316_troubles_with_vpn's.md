---
title: "troubles with vpn's"
date: 2011-05-13
forum: Server Platforms
---

### Post by tapi0n on 2011-05-13
This may be a stupid question but it's driving me crazy.

For this school project I'm setting up a nagios monitor. Got my servers in the local network monitoring, all going good. 

Now I've been asked to monitor servers on another network (ofcourse being maintained by the same people). Thing is, I'm totally new to Ubuntu server (started using it like a week ago) and I have no idea on how to even start setting up a vpn.

In windows it's just click click pew pew all is well. But all the information I can find about vpn's on ubuntu are either about graphical implementatios for dekstop releases or tutorials on how to set up a vpn server. 

Any help would be appreciated. I'm not looking for a concrete walktrough or anything, I just don't know where to start on the subject. 

I'm running Ubuntu 9.10 and the servers I'm supossed to monitor are all Windows servers (should that matter).

Cheers,

---

### Post by SeijiSensei on 2011-05-13
Here's a good place to start:

[http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html](http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html)

OpenVPN has support for both Windows and Linux.

---

### Post by tapi0n on 2011-05-14
Thanks mate, going to look into it now :) 

Got one question tho. Every piece of information I find explains both client and server side of the vpn. But the servers I got to connect to already allow you to make a vpn connection, so I'm assuming there's already some sort of vpn service running? Now seeing how windows (their windows servers) uses pptp vpn's, can't you just connect to that service?

It may be a badly formulated question, but I hope you know what I'm trying to say.

---

### Post by SeijiSensei on 2011-05-14
PPTP client for Linux:

[http://pptpclient.sourceforge.net/](http://pptpclient.sourceforge.net/)

---

### Post by tapi0n on 2011-05-14
Ok cheers mate. Seriously appreciate the input, you've helped me out a lot and helped me get on track to get this project going. Big thumbs up :)

---

