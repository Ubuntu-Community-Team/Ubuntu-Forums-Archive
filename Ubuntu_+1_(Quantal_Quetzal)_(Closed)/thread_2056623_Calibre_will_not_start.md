---
title: "Calibre will not start"
date: 2012-09-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by David D. on 2012-09-11
On my Quantal install I downloaded Calibre from the Ubuntu Software Center.  When I try to open Calibre, it starts to load then slows my system to a crawl, almost unresponsive.  I do get a message (eventually) stating a script is unresponsive and asking if I want to continue or stop the script.  With the computer being so slowed, it does not respond to clicking on a selection.  I have to reboot to recover.

Is anyone else having a problem with Calibre?

Is there a way to troubleshoot and fix this, or do I just need to wait for updates to resolve the problem?

---

### Post by effenberg0x0 on 2012-09-11
> **David D. said:**
> On my Quantal install I downloaded Calibre from the Ubuntu Software Center.  When I try to open Calibre, it starts to load then slows my system to a crawl, almost unresponsive.  I do get a message (eventually) stating a script is unresponsive and asking if I want to continue or stop the script.  With the computer being so slowed, it does not respond to clicking on a selection.  I have to reboot to recover.

Is anyone else having a problem with Calibre?

Is there a way to troubleshoot and fix this, or do I just need to wait for updates to resolve the problem?

Is it loading/importing a very large collection of ebooks, or maybe a not-so-big library that is not hosted locally (over LAN/WAN)? I have experienced effects similar to those you mentioned in these two cases. 

Importing books to a library/ converting formats can be cpu intensive and time consuming. Once that is done, it gets faster. Have a look at the options, maybe it is set to auto convert all your media to some specific format (if you have a Kindle for example).

You can load calibre from the console and try to see if something relevant comes up in stdout. That would be the easiest option, sometimes it's enough. You can also use strace and even gdb, depending on your will and available time to spend on it. IMO, the best thing would be to contact the author directly, report the problem as best as you can, and ask him how you can help debug this. He will probably have an idea of the potential causes and ask you smarter / more direct questions. It would be faster than jumping blindly into gdb.  

One more thing: I'm using the version from this ppa:
```
deb http://ppa.launchpad.net/n-muench/calibre/ubuntu precise main
deb-src http://ppa.launchpad.net/n-muench/calibre/ubuntu precise main
```
I think it's more recent than the one in Precise/Quantal repos.

---

### Post by mc4man on 2012-09-11
Until a bug is fixed you need to run calibre in this env
LIBOVERLAY_SCROLLBAR=0

so from terminal (or create an alias
```
LIBOVERLAY_SCROLLBAR=0 calibre
```

From menu's you'd need to edit the .desktop, ignore the 'untitled document' that also tries to open
```
gksu gedit /usr/share/applications/calibre.desktop
```

Edit the Exec= line to this
```
Exec=env LIBOVERLAY_SCROLLBAR=0 calibre
```

Or you can remove the repo calibre & get the upstream version which provides it's own libs (google

[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/1005677](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/1005677)

---

### Post by cariboo on 2012-09-11
The version of Calibre in the repositories is kind of buggy, I use the version from the authors [web site]("http://calibre-ebook.com/download_linux"), just run the binary install script and enjoy.

---

### Post by David D. on 2012-09-12
I installed the version from the web site.

---

### Post by mdurham on 2012-09-12
> **David D. said:**
> I installed the version from the web site.

Well, did it work correctly?

---

### Post by David D. on 2012-09-13
Yes, it is now working correctly.

---

