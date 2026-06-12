---
title: "Synaptic repositories vs. sources list"
date: 2006-11-01
forum: Repositories &amp; Backports
---

### Post by Bartender on 2006-11-01
Good day -
Since I'm on dial-up at home, I've been experimenting with Ubuntu for over a year without learning anything about updating, repositories, etc.  I talked a friend into Ubuntu'ing his old Dell.  He's got DSL and suddenly I've gotta get up to speed.  The u.s. servers have been unresponsive the last few days for some reason and I don't know if we should tweak his list or wait a few days to see if there's any change?
According to The Official Ubuntu Book, all I've gotta do to enable additional repos is open Synaptic, go to Settings>Repositories, then scroll down the list, check off the unchecked boxes, and click "Add".
There must be more to it than that from all the discussions I see about editing the sources.list.  On my own PC I checked all those boxes, closed out, rebooted the PC, and as far as I can tell my sources.list is the same as it was when I installed Dapper.  What is the difference between checking off boxes in Synaptic vs. manually editing sources.list?
Also, ubuntudemon's recommended list at the top of this section of the forum has some directions that confused me.  Why the extra command line steps?  How come you can't just save the edited sources.list?

EDIT: I just realized that if you click on the "Add" button first you get the 4 channels, 6.06 LTS, 6.06 LTS Security, 6.06 LTS Updates, and 6.06 LTS Backports.  If you just go down the list and don't touch the "Add" button, are these the same channels?  It kinda looks like they are but then why the "Add" button?
All I did was add check marks to the list that shows when you first open this window.

---

### Post by jpeddicord on 2006-11-01
The repositories directly edit sources.list for you. All you should have to do is check them all, and then close the window. If it asks you to reload, reload, but if not, then hit Reload from Synaptic.

---

### Post by aysiu on 2006-11-01
Synaptic edits the sources.list directly, but even if you check all the boxes, there are some repositories you can never enable through Synaptic.

If, for example, you want the PLF repositories, you'd have to add those in manually. But I believe you can get Commercial, Universe, and Multiverse all through checkboxes--that's quite a lot of software available!

---

### Post by Bartender on 2006-11-02
Thanks for the help.  I've been reading up on this and think I understand a little better.
My friend with the DSL connection e-mailed me this morning.  Everything seemed to be back to normal.  He was able to update at his typical speeds, about 160 Kbps or so.  That's a relief!

---

