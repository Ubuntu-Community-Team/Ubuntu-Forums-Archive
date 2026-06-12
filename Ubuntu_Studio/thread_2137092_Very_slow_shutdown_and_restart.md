---
title: "Very slow shutdown and restart"
date: 2013-04-19
forum: Ubuntu Studio
---

### Post by jonathanfv on 2013-04-19
Hi people. I'd need some help. When I shutdown or restart my computer, it's always very slow. It consistently takes around 30 seconds, with no exception. I tried reading the output text before it shuts down, and at first, I saw that it failed to stop the vboxnetadp deamon, so I uninstalled Virtual Box to see if it would make a difference, to no avail. It did just the same. I red in some places it was caused by network-manager, but I'm using WICD. So I'm having a hard time finding out what takes so much time to shutdown or where the problem is. Any idea how come my computer takes a longer time to shutdown than to startup?

Thanks to anyone who can help (or try helping).

---

### Post by matt_symes on 2013-04-20
Hi

30 seconds does not seem too unreasonable to me - depending on hardware. What times are you expecting ?

Anyway, check your logs.

```
/var/log/syslog
```

Post the relevant sections here if you like.

Kind regards

---

### Post by jonathanfv on 2013-04-20
Hi! I'm checking my syslogs, but I can't seem to find anything too weird. I think that 30 seconds is a long shutdown cause I'm booting in 12-13 seconds. Oh well. If I can't find anything, I guess it's not that big of a deal either. Thank you once again, Matt.

---

### Post by matt_symes on 2013-04-20
Hi

If you want to post your syslog here i'll take a look for you. 

Two eyes are better than one and all that.

```
sudo apt-get install pastebinit
```

```
cat /var/log/syslog | pastebinit
```

Post the link back here.

If your booting much faster than shutting down then maybe there is something going on.

BTW: One thing you can do is stop service manually before shutting time and timing the shutdown. Do that until you find the offending service.

You can also so it with modules.

You can edit you service file to dump all running processes at specific points in the shutdown sequence to a file.

And other things you can do as well.

If you want to persue this, i'll help.

Kind regards

---

### Post by jonathanfv on 2013-04-29
Hey Matt! I'm very sorry I haven't replied earlier, I came back from an other city and I'm very busy with piled up work. But I still want to figure this one out. I just updated to 13.04 (the latest version of Bumblebee seemed to be configured for 13.04 and made my 12.10 system crash, so I either had to install an older version or update the entire system), and there's no change: it takes a very long time to shut down.

I'm looking at it, and it seems to me like acpid is taking a long time to shut down. I've posted the log on pastebin, like you asked me:

[http://paste.ubuntu.com/5617862/](http://paste.ubuntu.com/5617862/)

I'll also try to manually shut down various services and modules manually before shutting down, but it might take some time before I have enough time to dig in it. So if you're no longer interested in the problem, I'll understand, and I want to thank you for the help you've provided me with.

---

### Post by matt_symes on 2013-04-30
Hi

I'm subscribed to this thread so when you next post, i'll be notified :)

Kind regards

---

