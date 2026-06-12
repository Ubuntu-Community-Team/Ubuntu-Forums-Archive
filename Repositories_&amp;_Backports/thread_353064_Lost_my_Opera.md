---
title: "Lost my Opera"
date: 2007-02-04
forum: Repositories &amp; Backports
---

### Post by C4ffeine on 2007-02-04
Hey guys, I'm running 6.06 (dapper drake), recently migrated from Suse. There were certain features of Firefox I wasn't happy with, so I decided to install Opera.
I updated my sources list and ran 'sudo apt-get install opera' and it installed correctly, I can run the command several times and it will say I have the newest version.
Problem is, Opera is not showing in my 'Internet' drop down box from the 'applications' menu.
So, can anyone tell me where my opera may have went? Searching just makes me more confused. As you can tell, I am new to this ^.^;
Thanks in Advance.

**Edit: I can now run Opera, but it's from Command line, when I type 'opera'. So it's installed in my system, I just can't locate it to put it in my panel. It also seems that I am having the same troubles in Opera as I am in Firefox, I cannot view thumbnails when uploading files :(**

---

### Post by Grantium on 2007-02-21
Happened to me too.  I went to System/Preferences/Menu Layout, found and right clicked on Opera, then clicked "Browse" located the file then hit ok.  It showed after that.

---

### Post by ugarth on 2007-02-23
Search for a .desktop file in this wiki page
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
If you do a similar one and put it in the /usr/share/application/ dir then I think you'll get your menu entry, but I don't know if gnome on Suse has any quirk that doesn't allow that.

---

