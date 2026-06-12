---
title: "Two admin settings-boxes grayed-out"
date: 2009-11-30
forum: System76 Support
---

### Post by watchpocket on 2009-11-30
Hi all, I have a brand-new Wild Dog Performance desktop unit, model wilp6, arrived last week with Karmic pre-installed.

I've somehow caused two of my Administration settings boxes to be grayed-out.

My System --> Administration --> Login Screen Settings dialog box is completely grayed-out, and will not unlock when I click on the "Unlock" button.

Also the System --> Administration --> Time and Date setings dialog box is grayed-out, and when I click on the "Click to make changes" button, nothing opens.

I may have caused this by (unsuccessfully) trying to install gnome-shell via the terminal instead of with Synaptic Package Manager.

One other thing:  "Network Connections" no longer appears in the Notification area of the top panel.  

Basically I'm wondering where the best place to start troubleshooting for such things might be.  I may start by de-installing gnome-shell, unless anyone thinks that's not a good idea.  Thanks for any suggestions.

---

### Post by thomasaaron on 2009-12-01
> My System --> Administration --> Login Screen Settings dialog box is completely grayed-out, and will not unlock when I click on the "Unlock" button.

That is the way it is designed to be.

> Also the System --> Administration --> Time and Date setings dialog box is grayed-out, and when I click on the "Click to make changes" button, nothing opens.

It should pop up a password prompt when you click the little button with the key icon. If you can't see the prompt, it may be behind something. Sometimes gnome-shell does weird stuff. Move your mouse to the upper-right corner of the screen to show all of your desktops. That might reveal the prompt.
> 
One other thing: "Network Connections" no longer appears in the Notification area of the top panel. 

Please take a screenshot of your panel and attach it to this thread. It's an odd-looking icon. But again, it may just be some bug in gnome-shell. Sometimes my Empathy icon doesn't show up, and sometimes it does.

If you're using gnome-shell right now, bear in mind it is in the EARLY EARLY EARLY stages of development, and there are several nasty bugs. But it's fun.

---

### Post by watchpocket on 2009-12-02
It seems that all three of those problems I was having were a consquence of logging in in "failsafe" mode.  When I logged in to "GNOME", nonfailsafe mode, all three problems disappeared.

I still haven't been able to activate gnome-shell, though, and am not sure if I installed it correctly.  (I didn't know a few days ago that I 'd probably have been better off installing it via the synaptic Package Manager).  I have tons of "gnome-shell" files on my system, but haven't yet seen any change in the desktop's appearance.

I'm completely new to Ubuntu (though not to Linux -- only new to it on the desktop), and still need to spend some time just looking at & moving around the filesystem, etc. and familiarizing myself with things.

---

### Post by thomasaaron on 2009-12-03
Open a terminal and run...

gnome-shell --replace

If you want gnome-shell to start automatically, you have to use the above command as a Start Up Application. Let me know if you need further assistance with it.

---

### Post by calebbedford on 2010-03-19
Hey, I just had the same problem with the time and date settings appearing to be grayed out and unclickable.  It turns out you can click the little key icon even though it doesn't look like you can click it.  (You don't have to do the command for replacing the gnome shell.)

Good luck! ;)

---

