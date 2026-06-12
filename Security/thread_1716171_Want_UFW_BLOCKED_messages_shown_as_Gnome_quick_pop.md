---
title: "Want UFW BLOCKED messages shown as Gnome quick popup message"
date: 2011-03-28
forum: Security
---

### Post by schwermie on 2011-03-28
I don't know what the info screen is called. We i connect my LAN adapter, i see a short popup message. 

I want to generate such a message when UFW drops a packet. Any ideas/suggestions?

Regards, Marco

---

### Post by oklokl on 2011-03-28
gnome-system-log
ufw log.. show..
[http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)
It is recommended


terminal
host -t SOA local
ISP DNS .loca

---

### Post by BkkBonanza on 2011-03-28
There isn't a built in way to do that that I'm aware of. But I thought your idea was interesting so I looked into it a bit and came up with a way to do it with a script, a named pipe and a ufw cfg change. I don't use UFW so haven't tested that but I did test it manually with some UFW log messages found on the net.

Here is how I did it:

**1.** Create a named pipe for ufw log messages, 

sudo mkfifo /var/log/ufw-msgs

**2.** Then add a line to **/etc/rsyslog.d/20-ufw.conf** just under the current top one,

:msg,contains,"[UFW " |/var/log/ufw-msgs

this feeds matching UFW log messages to the named pipe. You could adjust the pattern here to catch only very specific entries. You may need to SIGHUP rsyslogd to reload cfg - not sure.

**3.** Create a script to catch the msgs and send them to screen. 
```

#!/bin/bash

while true; do
while read line; do
  ip=($line);
  ip=${ip[12]};
  notify-send -t 2000 UFW "IP Blocked: ""${ip:4}"
done</var/log/ufw-msgs
done

```
Save this to a file named **/usr/local/ufw-msgs**
And then **sudo chmod 755 /usr/local/ufw-msgs** so it can execute.
This script runs in a loop reading the named pipe and sending the IP from log entries to the screen with notify-send.

**4.** Run the script as a daemon to test it out.

**usf-msgs&**
(note: & makes it spawn into background and to stop it **pkill ufw-msgs**)

Do something to make a matching log entry occur...

--- notes ---

You may want to add that to the /etc/rc.local file so it runs at boot. I found that when run as root the notify messages showed up differently at screen bottom-right not top-right. Not sure why but you may want to run as a user to make them come out at top-right. 

eg. **sudo -u username /usr/local/ufw-msgs** 
(without & since rc.local spawns in background anyway)

If notify-send isn't installed then **sudo apt-get install notify-send**.
You can test notify-send at the cmd line to be sure it works.

**notify-send TestMsg "I am a test"**

The normal notify-osd package in Ubuntu is braindead and will not respect the timeout period set in your script. If you don't mind messages showing for 5 seconds then no problem. If you want to replace the notify-osd package with one that does respect the timeout you can add the [Leolik ppa]("https://launchpad.net/~leolik/+archive/leolik") fixed version. I tested it with that and get 2 second messages (set in the script above).

---

