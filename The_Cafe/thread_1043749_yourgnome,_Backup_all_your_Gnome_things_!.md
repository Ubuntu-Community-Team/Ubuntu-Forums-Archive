---
title: "yourgnome, Backup all your Gnome things !"
date: 2009-01-18
forum: The Cafe
---

### Post by mAbuYusuf on 2009-01-18
[SIZE="4"]**yougnome** allow to backup all things relative to Gnome on your Linux Machine ! it backup them in a single .tar.gz file, then restore them any time you need.

**yourgnome2** is now also available !, and with a GUI !
[/SIZE]

[COLOR="Navy"]**Download:** [yourgnome version 2 with GUI]("http://code.google.com/p/yourgnome/downloads/detail?name=yourgnome2.tar.gz&can=2&q=")
**Documentation:** [How to (Install & Use) yourgnome2]("http://code.google.com/p/yourgnome/wiki/HowTo")[/COLOR]

**_by yourgnome you backup the following:_**

1- all your themes.

2- background you use settings.

4- gnome-panel settings.

5- bluetooth-manager settings.

6- evolution settings.

7- file-roller settings.

8- gnome-screensaver settings.

9- gnome-session settings.

10- gnome-terminal settings.

11- gnome-volume-control settings.

12- metacity & compiz settings.

13- update-manager & notifier settings.

14- totem settings.

15- network configuration set by Gnome.

16- screenlets !

And, many more .. !

---

### Post by toupeiro on 2009-01-18
Thats cool and all ... but wouldn't you cover all that and more by backing up $HOME?

I run a little [cpio]("http://linuxmanpages.com/man1/cpio.1.php") script once a night to a USB drive that pretty much preserves all of those things.

It looks like you've put a lot of work into this.  I'd be nice to see it extended. (so people wouldn't use 2 different backup tools when 1 should do.)

---

### Post by mAbuYusuf on 2009-01-18
> **toupeiro said:**
> Thats cool and all ... but wouldn't you cover all that and more by backing up $HOME?

I run a little [cpio]("http://linuxmanpages.com/man1/cpio.1.php") script once a night to a USB drive that pretty much preserves all of those things.

It looks like you've put a lot of work into this.  I'd be nice to see it extended. (so people wouldn't use 2 different backup tools when 1 should do.)

Not all things are in $HOME, for example the background image !
and also, What about some people who don't need to backup there home directories, just want to GNOME configurations ?
Just like, what about if you want to copy your Gnome to a friend ?

and many more situations you may need to copy only Gnome settings and themes and ....

and i agree that backing up the whole $HOME useful in many cases, also backing up only Gnome settings and themes and so, should be useful in some cases.

Waiting for any comments or bugs or ..

---

### Post by toupeiro on 2009-01-18
> **mAbuYusuf said:**
> Not all things are in $HOME, for example the background image !
and also, What about some people who don't need to backup there home directories, just want to GNOME configurations ?
Just like, what about if you want to copy your Gnome to a friend ?

and many more situations you may need to copy only Gnome settings and themes and ....

and i agree that backing up the whole $HOME useful in many cases, also backing up only Gnome settings and themes and so, should be useful in some cases.

Waiting for any comments or bugs or ..

My background image is in my home directory... I think most people who don't use default artwork will have their background image somewhere in their home directory.  I guess I can see the usefulness of a tool to extract your gnome settings for the sake of sharing those configurations with others, but I don't know if I'd push it as a backup solution is all.

It's just some friendly constructive criticism.  I'm just trying to point out that you increase its usefulness and userbase by not siloing it only to gnome configurations.  If I had to choose a backup tool, one that could get everything, or one that would just preserve my gnome settings, I'd go for the one that could get everything.  It would be awesome if the tool that did everything, gave me an option to just restore my gnome settings if thats all I needed, but if I needed more, than I'm in the clear as well. :)

---

### Post by wolfen69 on 2009-01-18
meh. i just backup my personal files, .mozilla, and .mozilla thunderbird. i'm good to go. all other tweaks only take a few minutes.

---

### Post by Grant A. on 2009-01-18
```

zip -r back-up.zip /

```

And if you put that Zip on a CD, and unpacked it into a fresh ext3 drive, wouldn't that work better than any back-up device?

---

