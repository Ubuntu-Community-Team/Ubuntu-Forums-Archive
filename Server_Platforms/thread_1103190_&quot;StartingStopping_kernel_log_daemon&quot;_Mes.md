---
title: "&quot;Starting/Stopping kernel log daemon&quot; Messages"
date: 2009-03-22
forum: Server Platforms
---

### Post by mcfly1337 on 2009-03-22
I am running Ubuntu Server 8.10 Intrepid. I try to have it running 24/7. When I am idle (afk) from the server, say overnight, I come back to see a screen filled with messages.

```
* Starting kernel log daemon...
* Stopping kernel log daemon...
```

And this repeats many times, filling the entire screen.

Any reasons why Ubuntu is telling me this while I am idle so much?
I would prefer to stop these messages from echoing.

Thank you. :)

---

### Post by mcfly1337 on 2009-03-23
*bump*
:popcorn:

---

### Post by mcfly1337 on 2009-03-24
*another shameless bump*

Seriously? No ideas?

---

### Post by T Bag on 2009-04-02
I've been experiencing the same issue on a Ubuntu Server 8.04.1.  I'm not noticing any real problem with the performance of the Server, but I'd like to know why the kernel log daemon keeps stopping and starting.

---

### Post by mcfly1337 on 2009-04-02
I wonder... do you have Webmin installed? I suspect it has something to do with Webmin.

---

### Post by T Bag on 2009-04-02
Indeed I do!  What makes you think it has something to do with Webmin?  I'm not actively using it when these messages are coming up.

---

### Post by mcfly1337 on 2009-04-02
Webmin has a logging feature and I remember seeing the same messages echo-ed somewhere within Webmin. But I don't see how to turn it off. It's annoying.

---

### Post by kunix on 2009-07-14
mcfly1337, try turning off the Bandwidth Monitoring module in Webmin. Worked for me :)

---

### Post by mcfly1337 on 2009-07-14
I had edited the bandwidth scripts, never seeing what looked like a print or echo command to me. But I had never thought of actually turning off the module. >_< 

I'll post back with the results, but I have a feeling it's going to work. :)

---

