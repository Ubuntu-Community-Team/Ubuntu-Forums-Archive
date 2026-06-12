---
title: "having trouble invoking programs at startup?"
date: 2010-03-18
forum: Server Platforms
---

### Post by gobbledigook on 2010-03-18
Hi!

I have 9.10 and i have xbmc which i run as a media centre connected to my tv. to administer i ssh from my desktop.

At the moment everytime i reboot i have to login at the server box directly to start the things i want to :( here's how i do it at the moment:

login >
$startx (this opens a basic gui with fluxbox)
open a terminal >
$wine utorrent
$get_iplayer.cgi --port=1935 --getiplayer=/usr/bin/get_iplayer $
$xbmc

this starts starts basic gui, utorrent, starts an iplayer workaround to feed it into xbmc, starts xbmc.

sorry if i'm making this a bit basic and detailed but not really sure how to accomplish this in one script to use at startup? :)
i  have tried putting a few commands in /etc/init.d/local as per this [tutorial]("http://plope.com/Members/chrism/debian_rc_local_equiv")

my /etc/init.d/local looks like:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

vncserver :1
startx
xbmc
cd /home/server/
./get_iplayer.cgi --port=1935 --getiplayer=/usr/bin/get_iplayer

exit 0

```

any help would be greatly appreciated!! 

Thanx!

---

### Post by gobbledigook on 2010-03-19
*bump*

---

### Post by sv87411 on 2010-03-19
What you are trying probably won't work. 

The init.d script you have created will be run as root. I doubt XBMC will allow running as root and even if you did it is very risky. Try logging into your server as root and carefully running through your commands to see how it behaves.

You either need to setup autologin to your server which is risky or setup XBMC and the other things you require as daemons, but they may not perform as expected like this (see start-stop-daemon man pages) 

The manual process you are using now is, to me, the most sensible and secure approach. Why not setup a script that runs utorrent, iplayer and xbmc you can run once logged in and keep startx in the local script - assuming this works right now? This will speed things up and be safer.

---

### Post by sv87411 on 2010-03-19
> **gobbledigook said:**
> 
$wine utorrent


Oh, and if you are running a server and don't mind running apache/PHP then Torrentflux is a good web based interface Torrent client. Better than running a grotty (albeit not bad) Windows prog in my opinion ;)

---

### Post by gobbledigook on 2010-03-19
thanx for you help :)

i have got just xbmc to start by placing ```
exec xbmc
``` in  ~.xsession.

now i just need to startx and the other stuff manually... one down, 3 more to go!

> **sv87411 said:**
> Oh, and if you are running a server and don't mind running apache/PHP then Torrentflux is a good web based interface Torrent client. Better than running a grotty (albeit not bad) Windows prog in my opinion ;)

i would love to... but i'm a member of a private torrent group type thing, and they only support certain clients !!

---

### Post by gobbledigook on 2010-03-20
Grrr!!

now i can't start a vncserver session to wine utorrent!! 

Because i have put exec xbmc in ~.xsession, now when i start a vncserver session it tries to start xbmc as well! I prob should have seen this problem before... but i'm not great at this stuff :(

can i specify a different file to use?

---

