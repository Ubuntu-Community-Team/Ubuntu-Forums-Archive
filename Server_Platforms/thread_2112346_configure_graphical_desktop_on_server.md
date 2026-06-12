---
title: "configure graphical desktop on server?"
date: 2013-02-04
forum: Server Platforms
---

### Post by three_jeeps on 2013-02-04
I am running ubuntu 8.04 LTS server.  I am fine with doing all my work from the CL, HOWEVER, there are some things that can go a bit easier with the graphical desktop.

how can I easily drop in a desktop on this server that I can invoke from the CL, so that I can use it whenever I want?

Thanks for your help/pointers!

-John

---

### Post by Cheesemill on 2013-02-04
I wouldn't recommend this.

Support for the desktop packages available for 8.04 ran out nearly 2 years ago.

In fact support for 8.04 runs out altogether in 2 months, it would be a wise idea to start research on implementing an OS upgrade straight away.

---

### Post by spynappels on 2013-02-05
I'd agree with Cheesemill, you should be planning an OS upgrade as a matter of urgency.

The good news is that now desktop environments are supported for the same length of time as server environments, so if you install a DE on 12.04LTS, it will be supported for as long as the server components are, until 2016 if memory serves me correctly.

---

### Post by snowpine on 2013-02-05
Warnings aside,

```
sudo apt-get install ubuntu-desktop

```

Now you have (unsupported) Ubuntu desktop.

---

### Post by JayKay3OOO on 2013-02-05
You don't need a graphical desktop, just install webmin and do all server tasks through a web interface including updating the system and re-booting it.

[http://www.webmin.com/download.html](http://www.webmin.com/download.html)

---

