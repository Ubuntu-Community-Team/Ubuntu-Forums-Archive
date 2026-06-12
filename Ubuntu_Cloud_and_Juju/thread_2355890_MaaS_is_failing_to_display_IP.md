---
title: "MaaS is failing to display IP"
date: 2017-03-17
forum: Ubuntu Cloud and Juju
---

### Post by fabianbaier on 2017-03-17
[COLOR=#333333][FONT=Ubuntu]Hi,[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I am deploying Ubuntu 16.04 on my machine. The machine gets correctly installed via MaaS. However, when I look at the machine's IP configuration it is empty. Looking through my dhcp logfiles I see that the machine got an IP assigned which is not reflected in the webinterface nor does it look like that MaaS is aware of it. When the machine boots normally into the newly installed system it comes up online with an IP that is the one which was assigned by DHCP but just not showing in the webinterface. I am able to connect to the machine via ssh after I looked through the dhcp logfiles to see which IP it has.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Did anyone else experienced a similar behavior? How can I troubleshoot this better? Why is the IP not showing in the webinterface although the machien comes up fully deployed, pingable on its ip?[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Best,
FB[/FONT][/COLOR]

---

