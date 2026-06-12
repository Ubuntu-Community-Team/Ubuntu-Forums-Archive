---
title: "Problem with JACK"
date: 2015-02-23
forum: Ubuntu Studio
---

### Post by thorvi2008 on 2015-02-23
[SIZE=2][FONT=arial]I have a problem with setting up jack. If I use ALSA, sound works without any problems, but I need JACK running for Qtractor.
Command "jack_control start" give me output:
[/FONT][/SIZE]
[FONT=lucida console]dbus.exceptions.DBusException: org/freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-ufhqzZlgfn: Connection refused
[FONT=arial]
And if I try to run jack from qjackctl I get:
[/FONT][/FONT][FONT=lucida sans unicode][FONT=lucida console]
Could not connect to JACK server as client - Overall operation failed - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
Jack server is not running or cannot be started
[FONT=arial]
Could anybody help me with it, please?[/FONT]
[/FONT][/FONT]

---

### Post by marseille2 on 2015-02-23
I would first check to see what jackd is doing... just in case it's already running.  

```
 $ ps aux | grep jackd
```

If it's not a matter of just turning it on, and/or [loading jack-sink pulseaudio modules]("http://ubuntuforums.org/showthread.php?t=2266159&p=13232072#post13232072") ... then you might need to kill jackdbus and jackd... and maybe do a reset. (See this [post]("http://ubuntuforums.org/showthread.php?t=2265205&p=13228748#post13228748").)

---

### Post by thorvi2008 on 2015-02-23
Thanks a lot! :D
Turned out I didn't compile Jack with alsa enabled. After re-compiling everything works perfectly!

---

