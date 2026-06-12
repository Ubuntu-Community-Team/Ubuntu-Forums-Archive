---
title: "Ufw is Lying!"
date: 2010-10-01
forum: Server Platforms
---

### Post by Darth_tater on 2010-10-01
Hey all.  I am trying to set up an MPD and ICECast box and i have it all working, with one small problem.

ufw / iptables is not allowign me to connect to my mpd daemon.

I do get an error on mpd startup:

```



root@HOSTNAME/var/log/mpd# /etc/init.d/mpd start
 * Starting Music Player Daemon mpd                                                                                listen: bind to 127.0.0.1:6600 failed: Address already in use (continuing anyway, because at least one address is bound)
                                                                                                            [ OK ]


```

but i know mpd is up and running, because i can see it listening



```

root@HOSTNAME/var/log/mpd# netstat -apn|grep mpd
tcp        0      0 127.0.0.1:6600          0.0.0.0:*               LISTEN      31140/mpd
root@HOSTNAME/var/log/mpd#



```


But no matter how i try to connect, i keep getting connection refused errors.

SO What's preventing me from connecting?

Here is the output of ufw:

```


root@HOSTNAME/var/log/mpd# ufw status
Status: active

To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere
8000                       ALLOW       Anywhere
22/udp                     DENY        Anywhere
OpenSSH                    ALLOW       Anywhere
Anywhere                   ALLOW       XX.my.pc.here
1234                       ALLOW       Anywhere
6600                       ALLOW       Anywhere


```

Here is a bit more information for you:

```


root@HOSTNAME/var/log/mpd# nc 127.0.0.1 6600
OK MPD 0.15.0
^C


```

Netcat says that its up and running.  Lets see if we can be sure, though.

```

root@HOSTNAME/var/log/mpd# wget localhost:6600
--2010-10-01 11:49:12--  http://localhost:6600/
Resolving localhost... ::1, 127.0.0.1
Connecting to localhost|::1|:6600... failed: Connection refused.
Connecting to localhost|127.0.0.1|:6600... connected.
HTTP request sent, awaiting response... 200 No headers, assuming HTTP/0.9
Length: unspecified
Saving to: `index.html'

    [                                 <=>                                      ] 214         --.-K/s              ^C


```

now lets look at what's in index.html

```


root@HOSTNAME/var/log/mpd# vi index.html
OK MPD 0.15.0
ACK [5@0] {} unknown command "GET"
ACK [5@0] {} unknown command "User-Agent:"
ACK [5@0] {} unknown command "Accept:"
ACK [5@0] {} unknown command "Host:"
ACK [5@0] {} unknown command "Connection:"
OK


```


So what could be screwing with 127.0.0.1 getting its connections?


Thanks for your eyes / time / responses.

---

### Post by sh1ny on 2010-10-01
Actually you're connecting. Nothing to do with ufw, iptables.

---

### Post by Darth_tater on 2010-10-01
I've only tried to connect with mpd clients, and I keep getting connection refused errors and the like. I'll try net cat from a different computer to see what happens.

Thanks for the prompt response!

---

### Post by CharlesA on 2010-10-01
If net cat doesn't work, try nmap.

The port should be open.

---

### Post by Darth_tater on 2010-10-01
Nope.  Wget an NetCat both give me connection refused from a different machine.

This external machine can access a service running on port 8000 of the machine, though.

something is still in the way.

```


root@HOSTNAME:/home/bcr/ezstream# nmap -PN IPADDY

