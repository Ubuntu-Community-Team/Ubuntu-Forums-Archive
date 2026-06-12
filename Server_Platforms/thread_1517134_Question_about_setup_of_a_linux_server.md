---
title: "Question about setup of a linux server"
date: 2010-06-24
forum: Server Platforms
---

### Post by flibitboat on 2010-06-24
Does anyone know, or have any experience with, what the best way to set a network interface on a linux server to be up - so that virtual machines can bridge through the physical interface, but not allow anyone on a network to connect to the server itself?  Thank you :)

---

### Post by sikander3786 on 2010-06-25
Hi.

I run Virtual Box on Ubuntu- I have run XP and several Linux distros. One thing to note. I use IPBlock -IPList on my host and like it. It will stop connections on the guest XP.Thus you can block many connections from known malware sites on your venerable windows guests. Check it out.

Source: [http://art.ubuntuforums.org/showthread.php?t=1424685](http://art.ubuntuforums.org/showthread.php?t=1424685)

IPBlock might block all the unwanted connections and ports between the host and the guest. That way you might be able to achieve your goal.

Regards.

---

