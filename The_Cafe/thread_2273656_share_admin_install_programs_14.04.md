---
title: "share admin install programs 14.04"
date: 2015-04-14
forum: The Cafe
---

### Post by th1bill on 2015-04-14
Setting a Lenovo T60 up for a 9 year and 6 year old little girls.  I have given Admin to the mother and as I install games I seem not to get them in for the girls to play with.  Several are XP games that run in wine but I also plan to install a lot more games from get deb but having set mom as admin and the girls as regular, all installs are done from the admin account and really need help.

Thank you in advance for your help.

---

### Post by TheFu on 2015-04-15
By default, WINE installations go under the $HOME for the account used.
I've never tried to setup any WINE programs for more than 1 userid, but I would think .... 

This is just a guess:
* create a UNIX group, call it "games"
* Place all the userids into that group.
* Create a directory structure to hold the shared WINE games - NOT inside any HOME for any userid - perhaps /opt/games?
* Make certain there is enough storage there.
* setup the WINEPREFIX to be /opt/games for every userid involved [http://wine-wiki.org/index.php/WINEPREFIX](http://wine-wiki.org/index.php/WINEPREFIX) has more details. export WINEPREFIX=/opt/games
* Modify the permissions on the top level /opt/games - chgrp -R games /opt/games; sudo chmod -R g+swX /opt/games
* Now do all the installations again.
* for every game, make a tiny shell script to set the WINEPREFIX and run wine /opt/games/.... full-path-to-program.exe

Anyway, that would be how I attacked this - don't know if it will work or not. Sorry.

Google found these:
* [http://ubuntuforums.org/showthread.php?t=917422](http://ubuntuforums.org/showthread.php?t=917422)
* [http://www.linux-magazine.com/Online/Features/Practical-Wine](http://www.linux-magazine.com/Online/Features/Practical-Wine)
* [http://plug.org/pipermail/plug/2013-May/030404.html](http://plug.org/pipermail/plug/2013-May/030404.html)

What have you tried already?

---

