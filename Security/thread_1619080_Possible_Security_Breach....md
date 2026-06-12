---
title: "Possible Security Breach?..."
date: 2010-11-11
forum: Security
---

### Post by VcDeveloper on 2010-11-11
My kvm network looks like this:

Ubuntu 10.10 Desktop Server w/qemu-kvm (main server) 192.168.1.65
----------| Ubuntu 10.10 Desktop Server - As my Router (HTTP forward to **Web server**) 192.168.1.70
----------| Ubuntu 9.10 Desktop Server - Web 192.168.1.71
----------| Ubuntu 10.10 Desktop Server - MySql 192.168.1.72
----------| Ubuntu 10.10 Desktop Server - Postfix 192.168.1.73

I checked all my server logs and these entries are only in my **web server** auth.log:
```
Nov  8 07:35:09 *** sudo:     root : TTY=unknown ; PWD=/ ; USER=*** ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Nov  8 07:35:09 *** sudo:     root : TTY=unknown ; PWD=/ ; USER=*** ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Nov  8 07:35:09 *** sudo:     root : TTY=unknown ; PWD=/ ; USER=*** ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port

```I'm in bed sleeping at this time, so I no I didn't do this and the only one here!  I only use **GuideDog** to **Forward** HTTP to my **Web Server** and my **2Wire Router** only allows HTTP/HTTPS to my **Router Server**.

So how is this command being executed?  Its been doing these every since Monday and always at the same time.  I'm looking over my previous logs to try to see it I did something wrong.

---

### Post by CharlesA on 2010-11-11
Looks like it was having a proxy configured, the command was "gconftool"

Run it to see what it does, or if it even exists.

Check yer user's history and see if those commands are listed.

---

### Post by Grenage on 2010-11-11
Could it be the update notifier/checker?

---

### Post by VcDeveloper on 2010-11-11
> **CharlesA said:**
> Looks like it was having a proxy configured, the command was "gconftool"

Run it to see what it does, or if it even exists.

Check yer user's history and see if those commands are listed.

These are the only entries since Monday:
```

Nov  8 09:04:50 anointed pulseaudio[1392]: ratelimit.c: 1 events suppressed
Nov  8 "same as above"....

Nov 10 15:33:30 anointed os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/vda2
Nov 10 15:33:31 anointed 50mounted-tests: debug: /dev/vda2 type not recognised; skipping
Nov 10 15:33:31 anointed os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Nov 10 15:33:31 anointed os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/vda5
Nov 10 15:33:31 anointed 50mounted-tests: debug: /dev/vda5 is a swap partition; skipping
Nov 10 15:33:31 anointed os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Nov 10 15:35:36 anointed os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/vda2
Nov 10 15:35:36 anointed 50mounted-tests: debug: /dev/vda2 type not recognised; skipping
Nov 10 15:35:36 anointed os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Nov 10 15:35:36 anointed os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/vda5
Nov 10 15:35:36 anointed 50mounted-tests: debug: /dev/vda5 is a swap partition; skipping
Nov 10 15:35:36 anointed os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Nov 10 17:55:44 anointed pulseaudio[1411]: ratelimit.c: 1 events suppressed
Nov 10 17:55:49 anointed pulseaudio[1411]: ratelimit.c: 1 events suppressed

```

and that's it...., I don't have a proxy server running, just a simple network..., does the 9.10 (karmic) run this gconftool different than 10.10 (maveric), because I don't see this type of entry when I get the **Update Manger** notification.

In fact, I have received updates today to all the 10.10 servers accept the 9.10.  So could it be the updater as mention?

---

### Post by CharlesA on 2010-11-11
It should be the same tool. It's a config editor for Gnome as far as I can tell.

If you are worried that the machine was compromised, I'd say wipe the box and reinstall.

---

### Post by shadow120 on 2010-11-11
it looks like someone set up a proxy.  run sudo netstat -plntu  to see what ports are open and whats running on them.  if anything is out of the ordinary then i would say its compromised.

---

### Post by FuturePilot on 2010-11-11
There's nothing to worry about. [http://ubuntuforums.org/showpost.php?p=8742995&postcount=5]("http://ubuntuforums.org/showpost.php?p=8742995&postcount=5")

---

### Post by VcDeveloper on 2010-11-11
> **FuturePilot said:**
> There's nothing to worry about. [http://ubuntuforums.org/showpost.php?p=8742995&postcount=5](http://ubuntuforums.org/showpost.php?p=8742995&postcount=5)

This is what I get and it looks normal:
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:139           0.0.0.0:*               LISTEN      982/smbd        
tcp        0      0 192.168.1.71:139        0.0.0.0:*               LISTEN      982/smbd        
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1144/apache2    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1026/cupsd      
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      1144/apache2    
tcp        0      0 127.0.0.1:445           0.0.0.0:*               LISTEN      982/smbd        
tcp        0      0 192.168.1.71:445        0.0.0.0:*               LISTEN      982/smbd        
tcp6       0      0 ::1:631                 :::*                    LISTEN      1026/cupsd      
udp        0      0 0.0.0.0:37082           0.0.0.0:*                           615/avahi-daemon: r
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           615/avahi-daemon: r
udp        0      0 192.168.1.71:137        0.0.0.0:*                           978/nmbd        
udp        0      0 0.0.0.0:137             0.0.0.0:*                           978/nmbd        
udp        0      0 192.168.1.71:138        0.0.0.0:*                           978/nmbd        
udp        0      0 0.0.0.0:138             0.0.0.0:*                           978/nmbd
```> **shadow120 said:**
> it looks like someone set up a proxy.  run sudo netstat -plntu  to see what ports are open and whats running on them.  if anything is out of the ordinary then i would say its compromised.

Whew! Thanks!.....  I'm happy I don't have to scrape this **kvm**!

THANKS EVERYONE FOR YOUR RESPONSES!  I APPRECIATE YOUR HELP!...

---

