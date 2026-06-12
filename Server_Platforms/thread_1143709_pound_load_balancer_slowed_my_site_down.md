---
title: "pound load balancer slowed my site down"
date: 2009-04-30
forum: Server Platforms
---

### Post by bluethundr on 2009-04-30
guys,

 My site was setup under a Verizon FiOS static IP. It absolutely FLEW when it first launched. 

 Then I was asked to setup a second web server and load balance the two. Someone recommended using pound for this, and I got it setup rather easily.

 But the problem is now the site is incredibly slow to load! Once it loads the site clicks through rapidly. But the initial load times are terrible. 

 If I take pound out of the equation and point the firewall to one of the web servers instead of the pound load balancer it speeds right back up. Change again back to pound and it slows right down.

 Suggestions?

 Here is my config file:

```

## Minimal sample pound.cfg
##
## see pound(8) for details


######################################################################
## global options:

User            "www-data"
Group           "www-data"
#RootJail       "/chroot/pound"

## Logging: (goes to syslog by default)
##      0       no logging
##      1       normal
##      2       extended
##      3       Apache-style (common log format)
LogLevel        1

## check backend every X secs:
Alive           2

## use hardware-accelleration card supported by openssl(1):


######################################################################
## listen, redirect and ... to:

## redirect all requests on port 80 ("ListenHTTP") to the virtual IP address:
ListenHTTP
        Address 192.168.1.8
        Port    8080
End

Service

        BackEnd
                Address 192.168.1.5
                Port    8080
        End
        BackEnd
                Address 192.168.1.6
                Port 8080
        End
        Session
                Type IP
                TTL  300
        END
End

```

And I keep getting this error in my syslog:

```

Apr 30 06:24:50 DNS pound: (b7b3fb90) connect_nb: error after getsockopt: Connection refused

```


:confused::confused::confused:
          :frown:

---

### Post by Kareeser on 2009-04-30
From your statement that it's slow at first load, then flies after the connection is made, it sounds like there's some sort of timeout between when the incoming connection is received, to when it selects which server to serve the data.

1. Check both servers' logs, are both servers serving data?
2. Check the port used by the load balancing program for pinging (or something similar) the servers, make sure that port is open.

---

### Post by bluethundr on 2009-04-30
It actually turned out to be an internal DNS issue. I fixed resolv.conf on the DNS server and the site sprang to life!
:guitar:

Thanks for playing!

:lolflag:

---

