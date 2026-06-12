---
title: "Re-Installing Photoshop Elements 7"
date: 2010-06-04
forum: Wine
---

### Post by llanitedave on 2010-06-04
My wife got a copy of Photoshop Elements 7 last winter, and we installed it in Wine on her AMD64 desktop running Karmic (Since upgraded to Lucid).  Sometime in the last month or so it started giving her trouble (she can't really tell me exactly what, but I suspect it was just a Wine configuration issue) and she tried to remove it and re-install.  It didn't work, and she didn't mention it to me until recently.

Now I'm trying to get it to install from the disk.  I've done a search and removed every file that has "photoshop" in its name.  I've put the cd back in the drive, and double-clicked on the Autoplay.exe icon.

The install window appears on the screen, and I click the "Install Adobe Photoshop Elements 7" button.


The install Shield Wizard appears after a couple of quick flashes, but the only  option it gives me is to ***Remove*** Photoshop Elements 7.

Thinking that there must still be residual files that its finding, I click "Next", and "Next" again on the confirmation window, and the "Remove".

The Status Bar begins to fill, and files being removed zoom by too quick to read, but then the process aborts, saying "The Wizard was interrupted before Adobe Photoshop Elements 7.0 could be completely uninstalled."

So now, I can't install the new application and I can't remove the old one.  I'm a bit stuck.  There has to be a workaround.
Isn't there?  :(

---

### Post by cogadh on 2010-06-04
Is PS Elements the only thing you have installed with Wine? If so, just delete the .wine directory from your wife's home directory and start with a fresh "fake Windows".

---

### Post by llanitedave on 2010-06-04
Thanks, cogadh.  I was thinking along those same lines.  That's all she had.

I've been having problems with Wine myself since the upgrade, but all I've got is a bit of freeware that would be easy to re-install.

---

### Post by MishMich on 2011-03-24
I was having the same problem.  I purged Wine, removed the .wine directory, removed all the menu items, and it still 'said' it was uninstalling - when it actually seemed to install - but then wouldn't run.  Is the registry file kept within the /home/user/.wine directory?  Or is there a configuration file kept somewhere in the root filesystem?  The config manager was empty.  Despite removing all the menu entries, when I re-install wine, they reappeared (including other programs I uninstalled).  The other thing I noticed was that there were lots (I mean seriously lots) of duplicate wine applications under the 'other' menu - and the only way I could think of shedding them was to copy the stuff I wanted out of there to a different menu, and remove it completely.

I did this three times, the third time I purged, deleted the wine directory, menu items & menus, ran everything from the command line, including the installation.  The terminal threw up a lot of complaints about missing image files.  The registration screen was very poorly formatted.  I found I could launch it again by checking the original menu item again - and it went straight through to the updater, which is running now.  I guess some things work beter from the command line?  But it was still not as smooth as the original install.

---

