---
title: "Active Internet Processes"
date: 2010-09-13
forum: Security
---

### Post by mr-woof on 2010-09-13
Evening all,

just been looking on my system (10.04) using net stat:

If I do, netstat -l -p, i'm getting this:

roto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:31416                 *:*                     LISTEN      -               
tcp        0      0 localhost:smtp          *:*                     LISTEN      -               
tcp6       0      0 localhost:smtp          [::]:*                  LISTEN      -               
udp        0      0 *:bootpc                *:*                                 -               
udp        0      0 *:mdns                  *:*                                 -               
udp        0      0 *:46875                 *:*                                 -  

I know that boinc is on 31416, smtp etc. But what is 46875 at the bottom? It seems to change to a random port on reboot, which worries me. Is that normal?

Why is SMTP listening as well? I haven't installed any email servers, or is it just a normal Linux running process?

---

### Post by BkkBonanza on 2010-09-13
Redo the command as, **sudo netstat -lnp** (sudo required to show process info). You'll see which program is using the socket. Some like Skype will jump around as they are connected to different peers. That one in question isn't listening - so it's just an active connection. Probably Firefox since you're on this web site (assuming same machine).

SMTP isn't default. It means you have an email MTA (for sending email). It shouldn't be there unless you installed some mail server.

---

### Post by bodhi.zazen on 2010-09-14
lsof is also nice =)

```
sudo lsof -i -P -n
```

---

### Post by mr-woof on 2010-09-14
ah cheers guys :)

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:31416           0.0.0.0:*               LISTEN      1139/boinc      
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      1557/exim4      
tcp6       0      0 ::1:25                  :::*                    LISTEN      1557/exim4      
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1080/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           912/avahi-daemon: r
udp        0      0 0.0.0.0:46875           0.0.0.0:*                           912/avahi-daemon: r

I also thought the same about the smtp, does anything include exim4 in the it's install? The avahi-daemon is ok to leave running?

---

### Post by bodhi.zazen on 2010-09-14
> **mr-woof said:**
> ah cheers guys :)

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:31416           0.0.0.0:*               LISTEN      1139/boinc      
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      1557/exim4      
tcp6       0      0 ::1:25                  :::*                    LISTEN      1557/exim4      
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1080/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           912/avahi-daemon: r
udp        0      0 0.0.0.0:46875           0.0.0.0:*                           912/avahi-daemon: r

I also thought the same about the smtp, does anything include exim4 in the it's install? The avahi-daemon is ok to leave running?

The avahi daemon is IMO useless and IMO it is a shame it is included by default. Unless you use it, I would disable it.

It is not considered a security risk.

[ZeroConfPolicySpec - Ubuntu Wiki]("https://wiki.ubuntu.com/ZeroConfPolicySpec") 

[SecurityConsiderations – Avahi]("http://avahi.org/wiki/SecurityConsiderations")

---

### Post by mr-woof on 2010-09-14
Cool, I've removed exim4 as well. I've no idea how it was installed :)

I'm going to have a look now on how to disable the avahi daemon

---

### Post by bodhi.zazen on 2010-09-14
> **mr-woof said:**
> Cool, I've removed exim4 as well. I've no idea how it was installed :)

I'm going to have a look now on how to disable the avahi daemon

there are several ways to do that, edit the init script (in /etc/init) . Comment out the start lines or have it start on only some run levels or stop it on all run levels, you get the idea.

---

### Post by mr-woof on 2010-09-14
Thanks again Bodhi, I edited the /etc/init/avahi-deamon.conf and commented out all the lines :) So I've all got running now is:

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:8118          0.0.0.0:*               LISTEN      2127/privoxy    
tcp        0      0 0.0.0.0:31416           0.0.0.0:*               LISTEN      1120/boinc      
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1504/dhclient  

A lot tidier :)

---

### Post by bodhi.zazen on 2010-09-14
Sweet =)

---

