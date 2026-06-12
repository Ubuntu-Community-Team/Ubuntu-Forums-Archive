---
title: "Will gnome settings be complete by 12.04?"
date: 2012-02-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kelpdip on 2012-02-19
The only issue I've had with gnome3 or unity is the incomplete gnome settings. I've been sticking with gnome under the assumption they will be completed gradually, but I'm curious how many will still be missing in 12.04? Editing configs manually is one thing I've been happy to avoid with ubuntu.

---

### Post by gordintoronto on 2012-02-19
There's a forum for 12.04. Also, you could try the Alpha of 12.04 from a LiveCD.

---

### Post by wolfen69 on 2012-02-19
Here is the daily build of 12.04 [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by mörgæs on 2012-02-19
Moved.

---

### Post by jbicha on 2012-02-20
No. GNOME's System Settings is mostly complete now according to the developers. For more configuration options, install gnome-tweak-tool. There's also some Unity-specific customization tools. System Settings in Ubuntu 12.04 is better than in 11.10 though, with some Unity configurations built-in now.

Every choice/option/configuration setting has a complexity cost. Ubuntu & GNOME consciously try to keep that complexity low but with the most common configuration options available so that the operating system is useful to everyone.

---

### Post by williammanda on 2012-02-20
The printers isn't working for me. Can't add a printer.

---

### Post by gordintoronto on 2012-02-20
What printer? Turn it on, run "printing" from the Dash, click on the printer, make logical selections from there until the printer works.

---

### Post by sammiev on 2012-02-20
> **jbicha said:**
> No. GNOME's System Settings is mostly complete now according to the developers. For more configuration options, install gnome-tweak-tool. There's also some Unity-specific customization tools. System Settings in Ubuntu 12.04 is better than in 11.10 though, with some Unity configurations built-in now.

Every choice/option/configuration setting has a complexity cost. Ubuntu & GNOME consciously try to keep that complexity low but with the most common configuration options available so that the operating system is useful to everyone.

There is a lot of bugs in gnome3 that are not in 11.10. I'm testing 3 laptops with all different setups.

---

### Post by kelpdip on 2012-03-11
I guess this was also a problem with early gnome2, where it was released with an incomplete set of settings apps, and it gradually built up over time. It takes a leap of faith going to a gnome3 based LTS with the hope that third party apps like tweak-tool will restore the functionality at some point in the future. Unity is fine for what it is, but there are missing system settings for desktop/notebook users. :(

> **jbicha said:**
> No. GNOME's System Settings is mostly complete now according to the developers. For more configuration options, install gnome-tweak-tool. There's also some Unity-specific customization tools. System Settings in Ubuntu 12.04 is better than in 11.10 though, with some Unity configurations built-in now.

Every choice/option/configuration setting has a complexity cost. Ubuntu & GNOME consciously try to keep that complexity low but with the most common configuration options available so that the operating system is useful to everyone.

---

### Post by cariboo on 2012-03-11
> **gordintoronto said:**
> What printer? Turn it on, run "printing" from the Dash, click on the printer, make logical selections from there until the printer works.

If you are running gnome-shell only, the printer dialogue is broken, you have to run system-config-printer in order to get the same dialogue as in Unity.

---

### Post by Roasted on 2012-03-11
> **cariboo907 said:**
> If you are running gnome-shell only, the printer dialogue is broken, you have to run system-config-printer in order to get the same dialogue as in Unity.

Yeah... quite a pain, but at least it works. Is this something that's being worked on? I also found I couldn't rename my network printer. mc2430 isn't the most helpful when I have multiple printers on the network. I found myself having to edit CUPS via web interface (localhost:631) to handle it the way I wanted.

I also find the network settings in Gnome Shell to be aggravating. I cannot edit a wired network interface unless it's active. That means if I accidentally set the wrong static IP to eth0, and I go in to adjust it, I cannot edit it unless it's active. But if I goofed on the settings, I cannot ever get it active again to edit it... More than once I've had to log out, log in to Unity, edit it, log out, log in as Gnome Shell (preferred DE), and go to town from there... Meh.

---

### Post by cariboo on 2012-03-12
You can edit printer names, but you will lose the printing history, see the screen shots. As far as editing network connections, I can edit my wired connection when offline. I'm using Unity, and haven't tried to any of it running gnome-shell.

---

