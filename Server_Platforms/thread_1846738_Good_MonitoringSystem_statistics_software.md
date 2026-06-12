---
title: "Good Monitoring/System statistics software"
date: 2011-09-19
forum: Server Platforms
---

### Post by justinmiller621 on 2011-09-19
Hey all,

I've done a bunch of googling but have come go no good consensus on a popular and free system monitoring tool. I'd like to be able to access it via the web -- that's probably my biggest requirement. This is for personal use. 

I'd like to monitor things such as CPU temp, fan speeds, CPU usage. I'm not really concerned with network usage or really process usage. 

Any good ones out there?

---

### Post by vpharry on 2011-09-19
I suggest conky. Btw its kind of hard 2 set up n get it workin wid gud themes.... Try googling 4 it...

---

### Post by ibutho on 2011-09-19
Take a look at [Icinga]("https://www.icinga.org/") or [Nagios]("http://www.nagios.org/"). I don't know whether they are overkill for your needs, but I know Icinga has a web interface.

---

### Post by justinmiller621 on 2011-09-19
Nagios seemed like overkill when I looked at it. I'll checkout conky again -- I had previously looked at it, briefly. I'll check out Icinga too. Thanks.

---

### Post by Entilza on 2011-09-19
I'm using Ganglia for my servers, I liked that I could hook up Windows hosts to it very easily.  But I had to install the latest version of Ganglia for this to work. (3.2).  To get windows hosts to report data I used the sflow client, which shoots UDP packets to the host server every few seconds. [http://host-sflow.sourceforge.net/](http://host-sflow.sourceforge.net/)

Windows hosts don't report everything as in detail like the linux ones but it seems to work ok for the basic stuff.

---

