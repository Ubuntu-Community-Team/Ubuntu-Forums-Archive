---
title: "[tor] Hidden Services, don't connect ?"
date: 2010-05-02
forum: Server Platforms
---

### Post by seba22 on 2010-05-02
Welcome,


Today i start installing server what i wan't put inside TOR network working as Hidden Service.

First on my Ubuntu 8.04 server machine i want enable http connection to my server. It's just for test.

I read documentation posted here 

[https://www.torproject.org/docs/tor-hidden-service.html.pl](https://www.torproject.org/docs/tor-hidden-service.html.pl)

and start configuration.

```
apt-get update
apt-get install tor

```
After successfully install of tor package, i created directory
called 

```
/var/lib/tor/hidden_service/

```

Next in file
```
nano /etc/tor/torrc 
```

added

```
HiddenServiceDir /var/lib/tor/hidden_service/
HiddenServicePort 80 127.0.0.1:80
```

Next i rebooted my VM

And notice that directory 

```
ls
/var/lib/tor/hidden_service# 
```


Stay empty, don't create key and hostname.

When i'm runing tor by hand


```
/etc/init.d/tor start
Raising maximum number of filedescriptors (ulimit -n) to 32768.
Starting tor daemon: tor...
May 02 12:58:14.992 [notice] Tor v0.2.1.25. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
May 02 12:58:14.998 [notice] Initialized libevent version 1.3e using method epoll. Good.
May 02 12:58:14.999 [notice] Opening Socks listener on 127.0.0.1:9050
done.

```

I don't see any errors here.

Anyone have idea what goes wrong ?

---

### Post by seba22 on 2010-05-02
I created folder under root, and it should be owned by debian-tor.

Solution

```
"chown debian-tor /var/lib/tor/hidden_service/"
```

---

### Post by riptool on 2011-04-19
/var/lib/tor/hidden_service/ <<---Your directory has to be browsable by your webserver.

Meaning either change apache to default to that directory or just put your hidden service in the default apache dir of /var/www/

I know this is a year old but it might help others.

Tor chowns your hidden web directory on every restart of tor to tor-data. So you might have to chown to your username, install and configure everything without tor. Then restart tor.  Becasue once tor starts only tor-data has access to that hidden directory. Cant FTP, or SSH files to it at all.

---

