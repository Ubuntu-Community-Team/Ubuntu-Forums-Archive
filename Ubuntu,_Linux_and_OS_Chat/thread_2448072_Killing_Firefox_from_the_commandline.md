---
title: "Killing Firefox from the commandline"
date: 2020-07-31
forum: Ubuntu, Linux and OS Chat
---

### Post by salemboot on 2020-07-31
With the latest update 79.0, you can no longer use killall.
[I]killall firefox
firefox: no process found[/I]

Instead you can use:
[I]killall MainThread
Exiting due to channel error.
Exiting due to channel error.
Exiting due to channel error.
[/I]

So let's look at "/proc/pid/stat".
[I]cat /proc/12739/stat
12739 (**MainThread**) S 3512 12739 3512 34816 15233 4194560 551978 15048 113 24 8174 3959 10 12 20 0 64 0 1958217 2955112448 76249 18446744073709551615 93939634626560 93939635215853 140730397198832 0 0 0 0 4096 17663 0 0 0 17 0 0 0 43 0 0 93939635319016 93939635324368 93939645546496 140730397205385 140730397205410 140730397205410 140730397208543 0
[/I]

Normally that would show "(firefox)".

There are ways around this using "pgrep" or "pkill".   I just thought I would point it out.   Good job Firefox!

:guitar:

---

### Post by coffeecat on 2020-08-01
Not a request for support. *Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by ActionParsnip on 2020-08-01
Could use:
```
 
sudo kill -9 `ps -ef | grep firefox | awk {'print $2'}`

```

---

### Post by monkeybrain20122 on 2020-08-01
```
killall -9 firefox 
```

will work

---

### Post by monkeybrain20122 on 2020-08-01
> **ActionParsnip said:**
> Could use:
```
 
sudo kill -9 `ps -ef | grep firefox | awk {'print $2'}`

```

Why would you use sudo? Firefox is not a root process.

---

### Post by The Cog on 2020-08-01
```
pkill -f firefox
```

---

### Post by ajgreeny on 2020-08-01
I was just about to post this having found the thread I link to at the Mint forum.
> Have other users noticed that in, for example, the system-monitor a running firefox process now shows as **MainThread**, not **firefox**, and that the command ```
killall firefox
``` simply reports that no running process was found.
```
ps aux | grep firefox
``` still shows several firefox processes running.

I have read through the long thread which also discusses this in the Mint forum starting at [https://forums.linuxmint.com/viewtopic.php?p=1858610#p1858610](https://forums.linuxmint.com/viewtopic.php?p=1858610#p1858610) but that does not seem to come to any real conclusions about the reasons behind this.

I agree that it's not a huge problem but simply wonder if anybody has background information as to why this change has occurred

---

### Post by sdsurfer on 2020-08-03
I usually use

```
ps -aux | grep firefox
```

The first result will be firefox, take it down and it takes all the children with it.

```
sudo kill (process id) -9
```

I always had trouble without the brutality of -9.

I do note that on my System 76 Gazelles I almost never have to do that, on my older desktop almost daily. So in my case it's partly a Firefox resource hog problem, partly a hardware system resources problem.

---

