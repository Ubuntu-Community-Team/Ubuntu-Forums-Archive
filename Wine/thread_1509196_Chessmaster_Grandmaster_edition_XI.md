---
title: "Chessmaster Grandmaster edition XI"
date: 2010-06-13
forum: Wine
---

### Post by aduplat on 2010-06-13
Hello:

I need help to install and run chesmaster XI. As I know, it is possible to install this program using wine, but I don't know how to do this. I read some threads about this issue, but I couldn't find any positive result. I don't have any experience using Wine. 

Thanks,

---

### Post by lykeion on 2010-06-14
Running Windows programs with wine is not really an Ubuntu question. 
But since you've no experience with wine I will give you some advice.

Some general help on using wine:
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Wine appdb is the first place you should check to see what works and what doesn't for a specific Windows program:
[http://appdb.winehq.org/index.php](http://appdb.winehq.org/index.php)

And here's a link to the entry for Chessmaster XI:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10198](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10198)

PS Have you tried any linux chess programs? Start Ubuntu Software Center and search for chess.

---

### Post by bbneo on 2010-06-19
I am also interested in getting Chessmaster Grandmaster edition running under Ubuntu 10.04.  In fact, I just purchased it online ($20) after reading that it apparently runs pretty well under WINE, but I did start out with a 9.10 Ubuntu system, and then performed an Ubuntu upgrade to 10.04 after it didn't seem to be working.  I am willing to do a clean Ubuntu 10.04 install if that might work...

I actually have a somewhat virgin clean Ubuntu 10.04 install which I will try the Grandmaster download on...  Wish me luck.

---

### Post by serdar132 on 2010-07-24
Well, I either can not run Chessmaster on ubuntu 10.04.

Please some one help, I just download ubuntu a week ago. I was a mac user, when my mac blowed up I have installed linuc on my desktop pc. It is always said that linux is a open community and people help eachother, I have seen maybe more then 10 entries in the dorum people saying they can not run chessmaster grandmaster edition!

Help please!

---

### Post by logan85 on 2010-10-07
Hi everybody.

After 3 hours of searching and installing uninstalling, finally i got chessmaster xi to work on wine.

first remove your wine directory totally, by:
sudo apt-get remove --purge wine
sudo apt-get autoremove

then delete all your wine files
rm -rf $HOME/.wine
rm -f $HOME/.config/menus/applications-merged/wine*
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm

Now install wine 1.2, here are the informations how you can do that: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

now follow this blog (it's for starcraft 2 but chessmaster will work this way, too)
[http://jeffhoogland.blogspot.com/2010/07/howto-starcraft-2-on-linux-with-wine.html](http://jeffhoogland.blogspot.com/2010/07/howto-starcraft-2-on-linux-with-wine.html)
and install directx, too, by:
./winetricks directx9

after this restart your pc, and chessmaster will work.
I have some issues with sound, i don't know why, but it's not working, so i would appreciate any help.

hope this will work for you too!

edit: I emulate a virtual desktop, and I have allow directx etc box clicked.

later edit: I upgraded to ubuntu 10.10 and sound works perfect...

---

### Post by eec on 2010-11-06
it gives game.exe problem and kills itself.

is there a solution? 
or what may cause the problem?

eec

---

