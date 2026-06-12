---
title: "Multiple web servers on same port"
date: 2015-10-30
forum: Server Platforms
---

### Post by pqwoerituytrueiwoq on 2015-10-30
I'm not quite sure how to word this so please bear with me
What i want to do is use the sub domain name to determine which server/port the request goes to from my public ip
right now my router sends port 80 to my desktop, what i want to do it have it send port 80 to me desktop when subdomainA is used but when subdomianB is used it send it to my rpi on port 82
so basically this
subdomainA.example.com:80 -> 10.0.0.25:82
subdomainB.example.com:80 -> 10.0.0.50:81
right now i am using multiple ports externally for each, but apparently from work i can't use anything but 80 and 443
within my local network i am using 9 virtualhost so it is a bit of a mess with how i have scrambled the external ports (not all are used externally)

What i have to work with is my DD-WRT router (atheros based) and my rPi model B, to my understanding i guess i have to use what is called a reverse proxy
i really don't want to run every file that is requested from my desktop through my pi then to my router to over the Internet (i mainly use this to avoid uploading files or emailing them when IMing)
i don't know if a reverse proxy would do that, but if it does i would expect it's I/O speed to bottleneck transfers, but my desktop is left is sleep mode alot, my router has lighttpd installed but no mod_proxy module

---

### Post by TheFu on 2015-10-30
You want a "reverse-proxy". There are many choices.
* nginx
* apache
* pound
* htproxy
* probably 10 others.
[http://blog.jdpfu.com/2011/08/18/readers-ask-about-reverse-proxy-servers](http://blog.jdpfu.com/2011/08/18/readers-ask-about-reverse-proxy-servers)

---

### Post by pqwoerituytrueiwoq on 2015-10-31
thanks, i managed to get pound up and running
the most annoying part was having to type reverse proxy into every google search
i used pound cause it is supposed to be light weight and a rPi model B is no power house
```
pi@raspberrypi:~$ cat /etc/pound/pound.cfg
## Minimal sample pound.cfg
##
## see pound(8) for details


######################################################################
## global options:

User        "www-data"
Group        "www-data"
#RootJail    "/chroot/pound"

## Logging: (goes to syslog by default)
##    0    no logging
##    1    normal
##    2    extended
##    3    Apache-style (common log format)
LogLevel    0

## check backend every X secs:
Alive        30

## use hardware-accelleration card supported by openssl(1):
#SSLEngine    "<hw>"

# poundctl control socket
Control "/var/run/pound/poundctl.socket"


######################################################################
## listen, redirect and ... to:

## redirect all requests on port 8080 ("ListenHTTP") to the local webserver (see "Service" below):
ListenHTTP
    Address 10.0.0.25
    Port    89

    ## allow PUT and DELETE also (by default only GET, POST and HEAD)?:
    xHTTP        0

    Service
        HeadRequire "Host: .*[snip].duckdns.org.*"
        BackEnd
            Address    127.0.0.1
            Port    82
        End
    End
    Service
        HeadRequire "Host: .*[snip].duckdns.org.*"
        BackEnd
            Address    10.0.0.50
            Port    81
        End
    End
End
ListenHTTPS
    Address 10.0.0.25
    Port    443
    Cert    "/etc/ssl/certs/ssl-cert-pound.pem"
    xHTTP    0
    Service
        URL         "^/([secret folder name]|icons).*"
         HeadRequire "Host: .*[snip].duckdns.org.*"
        BackEnd
            Address    127.0.0.1
            Port    81
        End
    End
End
pi@raspberrypi:~$
```

---

