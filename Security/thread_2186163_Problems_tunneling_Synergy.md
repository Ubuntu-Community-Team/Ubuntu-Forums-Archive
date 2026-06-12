---
title: "Problems tunneling Synergy"
date: 2013-11-06
forum: Security
---

### Post by jcllings on 2013-11-06
So I've two Ubuntu boxes, a laptop and a dekstop. I have synergy set up between them but the fly in that ointment, of course, is security. 

I want to tunnel the connection using autossh but I can't get it to work to save my life... and I've done it successfully before. What I'm afraid of is that there's something new, as in security settings, out there that I don't know about. :-/

Synergy config:

```
 
  section: screens
        clientmachine:
                halfDuplexCapsLock = false
                halfDuplexNumLock = false
                halfDuplexScrollLock = false
                xtestIsXineramaUnaware = false
                switchCorners = none
                switchCornerSize = 0
        servermachine:
                halfDuplexCapsLock = false
                halfDuplexNumLock = false
                halfDuplexScrollLock = false
                xtestIsXineramaUnaware = false
                switchCorners = none
                switchCornerSize = 0
 end

 section: aliases
     clientmachine:
             cm
     servermachine: 
             sm
             localhost
 end

 section: links
        clientmachine:
                right = servermachine
                left = servermachine
        servermachine:
            right = clientmachine
                left = clientmachine
 end

 section: options
        relativeMouseMoves = false
        screenSaverSync = true
        win32KeepForeground = false
        switchCorners = none
        switchCornerSize = 0
        keystroke(Control+Alt+Home) = lockCursorToScreen(toggle)
 end

```
Command to start server:
```

synergys -c synergyconfig

```

Command to start client:
```

/usr/bin/synergyc --daemon --name cm sm

```

---

### Post by jcllings on 2013-11-06
So on the client machine I've tried:

 1886  ssh -f -N -L localhost:24800:sm:24800 sm
 1909  ssh -f -N -R localhost:24800:sm:24800 sm
 1921  ssh -L 24800:sm:24800 sm
 1922  ssh -f -L 24800:sm:24800 sm
 1923  ssh -f -N -L 24800:sm:24800 sm
 1928  ssh -vv -N -L localhost:24800:sm:24800 sm
 1946  ssh -f -N -L localhost:24800:sm:24800 sm
 1952  ssh -f -N -L 24800:sm:24800 sm
 1956  ssh sm -f -N -L 24800:sm:24800
 1982  ssh sm -f -N -L 24800:sm:24800

---

### Post by jcllings on 2013-11-06
Solved with following info:

[http://synergy-foss.org/wiki/Security#.28Optional.29_Configuring_the_Clients_with_autossh](http://synergy-foss.org/wiki/Security#.28Optional.29_Configuring_the_Clients_with_autossh)

Using same config, client start command is:
```
/usr/bin/synergyc --daemon --name cm localhost
```

Server start command is same. 

Client side autossh command:
```
autossh -f -N -q -L 24800:localhost:24800 sm
```

---

