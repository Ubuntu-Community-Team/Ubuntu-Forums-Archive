---
title: "auto close app before it gets killed at logout"
date: 2013-04-21
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-04-21
[[IMG]http://i.imgur.com/QHAePHfs.png[/IMG]](http://i.imgur.com/QHAePHf.png) - this error flashes at logout when gmusicbrowser is open at logout, too fast to read but not for the cleanupscript to get a screenshot of
when i logout gmusic browser is killed, i was able to close it in the past using the lightdm session-cleanup-script, but now it gets killed before by script can close it
```
#!/bin/bash
backlightx --get current > /var/log/backlightx
pid="$(pgrep -f gmusicbrowser | head -1)"
if [ "0$pid" -gt "0" ]; then
    user="$(ps aux | awk '{print $1" "$2}' | grep $pid | awk '{print $1}')"
    sudo -u "$user" gmusicbrowser -cmd Quit
fi
ogg123 /usr/share/sounds/ubuntu/stereo/desktop-logout.ogg 2> /dev/null &
```

---

