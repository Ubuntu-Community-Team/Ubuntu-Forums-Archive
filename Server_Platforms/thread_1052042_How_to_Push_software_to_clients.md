---
title: "How to Push software to clients"
date: 2009-01-27
forum: Server Platforms
---

### Post by MaindotC on 2009-01-27
In Server 2003 you can deploy software to clients in a windows domain and those that adhere to Active Directory.  How would you do this in a Linux distribution?  My first thought would be to set up a repository and load the repo address in sources.list, but make the package a required installation or upgrade like some of the updates we download to our Ubuntu machines.

---

### Post by netztier on 2009-01-27
> **strAlan said:**
> In Server 2003 you can deploy software to clients in a windows domain and those that adhere to Active Directory.  How would you do this in a Linux distribution?  My first thought would be to set up a repository and load the repo address in sources.list, but make the package a required installation or upgrade like some of the updates we download to our Ubuntu machines.

Did you ever take a look at [Landscape]("http://www.canonical.com/projects/landscape")?

regards

Marc

---

### Post by bluefrog on 2009-01-27
[http://www.glpi-project.org/spip.php?lang=en](http://www.glpi-project.org/spip.php?lang=en)

---

### Post by MaindotC on 2009-01-27
Thanks for the reply.  I've not seen Landscape before but it looks like an interesting tool and could possibly acheive what I'm looking for.  Unfortunately, this is for a class experiement so I can't purchase software.  Thank you for the suggestion though - if I ever get to work in a Ubuntu environment this is something I'd like to learn :D

---

### Post by netztier on 2009-01-28
> **strAlan said:**
> Thanks for the reply.  I've not seen Landscape before but it looks like an interesting tool and could possibly acheive what I'm looking for.  Unfortunately, this is for a class experiement so I can't purchase software.  Thank you for the suggestion though - if I ever get to work in a Ubuntu environment this is something I'd like to learn :D

D'oh! I never even realised that canonical is marketing Landscape as SaaS primarily (Software as a Service). This means that the Web UI and the the database holding information about the machines you manage is hosted on Canonical's Web site, and that all your machines talk to Canonical's Landscape servers to poll configuration/inventory/management tasks you might have waiting for them there.

I can see some benefit in such an approach when having to manage systems (servers or clients) that are scattered across the Internet. This is beneficial in a "digital nomad" world, where users are more often abroad and mobile than in a central or branch office connected to a company network.

However, I don't think that such an approach is "enterprisey" [1] enough for adoption by a large company. I for one would prefer to have Landscape running inside my network, have complete control locally; road-warriors would have to work via VPN anyway and could talk to the server that way. 

It seems that you can get a standalone version, but you'd have to contact Canonical's sales department for that. I'd try my luck and make an equiry about special pricing for classroom or educational use.

regards

Marc



[SIZE="1"][1] I presume that there's not that many large companies running *Ubuntu* in such an "enterprisey" way ;-). <sarcasm> They still prefer to sell their souls, grandmas and daughters to that certain company from Redmond. Or Armonk, at that. </sarcasm>[/SIZE]

---

