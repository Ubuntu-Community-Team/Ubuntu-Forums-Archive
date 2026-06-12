---
title: "Open Source Backup Utility Development"
date: 2011-04-23
forum: The Cafe
---

### Post by darkfeline on 2011-04-23
To me, one of the most troublesome aspects of using multiple computers is keeping files synced; this applies especially to rc files and the like, but also certain projects I may be working on.  Cue my project idea: chronica ([http://sourceforge.net/projects/chronica/](http://sourceforge.net/projects/chronica/)).

The main idea is to provide a utility which serves as a wrapper for rsync.  Now, rsync is great and awesome, but certain problems arise when writing scripts to sync files with rsync across a USB drive or Dropbox to multiple computers, especially if the files don't go to the same place on each computer, e.g. on my desktop my .vimrc file may go in /home/user1 and on my laptop it goes in /home/user2, or I want to run rsync with different options according to the file, e.g. I want to preserve file ownership on this machine but not that.

chronica allows you to set profiles for different machines and pull/push to sync files.  For example, after I change my .bashrc on machine A, I push it to my USB drive with profile A, and I then go to my laptop and pull it from my USB drive with profile B.

Right now chronica is just usable, and very rough (no input checking, error checking, little documentation), though I hope to polish it up and maybe add a simple GTK interface to manage profiles and syncing.  This is one of my first open source projects, so please give my any ideas, suggestions, advice, criticisms you may have!

---

