---
title: "Power off or leave running?"
date: 2009-07-07
forum: Server Platforms
---

### Post by AndyXS on 2009-07-07
I have a samba file server running on a dell server and I was just wondering if it is best to power off when the server is not being used. We are only using it during office hours Mon - Fri, 9 - 5. Would shutting it down daily causes any problems or will it enhance the servers life?


Power off or leave running?

---

### Post by TuckLive on 2009-07-07
Opinions vary.  I have never seen any hard data that suggests either way is best.

---

### Post by TwiceOver on 2009-07-07
I'm a "Leave Running" kinda guy...

On a simple server when the drives spin down and the processor isn't working hard, it is maybe pulling 100w.  No worse than leaving a light bulb on all day.

---

### Post by amauk on 2009-07-07
I tend to leave the servers I manage running 24/7

gives you far more flexibility, including:
- running cronjobs out of hours (backup / general housekeeping)
- access to services all the time (for people working from home / on business trips, etc.)

Also, while a system is running, frequently used files / DB queries, etc will be cached for faster access
turn it off every night, and you'll lose the speed increases of caching

Power cycling machines (switching them off and on) doesn't harm them in any way *
so the only advantage to switching off servers outside office hours is the saving on running costs

I was asked once to calculate the running cost of a server, and it came out to £20 / month, running 24/7
(this was a couple of years back)


* Power cycling *can* cause already faulty hardware to fail sooner (mainly talking about PSUs spiking & blowing their internal fuse)
but it would have failed anyway, sooner or later

---

### Post by Thirtysixway on 2009-07-07
Personally I leave my server running 24/7 but that's because it's host to the printer in our house, and I run torrents, folding@home, and other things.  Also the brand of computer it is doesn't have a power switch, so even if the OS shuts down the machine is still physically powered on.

In your situation, it may be easier to leave it on.  That way nobody needs to worry about powering down on a Friday evening, or remembering to power up monday morning.

I wrote a blog post on automating Ubuntu Server shutdown
[http://noobbox.com/2009/02/09/automate-ubuntu-server-shutdown](http://noobbox.com/2009/02/09/automate-ubuntu-server-shutdown)
Along with something like wake-on-lan or having somebody remember to turn the server on, it could help.  But I still think that leaving it on is easier.

---

### Post by HermanAB on 2009-07-08
If you want your server to last 7 or more years, then put it on a UPS and leave it running. If you like buying new kit every 2 or 3 years, then it won't matter what you do.

The reason it will last longer on a UPS is due to protection against power surges, brown-outs and lightning induced spikes.

---

### Post by Vegan on 2009-07-08
My IBM, while a fossil, has good power management. When no users are on it, it snoozes until one surfaces. The average power consumption is rather low even when run continually.

More modern machines also have power management features that can cut costs when but in use.

---

### Post by georgerobbo on 2009-07-08
It really doesn't make a huge difference. You should be able to set the hard drive to power down after a period of inactivity etc. I would only recommend that it gets good airflow, by which I mean don't keep it in a cupboard. 
 
You should also be able to set the machine to shutdown/sleep on a friday evening and then in the bios change the wake up settings to get it to automatically power up on a monday morning.

---

