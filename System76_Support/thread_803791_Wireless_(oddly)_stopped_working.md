---
title: "Wireless (oddly) stopped working"
date: 2008-05-22
forum: System76 Support
---

### Post by jjdarling on 2008-05-22
Hi,

i've been having the problem that I outlined in pretty significant depth in this thread: [http://ubuntuforums.org/showthread.php?t=802894](http://ubuntuforums.org/showthread.php?t=802894)

What it basically seems to be boiling down to is that I accidentally toggled a button on my laptop (gazp5) to turn off the wireless. This is based on the fact that when I type in:
```

sudo cat /var/log/messages | grep switch
```

the response I get is a whole bunch of 

```
May 22 14:18:36 ubuntu kernel: [   41.305433] iwl3945: Radio disabled by HW RF Kill switch
May 22 14:18:38 ubuntu kernel: [   43.110673] iwl3945: Radio disabled by HW RF Kill switch
```

Going back to when the wireless went out sometime yesterday evening. There are a couple other random things in the log, but none seem particularly interesting.

Anyway, when I press Fn+F2 to turn the wireless back on, nothing happens, so I'm not sure if this is the problem. Any help would be appreciated.

---

### Post by thomasaaron on 2008-05-22
The switch is on the leading edge of your gazv5, on the left hand side. Toggle it to the right.

---

### Post by jjdarling on 2008-05-22
Haha, I'm a little embarrassed for never having noticed that before. 

Ok, I did that, but after playing around with a couple other things i got it to work as it should. Thank you for helping me. I've been consistently amazed with the support over at system76.

---

