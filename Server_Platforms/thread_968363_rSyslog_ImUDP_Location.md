---
title: "rSyslog ImUDP Location"
date: 2008-11-02
forum: Server Platforms
---

### Post by mattofak on 2008-11-02
Hey All;

I'm currently attempting to setup rSyslog on a research server and was hoping to use it as an aggregation server for logs. My intent is to have the logs transmitted to my server via UDP.

My first inclination was to just add the -r option to the /etc/init.d/rsyslog script, but further research shows that the -r option is depreciated. (And adding the -r option didn't work in any case)

Second was to add the following lines to my rSyslog conf file
$modload imudp
$InputUDPServerRun 514

rSyslog then proceeds to complain because it cannot find the module: imudp.so. And hence my problem, because neither can I! Where did canonical hide the rSyslog modules? Or at the very least, how do I tell rSyslog to listen on UDP:514?

Thanks!
Matt Walker

---

### Post by d1zzy on 2009-01-18
It depends on which version of Ubuntu you've got installed. I have an Intrepid installation which includes the imudp.so, and a Hardy install which only has the immysql, so I'm guessing you're on <=Hardy?

I had the same problem, so I tried adding the -r option to /etc/init.d/rsyslog, which didn't work. Whenever I did

```
ps -Aeo pid,args | grep log
```

it showed that the arguments in the startup script weren't carry through to the running executable - a really opaque problem!

At the time I got round it by modifying the startup script so as not to use start-stop-daemon. However I just saw [this]("http://wiki.rsyslog.com/index.php/Ubuntu") which seems to be a better solution; I'll try it myself tomorrow.

---

### Post by mattofak on 2009-01-18
Thanks for the reply. I did eventually figure the problem out, and I suppose I should record the answer here for posterity:

For whatever reason Canonical decided that the default /etc/init.d/* location needed to be revamped. So they put the actual startup scripts in /etc/default/*.

Now how these scripts actually get called is beyond me, because there's no reference to them in any of the init.d scripts, but there we go. Just another brilliant move from a company that produces a distribution that wont let you do 'apt-get install gnome'.

---

