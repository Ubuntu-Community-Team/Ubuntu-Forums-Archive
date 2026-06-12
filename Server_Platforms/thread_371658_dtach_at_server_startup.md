---
title: "dtach at server startup"
date: 2007-02-27
forum: Server Platforms
---

### Post by emil on 2007-02-27
Hi!

I'm using my server (6.10) as a headless machine in the closet and it is working very well. I've been looking into using it as a downloader for torrents and I've decided to use rTorrent which has most of the functions I need.

The problem is that I want to start rTorrent every time the server starts (I sometimes shutdown the server during sleeping hours, cramped living and disturbing fans etc). I've been playing around with putting something like this in /etc/rc.local :
```
su emil -c "screen -dmS torrents rtorrent"
```

This works and there is a screen session that I can connect to later on. The problem is that for some reason defined keys in rTorrent (like Ctrl-Q to quit or Ctrl-r to rehash) doesn't work when I start it in this mode. If I manually kill the screen session and then restart it the keys work...

So, I decided to try dtach instead. Added the following to my rc.local : 
```
su emil -c "dtach -n /tmp/rtorrent -e . rtorrent"
```

which means that dtach will start in detached mode (-n), use Ctrl+. as detach key (-e .), use the socket at /tmp/rtorrent and start the program rtorrent as user emil. 

But now nothing happens when I restart the server. The socket in /etc/rtorrent doesn't exist and the process is not running. If I run the command manually it starts rtorrent but it seems to disregard the -e . option. 

Is there a better way to start a detached process? Does anyone know why options sent to dtach are disregarded and why keys are not working when started via rc.local?

thanks

Emil

---

### Post by konsole on 2007-09-18
> **emil said:**
> Hi!

I'm using my server (6.10) as a headless machine in the closet and it is working very well. I've been looking into using it as a downloader for torrents and I've decided to use rTorrent which has most of the functions I need.

The problem is that I want to start rTorrent every time the server starts (I sometimes shutdown the server during sleeping hours, cramped living and disturbing fans etc). I've been playing around with putting something like this in /etc/rc.local : 

Yeah I've got a similar setup. Are you aware of this: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=438335](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=438335)

btw, i found that @reboot in cron works better than rc.local for rtorrent

---

