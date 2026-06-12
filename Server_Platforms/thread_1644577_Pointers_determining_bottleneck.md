---
title: "Pointers determining bottleneck?"
date: 2010-12-13
forum: Server Platforms
---

### Post by bobmct on 2010-12-13
Hi gents;
I've recently started admin'ing some ubuntu web servers and there is much of the config to learn.  However, I'm experiencing an issue where for increments of 8 mins and 32 secs apache does not respond.  The actual time can vary over the course of days but it seems to always come back.  I am thinking something is running on schedule that is usurping the system.  But the trick is: how to find it.

I've used top, crontab, ps -ef and examined just about anything I could find and also scoured the various logs without success.

I am hoping that some of you who may have performed similar diagnostics would be willing to share some pointers as to where to look and what to look for?  This particular system is running 2.6.28-17-server and has 24GB of RAM so it seems pretty healthy.

I appreciate your guidance - happy holidays :)

---

### Post by dtfinch on 2010-12-13
A Google search for 'apache "every 8 minutes"' brought up mention of chkservd (part of cPanel) that checks every 500 seconds (or 8 minutes 20 seconds). I have no idea if it's actually related to your problem, and I've never set up cPanel myself, but it may be worth checking out if you're using it.

Edit: If it's exactly 8:32, that's 512 seconds, a power of 2. So you might also look for things that that happen [every 512 seconds](http://www.google.com/search?hl=en&source=hp&q=%22512+seconds%22+apache).

---

### Post by koenn on 2010-12-13
i think dtfinch is on to something - it may very well be some 3th party tool polling your server at those intervals. 

If "non responsive" means you can't reach it with a browser, then you should also look at what's happening on your network. Could be something silly like syncing 2 storage devices or some other scheduled job  taking up lots of bandwith or stressing your switches, ... 

I recently have been playing with [Cacti]("http://www.cacti.net/"). If you have snmp on those servers you can use Cacti to graph a number of snmp counters (system load, bandwith usage, ...) and see if anything peaks at 8 minute intervals.
Then again, if those 8 minute performance drops are caused by such a polling tool already, it gets kinda messy. :)

---

