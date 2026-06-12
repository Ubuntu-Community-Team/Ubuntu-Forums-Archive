---
title: "Apps Ubuntu is missing (a.k.a. I need a Project)"
date: 2008-01-22
forum: Ubuntu Brainstorm
---

### Post by zachtib on 2008-01-22
I've been trying to get back into programming, and I'm looking for some ideas for relatively small applications that would be useful to the Ubuntu (and Linux in general) community.

I've posted before about this, but it never hurts to get some more input.  I've yet to see an idea that really grabs me and makes me want to start developing.

So, if there's any projects that you want to see started, give me some ideas.

---

### Post by peabody on 2008-01-23
[http://ubuntuforums.org/showthread.php?p=4189647](http://ubuntuforums.org/showthread.php?p=4189647)

Chew on that and help me out.  I'm tired of people saying Linux should have a program like this, so I stared prototyping the 'hotstring' functionality of AutoHotKey.

---

### Post by maybeway36 on 2008-01-23
An fstab editor, with CIFS support! :)

---

### Post by zachtib on 2008-01-23
> **maybeway36 said:**
> An fstab editor, with CIFS support! :)

hmm... that's an interesting idea....

---

### Post by desperado666 on 2008-01-23
Iphoto clone is missing

---

### Post by UbuWu on 2008-01-24
> **desperado666 said:**
> Iphoto clone is missing

[http://packages.ubuntu.com/hardy/graphics/lphoto](http://packages.ubuntu.com/hardy/graphics/lphoto)

---

### Post by E-Jey on 2008-01-26
Something like [this]("http://dot.kde.org/1169588301/") for gnome. To make this application is not so hard I think, but all the applications have to use it..

---

### Post by Neon Lights on 2008-01-26
I agree with E-Jay, I actually saw this thread and thought of that. xD

---

### Post by zekopeko on 2008-01-26
it already exists in the form of:
[http://live.gnome.org/Mathusalem](http://live.gnome.org/Mathusalem)

but i think the development slowed down.

+1 for this project.

---

### Post by family on 2008-01-26
You Windows+iTunes users who have an iPod know that it was a pain transporting your library to Linux. So, lots of people went to the IpodDrive:\iPod_Control\Music\F00...F49
and copied all of that to a Music folder on the Desktop.
Jukeboxes (Amarok, Rhythmbox, Banshee) can use ID3 to get the filename, but there is no way to organize the music by artist, genre, year...
Essentially, I am proposing an iTunes music-organizer clone for Linux;
(this is all i have)
```

#!/usr/bin/env python
from ID3 import *
from easygui import *
from os import system
import string
msgbox("Podrok uses EasyGUI (Tcl/Tk) and PyID3 to organize your random music into a Artist>Album>Title folder hierarchy.")
msgbox("No, it does absolutely nothing as of now. Sorry.")
usr = enterbox("What is your username?", "Enter your username.", argDefaultText = "Username")
def sort():
	# this should later work by "pick a folder to fully organize", but i dont have a way to place
	# all objects in a folder into seperate python objects
	# did i forget to mention that i am a nooblet?
	fp = fileopenbox("Specify a file to organize.", "Specify FilePath")
	str(fp)
	info = ID3(fp)
	str(info.artist)
	apath = string.join(string.split(info.artist), "-")
	system('sudo mkdir /home/%s/%s' % (usr,apath))
	system('sudo mv -f %s /home/%s/%s/%s' % (fp,usr,apath,info.title))
while 1:
	sort()

```
I know its terrible. Don't laugh. That's why I asked you to do it :).

---

### Post by Ub1476 on 2008-01-26
> **family said:**
> You Windows+iTunes users who have an iPod know that it was a pain transporting your library to Linux. So, lots of people went to the IpodDrive:\iPod_Control\Music\F00...F49
and copied all of that to a Music folder on the Desktop.
Jukeboxes (Amarok, Rhythmbox, Banshee) can use ID3 to get the filename, but there is no way to organize the music by artist, genre, year...
Essentially, I am proposing an iTunes music-organizer clone for Linux;
(this is all i have)
```

#!/usr/bin/env python
from ID3 import *
from easygui import *
from os import system
import string
msgbox("Podrok uses EasyGUI (Tcl/Tk) and PyID3 to organize your random music into a Artist>Album>Title folder hierarchy.")
msgbox("No, it does absolutely nothing as of now. Sorry.")
usr = enterbox("What is your username?", "Enter your username.", argDefaultText = "Username")
def sort():
	# this should later work by "pick a folder to fully organize", but i dont have a way to place
	# all objects in a folder into seperate python objects
	# did i forget to mention that i am a nooblet?
	fp = fileopenbox("Specify a file to organize.", "Specify FilePath")
	str(fp)
	info = ID3(fp)
	str(info.artist)
	apath = string.join(string.split(info.artist), "-")
	system('sudo mkdir /home/%s/%s' % (usr,apath))
	system('sudo mv -f %s /home/%s/%s/%s' % (fp,usr,apath,info.title))
while 1:
	sort()

```
I know its terrible. Don't laugh. That's why I asked you to do it :).

I thought Songbird can do this? It works kinda much like iTunes to me.

---

### Post by family on 2008-01-27
I wouldn't mind giving Songbird a try at all, but all I want is this one feature. No, I didn't know it was an iTunes clone... Has it sorted any of your music?
Anyways, I suppose if an app can already do it, no sense in asking for it in a different form, so I withdraw my request :). 

Although I perfectly happy with Amarok, I still need a music sorter. No offense, but Songbird is all plugins and 'just get it all working' atm, but it's destined for greatness.

---

