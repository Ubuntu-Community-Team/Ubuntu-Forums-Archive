---
title: "ebtables Usage . Please contact your question."
date: 2012-06-20
forum: Security
---

### Post by oklokl on 2012-06-20
Linux ubuntu 3.4.0-5-generic #11~precise1-Ubuntu SMP Wed Jun 6 01:55:41 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

ebtables v2.0.9-2 (June 2009)

sudo apt-get install ebtables

sudo ebtables -A FORWARD -s 00:11:22:33:44:55 -p IPV4 -j DROP


[http://ebtables.sourceforge.net/examples/basic.html#all](http://ebtables.sourceforge.net/examples/basic.html#all)

[COLOR=Red]When I'm add the settings and reboot it again.
 My settings are initialized.[/COLOR]


rebooting..

sudo ebtables -L

[COLOR=Red]Lost my setting.[/COLOR]

Bridge table: filter

Bridge chain: INPUT, entries: 0, policy: ACCEPT

Bridge chain: FORWARD, entries: 0, policy: ACCEPT

Bridge chain: OUTPUT, entries: 0, policy: ACCEPT




I'd like to keep my settings.
how should I do?

---

