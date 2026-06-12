---
title: "I'm looking for 7.10 server docs (new to Ubuntu)"
date: 2008-02-25
forum: Server Platforms
---

### Post by djtopper on 2008-02-25
I'm new to Ubuntu, have installed it on a few machines (Desktop edition) and have just recently decided to test it out as a replacement for an old Slackware based server.

I'm a bit in the dark though.  The server edition doesn't install a desktop GUI or anything like that, so getting things running / seeing what's installed is currently a challenge.

Are there any good docs on how to get a 7.10 Ubuntu Server Edition up and running?

Thanks,

DT

---

### Post by jken146 on 2008-02-25
[http://doc.ubuntu.com/ubuntu/serverguide/C/](http://doc.ubuntu.com/ubuntu/serverguide/C/)

---

### Post by faulkes on 2008-02-25
Please see the official and community documentation section in the following thread:

[http://ubuntuforums.org/showthread.php?t=702167](http://ubuntuforums.org/showthread.php?t=702167)

Thanks,

Faulkes

---

### Post by djtopper on 2008-02-27
Ok, thanks.  That's what I was looking for.

As a followup I'm curious to ask ... 

Why is there no X windows GUI installed by default on the server edition?  It would at the very least make reading all the docs much easier, no?

---

### Post by faulkes on 2008-02-27
> **djtopper said:**
> 
Why is there no X windows GUI installed by default on the server edition?  It would at the very least make reading all the docs much easier, no?

This issue was debated endlessy for quite some time.  The reasoning for not
having a GUI on the server, is that it is just that, a server and not typically
something a person sits at all day working on.  

Servers get put into closets, datacenters, under beds, whisked away by 
gnomes etc.. a GUI takes away resources (ram, cpu, etc.. etc..) from the 
server which it should otherwise be using for server based applications.

Faulkes

---

### Post by djtopper on 2008-02-27
That makes sense.  Unfortunately for me, it represents a hurdle.  Our network system uses a web based registration for each machine.  So the box I just installed Ubuntu on can't talk to the outside world.

Is there an easy way to get X installed / running similar to a Desktop flavor?  It sure would come in handy for new guys like me needing to read docs and configure machines at the same time.

Thanks,

DT

---

### Post by faulkes on 2008-02-27
> **djtopper said:**
> That makes sense.  Unfortunately for me, it represents a hurdle.  Our network system uses a web based registration for each machine.  So the box I just installed Ubuntu on can't talk to the outside world.

Is there an easy way to get X installed / running similar to a Desktop flavor?  It sure would come in handy for new guys like me needing to read docs and configure machines at the same time.

Thanks,

DT

```

sudo apt-get install ubuntu-desktop

```

Faulkes

---

### Post by sokraski on 2008-02-28
Take a look at webmin.  I learned a great deal with its help.  It does not configure anything for you, but gives you a GUI'ish server.  I use the file manager to edit files - I find it much easier than using vi commands.  I was also able to set up other services (monitoring, notifying, etc..) that I would have had no clue about.  The documentation tool is also great.

[http://www.webmin.com]("http://www.webmin.com")

---

### Post by jonabyte on 2008-02-29
> **faulkes said:**
>  whisked away by 
gnomes etc.. 


oooh where can I get a gnome to wisk my servers away...to far away place...:lolflag:

---

### Post by FakeOutdoorsman on 2008-02-29
> **djtopper said:**
> Is there an easy way to get X installed / running similar to a Desktop flavor?  It sure would come in handy for new guys like me needing to read docs and configure machines at the same time.

If you must install a graphical environment, you definitely won't need a heavyweight like Gnome.  Try just Openbox, or some other lighter alternative:
[URL="https://help.ubuntu.com/community/Installation/LowMemorySystems"]
Installation/Low Memory Systems[/URL] [Ubuntu Wiki]
[URL="http://urukrama.wordpress.com/openbox-guide/"]
Ubuntu Openbox guide[/URL]

General LAMP install info:
[Apache MySQL PHP]("https://help.ubuntu.com/community/ApacheMySQLPHP") [Ubuntu Wiki]

---

