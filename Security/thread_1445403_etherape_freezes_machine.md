---
title: "etherape freezes machine?"
date: 2010-04-02
forum: Security
---

### Post by skaramanger on 2010-04-02
Hello,

I'm using 9.10. My PC is connected to an Actiontec MI424WR (Verizon FIO) router/switch. I installed etherape to do some packet sniffing. I started attempting to start as super user from menu (gksudo -u root /usr/bin/etherape). Machine appears or just flatout locks up. My mouse and keyboard are unresponsive. I am unable to ssh in from a machine on my local network, I then press the reboot key. I changed to using the command line:

```
userprompt#sudo /usr/bin/etherape[CODE]

Same thing happens.  I tried waiting a minute or so. Still nothing.  Below is the only output I can find that relates to etherape in my messages log file. I have looked at a thread or two regarding network configuration:

[http://ubuntuforums.org/showthread.php?t=490789&highlight=etherape+error]("http://ubuntuforums.org/showthread.php?t=490789&highlight=etherape+error")

Is this whats happening here. I'm not sure, but I don't think so. I just have a router.. Right?

[CODE]Apr  2 13:33:41 localhost kernel: [250328.505539] etherape uses 
obsolete (PF_INET,SOCK_PACKET
```

Any suggestions?

TIA,

Skaramanger

Bump Please!

---

