---
title: "Tor Relay Error Message"
date: 2009-04-15
forum: Security
---

### Post by yeehi on 2009-04-15
I set up OperaTor successfully, I believe.
I would like to set up a Tor relay; however, I get the following error message when I use Vidalia to check if Tor is running:


Apr 15 22:26:46.979 [Notice] Tor v0.2.0.34 (r18423). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Apr 15 22:26:46.980 [Notice] Initialized libevent version 1.3e using method epoll. Good.
Apr 15 22:26:46.980 [Notice] Opening Socks listener on 127.0.0.1:9050
Apr 15 22:26:46.980 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Apr 15 22:26:46.980 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Apr 15 22:26:46.980 [Error] Reading config failed--see warnings above.
Apr 15 22:29:37.574 [Notice] Tor v0.2.0.34 (r18423). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Apr 15 22:29:37.574 [Notice] Initialized libevent version 1.3e using method epoll. Good.
Apr 15 22:29:37.574 [Notice] Opening Socks listener on 127.0.0.1:9050
Apr 15 22:29:37.574 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Apr 15 22:29:37.574 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Apr 15 22:29:37.574 [Error] Reading config failed--see warnings above.

---

### Post by prometheus442 on 2009-05-22
I'm actually having the same problem. Sorry I can't really help.

May 22 12:44:38.294 [Notice] Tor v0.2.0.34 (r18423). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
May 22 12:44:38.295 [Notice] Initialized libevent version 1.3e using method epoll. Good.
May 22 12:44:38.295 [Notice] Opening Socks listener on 127.0.0.1:9050
May 22 12:44:38.295 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
May 22 12:44:38.296 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
May 22 12:44:38.296 [Error] Reading config failed--see warnings above.

---

### Post by prometheus442 on 2009-05-23
Seriously. Can anyone help?

---

### Post by cometa2k7 on 2010-03-18
I have the same issues. Can anybody help?

---

### Post by ApEkV2 on 2010-03-18
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
*scroll over the X's and "unselect" them with the spacebar*
```

EDIT: i don't know how you have your tor setup, I had this problem just a day ago when I installed tor, and then installed vidalia to manage it.
If you want to use vidalia with tor, you need to make sure tor doesn't automatically start at computer's startup, sysv-rc-conf allows you to turn it off.

---

### Post by Falc7 on 2010-04-18
This helped me :)

---

### Post by UbNoob3 on 2010-06-06
> **ApEkV2 said:**
> If you installed tor, and then installed vidalia, you have to go into sysv-rc-conf (the command line) scroll down and unselect all the tor startup levels.
Vidalia automatically starts tor, so if tor is already running, there will be problems. Solution.....first you need to turn off tor....

```
*Turn off tor...*

pidof tor
sudo kill <the pid of tor>

*Install sysv-rc-conf...*

sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf

*scroll down with the arrow keys (alphabetical order) should look like...*
[COLOR=red]tor          [ ]        [X]         [X]         [X]        [X]        [ ]        [ ][/COLOR]
*scroll over the X's and "unselect" them with the spacebar*
```EDIT: i don't know how you have your tor setup, I had this problem just a day ago when I installed tor, and then installed vidalia to manage it.
If you want to use vidalia with tor, you need to make sure tor doesn't automatically start at computer's startup, sysv-rc-conf allows you to turn it off.
This also worked for me. Thanks very much ApEkV2 :)

---

### Post by PDA1 on 2010-06-15
That worked for me too.  The only problem is I get the following error message from FireFox-  Firefox is configured to use a proxy server that is refusing connections.   How do I fix that?

---

### Post by TiloBunt on 2010-11-03
Hi, 

ApEkV2 notes helped me as well. 

To get sysv-rc-conf you might need to install it first
```
sudo apt-get install sysv-rc-conf
```

then run it like 

```
sudo sysv-rc-conf
```

Remove all X in the tor like (online in the tor line to be like this)

```
tor         [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]
```

Just need to do it again. use the space bar to remove the X and "q" to exit the GUI. (no need to save)

---

