---
title: "Best kernel tweak for Multimedia server + multiple connections?"
date: 2013-10-01
forum: Ubuntu Studio
---

### Post by denywinarto on 2013-10-01
[COLOR=#000000][FONT=Verdana]Hi, i have a multimedia ubuntu 12.10 server for 28 clients,
[/FONT][/COLOR]the server stores 1080p / 720p videos
[COLOR=#000000][FONT=Verdana]Problem is, sometimes when there's too many simultaneous connections the server would crash and a physical restart is required.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]The server itself is running intel i3[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Now, i've heard about kernel tuning that could prevent this from happening..[/FONT][/COLOR]

I've found some references regarding this, but i'm not sure if this is suitable for my case.

[http://samiux.blogspot.co.uk/2011/04/howto-performance-tuning-on-ubuntu.html](http://samiux.blogspot.co.uk/2011/04/howto-performance-tuning-on-ubuntu.html)

Could anyone give me a hint or two for this?

[FONT=Verdana, Arial, Helvetica, sans-serif][COLOR=#000000]Also i've heard of low latency kernel, which one is better for my case?[/COLOR][/FONT]

---

### Post by su:bhatta on 2013-10-03
If you are running Ubuntu Studio, by default you have Linux Low Latency kernel installed. 

If you are not running Ubuntu Studio, you might get better results posting this thread to other sub-forums like 'Installation & Upgrades' where you will get better visibility for your thread.

---

### Post by cub on 2013-10-07
In your case the low latency kernel wouldn't give any special advantages since it's playback only. However, if you are already running the low latency kernel it should not be much difference for you.

I don't know what performance or tuning the link would provide, perhaps someone with more in depth kernel knowledge can help out there.

---

### Post by zequence on 2013-10-09
linux-lowlatency is not optimal for servers. So, I would recommend to try using linux-generic instead.

---

### Post by tgalati4 on 2013-10-09
When you look in the log files, what do you find?  They are located in /var/log.  The Intel i3 is not a server processor, nor is the motherboard that it sits on designed for server workloads.  Try installing your setup on a real server with a Xeon processor and see how that behaves.

---

