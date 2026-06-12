---
title: "[Solved] WoW Config.wtf reverts to default after logout/exit"
date: 2009-01-12
forum: Wine
---

### Post by gettensome on 2009-01-12
I just did a reinstall and followed a setup guide I hadn't used before.  The guide I followed claimed that installing the AddOn "ApplyToForhead"  may correct a graphical glitch that causes severe graphical glitches  when you move from outdoors to indoors during game play. This was the only difference in the basic installation instruction on WoWWiki!  Please note that the OpenGL Registry entry is what is really responsible for correcting said graphical glitching.

Now to the meat of the problem.  After a fresh install I wanted to get my config.wtf set up, but every time I would log out it would revert back to the installation defaults.

Curiously after each time I would login to the game AFTER first applying settings at the login screen,  Firestarter would notify my that an "Unknown process was attempting to contact a particular IP,  which I cant remember or locate within a log file.  Through repetition I noticed this and became suspicions of a virus/trojen/keylogger.

The solution, without reinstalling WoW is as follows;

Immediately access your WoW account and change your password.  If your account gets stolen, your account is not only gone, but so are your CD Keys as well.

1. delete all files related to the "ApplyToForhead" AddOn
2. Move you're warcraft folder from your ~/.wine/c_drive/program files/ directory to a path outside of your /.wine folder.
3. In Ubuntu, 'sudo apt-get remove wine'
4. rm -r ~/.wine
5. In Ubuntu 'sudo apt-get install wine
6. run winecfg, remember that you must also recreate the OpenGL String value just as before, set-up your application/graphics/audio tabs
7. Move your warcraft folder back to your wine Program Files folder

Done!  What you have just done is the wine equivalent of a complete reinstall of windows removing any possibilities that what ever could have been threatening your account is now gone.

---

### Post by Eviljim on 2009-01-12
It could also be innocent. Remember Warcraft does run its own "Warden" program to check for "illegal" third party addons. This could be the warden program getting data from the wow servers.

---

