---
title: "How to limit server bandwidth usage to 3 TB/month"
date: 2007-07-03
forum: Server Platforms
---

### Post by Quickjelly on 2007-07-03
So this is the issue, I've got a server from which I can send/receive 3TB's of data every month. After I've used up those 3 TB's I have to pay per gigabyte. :(

The company providing the server gave me no way to know how much bandwidth I have used or how much I have left, and no way to warn me when I've used what I'm allowed to.

What I need now is a tool that can show me how much bandwidth I have used and possibly turn off the network access when I've reached  like 2.8 TB's. or something like that to keep me from going over my limit. Does a app like this, or something similar, exist ?

Thanks in advance

---

### Post by crazyjx23 on 2007-07-03
The system monitor that I use on Ubuntu tells me bandwidth sent and received, but resets after I reboot my computer. If the server runs 24/7 than I guess you could use that, or record the bandwidth before you shutdown. If you have a good network set up, ya should be able to choke the bandwidth pretty well too in the mean time.

---

### Post by murraymca on 2007-07-03
Hiya,

This article will hopefully help you:  [http://www.linux.com/articles/50649](http://www.linux.com/articles/50649)

Just using iptables you can set up rules to monitor your bandwidth.  It also has a section at the bottom about saving the counters over reboots.  The article also suggests searching "bandwidth" on freshmeat - perhaps you will find a better solution there.

I'm not sure how to stop the traffic once it hits a certain limit, but I'm sure with simple iptables accounting and a script you would be able to do it ;)

Sorry for not being more helpful, hopefully the link is a good start.

All the best,

---

### Post by gombadi on 2007-07-04
I use vnstat to monitor my bandwidth usage. It runs every five minutes and stores its data in a file so is saved over reboots.

It is command line only but with cron you can get it to produce an email each day.

Have a look at the type of output it produces >> 
[http://bt.zagbot.com/ip-stats.txt]("http://bt.zagbot.com/ip-stats.txt")

"sudo apt-get install vnstat" is all it takes :D

---

### Post by crazyjx23 on 2007-07-04
well there ya go. beats my solution....

---

### Post by Quickjelly on 2007-07-04
Thank you guys, really appreciate all you people helping :)

---

