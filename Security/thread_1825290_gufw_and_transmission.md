---
title: "gufw and transmission"
date: 2011-08-15
forum: Security
---

### Post by claracc on 2011-08-15
Hello, I have lubuntu 11.04 installed in my laptop. Running transmission 2.13 and installed gufw in order to manage ports.

In transmission, I have selected in edit --> preferences--> net, to choose a random port for incoming connections each time transmission starts. In order to share files in transmission, I have configured ufw through gufw adding the following rule: Preconfigured tab, allow in app transmission, but I observe that always add the same port: 51413/tcp udp allow in form anywhere and no the random port established for incoming connections when transmission starts.

I think this is a not correct behaviour (perhaps a fail in integration between transmission and gufw or in some configuration file?). Is there any workaround in order to allow incoming connections in ufw when transmission starts with random incoming port?

Thanks in advance

---

### Post by kerry_s on 2011-08-15
It's like port forwarding, you need to set a port.

---

### Post by claracc on 2011-08-16
Ok, so I understand that I need a port number to allow traffic in.

But there is something wrong ( I think in gufw software) since I run transmission, it selects a random port to let the traffic in, then I open gufw to open this port by the add rule menu: preconfigured, allow in, app, transmission and it always opens the default port 51413, not taking into account that transmission lets the traffic in by other port (random one).

I think the correct behaviour would be that gufw could read in some file the opened port by transmission to let the traffic in.

Regards

---

### Post by kerry_s on 2011-08-16
i haven't used gufw in a long time, but if i remember right you can change that or manually set for any traffic from transmission.

---

### Post by claracc on 2011-08-16
Yes, I can set a port number to allow traffic in by adding rules through simple and advanced tabs in menu of gufw and they work well, I have to know the port's number opened to let traffic in by transmission and to write it.

What I think it doesn't work properly in this case is if I add the rule through preconfigured tab in menu, which always opens 51413 port no matter the port transmission is using to let traffic in.

---

### Post by kerry_s on 2011-08-16
> What I think it doesn't work properly in this case is if I add the rule through preconfigured tab in menu, which always opens 51413 port no matter the port transmission is using to let traffic in.

that is the default port, what else would it use? it's not like it knows what a user might set it to or what random port could come up, that's why you can manually configure. presets are nice, but it's a courtesy, not a requirement.

---

