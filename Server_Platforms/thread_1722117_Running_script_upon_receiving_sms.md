---
title: "Running script upon receiving sms"
date: 2011-04-05
forum: Server Platforms
---

### Post by costantino.amato on 2011-04-05
Hi all,
I have been using successfully gnokii on Ubuntu server 9.10 to send me alerts as Nagios' monitored hosts change state from normal to warning/critical.

I would like to be able to run specific scripts (I would say no more than 10) as the server receives sms containing specific keywords from authorized numbers (eg. "restart openvpn" would run a script containing the appropriate instructions to restart the daemon).
I guess this could be accomplished using a daemon to store messages in a Mysql db and other tables could be used to store authorized numbers, keywords and associated path to scripts etc..
Can I leverage the existing gnokii configuration or should I start from scratch? 
I am really a newbie so any sugestion is greatly appreciated.
Regards,
C.A.

---

