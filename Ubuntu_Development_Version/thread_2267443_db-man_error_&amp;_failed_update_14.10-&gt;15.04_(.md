---
title: "db-man error &amp; failed update 14.10-&gt;15.04 (grub removed)"
date: 2015-03-01
forum: Ubuntu Development Version
---

### Post by enricobe on 2015-03-01
[LEFT][COLOR=windowtext][FONT=&amp][COLOR=windowtext][FONT=Calibri]Hello.[/FONT][/COLOR][/FONT][/COLOR]
[COLOR=windowtext][FONT=&amp][COLOR=windowtext][FONT=Calibri]Today I have upgraded my Ubuntu 14.10 to 15.04. I would like to help in testing :) .[/FONT][/COLOR][/FONT][/COLOR]
[COLOR=windowtext][FONT=&amp][COLOR=windowtext][FONT=Calibri]I have launched the upgrade via terminal using[/FONT][/COLOR]
[/FONT][/COLOR][/LEFT]
```
[LEFT][COLOR=windowtext][FONT=&amp][COLOR=windowtext][FONT=Calibri]Update-manager -d[/FONT][/COLOR]
[/FONT][/COLOR][/LEFT]

```[LEFT]
[COLOR=windowtext][FONT=&amp][COLOR=windowtext][FONT=Calibri]I have followed the instructions and everything worked fine until a dbus error. I have taken a photo with my smartphone because the "print screen" didn't work.[/FONT][/COLOR][/FONT][/COLOR]
[COLOR=windowtext][FONT=&amp][COLOR=windowtext][FONT=Calibri]Here is the db-man error:[/FONT][/COLOR][FONT=Calibri] 
[/FONT][SIZE=2]http://i58.tinypic.com/aaxa94.jpg[/SIZE]
[/FONT][/COLOR]


[COLOR=windowtext][FONT=&amp][COLOR=windowtext][FONT=Calibri]Here  is the error when I tried to use the print screen function (in English  the message could be translated in "impossible to take a screenshot.  Impossible to create the file. Choose another path and retry".[/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=windowtext][FONT=&amp][FONT=Calibri] [http://i62.tinypic.com/2i6ndr9.jpg](http://i62.tinypic.com/2i6ndr9.jpg)

[/FONT]
[/FONT][/COLOR]
[COLOR=windowtext][FONT=&amp][COLOR=windowtext][FONT=Calibri]Anyway, the screenshot has actually been saved, but when I tried to open the image the following message appeared.[/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=windowtext][FONT=&amp][FONT=Calibri] [http://i58.tinypic.com/rlamug.jpg](http://i58.tinypic.com/rlamug.jpg)

[/FONT]
[/FONT][/COLOR]
[COLOR=windowtext][FONT=&amp][COLOR=windowtext][FONT=Calibri]Then I have closed the db-man  error, and the installation has continued normally. At the very end of the process, before the clean, the following error has been shown and now i can't start Ubuntu. Grub has been removed from my PC and now starts only Win8.1
[http://i57.tinypic.com/w6wemv.jpg](http://i57.tinypic.com/w6wemv.jpg)

[COLOR=windowtext]The dpkg --configure [/COLOR]-a has n[COLOR=windowtext]ever been started[/COLOR]
I don't know if  this can help, but this is my experience in the upgrading process :([/FONT][/COLOR][FONT=Calibri] Help me to restore my Ubuntu please :P
[/FONT][/FONT][/COLOR][/LEFT]

---

### Post by enricobe on 2015-03-01
Ok, i've restored my Ubuntu ;) 

I used the Boot Repair Utility ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) but it didn't work. So i followed the instructions in the boot-repair window which suggest to launch the following command FROM WINDOWS.
```
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
```
and now grub2 boots correctly.

About the bug of man-db, This is: [https://bugs.launchpad.net/ubuntu/+source/man-db/+bug/1422425](https://bugs.launchpad.net/ubuntu/+source/man-db/+bug/1422425)

Anyway, when i restored grub and has been able to boot ubuntu, I've seen that it's 15.04 so the installation has been completed correctly.

---

