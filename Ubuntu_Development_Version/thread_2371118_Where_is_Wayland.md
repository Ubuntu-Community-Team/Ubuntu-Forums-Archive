---
title: "Where is Wayland?"
date: 2017-09-11
forum: Ubuntu Development Version
---

### Post by Chanath on 2017-09-11
I am using Ubuntu default. It should be Wayland. I don't know how to check, if Wayland is there, so tried System Monitor. I can see Xorg, but cannot find any process called Wayland.

---

### Post by mc4man on 2017-09-11
post results of 
```
echo $DESKTOP_SESSION
```
```
env |grep xorg
```

---

### Post by Chanath on 2017-09-11
```
$ echo $DESKTOP_SESSION
ubuntu-xorg



```

```
$ env |grep xorg
MANDATORY_PATH=/usr/share/gconf/ubuntu-xorg.mandatory.path
DESKTOP_SESSION=ubuntu-xorg
DEFAULTS_PATH=/usr/share/gconf/ubuntu-xorg.default.path
XDG_DATA_DIRS=/usr/share/ubuntu-xorg:/usr/local/share/:/usr/share/:/var/lib/snapd/desktop
XDG_SESSION_DESKTOP=ubuntu-xorg
GDMSESSION=ubuntu-xorg
XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu-xorg:/etc/xdg



```

I rebooted twice to see, if I am on Ubuntu, not Ubuntu on Xorg. I am on Ubuntu, but this is what I get.

---

### Post by mc4man on 2017-09-11
Read the thread just below this one

---

### Post by Chanath on 2017-09-11
> **mc4man said:**
> Read the thread just below this one

Ok, thanks. 
I didn't read that thread before, thinking it was about virtual box. I have it on bare metal. Now, it is  
> echo $DESKTOP_SESSION
ubuntu




Now, Synaptic doesn't open. 

> $ env |grep xorg
MANDATORY_PATH=/usr/share/gconf/ubuntu-xorg.mandatory.path
DEFAULTS_PATH=/usr/share/gconf/ubuntu-xorg.default.path
XDG_DATA_DIRS=/usr/share/ubuntu-xorg:/usr/local/share/:/usr/share/:/var/lib/snapd/desktop
XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu-xorg:/etc/xdg




I see Xwayland in System monitor. So, its not pure Wayland?

---

### Post by Chanath on 2017-09-11
@mc4man

In one laptop what you said worked, but in another it didn't. Both has vanilla Ubuntu.

---

### Post by rrnbtter on 2017-09-11
Greetings,

> **Chanath said:**
> 
I see Xwayland in System monitor. So, its not pure Wayland?

xwayland is Wayland's port to X-server. It is for x11 app's compatibility.

---

### Post by Chanath on 2017-09-11
> **rrnbtter said:**
> Greetings,

xwayland is Wayland's port to X-server. It is for x11 app's compatibility.

So, a long way to Wayland? Like Xmir in a way. Something unfinished still?

---

### Post by Chanath on 2017-09-11
@mc4man
It worked in the 2nd laptop too. Thanks!
 I had to reinstall, though. There are surely some bugs.
It was good to reinstall, for I had another matter to check.

---

### Post by mc4man on 2017-09-11
It's in the other thread & one I created weeks ok, but to hopefully simplify 
There are 2 issues that exist here.

1. The first log in from a fresh install will use xorg (with no user intervention.
2. The log in screen's session options will Always show  'ubuntu'  as selected session (always, no matter what session was exited from.

If inclined you could read thru the bug report, as it's got some age, (I filed on july 7) & there were some minor changes along the way start down lower. (The bug title has been changed so often it really no longer reflects the actual issues, no matter really.

Reading from comment 24 down would give a decent idea of what's up.
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1705157](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1705157)

Side note:
When one logs out from one session to the other then you get a slightly mixed environment, comment 24 shows that.
When one restarts from one session or the other then there is no mixing. I don't think the mixing is that big a deal..

---

