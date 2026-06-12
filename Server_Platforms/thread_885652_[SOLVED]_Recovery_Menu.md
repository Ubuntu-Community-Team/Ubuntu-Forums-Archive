---
title: "[SOLVED] Recovery Menu"
date: 2008-08-10
forum: Server Platforms
---

### Post by G1ZmO65 on 2008-08-10
I created a CRON job to shut down my home server at a specific time each evening to save power but everytime it shuts down it ends up at the RECOVERY MENU and none of the options seems to resolve it.

Can anyone advise me on what to do to make it shutdown properly?

Thanks

Paul

actually the CRON job doesnt appear to be working but thats another issue

---

### Post by sisco311 on 2008-08-10
use the:
```
shutdown -P now
```or
```
poweroff
```command to turn of the computer.
-P = power of.

---

### Post by G1ZmO65 on 2008-08-10
Ah brill! Sorry to ask what probably seems a silly question :P

Thanks

Paul

---

### Post by sisco311 on 2008-08-10
for future reference

HowTo shutdown the computer at a specific time each day:

1.) set the default editor to nano:
```
export EDITOR=nano
```

2.) edit the crontab:
```
sudo crontab -e
```

3.) add the cron job:
> mm hh * * * /sbin/shutdown -P 5
replace mm and hh with the desired time.

For example to shutdown the computer at 01:30
> 30 01 * * * /sbin/shutdown -P 5

4.) save the file and exit:
Ctrl+o, Enter, Ctrl+x.

After the cron job (/sbin/shutdown -P 5) is executed you have 5 minutes
to cancel the shutdown with the:
```
sudo shutdown -c
```command.

---

### Post by sisco311 on 2008-08-10
> **G1ZmO65 said:**
> Ah brill! Sorry to ask what probably seems a silly question :P

Thanks

Paul

If your thread is solved, please mark it solved by selecting 
**Mark this thread as solved** from the **Thead Tools**.

---

### Post by josephwright on 2008-08-15
Very handy: I've been struggling with the same issue.  Perhaps a naive question, but why does "shutdown now" alone not work as expected?

Joseph Wright

---

### Post by windependence on 2008-08-15
I'm sure there are differing opinions about this but in most datacenters where I have worked we have come to the conclusion that shutting down and starting up once a day is harmful to the equipment. Components heat up and cool down and along with that comes expansiona and contraction, At one place I worked, we tried it both ways, having the users shut down at night and also having them leave the boxes on, and there was a very significant number of motherboard failures when we powered down each night. Not only that, but there was also a maked increase in hard drive failures as well, I am guessing because it is really hard on a drive to spin up. This was with 19,000 machines.

You are not saving much power at all, and what you are saving, you will probably be spending in hardware down the road.

-Tim

---

### Post by G1ZmO65 on 2008-08-15
Yes windependence, I know where you're coming fro on the thermal cycling issue. 
At work I make sure everything is left on however I really need to reduce our fuel bills at home and therefore decided on the shutdown option for my home machines as I have calculated that I'll save about £12/month just on the overnight downtime in addition to the other energy savings round the house. In general I would prefer to leave computers on but with fuel costs going the way they are....

On another point: 

sisco311 recommended setting the default editor to nano but I assume vim or another would do just as well for crontab or is there a specific reason for using nano?

Thanks,

---

### Post by windependence on 2008-08-15
Vim is fine, no prob.

Hey 12 pounds is a case of beer here. I'm all for it. :)

-Tim

---

### Post by Cadmus on 2008-08-15
I think the reason nano is posited as a good editor is it's straightforward if you're not used to text editors. What with Ubuntu positioning itself a good introduction to Linux, vi might give people The Fear (I know it did to me when I was an undergraduate).

---

### Post by windependence on 2008-08-15
Hey, I use nano and pico myself because I hate VI, but he was just asking if he could use it because he is comfortable with it. Of course that's the nice thing about Linux, you have a choice. ;)

-Tim

---

### Post by mibbster on 2009-08-31
see [http://ubuntuforums.org/showthread.php?p=7875521](http://ubuntuforums.org/showthread.php?p=7875521)

---

