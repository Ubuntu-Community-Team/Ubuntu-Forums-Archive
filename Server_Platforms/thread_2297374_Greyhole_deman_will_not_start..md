---
title: "Greyhole deman will not start."
date: 2015-10-03
forum: Server Platforms
---

### Post by declan4 on 2015-10-03
When I ask for status from greyhole I get:
```
$ sudo service greyhole status
greyhole stop/waiting

```
Then if I try to start the demon I get
```

$ sudo greyhole -D
Found an already running Greyhole daemon with PID .
Can't start multiple Greyhole daemons.
Quitting.

```
The pid file does not exist. I checked and the log file looks like:
```
$      sudo greyhole -LOct 03 08:45:47 WARN daemon: PHP Warning [2]: file_get_contents(/var/run/greyhole.pid): failed to open stream: No such file or directory in /usr/bin/greyhole on line 3242; BT: greyhole[L3273] run() => greyhole[L3242] file_get_contents(/var/run/greyhole.pid)

```

Could sure use some help here.
/Dec

---

### Post by gboudreau on 2015-10-03
- Check in /var/log/greyhole.log and /var/log/greyhole.err if you see anything, when you try to start the daemon.
- Make sure you're running the latest version: ```
apt-get install greyhole
```
- Greyhole uses this command to check if there is already another running daemon; try to run this manually, see what it shows:
```
ps ax | grep "greyhole --daemon\|greyhole -D" | grep -v grep
```

---

### Post by declan4 on 2015-10-04
That was it, I Had not installed the latest greyhole. Now the deamon is running.
Thank you very much for support,
/Dec

---

