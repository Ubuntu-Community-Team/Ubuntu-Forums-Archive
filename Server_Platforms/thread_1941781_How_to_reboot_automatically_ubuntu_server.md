---
title: "How to reboot automatically ubuntu server"
date: 2012-03-16
forum: Server Platforms
---

### Post by franckluke on 2012-03-16
Hi ,
I just  build my ubuntu server and i have one problem every morning i need
to reboot my server automatically to swicth off and after 3 minutes and tur on.
And can see everything back in normal.
Thank's for your help

---

### Post by nothingspecial on 2012-03-16
*Thread moved to **Server Platforms**.*

---

### Post by rubylaser on 2012-03-16
Sounds like an odd request as turning linux servers off daily really isn't something you should ever need to do.  I'd love to hear why you need to do this.  But, here are some ideas to get you started.

Turning off via cronjob is very easy.

```
sudo -i
```
```
crontab -e
```
and paste in something like this...
```
0 3 * * * /sbin/shutdown -h now
```

Getting it to turn back on is slightly more tricky.  You could either use Wake On LAN from another machine or use the system's BIOS timer to turn it back on.  It's still in the morning, so I may not be thinking of the best way to accomplish this.

---

### Post by volkswagner on 2012-03-16
does your system become unresponsive after some amount of time?
Perhaps you can check logs for helpful information if this is true.

Creating a reboot script would be more of a workaround, although it seems like this is what you are requesting.

Lets see if you can clarify what you are looking for in a little more detail.

---

### Post by Holdolin on 2012-03-16
I too find it interesting to need to reboot a server every day.  Mine tend to go months without rebooting.  However, if that is what you wish to do, I would imagine you could set it up as a cron job.

---

### Post by Hank_The_Dog on 2012-03-16
I would say cron is your best bet..

Did you install Ubuntu Server, or the desktop edition? If you installed the desktop edition, you need to set it to automatically log in, or else it will pause on the log in screen without a monitor/keyboard/mouse connected.

---

### Post by Vishal Agarwal on 2012-03-16
check for the logwatch package installed. 

$ logwatch --detail High --mailto [email]youris@domain.com[/email]

Check the logwatch report  send to your email id carefully, you may get the clue for your problem

---

### Post by Demented ZA on 2012-03-17
Op still hasn't said why server needs to be rebooted(???)

I would have installed acpid package 
```
sudo apt-get install acpid
```and run reboot as root from crontab.

I might be wrong or missing something, mostly because I haven't needed to do this before and it scares me having to do so, but if I ever did, that's how I would go about it.

Edit: Powersaving might be a good reason to do this? If so, then Rubylaser's suggestion is better suited.

---

### Post by ssam on 2012-03-17
there is a package called watchdog. its set the kernel to automatically reboot if it certain conditions are not met.

for example I have an beagleboard music server, and the network card can sometimes get upset by electrostatic discharges from the speakers/amp being switched on and off. I use watchdog to trigger a reboot if the network goes down (it also tries a reconnect script first).

---