Starting Nmap 5.00 ( http://nmap.org ) at 2010-10-01 14:16 PDT
Interesting ports on IPADDY:
Not shown: 997 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
8000/tcp open  http-alt

Nmap done: 1 IP address (1 host up) scanned in 0.31 seconds



```

---

### Post by endotherm on 2010-10-01
> **Darth_tater said:**
> Nope.  Wget an NetCat both give me connection refused from a different machine.

This external machine can access a service running on port 8000 of the machine, though.

something is still in the way.

well, MPD should be a "filtered" protocol, so it can only be reached from localhost.

---

### Post by Darth_tater on 2010-10-01
> **endotherm said:**
> well, MPD should be a "filtered" protocol, so it can only be reached from localhost.

but shouldn't nmap on the *local* machine still get a result?  see my above post for the nmap result run on the *local* machine.  the results from the local machine the other 2 machines i used.

---

### Post by geoffmcc on 2010-10-01
To verify if this is a firewall issue you can simply ```
sudo ufw disable
``` and see if you have any issues.

If it does in fact turn out to be firewall use netstat to check for other tcp and udp ports that need to be opened.

Also, if it applies to you, have you forwarded the port on router?

---

### Post by Darth_tater on 2010-10-01
```


root@HOSTNAME/home/bcr/ezstream# /etc/init.d/mpd start
 * Starting Music Player Daemon mpd                                                                                listen: bind to 127.0.0.1:6600 failed: Address already in use (continuing anyway, because at least one address is bound)
                                                                                                            [ OK ]
																											
root@HOSTNAME/home/bcr/ezstream# netstat -apn | grep mpd
tcp        0      0 127.0.0.1:6600          0.0.0.0:*               LISTEN      31451/mpd


```


Yep, we're up!

```

root@HOSTNAME/home/bcr/ezstream# /etc/init.d/mpd stop
 * Stopping Music Player Daemon mpd                                                                         [ OK ]
root@HOSTNAME/home/bcr/ezstream# netstat -apn | grep mpd


```


Yep, wr're down!

```

root@HOSTNAME/home/bcr/ezstream# ufw disable
Firewall stopped and disabled on system startup

root@HOSTNAME/home/bcr/ezstream# /etc/init.d/mpd start
 * Starting Music Player Daemon mpd                                                                                listen: bind to 127.0.0.1:6600 failed: Address already in use (continuing anyway, because at least one address is bound)
                                                                                                            [ OK ]
root@HOSTNAME/home/bcr/ezstream# netstat -apn | grep mpd
tcp        0      0 127.0.0.1:6600          0.0.0.0:*               LISTEN      31647/mpd


```

ufw is disabled and we are up and running!  Lets see what's up!

```

root@HOSTNAME/home/bcr/ezstream# nmap -PN 127.0.0.1

Starting Nmap 5.00 ( http://nmap.org ) at 2010-10-01 15:35 PDT
Interesting ports on localhost (127.0.0.1):
Not shown: 997 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
8000/tcp open  http-alt

Nmap done: 1 IP address (1 host up) scanned in 0.30 seconds
root@HOSTNAME/home/bcr/ezstream# ufw status
Status: inactive


```


ufw is inactive, but we see nothing!

---

### Post by CharlesA on 2010-10-01
> **Darth_tater said:**
> but shouldn't nmap on the *local* machine still get a result?  see my above post for the nmap result run on the *local* machine.  the results from the local machine the other 2 machines i used.

Using nmap to scan the machine from itself is unreliable. It's best to run it from a different machine.

Anyway, it's listening on 127.0.0.1:6600, which is the loopback address, so it won't answer incoming connections that are not from the lo interface.

This is what it would look like if it's listening for external connections:

```

[COLOR="Blue"]tcp        0      0 127.0.0.1:6010          0.0.0.0:*               LISTEN[/COLOR]
[COLOR="Red"]tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN[/COLOR]

```

Red is external, Blue is localhost only.

---

### Post by Darth_tater on 2010-10-02
Thank you all!

I have figured out that there were a few issues, but now it is all working.

issue 1) the /etc/defaults/mpd file was not pointing to the correct config file.  this is why the daemon was trying to connect to the loopback multiple times.

while i still dont understand why 127.0.0.1 wouldn't have also worked, i set the daemon to listen to box's network IP and it works perfectly.

issues 2)  I do not know if ufw/iptables was in the way, ufw is disabled and it works.  I have not yet had the chance to switch ufw back on and retest.  


i am tethering to my phone right now, but when i get to a more stable connection, i will try enabling ufw and (if i remember) post back with the results.

---

### Post by Darth_tater on 2010-10-02
Well, it looks like i was able to enable ufw and still connect in remotely.

Thankyou all!

just to be clear: the solution was a combination of things: i needed to set mpd to listen on the correct interface.

---

