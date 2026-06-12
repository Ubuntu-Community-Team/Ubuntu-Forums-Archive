---
title: "Kernel panic, shoddy driver."
date: 2010-04-12
forum: Server Platforms
---

### Post by Grenage on 2010-04-12
Greetings,

One of my test servers has a serial card in it, which handles an external temperature array.  Since the card has been operating, I have experienced a few 'random' kernel panics; /var/log/messages would seem to indicate that the card drivers are at fault:

```
Apr  9 15:05:03 nagios kernel: parity=0 overrun=0No of Errors In ttyD0 brake=0
frame=0 parity=0 overrun=0No of Errors In ttyD0 brake=0 frame=0 parity=0 overrun=0No
of Errors In ttyD0 brake=0 frame=0 parity=0 overrun=0No of Errors In ttyD0 brake=0
frame=0 parity=0 overrun=0No of Errors In ttyD0 brake=0 frame=0 parity=0 overrun=0No
of Errors In ttyD0 brake=0 frame=0 parity=0 overrun=0No of Errors In ttyD0 brake=0
frame=0 parity=0 overrun=0No of Errors In ttyD0 brake=0 frame=0 parity=0 overrun=0No
of Errors In ttyD0 brake=0 frame=0 parity=0 overrun=0No of Errors In ttyD0 brake=0
frame=0 parity=0 overrun=0No of Errors In ttyD0 brake=0 frame=0 parity=0 overrun=0No
of Errors In ttyD0 brake=0 frame=0 parity=0 overrun=0No of Errors In ttyD0 brake=0
frame=0 parity=0 overrun=0No of Errors In ttyD0 brake=0 frame=0 parity=0 overrun=0No
of Errors In ttyD0 brake=0 frame=0 parity=0 overrun=0No of Errors In ttyD0 brake=0
frame=0 parity=0 overrun=0No of Errors In ttyD0 brake=0 frame=0 parity=0 overrun=0No
of Errors In ttyD0 brake=0
```

ttyD is the serial adapter.  Those messages come up all the time, but I don't get any output when the system does eventually go down.

I suspect I know the answer, but are there any avenues to explore, given that there are no other drivers available?

---

