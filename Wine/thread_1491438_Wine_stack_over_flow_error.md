---
title: "Wine stack over flow error"
date: 2010-05-23
forum: Wine
---

### Post by aprillia99 on 2010-05-23
ok TY i got the .DLL file i needed can anyone tell me why this program  isnt running

******************
 wine /home/kyle/Desktop/LeagueOfLegendsDownloader04_27_2010.exe
err:seh:setup_exception_record stack overflow 1868 bytes in thread 0019  eip 7bc3f33e esp 00c80be4 stack 0xc80000-0xc81000-0xe80000
err:seh:setup_exception_record stack overflow 824 bytes in thread 0009  eip 7bc81c06 esp 00a80ff8 stack 0xa80000-0xa81000-0xc80000
kyle@kyle-laptop-Asus:~$ 
***************
can any one shade some light on this for me very appreciated 
Ty

EDIT

This is a installer for a game downloader, the game is league of legends  if that matter at all.

---

### Post by cogadh on 2010-05-24
The game name does matter, since that game does not really work in Wine:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=10436](http://appdb.winehq.org/objectManager.php?sClass=application&iId=10436)

---

