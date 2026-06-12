---
title: "lxde is awesome (lightweight x11 desktop enviornment)"
date: 2008-03-29
forum: The Cafe
---

### Post by chris4585 on 2008-03-29
there's a new kid on the block that everyone should try, go to [http://lxde.sourceforge.net]("http://lxde.sourceforge.net") its pretty straight forward

add the repo in /etc/apt/sources.list

deb [http://people.linux.org.tw/~pcman/ubuntu/](http://people.linux.org.tw/~pcman/ubuntu/) ./

sudo apt-get update

sudo apt-get install lxde

logout and choose lxde session pretty cool i'm using 1/3 the ram i use with gnome! =)

please correct me if thats the wrong repo i might of mistyped it

---

### Post by mrgnash on 2008-03-29
Sounds great for older machines :)

---

### Post by PCMan on 2008-03-29
> **chris4585 said:**
> there's a new kid on the block that everyone should try, go to [http://lxde.sourceforge.net]("http://lxde.sourceforge.net") its pretty straight forward

add the repo in /etc/apt/sources.list

sudo apt-get update

sudo apt-get install lxde

logout and choose lxde session pretty cool i'm using 1/3 the ram i use with gnome! =)

Please don't use the repo now.
Some packages in this repo have some problems.
I'm rebuilding the new packages now, and I'll upload them later.

After I finish it today, I'll post the news in Ubuntu Cafe forum. Please stay tunned.

---

### Post by chris4585 on 2008-03-29
ok thanks for the update!

---

### Post by RadenMu'az on 2008-03-29
Thanks a lot  chris4585 telling the repo and PCMan for your repo. :)
Before I found your thread, I have wasted **_a lot_** of time installing LXDE. ???:

First, I tried really old lxsession1.1 and lxpanel2.4 DEBs from SourceForge, PCManFM 3.2 from standard Ubuntu repo and Openbox 3.4 DEBs from the official website. This LXDE is  slow and a little buggy. The old PCManFM drives me crazy as it refresh the screen, painting the wallpaper, thus makes my computer crawl.
So, I remove these old LXDE and PCManFM

Tried the LXDE installer script from [PCMan's thread]("http://ubuntuforums.org/showthread.php?t=707008"), but it sucks because it use the files from SVN. These SVN files are too unstable and buggy, I always got errors while running ./configure and make to these files. You **shouldn't** use this script as stable LXDE debs are on their way.

After some googling and thinking, I have done this to install LXDE
1. Install lxde-common DEB from [some debian guy's repo]("http://people.linux.org.tw/~andrew/debian/")
2. 'Checkinstall'ed pcmanfm3.9.1 and lxappearance TGZ downloaded from SourceForge and save the DEBs in my hard disk
3. Somehow managed to install openbox from PCMan's lxde svn installer script
4. Normally installed lxpanel and lxsession DEBs from [Baltix Linux's LXDE repo]("http://ftp.akl.lt/Linux/Baltix/Baltix-Ubuntu_packages/gutsy/LXDE/")

It took me long enough, maybe 2 days :x,
but hey, it works! Somehow close to or a bit faster than Xfce on my VIA C3 800Mhz box. :grin:

---

### Post by PCMan on 2008-03-29
> **RadenMu'az said:**
> Thanks a lot  chris4585 telling the repo and PCMan for your repo. :)
Before I found your thread, I have wasted **_a lot_** of time installing LXDE. ???:

First, I tried really old lxsession1.1 and lxpanel2.4 DEBs from SourceForge, PCManFM 3.2 from standard Ubuntu repo and Openbox 3.4 DEBs from the official website. This LXDE is  slow and a little buggy. The old PCManFM drives me crazy as it refresh the screen, painting the wallpaper, thus makes my computer crawl.
So, I remove these old LXDE and PCManFM

Tried the LXDE installer script from [PCMan's thread]("http://ubuntuforums.org/showthread.php?t=707008"), but it sucks because it use the files from SVN. These SVN files are too unstable and buggy, I always got errors while running ./configure and make to these files. You **shouldn't** use this script as stable LXDE debs are on their way.

After some googling and thinking, I have done this to install LXDE
1. Install lxde-common DEB from [some debian guy's repo]("http://people.linux.org.tw/~andrew/debian/")
2. 'Checkinstall'ed pcmanfm3.9.1 and lxappearance TGZ downloaded from SourceForge and save the DEBs in my hard disk
3. Somehow managed to install openbox from PCMan's lxde svn installer script
4. Normally installed lxpanel and lxsession DEBs from [Baltix Linux's LXDE repo]("http://ftp.akl.lt/Linux/Baltix/Baltix-Ubuntu_packages/gutsy/LXDE/")

It took me long enough, maybe 2 days :x,
but hey, it works! Somehow close to or a bit faster than Xfce on my VIA C3 800Mhz box. :grin:

OK, I got the repo work. You can install lxde via apt-get now.
[http://ubuntuforums.org/showthread.php?t=738958](http://ubuntuforums.org/showthread.php?t=738958)

---

### Post by Chilli Bob on 2008-03-29
Just installed LXDE.  Running just the system monitor, I'm using 149.7MB in Gnome, and 116.2MB in LXDE.  Not as big a change as I expected, but the desktop effects seem to run smoother.  (This is a fairly old PC - P3)
The windows look nice, but what is the story with the menu??  Black text on a black background?? Does anyone know how to change this?

---

### Post by PCMan on 2008-03-29
> **Chilli Bob said:**
> Just installed LXDE.  Running just the system monitor, I'm using 149.7MB in Gnome, and 116.2MB in LXDE.  Not as big a change as I expected, but the desktop effects seem to run smoother.  (This is a fairly old PC - P3)
The windows look nice, but what is the story with the menu??  Black text on a black background?? Does anyone know how to change this?

It's a weird bug caused by the background image of panel.
If you set gtk-theme-name in your ~/.gtkrc-lxde, this won't happen.
Otherwise, turn off the background image from prefrence dialog of lxpanel can fix this, too.
Besides, lxde-common by default install a gtkrc for you. I have no idea why yours doesn't work...

The memory usage is not very accurate since the gnome system monitor starts many gnome services that LXDE doesn't need at all. In addition, ubuntu starts many useless services by default. If you install LXDE on an clean debian system, the memory usage should < 100 MB.  In the most extreme case, the value will be 50 ~ 60 MB.

---

### Post by Chilli Bob on 2008-03-29
OK, I turned off the background image and it's working fine. It's quite a nice DE really. And PCmanFM rocks compares to Nautalis.

---

