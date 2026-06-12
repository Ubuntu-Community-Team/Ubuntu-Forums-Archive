---
title: "CTRL-ALT-F1 to get to console.. saves system resources?"
date: 2009-01-26
forum: Server Platforms
---

### Post by orionMX on 2009-01-26
Hello All,

I would like to keep kdm for occasional use.  I would also like to run web application servers in console mode.  I have read various ways to disable kdm/gdm and am not happy with those solutions because there are times when I would like to use the GUI.  

My question is this:
Will I be saving system resources by entering a console via CTRL-ALT-F1?  Does that in effect shutdown the kde/xserver, thus saving those system resources?  Is booting directly into console, by removing kdm from RL2 the same as using the CTRL-ALT-F1 shortcut?

I have been purposely redundant so that the question is clear.  Thanks for your indulgence.

orionMX

---

### Post by snova on 2009-01-26
> **orionMX said:**
> Will I be saving system resources by entering a console via CTRL-ALT-F1?  Does that in effect shutdown the kde/xserver, thus saving those system resources?

No, it's all still running.

> Is booting directly into console, by removing kdm from RL2 the same as using the CTRL-ALT-F1 shortcut?

No, because then there are no graphics running.

---

### Post by orionMX on 2009-01-26
OK... thanks.  What, then is your best suggestion.  After hitting CTRL-ALT-F1, can I then stop kdm (graphical services) from the terminal?  And how can I accomplish this?  Could I then restart kdm if needed?

Thanks

---

### Post by snova on 2009-01-26
> **orionMX said:**
> After hitting CTRL-ALT-F1, can I then stop kdm (graphical services) from the terminal?

```
sudo /etc/init.d/kdm stop
```

> And how can I accomplish this?  Could I then restart kdm if needed?

```
sudo /etc/init.d/kdm start
```

---

### Post by orionMX on 2009-01-26
Thanks!!  Saved a bunch o'RAM !!  Am now Googling other services that might be able to be shut off when going to terminal and "server mode".  Someday I will resinstall a server only distro, but for now am still getting comfortable with Linux in general.  My ultimate goal is to stop the dual boot setup on this box, go to Linux server only, and get rid of windows on my entire home network.  Thanks for your help, it has given me much insight and confidence.

frank

---

### Post by electrogeist on 2009-01-27
> **orionMX said:**
>  I have read various ways to disable kdm/gdm and am not happy with those solutions because there are times when I would like to use the GUI.  

Then you can type "startx"

---

