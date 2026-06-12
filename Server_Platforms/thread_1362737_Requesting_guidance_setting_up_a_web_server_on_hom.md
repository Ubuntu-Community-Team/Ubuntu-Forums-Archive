---
title: "Requesting guidance setting up a web server on home network"
date: 2009-12-23
forum: Server Platforms
---

### Post by JavaBeanHead on 2009-12-23
Hello Gurus . . . 
 
I've read several tens of posts in an attempt to find guidance on how to set up a web server within my local network at home (yet separated from the other hosts in my network). The ultimate goal is to set up and host a website using Joomla or Drupal.
 
I've drawn some assumptions based on what I've read, and I just wanted to litmus test it with you guys.
 
I keep reading about BIND and named.conf files . . . and the Split DNS (a.k.a. Split Horizon DNS) setups versus DMZ. Are there advantages / disadvantages to these? My router is a gateway from AT&T's U-verse service, and it does have a DMZPlus mode on it, but the manual doesn't say to what degree a device placed in the DMZ is shielded from the internal 'private' LAN. 
 
Are there any risks with putting Ubuntu Server (running a firewall like Firestarter, Shorwall, Firewall Builder) into the DMZ? Is there a potential that this can compromise the security of my internal 'private' machines and the data on them? If I put the server into the DMZ, does that preclude me from needing to use a Split DNS configuration? Or do I need to do DMZ as well as Split DNS? 
 
Is all of [this]("http://www.bind9.net/manual/bind/9.3.2/Bv9ARM.ch04.html#id2549203") necessary if I use the DMZ?
 
What are your thoughts on Firestarter versus Shorewall?
 
Any other things I should know?
 
Happy Holidays,
JavaBeanHead
 
PS - here is a list of some of the posts I've read. Maybe this is why I'm so conflicted to what's applicable, and what is not:

[LIST]
[*][http://joomlapanel.com/joomla-article/joomla-tutorial/135-setup-a-dedicated-web-server.html](http://joomlapanel.com/joomla-article/joomla-tutorial/135-setup-a-dedicated-web-server.html)
[*][[SIZE=1]http://www.zimbra.com/forums/installation/23352-split-dns-debian.html[/SIZE]]("http://www.zimbra.com/forums/installation/23352-split-dns-debian.html")
[*][http://www.bind9.net/manual/bind/9.3.2/Bv9ARM.ch04.html#id2549203](http://www.bind9.net/manual/bind/9.3.2/Bv9ARM.ch04.html#id2549203)
[*][http://utalk.att.com/utalk/board/message?board.id=HSIA&thread.id=8146&view=by_date_ascending&page=1](http://utalk.att.com/utalk/board/message?board.id=HSIA&thread.id=8146&view=by_date_ascending&page=1)
[*][http://utalk.att.com/utalk/board/message?board.id=HSIA&thread.id=8411](http://utalk.att.com/utalk/board/message?board.id=HSIA&thread.id=8411)
[*][http://wiki.zimbra.com/index.php?title=Ubuntu_8.04_LTS_Server_%28Hardy_Heron%29_Install_Guide]("http://wiki.zimbra.com/index.php?title=Ubuntu_8.04_LTS_Server_%28Hardy_Heron%29_Install_Guide")
[/LIST]

---

