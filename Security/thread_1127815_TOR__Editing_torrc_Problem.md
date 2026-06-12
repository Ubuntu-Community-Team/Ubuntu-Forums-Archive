---
title: "TOR : Editing torrc Problem"
date: 2009-04-16
forum: Security
---

### Post by yeehi on 2009-04-16
I get the following error while I am trying to set up a TOR relay:

```
Apr 17 02:48:05.930 [Notice] Initialized libevent version 1.3e using method epoll. Good.
Apr 17 02:48:05.930 [Notice] Opening OR listener on 0.0.0.0:9001
Apr 17 02:48:05.930 [Notice] Opening Directory listener on 0.0.0.0:9030
Apr 17 02:48:05.930 [Notice] Opening Socks listener on 127.0.0.1:9050
Apr 17 02:48:05.930 [Notice] Opening Control listener on 127.0.0.1:9051
Apr 17 02:48:20.393 [Notice] Guessed our IP address as x
Apr 17 02:48:34.630 [Notice] Tor has successfully opened a circuit. Looks like client functionality is working.
Apr 17 02:48:34.666 [Notice] Now checking whether ORPort x:9001 and DirPort x:9030 are reachable... (this may take up to 20 minutes -- look for log messages indicating success)
Apr 17 02:55:00.224 [Warning] Couldn't open "/home/x/.vidalia/torrc.tmp" (/home/x/.vidalia/torrc) for writing: Input/output error

```

I think it is because I have the wrong entry in the torrc file (below). What should I have, instead of this:


```
############### This section is just for location-hidden services ###

## Once you have configured a hidden service, you can look at the
## contents of the file ".../hidden_service/hostname" for the address
## to tell people.
##
## HiddenServicePort x y:z says to redirect requests on port x to the
## address y:z.

#HiddenServiceDir /var/lib/tor/hidden_service/
#HiddenServicePort x

HiddenServiceDir x
HiddenServicePort x

#HiddenServiceDir /var/lib/tor/other_hidden_service/
#HiddenServicePort x
#HiddenServicePort x

```


(I have used ¨x¨ in the above code to replace some details.)

---

### Post by riptool on 2011-04-19
Looks like "x" directory is in your home directory. Tor can only access root files and tor-data owned files. THus it can NOT access anything in your user directory. 

You can add a run as command to the torcc to make tor run as you. Thus giving tor access to your home directory.  Or just put your user directory to the default of /var/www/hiddenfoldhere

---

