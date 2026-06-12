---
title: "Strange thing with ubuntu server"
date: 2006-11-10
forum: Server Platforms
---

### Post by Blux on 2006-11-10
I've searched the whole forum to find something to help and did a lot of google with no success.

I installed ubuntu server 6.06 LTS and did a LAMP installation.
I have a Intel celeron 400MHz, I work in console only and I'm not too good in linux by the way, so please be explicit and very precise.

I configured lot of things (including vsftpd, ssh, mysql, etc...) and  the server does something very strange. After some times without activity, he suddently do something like poweroff. Everything seems yo be off (even the power LED is off, and the network card LED) and that pisses me off.

I can't see what's happening and I've checked the syslog file but apparently I did a restart when presssing the power button. I want to disable that hibertane or suspend, but I really don't know how.

Please help me!!

---

### Post by Blux on 2006-11-11
Problem solved. My integrated graphic card isn't managed correctly with ubuntu. I installed an old pci ati video card and now my server isn't closing by itself. Here's what I think :

After X mins of inactivity, ubuntu stop displaying on the monitor.

After another X mins of inactivity, ubuntu send a signal to close the monitor, but wasn't interpreted correctly by the mobo and it power off the entire system without writing anything in the log files.

I hope this will help anybody else with integrated graphic and strange behavior.

---

