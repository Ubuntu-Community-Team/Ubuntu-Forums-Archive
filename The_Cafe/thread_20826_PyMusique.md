---
title: "PyMusique"
date: 2005-03-18
forum: The Cafe
---

### Post by trentonjray on 2005-03-18
Thanks to 'Saint' Jon Johansen 

[http://fuware.nanocrew.net/pymusique/](http://fuware.nanocrew.net/pymusique/)

"Joined by Jon Johansen, the Norwegian programmer responsible for distributing DVD-cracking code in late 1999, the programmers say their "PyMusique" software is a "fair" interface for iTunes, primarily aimed at allowing people who use the Linux operating system to purchase music from Apple's store." 

For the lazy out there (myself included) who want to get the goods and not read the website.. simply paste this bad boy into /etc/apt/sources.list
```

deb http://fuware.nanocrew.net/pymusique/ deb/ 
```
packages required are listed below, all available via apt-get once you add the source above. Dependancies are on the main page but again.. sometimes its easier to read everything all at once, so they are listed below as well

**the PyMusique program**
pymusique,
python2.4-mcrypt
libfaad2
gstreamer0.8-faad
python2.4-vlc 

**Dependencies**
python
python-gtk2
gnome-python
python-mcrypt
python-libxml2
python-twisted
gstreamer-python or vlc-python (optional, preview support)

"Rock over London, Rock on Chicago.. news.com.com, tech news first!"

---

### Post by skabber on 2005-03-21
I get this when I try to launch it

```
:~ $ pymusique
sys:1: DeprecationWarning: Non-ASCII character '\xc3' in file /usr/bin/pymusique  on line 613, but no encoding declared; see http://www.python.org/peps/pep-0263. html for details
Traceback (most recent call last):
  File "/usr/bin/pymusique", line 854, in ?
    window = GUI()
  File "/usr/bin/pymusique", line 89, in __init__
    self.CreateMenu()
  File "/usr/bin/pymusique", line 246, in CreateMenu
    ui = gtk.UIManager(gtk.UI_MANAGER_MENUBAR)
TypeError: gtk.UIManager.__init__() takes exactly 0 arguments (1 given)
```

---

### Post by tim1 on 2005-03-22
I wrote about this a week ago ...  :neutral: 

Anyway, Apple changed iTMS so that pyMusique won't work anymore. It would be better if they released iTunes for Linux IMO  :smile: 

greets, tim

---

### Post by bored2k on 2005-03-22
[QUOTE=tim1]I wrote about this a week ago ...  :neutral: 

Anyway, Apple changed iTMS so that pyMusique won't work anymore. It would be better if they released iTunes for Linux IMO  :smile: 

greets, tim[/QUOTE]
 I dont get it. 

If youre buying from them, why do they block pyMusique?

---

### Post by ember on 2005-03-22
[QUOTE=bored2k]I dont get it. 

If youre buying from them, why do they block pyMusique?[/QUOTE]
 Because PyMusique doesn't really care about the DRM-thing (at least that's what I read)

---

### Post by Rancoras on 2005-03-22
Doesn't matter anymore because Apple closed the hole.

[http://apple.slashdot.org/apple/05/03/22/136207.shtml?tid=141&tid=3](http://apple.slashdot.org/apple/05/03/22/136207.shtml?tid=141&tid=3)

---

### Post by josue on 2005-03-22
[QUOTE=Rancoras]Doesn't matter anymore because Apple closed the hole.

[http://apple.slashdot.org/apple/05/03/22/136207.shtml?tid=141&tid=3](http://apple.slashdot.org/apple/05/03/22/136207.shtml?tid=141&tid=3)[/QUOTE]
 Indeed, the great feature of pymusique, is that it simply didn't add the DRM to the songs you bought and download, therefore you were free to do whatever you wanted with the songs.
But sure enough, Apple has blocked it.

---

### Post by poofyhairguy on 2005-03-22
[QUOTE=josue]Indeed, the great feature of pymusique, is that it simply didn't add the DRM to the songs you bought and download, therefore you were free to do whatever you wanted with the songs.
But sure enough, Apple has blocked it.[/QUOTE]


Everytime Apple does this, some Russian guys make money hand over fist....

---

### Post by blinksilver on 2005-03-22
the same day they made the fix, it was broken

---

### Post by poofyhairguy on 2005-03-23
[QUOTE=blinksilver]the same day they made the fix, it was broken[/QUOTE]

Yep. Its free again!

---

### Post by chronusdark on 2005-03-28
i get this error when apt-getting it:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pymusique: Depends: python (< 2.4) but 2.4-0ubuntu6 is to be installed
E: Broken packages

```

---

