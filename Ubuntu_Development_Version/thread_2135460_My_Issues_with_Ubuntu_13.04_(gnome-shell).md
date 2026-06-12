---
title: "My Issues with Ubuntu 13.04 (gnome-shell)"
date: 2013-04-14
forum: Ubuntu Development Version
---

### Post by techgs on 2013-04-14
I have installed Ubuntu 13.04 (beta 2 )  - Gnome Shell  ( 3.8.1  Updated )

Everything is working absoluately in stunning way.  

Boot time improvement is very clearly visible.  So to shutdown time.-- Congrats to development team.

Currently there are two  major issues which I could not find any solution.

1. Ubuntu Software Center  -  On the main page - left pane  nothing is visible.  ( Screen shot attatched.  )

2.  Whenever I do [I] sudo apt-get update 
[/I]  all the repository index files are re-downloaded -- ( Every time 25 mb gets downloaded with every  sudo apt-get update.  This is very annoying as I have limited internet bandwidth @ my disposal.  I have tried to change the update server etc. Nothing helped me.

Any help in this regard is highly appreciated.  

Notes : 1.   System is full updated uptill 14th April, 2013.  
2.  Both the problems are from the time of default installation only.  Gnome3 upgrade to 3.8.1 has not changed the situation.
3.  nVidia Graphic card - Upgrade from  open source video driver Nouveau to  Proprietory Driver nVidia 313 has not changed the situation.
4. No fonts changed.


My PC Specs are as follows.

1.  CPU : Intel Core i 3 540 ( microcode installed )
2.  Ram 8 GB
3.  Hard Drive :  500 GB Western Digital - Sata
4.  Graphic Card :  nVidia Geforce 210 - 1GB  (  Used Proprietory Driver nVidia 313 )
5.  Monitor : LED Kingston Tech Corporation ( Resolution and profile - automatically detected by Ubuntu )  - no ssues.

---

### Post by pfeiffep on 2013-04-14
I have a fully populated Software center in 13.04 (using gnome session fallback) - however I don't rely on software center or software updater in raring - instead I make use of CLI
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```

---

### Post by kurt18947 on 2013-04-14
Hmmm, I'm not sure what to tell you.  Ubuntu Software Center's left panel seems to fill in as expected.  I usually do CLI updates as well, the  only things that appear to download are packages which have changed.  Maybe try changing servers to see if that makes a difference?  I use one of 4 University hosted mirrors fairly near me.

---

