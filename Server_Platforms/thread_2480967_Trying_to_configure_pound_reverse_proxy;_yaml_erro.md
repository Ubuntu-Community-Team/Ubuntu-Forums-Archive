---
title: "Trying to configure pound reverse proxy; yaml errors"
date: 2022-11-15
forum: Server Platforms
---

### Post by pqwoerituytrueiwoq on 2022-11-15
So i look at the documentation:
[https://manpages.debian.org/experimental/pound/pound.8.en.html](https://manpages.debian.org/experimental/pound/pound.8.en.html) (ctrl+f search: [FONT=Courier New]_URL: "_[/FONT])

```

## Minimal sample configuration
##
## see pound(8) for details

## NOTE: pound currently only seems to work with non-loopback
## addresses. This sample therefore will not work until adapted.

Global:
  User:         "_pound"
  Group:        "_pound"
  #RootJail     "/chroot/pound"

Backends:
  - &be
    Address: 10.0.0.69
    Port: 80

# This section must exist, but may be empty.
HTTPListeners:

# This section must exist, but may be empty.
HTTPSListeners:
  - Address: 10.0.0.69
    Port: 443
    Services:
      - URL: ".*.(gif|jpg|png)"
      Backends:
        - *be
    Certificates:
      - "/etc/pound/pound.pem"

```
and this is the result:
```

$ sudo systemctl start pound.service; if [ $?0 -ne 0 ];then systemctl --no-pager -l status pound.service ;fi
Job for pound.service failed because the control process exited with error code.
See "systemctl status pound.service" and "journalctl -xeu pound.service" for details.
× pound.service - LSB: reverse proxy and load balancer
     Loaded: loaded (/etc/init.d/pound; generated)
     Active: failed (Result: exit-code) since Tue 2022-11-15 14:53:14 UTC; 23ms ago
       Docs: man:systemd-sysv-generator(8)
    Process: 56561 ExecStart=/etc/init.d/pound start (code=exited, status=1/FAILURE)
        CPU: 17ms

Nov 15 14:53:14 niceserver systemd[1]: Starting LSB: reverse proxy and load balancer...
Nov 15 14:53:14 niceserver pound[56566]: Can't load configuration - YAML error "did not find expected '-' indicator" at line 26
Nov 15 14:53:14 niceserver pound[56561]:  * Failed to validate config file, refusing to start
Nov 15 14:53:14 niceserver pound[56561]:  * Starting reverse proxy and load balancer pound
Nov 15 14:53:14 niceserver pound[56567]: Can't load configuration - YAML error "did not find expected '-' indicator" at line 26
Nov 15 14:53:14 niceserver systemd[1]: pound.service: Control process exited, code=exited, status=1/FAILURE
Nov 15 14:53:14 niceserver systemd[1]: pound.service: Failed with result 'exit-code'.
Nov 15 14:53:14 niceserver systemd[1]: Failed to start LSB: reverse proxy and load balancer.

```

---

### Post by TheFu on 2022-11-15
I used pound as an SSL termination reverse proxy for a few years, then something broke. I wasn't able to figure it out, but I switched to using nginx for that purpose and never looked back.  That must be at least 10 yrs ago.   Plus, there's a bonus in that nginx is popular enough for Let's Encrypt cert renewals to understand the nginx config files and modify those.

Line 26 has this:
      - URL: ".*.(gif|jpg|png)"
Is that correct?

I'd run the config file through a YAML validator as a first step.

---

### Post by pqwoerituytrueiwoq on 2022-11-15
yep it is
yalmlint said the same error, so i copy/paste the example into it and it looks different than on the web page... and that is valid that way

```
Backends: 
  - 
    Address: "10.1.1.100"
    Port: 80
    Threads: 16
  - 
    Address: "10.1.1.101"
    Port: 80
    Threads: 16
HTTPListeners: 
  - 
    Address: "123.1.2.3"
    Port: 80
    Services: 
      - 
        Backends: 
          - 
            Address: "10.1.1.101"
            Port: 80
            Threads: 16
        URL: .*.(gif|jpg|png)
      - 
        Backends: 
          - 
            Address: "10.1.1.100"
            Port: 80
            Threads: 16
        Session: 300
    Threads: 32
HTTPSListeners:

```

i also just got HTTPS setup in apache2 doing what i wanted to do... not as viable for routing to other systems, but not what i am using that for right now...

the only thing i want https for is accessing my stuff remotly, http is good on my lan, but on wan i want https

in the process of migrating my rpi stuff to a full x86 server and i was using pound on my pi

---

