---
title: "Firestarter Events Information"
date: 2009-07-30
forum: Security
---

### Post by BJ_Covert_Action on 2009-07-30
Howdy Everyone,

I tend to keep firestarter open to monitor my firewall traffic when I am online. Generally, I can identify a given active connection at a given point and am comfortable doing whois lookups on various IP's to give myself a bit more information.

However, I am a bit of a networking/security newbie and I was hoping to be able to learn more about the traffic firestarter shows me. For instance, whenever an event occurs, I would like to be able to figure out why it was blocked. I would also like to figure out any information I can about the data that was blocked. I don't really know a whole lot about networking protocols or syntax, but I am willing to learn. I have a networking reference manual for dummies, but that talks more about configuring systems than anything.

I was curious if anyone knows any ways to gather more information regarding events and connections that are shown in firestarter. Is there a detailed log file somewhere? Is there a way to get more traffic details than what is shown in firestarter (protocol, IPs, and ports). Is there a good way to check out traffic and learn more about what it really is?

Thanks for any advice/resources in advance,
Brady

---

### Post by bodhi.zazen on 2009-07-31
If you want to learn these things start by familiarizing yourself with your logs. They are in /var/log

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

Next, learn the common servers and their default ports - ssh, ftp, http, and https at a minimum.

If you find traffic on port 139, what is the default traffic / server on that port ?

[http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)

Next ditch firestarter. Learn iptables.

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

Last learn to use snort

---

### Post by BJ_Covert_Action on 2009-08-02
Awesome, thanks for the links and hints. That will give me some reading material for this week. I have snort on my 'to-learn' list. As many things though, time runs short.

Any other resources folks could provide would be greatly appreciated.

---

