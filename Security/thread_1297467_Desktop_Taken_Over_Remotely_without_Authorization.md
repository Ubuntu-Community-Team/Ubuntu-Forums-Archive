---
title: "Desktop Taken Over Remotely without Authorization"
date: 2009-10-21
forum: Security
---

### Post by ehsanul on 2009-10-21
I was browsing online in Ubuntu 8.04, when suddenly my mouse was acting strange. It would not go where I wanted it to go, disappeared, reappeared and the like. I assumed it was just Gnome being weird. The screen might've even flickered.

Right after that, the mouse moved on its own a little, so I thought it might've been my mouse acting strange. But it moved in a human-like motion, and I kept my mouse still after it started moving, in the air (it's optical). 

Then, I suddenly got a gnome notification saying that someone else was controlling my desktop. It even showed a human-readable address, some alphanumeric characters followed by @njit.edu or something similar. NJIT is the university where I study, and I live on campus using NJIT servers for internet connectivity. I quickly shutdown, kinda panicked. This was quite unexpected, have been using ubuntu for over a year with no such issues.

I looked through the system log, and the only thing that seems notable to me are these repetitive logs (though these occur in yesterday's log as well):
> 
Oct 21 20:05:50 ehsanul-laptop kernel: [ 1668.601616] wlan0: CTS protection disabled (BSSID=00:1d:70:92:ad:40)
Oct 21 20:05:50 ehsanul-laptop kernel: [ 1666.831749] wlan0: CTS protection enabled (BSSID=00:1d:70:92:ad:40)

I connect via wifi, and njit lets anyone connect to the wifi, but to actually use the net and not just stuff on njit servers, they offer a popup when you visit any website, which allows you to input a username/password combination. Then you get access to the net, and I guess you're also registered as part of the network. I don't know.

Are there any other logs I could look at, because I didn't properly see the address or whatever was being offered to me in the notification that my desktop was being controlled by someone else..

Also, obviously I want to know how to shield myself from such an attack, as well as how it was done.

---

### Post by HermanAB on 2009-10-21
Sounds like you have VNC running.  You probably experimented with it some time ago and forgot all about it.  VNC is best uninstalled.

---

### Post by ehsanul on 2009-10-21
> **HermanAB said:**
> Sounds like you have VNC running.  You probably experimented with it some time ago and forgot all about it.  VNC is best uninstalled.

You're right, wow.. Vino VNC server is running on my computer, though I have no idea how. I'm actually pretty damn sure I've never used it before, as I haven't heard of it, and didn't install it myself. Does it come with the distribution?

I went to vino preferences, and found that it was allowing anyone to view and control my desktop, without asking for confirmation, nor a password. This can't be the default setting, can it? It does seem so. I changed that, but I should probably uninstall it too anyways, just to be sure.

Thanks a lot! :)

---

### Post by cariboo on 2009-10-21
Vino is enabled by default in Karmic, but it is set to not allow connections by default.

---

