---
title: "mumble server not starting automatically"
date: 2012-05-08
forum: Server Platforms
---

### Post by mons00n on 2012-05-08
My Ubuntu 10.04 server's HDD finally died on me...so I'm upgrading the beast to 12.04 x64.  I got everything up and going, but now mumble-server is not starting on bootup.  I have to 'sudo /etc/init.d/mumble-server restart' before I can connect.  I've already done 'sudo dpkg-reconfigure mumble-server' and told it to start automatically...but it didn't help.

Any other ideas on why this may be or what I can do to change things?  Thanks!

---

### Post by jerome1232 on 2012-05-08
Anything interesting in /var/log/mumble-server/mumble-server.log ?

---

### Post by mons00n on 2012-05-08
> **jerome1232 said:**
> Anything interesting in /var/log/mumble-server/mumble-server.log ?

I cleared the log file, rebooted, and this is all that was in there:

```
<W>2012-05-07 23:47:16.120 Initializing settings from /etc/mumble-server.ini (basepath /etc)
<W>2012-05-07 23:47:16.121 OpenSSL: OpenSSL 1.0.1 14 Mar 2012
<W>2012-05-07 23:47:16.234 SSL: Adding recommended CA UTN-USERFirst-Client Authentication and Email
<W>2012-05-07 23:47:16.240 ServerDB: Openend SQLite database /var/lib/mumble-server/mumble-server.sqlite
<W>2012-05-07 23:47:16.246 DBus registration succeeded
<W>2012-05-07 23:47:16.253 MurmurIce: Endpoint "tcp -h 127.0.0.1 -p 6502" running
<W>2012-05-07 23:47:16.343 Murmur 1.2.3 (1.2.3-2ubuntu4) running on X11: Ubuntu 12.04 LTS: Booting servers
<W>2012-05-07 23:47:16.355 1 => Announcing server via bonjour
<W>2012-05-07 23:47:16.363 1 => Not registering server as public

```

I have a password set so I assume that's why it's not registering as public.  When connecting it just says "Connection refused".  After restarting mumble the logfile picks up with:


```
<W>2012-05-07 23:55:07.391 Initializing settings from /etc/mumble-server.ini (basepath /etc)
<W>2012-05-07 23:55:07.392 OpenSSL: OpenSSL 1.0.1 14 Mar 2012
<W>2012-05-07 23:55:07.441 SSL: Adding recommended CA UTN-USERFirst-Client Authentication and Email
<W>2012-05-07 23:55:07.442 ServerDB: Openend SQLite database /var/lib/mumble-server/mumble-server.sqlite
<W>2012-05-07 23:55:07.448 DBus registration succeeded
<W>2012-05-07 23:55:07.450 MurmurIce: Endpoint "tcp -h 127.0.0.1 -p 6502" running
<W>2012-05-07 23:55:07.483 Murmur 1.2.3 (1.2.3-2ubuntu4) running on X11: Ubuntu 12.04 LTS: Booting servers
<W>2012-05-07 23:55:07.489 1 => **Server listening on [::]:64738**
<W>2012-05-07 23:55:07.492 1 => Announcing server via bonjour
<W>2012-05-07 23:55:07.498 1 => Not registering server as public
```

Where the primary difference seems to be the bolded statement that the server is actually listening.  Any clue why it wouldn't be listening right from the get go?

---

### Post by mons00n on 2012-05-09
anyone have any ideas on this one?

---

### Post by papibe on 2012-05-13
Hi mons00n.

One possible solution, without having to deal with init scripts, is to use a root crontab, with the tag '@reboot'.
```
# m h  dom mon dow   command
@reboot  /path/to/script.sh
```

As a precaution, I'd add a few seconds wait before restarting the service:
```
!#/bin/bash
sleep 5
service mumble-server restart
```
Just a thought.
Regards.

---

### Post by mons00n on 2012-05-13
> **papibe said:**
> Hi mons00n.

One possible solution, without having to deal with init scripts, is to use a root crontab, with the tag '@reboot'.
```
# m h  dom mon dow   command
@reboot  /path/to/script.sh
```

As a precaution, I'd add a few seconds wait before restarting the service:
```
!#/bin/bash
sleep 5
service mumble-server restart
```
Just a thought.
Regards.

This worked beautifully thanks!!

---

### Post by randomlaughter on 2013-04-14
I was encountering a similar issue while trying to run mumble-server with only a loopback interface active. To resolve this I had to set the "host" field in the .ini file to "localhost" instead of leaving it blank. 

I suspect that this indicates murmurd was failing to start because it could not listen on my inactive ethernet interface. See whether changing the "host" field in your mumble-server.ini file to the correct external ip fixes the issue. (Might be necessary to move the starting of the server later in the start up sequence also.)

---

