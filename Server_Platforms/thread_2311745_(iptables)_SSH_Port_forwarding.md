---
title: "(iptables) SSH Port forwarding?"
date: 2016-01-29
forum: Server Platforms
---

### Post by Daniel_Schmid on 2016-01-29
Hey i exedentlly blocked the port 22 on my home-server with ubuntu. 

I wrote this via. PUTTY: [COLOR=#000000][FONT=Arial]iptables -A INPUT -p tcp --dport 22 -j DROP;[/FONT][/COLOR]


Please help me ... but dont write to complicated im new to linux ...



Graetings

---

### Post by leith98b on 2016-01-29
So you just want to remove that rule?  One way would be to do an "iptables -nvL --line-numbers" and see which rule that is, then do an "iptables -D INPUT <num>" with the number of the rule you want to remove.  Does that help?

---

### Post by darkod on 2016-01-29
You can't do it over ssh now. You will have to connect the server to monitor and keyboard, log in and delete the rule with identical command only using -D at front.
```
sudo iptables -D INPUT -p tcp --dport 22 -j DROP
```

Another option is simply to reboot the server, holding the power button. When entering iptables rules in the command line they are temporary unless you make them permanent to load on boot. So rebooting the server will make that rule go away...

---

