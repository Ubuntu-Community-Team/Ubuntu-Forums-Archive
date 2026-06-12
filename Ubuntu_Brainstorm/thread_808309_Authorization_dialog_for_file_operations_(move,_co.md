---
title: "Authorization dialog for file operations (move, copy, edit)"
date: 2008-05-26
forum: Ubuntu Brainstorm
---

### Post by skullmunky on 2008-05-26
1. In Konqueror, Dolphin, and Nautilus, when you copy or move a file into a directory where you don't have privileges, prompt for password to sudo it, as in the OSX finder.  

2. Make an "Open as administrator ... " context menu item for editing files.  For example, R-click on /etc/X11/xorg.conf, "Open as administrator with Text Editor", which would mean "gksudo gedit /etc/X11/xorg.conf." 

This would be handy for new users and experienced ones alike, instead of the more cumbersome and not intuitively obvious

open terminal
gksudo nautilus
do stuff

---

### Post by smartboyathome on 2008-05-26
This should be possible now, since we have policykit. Though it may take some time to impliment it. This has been suggested before.

---

### Post by Gina on 2008-05-26
I do that with a bash script called by a launcher on the desktop or panel.  The standard password dialog is shown.  This is so small and compact that it could easily be included by default.  Or, as has been said implemented in the system.

I really do feel a better, more newbie-friendly (or other users) way of changing config files should be provided.

---

### Post by irrdev on 2008-05-27
This a great suggestion! I run a local web server on my machine for development purposes. Since Apache is configured to use /var/www as a web directly, I constantly have to start nautilus using gksudo. It would be much easier to have prompted graphical authorization from nautilus running using the local user.

---

### Post by mister_pink on 2008-05-27
Good suggestion, but thing number 2 is already done. Just install nautilus-gksu

---

### Post by skullmunky on 2008-05-27
Wow!  You're right, Mr. Pink ... that's uncanny, it's *exactly* what I was proposing.  Is that installed by default?  

Could it be added to Konqueror and Dolphin also?

---

### Post by Gina on 2008-05-28
> **mister_pink said:**
> Good suggestion, but thing number 2 is already done. Just install nautilus-gksuThank you for that - just the ticket :):)  Much better than my solution :lolflag:

It's not available in Add/Remove but is from Synaptic (I used the Search).  After installing you need to reboot to make it work.  "Open as administrator" item is added to the menu when right-clicking on a file.  I have just confirmed that it works as expected with the usual password dialog. :)

---

### Post by smartboyathome on 2008-05-28
> **skullmunky said:**
> Wow!  You're right, Mr. Pink ... that's uncanny, it's *exactly* what I was proposing.  Is that installed by default?  

Could it be added to Konqueror and Dolphin also?

Nope, nor will it be, because the devs take the stance that they should eliminate the need for it in Nautilus rather than include it. :(

Also, it doesn't work with Konqueror or Dolphin, they have separate plugins I think.

---

### Post by skullmunky on 2008-06-03
If anyone knows the plugins to do this in kde's browser, please let me know :)   

I'm confused - if the devs want to eliminate the need for this in nautilus, what's the alternative way to get the job done?

Any thoughts on thing # 1?

---

### Post by Wolki on 2008-06-03
> **skullmunky said:**
> I'm confused - if the devs want to eliminate the need for this in nautilus, what's the alternative way to get the job done?


Giving individual programs the capabilities to temporarily elevate themself for the required action. For example, to edit a config file in gedit, only the actual saving (and occasionally the opening) needs to be done as root, everything else (drawing the window etc) could be done by the program as a regular user. Such things can be done, as smartboyathome mentions, with PolicyKit.

And if the need to edit the config file in the first place can be removed, even better :)

> Any thoughts on thing # 1?

Basically the same, PolicyKit could also solve this, it would just need to be properly implemented in nautilus.

---

### Post by Awalton on 2008-06-12
You can follow the issue here:
[http://bugzilla.gnome.org/show_bug.cgi?id=490200](http://bugzilla.gnome.org/show_bug.cgi?id=490200)

Running Nautilus as root is scary. It's even worse now that we have GVFS, as you now have to start gvfsd and its daemon collection as the root user as well. And apparently it's currently buggy in the case that gvfsd isn't started as we can spin in an infinite loop. The fix for the infinite-loop bug has been committed, but not yet pushed to Ubuntu, however.

---

