---
title: "I need help writing a script to record from an internet stream"
date: 2010-02-01
forum: The Cafe
---

### Post by kevin11951 on 2010-02-01
I am trying to find a way to record the stream from this URL every day from 6pm-9pm:  mms://winmedia.voxcdn.net/3137-live1-wmv?MSWMExt=.asf

I can play it in both vlc and totem fine, but they stream a new episode every day from 6pm-9pm, and i am not always at the computer, so i want it to record from that stream, starting at 6pm for 3 hours, then stop and save it somewhere.

I know its possible, but i just dont know how.

---

### Post by loell on 2010-02-01
basically you need mplayer to capture the .ASF stream.

refer to this thread,
[http://ubuntuforums.org/showthread.php?t=436926]("http://ubuntuforums.org/showthread.php?t=436926")

**ie** mplayer -dumpstream mms://winmedia.voxcdn.net/3137-live1-wmv?MSWMExt=.asf


then most probably put it in a cron job. :)

---

### Post by kevin11951 on 2010-02-01
> **loell said:**
> basically you need mplayer to capture the .ASF stream.

refer to this thread,
[http://ubuntuforums.org/showthread.php?t=436926]("http://ubuntuforums.org/showthread.php?t=436926")

**ie** mplayer -dumpstream mms://winmedia.voxcdn.net/3137-live1-wmv?MSWMExt=.asf


then most probably put it in a cron job. :)

how do i force it to stop after exactly 3 hours?

something like this comes to mind:
```

mplayer -dumpstream mms://winmedia.voxcdn.net/3137-live1-wmv?MSWMExt=.asf &
sleep 10800
killall mplayer

```

but what if i am using mplayer for something else when it finishes, bye bye mplayer...

---

### Post by loell on 2010-02-01
err, don't use killall then? ;)

you now have to 'kill [processID]'  , in which case your script must catch **ps aux | grep mplayer**, then kill the lesser process ID number.

---

### Post by andrew.46 on 2010-02-01
Hi kevin,

> **kevin11951 said:**
> but what if i am using mplayer for something else when it finishes, bye bye mplayer...

Try running:

```
kill $! 
```

after your sleep command, this should kill the most recently backgrounded process in the script and is easier than grabbing the exact pid.

All the best,

Andrew

---

