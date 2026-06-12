---
title: "Automatically suspending and resuming"
date: 2011-05-31
forum: Server Platforms
---

### Post by gameguy on 2011-05-31
Hi all. I just got a new computer, so turned my old laptop into a server. I am in high school, and my mum is worried about the power bill, so I was wondering if I would be able to turn my laptop off automatically at 8:30 am, and start it up again on 3pm (mon-friday only - weekends it will stay on overnight).

---

### Post by egpetrich on 2011-06-02
The first hurdle is working out how to put the system to sleep. The package "pm-utils" contains command-line tools to suspend and hibernate, but just because you install the package (and its dependencies) doesn't mean it'll just work. Still, give it a try; it might work out of the box.

For your next hurdle, you'll need to work out how to wake your system up at a specified time. You may need to adjust your BIOS settings to allow wake from RTC (real time clock).

I don't know if there are any pre-built scripts for setting the alarm. Most of what I have seen involves commands accessing the /proc and /sys hooks. Digging through my notes, I found this sequence, which presumably sets the alarm for one minute in the future:
```
sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
sudo sh -c "echo `date '+%s' -d '+ 1 minute'` > /sys/class/rtc/rtc0/wakealarm"
```

Once you know how to safely suspend your system and wake it up at a specified time, you can automate. You may wish to be more careful than simply saying, "suspend at 8:30 AM every weekday." What if you're home sick? I'm not very good at writing shell scripts on the fly, but you can probably write a script to cover any contingencies that come to mind. Put that script into the crontab of root and set it to run at the appropriate time.

Also, check out the package "powernap", which you can configure to automatically suspend your system after a certain interval of inactivity. (Not quite what you asked for, but maybe it'll give you ideas.)

---

### Post by arrrghhh on 2011-06-02
If you have issues waking, look at WOL or Wake On LAN.  Using a 'magic' packet, you can wake the machine over ethernet - works when the rig is off as well.  I used to do this thru my router.  Turn off the server at a set time, use the router to send a magic packet to turn it back on at a set time.

---

### Post by gameguy on 2011-06-03
I would use the magic packet thing, but it is a game server, and hosts for my other friends at school. For that, I need to be home, and some days I get back too late for that. Also, the pm-utils is already installed (11.04)

---

