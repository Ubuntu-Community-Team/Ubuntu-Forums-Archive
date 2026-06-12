---
title: "[Q] Need some help ubuntu server"
date: 2022-05-08
forum: Ubuntu, Linux and OS Chat
---

### Post by wou5er on 2022-05-08
Hello,

Recently using using ubuntu server 18.04. I've searched the web for answers but nothing mayby i'm searching wrong?
Any way I'm having some trouble on accessing my web-based projects like: Domoticz , HyperHDR.
Both managed in the browser.

The problem is i'm not able to connect to those ip adress... when i do i get a error: Conection Refused.

It has to do something with a EUfirewall... but i check and its not running.

Any help would be appreciated.

---

### Post by TheFu on 2022-05-08
Standard support for 18.04 ends in 12 months.  It would be smart to not bother with that release and use 20.04 for production and 22.04 for learning. Each of those has 5 yrs of standard support from the release date - 20.04 has 3 more years. 22.04 has 5 yrs.

What is the IP of the client machine and what is the IP of the server machine?
How did you install the listed projects?
Are these CORBA servers, REST interfaces, HTTP, HTTPS or some other protocol?  Please don't assume everyone has heard of the tools. I haven't.  I searched for Domoticz ... and have to say I've looked into home automation before, but never heard of that tool/project.  Same for HyperHDR, though I think Home-Assistant handles lighting too.

Without the exact protocols and infrastructure tools used, we'd have to guess between 50+ different answers.  **Please don't make us guess.**  Connection refused usually means the server you think is running, isn't actually running.  Is some sort of container being used or did you install a bunch of .deb packages?  

Installing server stuff usually isn't sufficient. Configuration is required. Often, that configuration is significant and requires editing text config files.

Domoticz says on their installation wiki that Ubuntu 20.04 is the minimum version required.  Code made for 20.04 won't work on 18.04. They have different libraries.

I have no clue what "a EUfirewall" is.  That isn't the normal firewall interface used on 18.04 server.  18.04 uses iptables in the kernel as the firewall and the main CLI tool used to manage FW rules.  There's also ufw, which is a simpler CLI tool that makes iptables commands.  In 22.04, nftables is used instead as the firewall.

---

