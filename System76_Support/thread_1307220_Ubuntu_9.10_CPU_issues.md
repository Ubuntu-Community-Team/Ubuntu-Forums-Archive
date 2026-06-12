---
title: "Ubuntu 9.10 CPU issues"
date: 2009-10-30
forum: System76 Support
---

### Post by Lee_Machine on 2009-10-30
I've had this problem since the Beta, but of course I waited for the final release and the S76 driver to support Karmic

So my issue is after coming back from Suspend/Hibernate I have extreme CPU hogging issues. It's not just one app that does this, but more than often it's Firefox, Gnome Log Viewer, and any video, with any video player.

I cannot seem to find the issue in the log, but I am no means an expert.

By CPU issues I mean while watching any video with mplayer it runs at 80-90%, and when using Gnome Log Viewer it never drops below 80%

I have attached my logs. 

This is with a Pangolin Performace Panp4n.

The only way to fix it is to reboot.


Thanks,

---

### Post by thomasaaron on 2009-10-31
Crap. It's just about overheating your CPU too. You have a ton of theses...

> Oct 31 00:48:14 brandon-laptop kernel: [14223.576335] CPU1: Temperature/speed normal
Oct 31 00:48:14 brandon-laptop kernel: [14223.580163] CPU1: Temperature above threshold, cpu clock throttled (total events = 24898)

What nVidia driver are you showing in Admin > Hardware Drivers?

Also, you did the online upgrade, right?

(I can't really tell what process is causing it.)

---

### Post by Lee_Machine on 2009-10-31
I'm running 185.18.36

Should I compile and use the newest one that came out a few days ago? 

I did a fresh install when the Beta came out and have been doing updates since then. 

The laptop does get hot, but that does happens when its running at 90% capacity.  :D

I have been waiting for the Kubuntu 9.10 final. I'm going to install that and see if the issue persists. 

Thanks again.

---

### Post by Lee_Machine on 2009-11-01
So I installed Kubuntu on another partition, and WOW I haven't had that many issues with any OS install in a long time. Anywho the CPU issue isn't that big of a deal. I'm waiting for Mint8 anyways, which is good ol' GNOME. 


On a side note, any chance of you guys making the S76 driver installable on Mint? Or a how-to in modifying the driver to do so?

Lastly, the S76 driver will not install out-of-the-box with Kubuntu 9.10. It requires python-gtk2, and of which is not in the default Kubuntu repos.

---

### Post by jdb on 2009-11-01
> **Lee_Machine said:**
> 
 It requires python-gtk2, and of which is not in the default Kubuntu repos.

WOW!, pygtk is a pretty common package.
It must not have glade either!!!

jdb

---

### Post by thomasaaron on 2009-11-02
We probably won't try to get it to run on Mint, to be honest. Somebody wrote a how-to for converting it, though...

[http://ubuntuforums.org/showthread.php?t=802181&highlight=system76+driver+linux+mint](http://ubuntuforums.org/showthread.php?t=802181&highlight=system76+driver+linux+mint)

(I think that was for Jaunty, though.)

Also, Lee Machine, I think a fresh install of Karmic should take care of the CPU problem. We're not seeing that on the shop machines, so it probably was just some incompatible configuration that got carried over from Jaunty.

---

