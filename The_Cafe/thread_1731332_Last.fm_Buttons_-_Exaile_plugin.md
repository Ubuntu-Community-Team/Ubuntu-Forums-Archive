---
title: "Last.fm Buttons - Exaile plugin"
date: 2011-04-17
forum: The Cafe
---

### Post by brunofin on 2011-04-17
Hi all,

I just finished developing this plugin for Exaile, Last.fm Buttons.

It adds Love and Ban buttons to Exaile's interface.

You can get it from here:

[http://sites.google.com/site/lastfmbuttonsplugin/](http://sites.google.com/site/lastfmbuttonsplugin/)

I hope you all like it! :D

Please read the plugin description, and if anything goes wrong, tell me.

[IMG]http://dl.dropbox.com/u/18425469/screenshot-small.png[/IMG]

---

### Post by NightwishFan on 2011-04-17
Oh, thats awesome. :) I might have to give it a try.

---

### Post by thilina1024 on 2011-08-29
Thanx brother. It works fine. :)

---

### Post by monuis on 2011-08-29
hi thanks for your information i am new to this forum

---

### Post by coronero on 2012-05-30
Trying with exaile 3.2.2 on ubuntu precise, and here's what I get in the terminal:


[FONT="Courier New"]Traceback (most recent call last):
  File "/home/llozan/.local/share/exaile/plugins/lastfmbuttons/__init__.py", line 115, in loveButtonActionPerformed
    self.love(tracktitle, trackartist)
  File "/home/llozan/.local/share/exaile/plugins/lastfmbuttons/__init__.py", line 234, in love
    print 'Session key: \'' + sk + '\''
TypeError: cannot concatenate 'str' and 'NoneType' objects[/FONT]


which I think means that the session key is null.

---

