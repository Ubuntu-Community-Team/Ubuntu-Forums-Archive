---
title: "panp6 - fan turns off randomly"
date: 2010-01-18
forum: System76 Support
---

### Post by revlimiter on 2010-01-18
I've been searching forums for an answer to this for about an hour. No luck. Hoping someone smart will know something. 

The fan on my shiny new panp6 turns off at odd times and never turns back on. I've seen it shut off anywhere between 42 and 50 degrees. It never restarts. The system just gets hotter and hotter after that. 

Hitting the silent mode switch a few times seems to trigger it to come back on, but not always. And by a few times I mean between 2 and 10. A simple off-on toggle doesn't always do anything. 


What I've done: installed sensors-applet. Nothing else.

---

### Post by thomasaaron on 2010-01-19
```
I've seen it shut off anywhere between 42 and 50 degrees. 

```

That doesn't sound abnormal.

> It never restarts.

That does sound abnormal.

Does the machine ever overheat and shut down? How hot does it get if you just leave it.

Open a terminal and run this command...

glxgears

...and then open two or three more tabs in the terminal and run glxgears in all of them. In other words, I want a few instances of glxgears running simultaneously.

How hot does it get?
Does the fan ever come on?

---

### Post by revlimiter on 2010-01-19
I've been running it all morning. The fan hasn't shut off yet. It's running at a comfy 48*. 

When or if the fan shuts off, I'll try your stress test and let you know. Thanks!

---

### Post by thomasaaron on 2010-01-19
OK. 

I'm also interested in knowing if there are any suspend/resume cycles involved.

---

### Post by revlimiter on 2010-01-19
When I was having the problems yesterday, yes and no. It did it immediately after a reboot once with no suspends. It also did it after a couple suspend cycles. 

Today, I've suspended twice. No problems yet. 

I did run glxgears just to see what would happen. I let it get up to 70 and then turned the gears off. It cooled back to 48, no problem. And the fan never turned off.

---

### Post by thomasaaron on 2010-01-19
I thought the problem was that the fan would not turn on.

It has to cool off both the cpu and the graphics card. So, if the temp is 48, that is the CPU. That doesn't mean the graphics card doesn't still need cooling. But it should turn off eventually.

---

### Post by revlimiter on 2010-01-19
The problem was the fan turning off and then not turning back on EVER. I don't care if it turns off and then on. I don't care if it stays on. I just want it to sometimes turn back on when the system is in danger of becoming a puddle of plastic. 

However, I'm not seeing the problem anymore. 

Sorry for wasting your time.

---

### Post by thomasaaron on 2010-01-20
Not a waste at all. Please let me know if you need any assistance.

---

