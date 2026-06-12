---
title: "server crash - logs?"
date: 2008-12-02
forum: Server Platforms
---

### Post by ljubomir on 2008-12-02
Hi,

As of recently my ubuntu server started crashing after a few hours of work (uptime varies from 30m to 12h). Ssl session freezes and samba shares become unavailable. 
What logs (and where are they located) should I inspect for clues?

Thanks!

---

### Post by __Ryan__ on 2008-12-02
You can run:

```
dmesg | less
```

at the command line. 

You can also view the system logs by going to 

**System -> Administration -> System Log**

---

### Post by Masuran on 2008-12-02
Just a short list:
[LIST]
[*]/var/log/syslog
[*]/var/log/messages
[/LIST]

If you suspect a particular program to be the culprit checkt the logs of that program.

You say that the server freezes after some time, perhaps a memory issue? Leaky software could fill up the memory driving the server to a halt. Are you running any special software?

---

### Post by ljubomir on 2008-12-02
@Ryan: dmesg only applies to the running machine, doesn't it? No trace of actions before the reboot. And no X here, so no GNOME tools either ;)

@Masuran Yeah, I suspect the memory too, but have to find a spare monitor to run memtest on it :)

Thanks for the help!

---

