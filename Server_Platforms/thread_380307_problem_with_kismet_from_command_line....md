---
title: "problem with kismet from command line..."
date: 2007-03-09
forum: Server Platforms
---

### Post by Mia_tech on 2007-03-09
after installing kismet, I've tried to launched it from the CLI, but it says the server failed to launch
and Im using su kismet
is there any specific options that goes with the command in order for kismet to work, I been through the man page and --help not very helpful 
thanks

---

### Post by Aberrix on 2007-03-09
> **Mia_tech said:**
> Im using su kismet

how about ```
sudo kismet
```

?

---

### Post by Mia_tech on 2007-03-09
> **Aberrix said:**
> how about ```
sudo kismet
```

?

that is how i started it
sudo kismet and also su and then kismet
here's the output


~ # kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: No packsources were enabled.  Make sure that if you use an enablesource line that you specify the correct sources

---

