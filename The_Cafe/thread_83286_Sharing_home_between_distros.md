---
title: "Sharing /home between distros"
date: 2005-10-28
forum: The Cafe
---

### Post by CurlyChris on 2005-10-28
When I moved to Ubuntu from MEPIS, roughly 6 months ago (Mepis 3.3 refused to play nicely with my laptop internal wireless card for no obvious reason so I jumped ship), I simply reused my Home folder.  This resulted in a few minor legacy "issues," such as having an entry for NVidia drivers in my System > Preferences menu (how can I remove this?) and an obsolete folder for KDE stuff (which I deleted), but nothing problematic. 

Over the summer I upgraded from a 40G to 80G HDD as I was rapidly running out of space in my /home partition, and this gave me the opportunity to repartition from scratch, so I gave myself a nice 30G to play with for /home, leaving enough left over to still dual boot with XP (I need it for work) and have a spare 7G to play with at some point..... ;) 

That point has now arrived, so I've decided to get hold of SUSE 10 OSS to stick on the spare partition, see what it's got vs Breezy, have a play and further my linux experience.  I installed last night, opting to share not only the /home partition with Ubuntu, but my /home/username folder too....

When my shiny new SUSE desktop came up, I then realised my mistake! :) 

My questions to all you multi-linux booters out there are, do you have a separate folder for each distro?  Or do you not bother sharing /home at all?  Or do you do something else?

On reflection, the 'separate folder' option seems to be the safest way to multi-boot distros, as the config files for applications within each distro are kept separate from each other.  So I could have /home/username_for_Breezy, /home/username_for_SUSE, etc.

But what about the need to just have a single version of stuff, such as Tomboy notes or GRAMPS data?  Do you then put in symbolic links to the equivalent file in your "master" Home folder for each application that needs it or is there a more elegant solution?

Interestingly, rebooting into Ubuntu was not a problem!  The only thing that had changed was that I had no desktop background!  The Applications menu was just as I'd left it, whereas I'd expected it to be filled with all the apps from the SUSE distro!

Anyway, just interested in your thoughts/experiences before I restore my imaged /home partition and reinstall SUSE.

Chris

BTW, it makes me feel quite geeky to say that I'm now _triple_-booting my laptop!! :p

---

### Post by Remmelas on 2005-10-28
Since Ubuntu i haven't bothered with multiple installs of linux, but, an easy solution is to share the /home partition, but make seperate users for each install.  Then, when I needed something to be 'the same' in each distro, i could us symlinks from the secondary install users directory to the originals, of course, there are permissions issues with that, but making sure both users are in a group with the same gid on both install (ie.  add a group called usershare with a gid of 1000 in both installs, then make sure that both users are part of that group on both installs).  make sure all files are +rw for the group, and group owned to the usershare group.  anyway... seperate, but shared, not quite the best of both worlds, but mostly safe if you really want to dual boot linux distros

---

### Post by CurlyChris on 2005-10-28
Thanks for your thoughts and suggestions, Remmelas!

Good to know I was thinking along the right lines, although I hadn't even considered the issue of permissions!! :???: 

Just to say that from what I've seen of SUSE so far, I don't think I'll be leaving Ubuntu any time soon  :)  but I'm still interested in playing with it for a little while longer!

Cheers

Chris

---

