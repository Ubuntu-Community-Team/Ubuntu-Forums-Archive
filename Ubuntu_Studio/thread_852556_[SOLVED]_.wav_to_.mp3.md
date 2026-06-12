---
title: "[SOLVED] .wav to .mp3"
date: 2008-07-07
forum: Ubuntu Studio
---

### Post by AnLGP on 2008-07-07
Hello,

I have a player on my website that can only play mp3 files.  How do I convert them from .wav to .mp3?  I have GRIP installed but can't quite seem to figure it out.

---

### Post by Stochastic on 2008-07-07
try using soundconverter ```
sudo apt-get install soundconverter
```
it's pretty straightforward.

---

### Post by AnLGP on 2008-07-07
SoundConverter 0.9.7
  using Gstreamer version: 0.10.19, Python binding version: 0.10.12
required gstreamer element 'decodebin' not found.

---

### Post by Stochastic on 2008-07-07
which repositories do you have enabled in System -> Administration -> Software Sources ?

Edit: hmm, I just read your signature, looks like your error may be debian specific.

---

### Post by AnLGP on 2008-07-07
I'm using debian.  I don't know how to view that would it be under sources.lst?

# deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) lenny main

deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) lenny main
deb-src [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) lenny main

deb [http://security.debian.org/](http://security.debian.org/) lenny/updates main
deb-src [http://security.debian.org/](http://security.debian.org/) lenny/updates main

---

### Post by Stochastic on 2008-07-07
just for clarification, the error you posted, is it from the apt-get install command, or is it an error you receive while trying to run soundconverter?

---

### Post by AnLGP on 2008-07-07
while trying to run soundconverter

---

### Post by Stochastic on 2008-07-07
try looking for which package in your repos has the decodebin file

```
apt-file search decodebin
```
you may need to install apt-file first for this command to work

---

### Post by AnLGP on 2008-07-07
linux:/home/steve# apt-get install file
Reading package lists... Done
Building dependency tree       
Reading state information... Done
file is already the newest version.
file set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
linux:/home/steve# apt-file search decodebin
bash: apt-file: command not found

---

### Post by Stochastic on 2008-07-07
you did ```
apt-get install file
```

you should have done ```
apt-get install apt-file
```

---

### Post by AnLGP on 2008-07-07
ts-decodebin.html
gstreamer0.10-plugins-base: /usr/lib/gstreamer-0.10/libgstdecodebin.so
gstreamer0.10-plugins-base: /usr/lib/gstreamer-0.10/libgstdecodebin2.so
gstreamer0.10-plugins-base-dbg: /usr/lib/debug/usr/lib/gstreamer-0.10/libgstdecodebin.so
gstreamer0.10-plugins-base-dbg: /usr/lib/debug/usr/lib/gstreamer-0.10/libgstdecodebin2.so
gstreamer0.10-plugins-base-doc: /usr/share/gtk-doc/html/gst-plugins-base-plugins-0.10/gst-plugins-base-plugins-decodebin2.html
gstreamer0.10-plugins-base-doc: /usr/share/gtk-doc/html/gst-plugins-base-plugins-0.10/gst-plugins-base-plugins-plugin-decodebin.html
gstreamer0.10-plugins-base-doc: /usr/share/gtk-doc/html/gst-plugins-base-plugins-0.10/gst-plugins-base-plugins-plugin-decodebin2.html
libgstreamer-perl: /usr/share/doc/libgstreamer-perl/examples/manual/decodebin.pl
pitivi: /usr/lib/pitivi/python/pitivi/elements/singledecodebin.py
python-gst0.10: /usr/share/doc/python-gst0.10/examples/decodebin.py
python-gst0.10: /usr/share/gst-python/0.10/examples/decodebin.py
linux:/home/steve#

---

### Post by Stochastic on 2008-07-07
try installing a couple of the basic ones and see if the error goes away ```
sudo apt-get install gstreamer0.10-plugins-base python-gst0.10
```

---

### Post by forger on 2008-07-07
I'm afraid debian lacks some restricted formats like mp3...
[http://forums.debian.net/viewtopic.php?t=15173&view=previous&sid=307423d330f1321578d74f8453fc57ea](http://forums.debian.net/viewtopic.php?t=15173&view=previous&sid=307423d330f1321578d74f8453fc57ea)

[http://www.debian-multimedia.org/](http://www.debian-multimedia.org/)

---

### Post by AnLGP on 2008-07-07
linux:/home/steve# soundconverter
SoundConverter 0.9.7
  using Gstreamer version: 0.10.19, Python binding version: 0.10.12
  using gnomevfssrc
  'lame' element not found, disabling MP3.
output_mime_type_ogg_vorbis
Queue done in 0s

---

### Post by Stochastic on 2008-07-07
forger is right about mp3 support in debian, you'll need to install lame somehow.  As for soundconverter, did a GUI popup for you to use or is your version lacking the GUI?

---

### Post by AnLGP on 2008-07-07
A GUI popped up.  Any idea how to install lame?

---

### Post by Stochastic on 2008-07-07
the [www.debian-multimedia.org](www.debian-multimedia.org) repository that forger linked to will most likely have it.  You'll want the gstreamer-lame version if there is such a thing in that repo.  You really should be talking about this on the debian forums rather than the ubuntu forums.

edit: I just looked and once you've added that repo you'll want the gstreamer0.10-lame package

---

### Post by forger on 2008-07-07
No offense, but if you ask me, you should be trying ubuntu first before trying out debian, seems you still don't know how to do "simple" tasks on your own, which should be necessary for a debian user, such as adding new sources, and ubuntu has all of these inside its repositories, plus they make sure most of the packages in stable releases work

It's just my opinion, no hard feelings I hope :)

---

### Post by AnLGP on 2008-07-07
I tried Ubuntu for 10 months before I tried out Debian.  :)  I realize that's not a whole lot of time but I do know how to edit the sources.list and can install things fine if they're in packages (which they usually are) or if I can do a simple apt-get install ....  which is all I have to do most of the time.  It's when I've got to run around like a goose when things get a bit complicated.  I don't mind the learning curve.

---

### Post by forger on 2008-07-07
Ah, well then, read on! :D

---

### Post by AnLGP on 2008-07-07
yeah.  btw, no offense taken and I solved the problem.

---

### Post by Stochastic on 2008-07-08
How did you end up solving the probelm? (it's customary to post it so that the next person who reads the thread, with the same issue, can fix it without tracking you down to ask)

---

### Post by AnLGP on 2008-07-08
I did this:

sudo apt-get install soundconverter gstreamer0.10-plugins-base python-gst0.10

then:

added the appropriate sources.list from here to my sources.list

[http://www.debian-multimedia.org/](http://www.debian-multimedia.org/)

then:

gstreamer0.10-lame package

---

