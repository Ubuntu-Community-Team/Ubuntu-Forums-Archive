---
title: "UFW blocks them all"
date: 2013-05-05
forum: Server Platforms
---

### Post by timepilot on 2013-05-05
I just installed ufw on the server.\\:D/  It works so good webpages don't load, ssh is very slow and I can't login to mail, other than that it works really good.:lolflag:  I think the online tutorial to install it is leaving out most of the steps needed to actually make it a useable firewall. I think there is way more to configure then just allowing ports. Could someone tell me what else I need to configure and some examples would help?

Here are the ports that are allowed.
21/tcp
25/tcp
53/tcp
53/udp
80/tcp
110/tcp
143/tcp
443/tcp
xxxx/ssh

---

### Post by brent1975 on 2013-05-06
When you are saying they are open are you saying that because you added these ports or have you verified them?
to verify they are set  sudo iptables -L

have you flushed the tables and disabled ufw?

to flush [COLOR=#000000]sudo ufw [/COLOR][COLOR=#666600]--[/COLOR][COLOR=#000000]force reset

to disable  sudo ufw disable

Have you thought about working with IPtables by itself and leaving out UFW? Basic IPtables is very simple to set up for basic open close. Of course you can get very complex with them too... UFW is just an easy way to manage IPtables.. I personally would just dig right in. Here is a tutorial that you can use. Very simple and not complicated as long as you know how to use the terminal. [http://forums.iso-world.com/index.php/topic/18-iptables/](http://forums.iso-world.com/index.php/topic/18-iptables/)  overall the end result will be the same. :)


[/COLOR]

---

