---
title: "Dansguardian + Squid + Webmin = Not Working"
date: 2011-03-22
forum: Server Platforms
---

### Post by Sternfan on 2011-03-22
Hi all,

I have a proxy server (squid-3) that I would like to setup Dansguardian to do additional web filtering.  

The system:
Ubuntu 10.10 - all updates as of today
Dansguardian - 2.10.1.1-2ubuntu0.1 (latest update)
Squid3 - latest update (not squid 2.7)
Webmin - 1.530 (all updates)
Webmin dansguardian module - 0.7.1

Ok - I have all of the above installed.  When I go to the DG module page in Webmin, I get the following:

[B]Warning - the version of DansGuardian you have is not supported by this Webmin module version
Webmin Module Version 0.7.1 supports DG version 2.10 (& 2.9)
Currently installed DG version [/B]

This obviously makes no sense, since I am running DG version 2.10.1...

Any help resolving this greatly appreciated.

Rob

PS.  I have squid installed, but not configured (still tinkering) - could this be the problem?  That squid needs to be running for DG to work?

---

### Post by jaimerosario on 2011-04-10
Dansguardian Module needs to be configured correctly.

Dansguardian Web Module defaults points dansguardian binary in /usr/bin/ where in Ubuntu is in /usr/sbin.

---

### Post by Sternfan on 2011-04-12
Thanks a bunch.  I knew it had to be something like that.

Rob

---

### Post by Rakeshvijayan on 2012-04-28
how you correct this ,friend I have the same problem I am not good in this topic .expecting your help soon

---

### Post by jaimerosario on 2012-05-02
Edit [FONT="Courier New"]**/etc/webmin/dansguardian/config**[/FONT] and match the following values:

```

binary_file=/usr/sbin/dansguardian
pid_file=/var/run/dansguardian.pid
start_cmd=/etc/init.d/dansguardian start
stop_cmd=/etc/init.d/dansguardian stop
restart_cmd=dansguardian -r
autoreload=1
autorestart=1
restart_type=1
log_path=/var/log/dansguardian
show_fixedlists=0
conf_dir=/etc/dansguardian
log_format=followDansGuardian
messages_path=followDansGuardian

```

---

### Post by marcelorider on 2012-06-05
thanks a bunch @jaimerosario

---

### Post by Rakeshvijayan on 2012-06-06
> **jaimerosario said:**
> Edit [FONT=Courier New]**/etc/webmin/dansguardian/config**[/FONT] and match the following values:

   Great help man , I need 1 more help from your side to resolve dansguardian 
please read this thread  [http://ubuntuforums.org/showthread.php?p=12003140&posted=1#post12003140](http://ubuntuforums.org/showthread.php?p=12003140&posted=1#post12003140)

---

