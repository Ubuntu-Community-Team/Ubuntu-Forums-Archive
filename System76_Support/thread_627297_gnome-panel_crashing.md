---
title: "gnome-panel crashing"
date: 2007-11-29
forum: System76 Support
---

### Post by GregCwx1 on 2007-11-29
Wondering if anyone else has experienced this problem...

About a week ago I was modifying my desktop and adding apps and applets to the top panel. I decided to add the windows-list applet and that's when it all started to go bad. The gnome-panel crashed and I had to reset X and log in again. Only problem, the panel crashed again. So, I thought I'd try my 'test' account and that too did not allow much to happen after the gnome-panel crashed.

I logged out to the terminal (always a savior to have that ;-). rm- fr .gnome* and .gconf* hidden directories, did a sudo apt-get update, etc., and also a apt-get -reinstall -install gnome-panel and a sudo reboot to get everything back to normal. What a royal pain!

So, I think I'm back to stability but a few days later I decide to start messing around again and I go to add another app, I think it's the desktop view button applet and it all starts again. I try logging in several times and always the same result. As soon as the gnome-panel crashes your desktop session is pretty much toast. Go through the steps again and get back to where I started.

I've posted this problem to the gnome-panel bug page where I see there are plenty of other problems with that aspect of gnome. I have a pretty high threshold of pain when it comes to difficult and unstable environments but I have to say I'm getting a bit tired of this ubuntu version. I have been running RH 7.3 for over four years and made the switch to KDE pretty early with that desktop system. I'm pretty sure I have had way more problems with this distribution of Linux than I ever had with RH and KDE.

Anyone seeing these kinds of instabilities? Should I switch to KDE or try another complete reinstall of Gnome? Thanks for your thoughts.

Daru2 notebook with 2GB RAM and 80GB HDD, Ubuntu 7.10 clean install after a botched upgrade attempt from Feisty (7.04).

Thanks for reading...

---

### Post by palintheus on 2007-11-30
hmm, haven't been having any issues adding applets or buttons to the panel, will try different ones over the next day and update though.

---

### Post by thomasaaron on 2007-11-30
If once it crashes, it continues to crash, you may be saving your sessions. So, when you try to boot up again, it boots up the (crashed) session you just left.

Try going to System > Preferences > Sessions > Session Options 
and uncheck the "Automatically remember..." box.

---

### Post by GregCwx1 on 2007-11-30
The sessions are not being saved. These are clean logins that cause the gnome-panel to crash. Problem is, I can't find any core files. Any idea where to look for the crash info besides /var/crash? I've already looked there and found nothing.

---

### Post by thomasaaron on 2007-11-30
cat /var/log/messages

---

### Post by palintheus on 2007-11-30
I have added/removed several buttons/applets to both panels randomly and can say that my panel never crashed, so it doesn't seem to be a bug issue...

---

