---
title: "associate .txt with native app"
date: 2009-12-23
forum: Wine
---

### Post by junapp on 2009-12-23
I have an legacy terminal based program I run in wine which has a feature which generates a text file and sends it down to the terminal and subsequently launches notepad to view it.

I had this same problem before and recall having to write a little script which would get called instead which would launch whatever the gnome default was. After a tweak to the .reg files it worked great. 

After my recent upgrade to Karmic (fresh install), I cannot find that little script in my backup, so I probably put it in sbin or some other place so I didn't end up backing it up (mostly just backup my home folder).

So, when running an application in Wine which tells Wine to open a .txt file, how do you make it so it runs whatever the gnome default is for opening that type of file? I've searched all over figuring that if I was able to find it once I should be able to find it again, but no luck yet.

---

### Post by junapp on 2009-12-23
this rings a bell although I'm getting "file could not open" error when applying the method to text files (posting here mostly as my own personal scratch pad).

[http://www.winehq.org/pipermail/wine-users/2008-January/028730.html](http://www.winehq.org/pipermail/wine-users/2008-January/028730.html)

---

### Post by junapp on 2009-12-29
*bump*

anyone have a solution for opening txt files with gedit from an application running in wine which tries to open in notepad?

edit:
this link has the attachments - almost working
[http://www.spinics.net/lists/wine/msg30423.html](http://www.spinics.net/lists/wine/msg30423.html)

---

### Post by junapp on 2009-12-29
just for the record, the file in the link above needed to be amended slightly to handle spaces in the path.
from
$cmd_open `winepath $url_file`;
to
$cmd_open "`winepath $url_file`";

---

