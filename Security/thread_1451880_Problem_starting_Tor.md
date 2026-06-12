---
title: "Problem starting Tor"
date: 2010-04-11
forum: Security
---

### Post by infornography on 2010-04-11
I am trying to use the torbutton Firefox extention on xubuntu 9.10. I had it working when I first installed it, but now I can't get tor to start properly. When I try to run it using Vidalia I get the following error message:

Apr 11 17:24:12.335 [Notice] Tor v0.2.1.25. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Apr 11 17:24:12.337 [Notice] Initialized libevent version 1.4.11-stable using method epoll. Good.
Apr 11 17:24:12.337 [Notice] Opening Socks listener on 127.0.0.1:9050
Apr 11 17:24:12.337 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Apr 11 17:24:12.337 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Apr 11 17:24:12.338 [Error] Reading config failed--see warnings above.

I have no idea why it would work only the first time and not others, can anybody help with this?

Thanks in advance.

---

### Post by ApEkV2 on 2010-04-11
If you installed tor, and then installed vidalia, you have to go into sysv-rc-conf (the command line) scroll down and unselect all the tor startup levels.
Vidalia automatically starts tor, so if tor is already running, there will be problems. Solution.....first you need to turn off tor....

```
*Turn off tor...*

pidof tor
sudo kill <the pid of tor>

*Install sysv-rc-conf...*

sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf

*scroll down with the arrow keys (alphabetical order) should look like...*
[color=red]tor          [ ]        [X]         [X]         [X]        [X]        [ ]        [ ][/color]
*scroll over the X's for tor and "unselect" them with the spacebar*
```

If you want to use vidalia with tor, you need to make sure tor doesn't automatically start at computer's startup, sysv-rc-conf allows you to turn it off.

btw this is the third post about this problem in the past 30 days, doing a quick search wouldn't hurt

---

