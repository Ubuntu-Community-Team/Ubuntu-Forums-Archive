---
title: "Connect two ubuntu machines"
date: 2016-11-28
forum: Server Platforms
---

### Post by watowato on 2016-11-28
Hey!

I'm running Ubuntu 16 on my desktop machine and I have VPS outside my network. On VPS is also installed Ubuntu 16. How could I pair these two machines with some remote desktop client?

The problem I have is that I can connect to VPS only from VPS services provides website. I click to Console and then opens new Mozilla Firefox window and I have option to type something in terminal. But it's sometimes hard to do some things because i can't use some shortcut commands or just paste some commands. Because I'm accessing VPS terminal through mozilla firefox.

Can somebody suggest me something?

---

### Post by darkod on 2016-11-28
Install openssh-server on your VPS (if not already installed) and then you can connect by ssh sessions from anywhere. You might need to do or adjust some firewall rules if there is a firewall in front of your VPS. If there is not, it is advisable to use iptables firewall on the VPS to prevent attacks.

---

