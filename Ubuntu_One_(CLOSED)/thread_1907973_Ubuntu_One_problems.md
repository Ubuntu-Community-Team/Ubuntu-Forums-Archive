---
title: "Ubuntu One problems"
date: 2012-01-12
forum: Ubuntu One (CLOSED)
---

### Post by tomopotamus on 2012-01-12
Hey everyone,

As of late I've been having some problems with Ubuntu One.  Everything was working fine until a couple days ago, when I noticed that nothing was really being uploaded or downloaded to my account, although the little OSD message was appearing saying that it was.  After a while, I looked to see what percent the work was at and it said 6%.  It would stay there for awhile, but when I would look again, it would be at 2%.

I use the Ubuntu One indicator app and when I click on that to see what's going on, it will often just saying syncing or fetching meta data or something; but it seems like nothing is ever getting done.

When I run the u1sdtool command to look at the status, this is what appears:

```
tom@tom-laptop:~$ u1sdtool -s

(u1sdtool:10491): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(u1sdtool:10491): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(u1sdtool:10491): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(u1sdtool:10491): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
State: WAITING
    connection: With User With Network
    description: waiting before try connecting again
    is_connected: False
    is_error: False
    is_online: False
    queues: WORKING

```

That number after u1sdtool, in parenthesis, is often different.

I just ran the command again, and this is what appeared:
```
tom@tom-laptop:~$ u1sdtool -s

(u1sdtool:10537): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(u1sdtool:10537): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(u1sdtool:10537): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(u1sdtool:10537): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
State: CHECK_VERSION
    connection: With User With Network
    description: checking protocol version
    is_connected: True
    is_error: False
    is_online: False
    queues: WORKING

```

If I had to guess, I would say that the problem has something to do with those "theme engine" lines, but I don't know (yet!) what any of that means.

I've already tried reinstalling everything to do with Ubuntu One in Synaptic, but that didn't do the trick.  Any other help would be greatly appreciated!

ETA:  I should probably also mention that it appears Ubuntu One will connect and then disconnect a little bit later.

---

### Post by rft183 on 2012-01-14
I've been having problems with mine too.  I think it started after the last update I downloaded.  The client seems to be connecting and disconnecting over and over.  The popup notice comes up every so often, but always says the same thing.  I completely uninstalled ubuntuone (including deleting my keys) and reinstalled and it seems to be doing the same thing...

---

### Post by rft183 on 2012-01-19
So tomopotamus,have you figured out what is going on yet?  I haven't...

---

### Post by amodra on 2012-02-28
I hit the same warning when running emacs.  Fixed by
sudo apt-get install gtk2-engines-pixbuf

---

