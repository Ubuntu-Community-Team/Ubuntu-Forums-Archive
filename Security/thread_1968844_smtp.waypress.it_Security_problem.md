---
title: "smtp.waypress.it??? Security problem?"
date: 2012-04-29
forum: Security
---

### Post by Ashrael on 2012-04-29
Hi all,

when I start up iftop, I see a connection to smtp.waypress.it, but I have no mail account configured nor do I know why I should be connected to this smtp server?

Anybody have a clue here? Has the Italian CIA broken into my laptop? :)

any help appreciated.

---

### Post by unspawn on 2012-04-30
> **Ashrael said:**
> when I start up iftop, I see a connection to smtp.waypress.it, (..) any help appreciated.
The FQDN suggests it's a MTA but your post doesn't show it was a TCP/25, UDP/6881 or TCP/22 connection. What you could do:
- check which process Id uses the connection and check its logs,
- search your system and daemon logs and login accounting for the corresponding IP address,
- sniff packets and check the payload in any network traffic analyzer.

---

### Post by Ashrael on 2012-06-05
I haven't looked into this any further, but thinking about it for awhile I think it might be the weather applet I installed. I will look into this further when I get the time... thanks.

---

