---
title: "Web monitoring traffic in LTSP network"
date: 2009-09-22
forum: Server Platforms
---

### Post by Indio77 on 2009-09-22
Hi all,

I manage a small LAN with a LTSP server and about 10 thin client. Everything works fine :guitar:

Now i'd like to install on the LTSP server a tool to monitor client web traffic... in few words 

i'd like to know which username has visited which url and how mutch time he/she spent in that url.

What tool do you reccomend me to use?

thanks in advance
Indio77

---

### Post by Lars Noodén on 2009-09-23
One possible option is called [cacti](http://packages.ubuntu.com/search?searchon=names&keywords=cacti")
[http://packages.ubuntu.com/search?searchon=names&keywords=cacti](http://packages.ubuntu.com/search?searchon=names&keywords=cacti)

You will have to decide if it does what you want.  There may be LTSP-specific tools out there.  What problem are you trying to solve?

---

### Post by ukripper on 2009-09-23
You can use nagios and cacti to monitor trends and manage alerts. Nagios which is perl based will alert you of http service running and can be customized for more detail info. Cacti will give you graphs for trend speculation.

I use both to manage my network.

---

### Post by Indio77 on 2009-09-23
Hi all thanks for you answers,

i didn't know cacti and i'll have a look....

in particular i only need a tool which tell me which LTSP user have visited which web site and for how mutch time... no more

---

