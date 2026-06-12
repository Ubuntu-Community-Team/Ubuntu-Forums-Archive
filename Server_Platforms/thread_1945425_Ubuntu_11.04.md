---
title: "Ubuntu 11.04"
date: 2012-03-23
forum: Server Platforms
---

### Post by taundertaker773 on 2012-03-23
Recently after installing my Ubuntu server 11.04 text mode yet with the (squid/2.7.STABLE9) im now left with the blocking torrents yet with the online streaming please if by any means you can help me block these it will be greatly appreciated cause my colleagues are chewing bandwidth?

---

### Post by Perfect Storm on 2012-03-23
Moved to Server forum.

---

### Post by d4m1r on 2012-03-23
> **taundertaker773 said:**
> Recently after installing my Ubuntu server 11.04 text mode yet with the (squid/2.7.STABLE9) im now left with the blocking torrents yet with the online streaming please if by any means you can help me block these it will be greatly appreciated cause my colleagues are chewing bandwidth?

Huh? You are going to have to explain yourself more...You would like to block people from using Bittorrent on your Ubuntu server?

---

### Post by dharmavir on 2012-03-24
I think ufw (uncomplicated firewall) should be able to help you block or unblock required ports.

ufw should already be installed and here is quick tip on how to use it:

[COLOR=#000000][FONT=Tahoma][FONT='Lucida Console']To enable UFW on your system to have UFW take care of IPTABLES:[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma][FONT='Lucida Console'] $ sudo ufw allow ssh/tcp
 $ sudo ufw logging on
 $ sudo ufw enable
 $ sudo ufw status[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma][FONT='Lucida Console'] Now to add any port like www / https / mysql etc just try following:[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma][FONT='Lucida Console'] $ sudo ufw allow www[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma][FONT='Lucida Console'] and then check status to see whether it really worked or not?[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma][FONT='Lucida Console'] [/FONT][FONT=Lucida Console]$ sudo ufw status[/FONT][/FONT][/COLOR]
[FONT=Lucida Console] and you will see those port added as exception/opened in the firewall.[/FONT]

---

### Post by bubylou on 2012-03-24
If you want the proxy server to block your colleagues from using torrents and streaming they will have to change there network configuration so that they have to connect to your server then the internet. Depending on home tech savy they are they can simply go straight to the internet and ignore your blocks. You could force them to use your proxy server by only giving it internet access from your router. Perhaps you have a setting in your router that will allow you to these block ports instead. That would be a much simpler solution.

---

