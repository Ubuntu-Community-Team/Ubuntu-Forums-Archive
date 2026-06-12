---
title: "telnet to apache, connection drops"
date: 2011-04-14
forum: Server Platforms
---

### Post by felixnine on 2011-04-14
lucid up-to-date
apache 2.2.14-5ubuntu8.4
telnet 0.17-36build1

i'm trying to use telnet to connect to my local apache2 server:

```

andrew@octagon >> telnet localhost 80                                                                                                                   
Trying ::1...
Connected to localhost.
Escape character is '^]'.
POST /test/Connection closed by foreign host.

```

so i started typing my command (POST /test/), but the connection just drops after about 15 seconds. this doesn't happen with other remote servers i've tried. is it a server config issue?

---

### Post by Doug S on 2011-04-14
Just out of interest, I tried what you were doing with the same results.
It might be the keep alive timeout listed in the apache2.conf file in /etc/apache2 (I didn't try an experiment changing it, but would be interested in the results if you try it)
 
```

#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 15

```

---

### Post by felixnine on 2011-04-14
i'd read about that directive before, but didn't try it initially because apache is closing the connection *during* a request, not between them (though it is odd that it's set to 15 seconds as well).

in any case, no, that didn't fix it :(

thanks for the reply though.

---

### Post by SeijiSensei on 2011-04-14
It's a lot easier to test with GET:

```

telnet localhost 80
[stuff]
GET / HTTP/1.0
[hit the enter key again]

```

*Make sure you type Enter twice* as I did above.  If you have "name" virtual hosts, use:

```

GET / HTTP/1.1
Host: virtual.example.com


```

In order to POST, you have to send [special headers]("http://developers.sun.com/mobility/midp/ttips/HTTPPost/").

---

### Post by felixnine on 2011-04-14
thanks, but it's not really about the type of request, it's that my local apache server just drops the connection before i can enter the first line.

---

### Post by SeijiSensei on 2011-04-14
> **felixnine said:**
> in any case, no, that didn't fix it

Did you restart Apache after increasing the time out value?  Apache only reads its configuration files at startup.

---

### Post by felixnine on 2011-04-14
i did, yes. changed KeepAliveTimeout to 100.

```

andrew@octagon >> sudo apache2ctl restart                                                                                                               
andrew@octagon >> time telnet localhost 80                                                                                                              
Trying ::1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.
telnet localhost 80  0.01s user 0.00s system 0% cpu 13.009 total

```

this certainly isn't crucial, i'm just trying to wrap my head around it. it'd be nice to know how to fix it if it comes up again.

---

### Post by Doug S on 2011-04-14
I went to my old ubuntu 6.? server and had 5 minutes before the telent session was closed by the host. However, it closed immediately after a "GET"
 
Back on the new server, I found the file /etc/apache2/mods-available/reqtimeout.conf
I modified the numbers, just to see if that was indeed the source. It was. I did not read much, but it appears to me as though at least one of it purposes is to prevent exactly what you are trying to do (i.e. typing requestes directly).
 
I changed these:
```
 
RequestReadTimeout header=10-20,minrate=500
RequestReadTimeout body=10,minrate=500

```to these:
```
 
RequestReadTimeout header=100-200,minrate=1
RequestReadTimeout body=100,minrate=1

```
Of course followed by:
```
 
sudo /etc/init.d/apache2 restart


```
Note: I had noticed the timeout wasn't exactly 15 seconds at first. I think it was always 10 plus some overhead. Now it is 100 plus the same overhead.
Anyway, I am changing things back now, as I really do not want to mess with this stuff.
I think you could also not even load this module by removing the links from /etc/apache2/mods-enabled.

---

### Post by felixnine on 2011-04-14
oh, neat! thanks for doing some digging. but now i wonder why that's not the case on the remote server i tried it on. perhaps an older version without the module, or something.

---

