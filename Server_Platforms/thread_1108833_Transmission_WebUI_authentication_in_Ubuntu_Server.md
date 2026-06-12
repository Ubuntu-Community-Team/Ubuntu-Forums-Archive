---
title: "Transmission WebUI authentication in Ubuntu Server"
date: 2009-03-28
forum: Server Platforms
---

### Post by mha2908 on 2009-03-28
Hi, I'm running a headless Ubuntu Server, and finally I made a startscript which starts transmission-daemon on boot. This makes it possible to open the Transmission WebUI from any computer elsewhere. BUT: I can't make any authentication. This is my settings file (i think - grabbed from /home/myusername/.config/transmission-daemon/settings.json):

```
                                
{
    "blocklist-enabled": 0,
    "download-dir": "\/etc",
    "download-limit": 100,
    "download-limit-enabled": 0,
    "encryption": 1,
    "max-peers-global": 200,
    "peer-port": 51413,
    "pex-enabled": 1,
    "port-forwarding-enabled": 0,
    "rpc-access-control-list": "+127.0.0.1",
    "rpc-authentication-required": 1,
    "rpc-password": "mypassword",
    "rpc-port": 9091,
    "rpc-username": "myusername",
    "upload-limit": 100,
    "upload-limit-enabled": 0
}l

```

Is it the right settingsfile? I mean, the daemon is started on boot with this script:

```

#!/bin/sh.

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
NAME="Transmission"
DESC="torrent daemon"

case "$1" in
        start)
                echo -n "Starting $DESC: "
                transmission-daemon
                echo "$NAME."
                ;;
        stop)
                echo -n "Stopping $DESC: "
                killall transmission-daemon
                echo "$NAME."
                ;;
        *)
                N=/etc/init.d/$NAME
                echo "Usage: $N {start|stop}" >&2
                exit 1
                ;;
esac
exit 0

```

Where the hell does it get it's settings from? Just a thought: outside my home folder somewhere?

By the way - i'm NOT using lighttpd which i ran into in many guides about setting it up. I use Apache2 but I don't know if it makes much of a difference. Plz help me about this, and feel free to ask!

---

### Post by MrWES on 2009-03-28
Add your IP to your settings.json file

```
"rpc-whitelist": "127.0.0.1,192.168.1.121,192.168.1.100",
"rpc-whitelist-enabled": 1,

```

Change the IP's to meet your needs.


Bill

Here's my complete settings.json file

```
{
    "blocklist-enabled": 1,
    "download-dir": "\/media\/external\/Downloads",
    "download-limit": 100,
    "download-limit-enabled": 0,
    "encryption": 2,
    "lazy-bitfield-enabled": 1,
    "message-level": 2,
    "open-file-limit": 32,
    "peer-limit-global": 500,
    "peer-limit-per-torrent": 60,
    "peer-port": 51413,
    "peer-port-random-enabled": 0,
    "peer-port-random-high": 65535,
    "peer-port-random-low": 1024,
    "peer-socket-tos": 0,
    "pex-enabled": 1,
    "port-forwarding-enabled": 1,
    "preallocation": 1,
    "proxy": "",
    "proxy-auth-enabled": 0,
    "proxy-auth-password": "",
    "proxy-auth-username": "",
    "proxy-enabled": 0,
    "proxy-port": 80,
    "proxy-type": 0,
    "rpc-authentication-required": 0,
    "rpc-enabled": 1,
    "rpc-password": "",
    "rpc-port": 9091,
    "rpc-username": "",
    "rpc-whitelist": "127.0.0.1,192.168.1.121,192.168.1.100",
    "rpc-whitelist-enabled": 1,
    "upload-limit": 75,
    "upload-limit-enabled": 0,
    "upload-slots-per-torrent": 5
}

```

---

### Post by martinw89 on 2009-07-26
Hi mha2908,
I apologize for bringing back such an old thread, but this was quite a problem for me and I wanted other users to be aware of the way to fix this.

I installed the latest stable Transmission release on my Intrepid server from [kab's unofficial repository](http://forum.transmissionbt.com/viewtopic.php?f=13&t=5604).  I am not sure whether the default settings differ from the official package's settings, but it seems many users have the same problem with the official package.

Even though I had stopped the daemon before editing /etc/transmission-daemon/settings.json, the "rpc-authentication-required" setting ALWAYS reverted itself when starting the daemon back up.  This basically meant I could not disable authentication.  Other settings were keeping, so after some poking around I found the problem.  **transmission-daemon was being started with the --auth flag because of its options in /etc/default/transmission-daemon.**


[SIZE="4"]**To Fix:**[/SIZE]
[LIST=1]
[*]Edit "/etc/default/transmission-daemon".
[*]It has the following line:```
OPTIONS="--auth --config-dir $CONFIG_DIR"
```
[*]Change the line to:```
OPTIONS="--config-dir $CONFIG_DIR"
```
[/LIST]
Now, transmission-daemon will listen to settings.json for the "rpc-authentication-required" setting, instead of overwriting it.  Hope this helps! :D

---

### Post by lotus49 on 2009-08-07
> **martinw89 said:**
> Hi mha2908,
I apologize for bringing back such an old thread, but this was quite a problem for me and I wanted other users to be aware of the way to fix this.
[...]
Hope this helps! :D

Don't apologise, and it certainly did.  I have been struggling with this for 40 minutes and it was driving me bonkers.

Thanks for posting this I appreciate it.

---

### Post by Nick_NS on 2009-09-19
Yeah, no apologies required. This had been iritating me for a couple days now.

Thanks!

---

### Post by son9o on 2012-06-03
I realise the thread is at least 3 years old, but wanted to say thanks from 2012, I couldn't turn the authentication on, how irritating.

---

