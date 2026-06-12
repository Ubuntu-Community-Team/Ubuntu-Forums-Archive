---
title: "help on installing moinmoin"
date: 2005-03-16
forum: Server Platforms
---

### Post by bonovoxpsu on 2005-03-16
hello - first post here from a happy ubuntu user.

i'm wondering just how to get moinmoin working.  i have apache, python, and moin all installed and really, i don't know where to go from here.  the instructions on moin's site don't really seem too helpful.  

i'm sorry for this vague post, but i'm not sure how to proceed.  thoughts?

---

### Post by Myles3 on 2005-03-16
Do you have to use moinmoin? If you don't consieder installing MediaWiki with PHP and MySQL. It is problely the best one out there.

---

### Post by bonovoxpsu on 2005-03-16
alright then - i'll give it a shot.  any caveats with installation?  or is it basically apt-get mediawiki and mysql?

---

### Post by alastair on 2005-03-16
Moin Moin is pretty easy to install - but it is not just a double-click on an icon and away you go. There's a doc in the package on how to do it (INSTALL.html) - and a python script automates most of it. It doesn't need anything else except a web server - this simplicity is attractive.

MediaWiki will also require some thought and reading. You will have to do some work - but it's a learning experience.

---

### Post by goofrider on 2005-03-17
[QUOTE=bonovoxpsu]hello - first post here from a happy ubuntu user.

i'm wondering just how to get moinmoin working.  i have apache, python, and moin all installed and really, i don't know where to go from here.  the instructions on moin's site don't really seem too helpful.  

i'm sorry for this vague post, but i'm not sure how to proceed.  thoughts?[/QUOTE]
 Read the following instructinos:

[http://moinmoin.wikiwikiweb.de/HelpOnInstalling/BasicInstallation](http://moinmoin.wikiwikiweb.de/HelpOnInstalling/BasicInstallation)
[http://moinmoin.wikiwikiweb.de/HelpOnInstalling/ApacheOnLinux](http://moinmoin.wikiwikiweb.de/HelpOnInstalling/ApacheOnLinux)

If u get an error like "*Invalid Python installation: cannot find /usr/lib/Python2.x/config/Makefile*", that means u need to install the **python-dev** package (u can use apt-get or Synaptic to do that.

---

### Post by bonovoxpsu on 2005-03-17
i'm basically looking for my own personal notes/journal/information software package.  a wiki seems to be the most flexible solution, but i could be wrong.  

as of now, i'm just poking around - i may try and just get this moinmoin setup, because i've fought with it for a couple days now and i just want to win...  :p

---

### Post by Myles3 on 2005-03-17
If you going to be using it for only personal things and even softwear why don't you use a Blog. Wordpress or MovableType are good. But if you want anything more  advanced you might want to try a CMS such as Drupal or PHP Nuke.

---

### Post by goofrider on 2005-03-18
[QUOTE=bonovoxpsu]i'm basically looking for my own personal notes/journal/information software package.  a wiki seems to be the most flexible solution, but i could be wrong.  

as of now, i'm just poking around - i may try and just get this moinmoin setup, because i've fought with it for a couple days now and i just want to win...  :p[/QUOTE]

Have u tried TomBoy? It's a desktop note-taking software for Gnome that supports internal page links just like a wiki, except it lives on your desktop, and it's a GTK# app. :)

[http://www.beatniksoftware.com/tomboy/](http://www.beatniksoftware.com/tomboy/)

Now it'll be absolutely sweet if it supports some kind of export/sync to wiki.... :-D

---

### Post by ihristov on 2006-10-19
If you are looking for personal use forget the apt packages, try the DesktopEdition
[http://moinmoin.wikiwikiweb.de/DesktopEdition](http://moinmoin.wikiwikiweb.de/DesktopEdition)

Easy as pie:

1. Download and unpack
2. start it
  ```
python main.py
```
3. fire a browser to
  [http://localhost:8080/](http://localhost:8080/)

and start using it

---

### Post by jfdill_2 on 2006-11-29
This thread is a bit old, but here's my 2c.

For small note taking, I recommend TiddlyWiki, it's a self-contained Javascript app, nothing to "install" besides a web browser :)  It's nice because you can save it to a thumb drive or whatever and you don't need any supporting software, works the same on Linux or Windows.  I often use this for customers to document network / e-mail settings, other things they need to know.  The only thing is that as pages get larger, it can become slow.

[http://www.tiddlywiki.com/](http://www.tiddlywiki.com/)

For more intensive note taking, I like DokuWiki, very easy to install, depends only on PHP, stores pages as files which makes it easy to sync to multiple locations.  On my ToDo list is to see if I can store in SVN and get it to run off a thumb drive.  It should be possible to run it with nanoweb for example.

[http://wiki.splitbrain.org/wiki:dokuwiki](http://wiki.splitbrain.org/wiki:dokuwiki)

SnipSnap is another one that I have played with that is Java-based and comes bundled with Jetty, which also makes it easy to run off a thumb drive provided JVM is installed, works on Linux or Windows.  What's nice is that it is sort of a blog / wiki hybrid.  The downsides are that it seems not to be very actively developed, and if you want to put it on the web you are going to need hosting that supports Java, inexpensive vhost-based hosting might be the best bet in that case.

[http://snipsnap.org/space/start](http://snipsnap.org/space/start)

If you want to shop around, WikiMatrix has a very nice comparison engine and includes nearly all of the Wiki software that is out there.  There are also discussion forums, and user comments and reviews.

[http://www.wikimatrix.org/](http://www.wikimatrix.org/)

---

### Post by mudfly on 2007-12-12
> **ihristov said:**
> If you are looking for personal use forget the apt packages, try the DesktopEdition
[http://moinmoin.wikiwikiweb.de/DesktopEdition](http://moinmoin.wikiwikiweb.de/DesktopEdition)

Easy as pie:

1. Download and unpack
2. start it
  ```
python main.py
```
3. fire a browser to
  [http://localhost:8080/](http://localhost:8080/)

and start using it

Thank you for pointing out this project to me, sir! Too bad the last release is over a year old now. I hope they update the DE with 1.6 when its released. :KS

---

### Post by dokudoug on 2008-01-18
Bitnami's DokuWiki stack rocks! [http://bitnami.org/search?q=dokuwiki](http://bitnami.org/search?q=dokuwiki) Easy to install--only one commandline step and a few clicks--and you're there! Ooh, it took me right back to Mac OS 7.1.You know, this free software lark might really take off!

I tried moinmoin's desktop version first, downloaded from here: [http://moinmo.in/DesktopEdition](http://moinmo.in/DesktopEdition) but both the .zip and .tbz archives presented for download failed to unpack and I just gave up, there and then. Good decision.

Let's face it, some people like a complicated install: e.g. [http://www.linuxadmin.dk/blog/?cat=4](http://www.linuxadmin.dk/blog/?cat=4) and some don't. Me, I just want to get on with my content, and dokuwiki on bitnami is lovely. Hats off! And thanks to jfdill_2 for pointing me to it.

---

