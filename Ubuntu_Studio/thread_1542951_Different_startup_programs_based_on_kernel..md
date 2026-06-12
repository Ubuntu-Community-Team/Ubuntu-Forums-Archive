---
title: "Different startup programs based on kernel."
date: 2010-07-31
forum: Ubuntu Studio
---

### Post by devonbadman on 2010-07-31
I currently use two kernels, realtime for when I'm using jack to edit audio, and the standard kernel for when I'm just using the computer for general use as the realtime kernel sometimes fails on shutdown due to pulseaudio fighting with jack.

Is there anyway to set jack to start on startup, but only if I'm using the realtime kernel? I don't want to use seperate users, but wondered if it could be setup in a file run on login kinda like this;

```

if (uname -a == *rt*) {
   exec /usr/bin/qjackctl;
}

```Cheers.

---

### Post by trulan on 2010-07-31
Did you try putting that line in /etc/rc.local ?  It gets executed on startup (by default it's empty) and should be an easy way to do what you are wanting to do.

---

### Post by AutoStatic on 2010-07-31
I wouldn't use /etc/rc.local, unless you start up qjackctl as a specific user. Now it will run as root while it's a user space app. If you're using Gnome you could try creating a new Startup Application entry (System - Preferences - Startup Applications) that points to the little script.
The script itself won't work, it should look like this:

```
#!/bin/bash

if [ `uname -r | cut -d '-' -f 3` = "rt" ]; then
    /usr/bin/qjackctl;
fi

```

---

### Post by devonbadman on 2010-07-31
> **AutoStatic said:**
> I wouldn't use /etc/rc.local, unless you start up qjackctl as a specific user. Now it will run as root while it's a user space app. If you're using Gnome you could try creating a new Startup Application entry (System - Preferences - Startup Applications) that points to the little script.
The script itself won't work, it should look like this:

```
#!/bin/bash

if [ `uname -r | cut -d '-' -f 3` = "rt" ]; then
    /usr/bin/qjackctl;
fi

```

Cheers for that. It works, but I forgot my realtime kernel is appended with "realtime", not "rt"

I never meant that code that I put to work, it was just an outline of what I meant.

Thanks again.

---

