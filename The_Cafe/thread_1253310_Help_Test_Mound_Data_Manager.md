---
title: "Help Test: Mound Data Manager"
date: 2009-08-29
forum: The Cafe
---

### Post by jpeddicord on 2009-08-29
Over the past month or so I've been writing an application that can manage application data. It can take snapshots of data that your applications store, revert, and delete the stored data. For example, you could store a snapshot of your Firefox profile, and when something goes wrong, revert back to it. It works very well with games: if you mess up one of your save files or settings you can just revert the data for that game.

It's called [Mound Data Manager]("https://launchpad.net/mound"), and here is a nice pretty screenshot (0.3.99):
[IMG]http://img405.imageshack.us/img405/3374/mdm0399.png[/IMG]

When run, Mound will look for a line in application desktop files labeled X-UserData and parse it to figure out where data for that application is stored in the home folder. If it can't find that line, it will fall back to an entry in /etc/userdata which is installed when Mound is installed.

For example, a userdata line for Firefox would be:
  firefox ~/.mozilla/firefox

That data is then able to be managed using snapshots and other small features. Snapshots are taken using tar, so it should be pretty robust.

Here's where I need some help: I've tested with with a nice range of applications and conditions, but that obviously won't cover everything.
There are thousands of applications in the repositories, and it can't cover everything. It would be nice to see applications ship with X-UserData entries in their desktop files, but that's not a great short-term solution (especially with a product so young). Mound needs to ship more entries in the supplied /etc/userdata file. So, if you notice that an application you use doesn't show up in Mound, let me know what the appropriate UserData line would be.

I'd also appreciate testing of Mound's features. Things it should be able to do:
[LIST]
[*]Take new snapshots
[*]Revert to previous snapshots
[*]Export snapshots
[*]Import snapshots
[*]Delete snapshots
[*]Delete application data (see Application menu)
[*]Show application details (see Application menu)
[*]Prevent an application from being managed while it is still running
[*]Not crash (haven't found one crasher yet, but you never know)
[/LIST]

Translations are also **very** welcome, and can be done on Launchpad: [https://translations.launchpad.net/mound](https://translations.launchpad.net/mound)

**Download: [https://launchpad.net/mound/+download](https://launchpad.net/mound/+download)** (must install to use for the first time)
**PPA: [https://launchpad.net/~jpeddicord/+archive/mound](https://launchpad.net/~jpeddicord/+archive/mound)** (single package: mound-data-manager)

I'd appreciate if bugs were [filed on Launchpad]("https://bugs.launchpad.net/mound/+filebug"), but I'll be active in this thread as well.

Changelog of new features:
```
0.3.99
    * 0.4 RC
    * Several performance & bug fixes
    * Translatable

0.3.1
    * 0.4 series beta 1
    * New UI that makes better use of space, thanks ~rugby417 and ~laudeci
      for their suggestions and contributions
    * Importing/exporting of snapshots now works
    * Launchpad menu items available
    * More default userdata additions
    * Fix: XDG environment variables were ignored
    * Fix: load applications from all XDG data directories
    * Fix: Applications were sorted in a weird way, now alphabetical

0.2.1
    * Bugfix release for Jaunty

0.2.0
    * First (non-preview) release
    * Added Details menu item for extra information about the selected app
    * Baobab integration
```

Posted also on [http://jacob.peddicord.net/2009/09/mound-data-manager.html](http://jacob.peddicord.net/2009/09/mound-data-manager.html) (Planet Ubuntu) with some more technical details.

Hope you enjoy!

---

### Post by MaxIBoy on 2009-08-30
SWEET! I am definitely going to try this soon, if it works it would be awesome!

One thing though. Is this the kind of thing where it either works or it doesn't? Or is it the kind of thing where it either works or it destroys everything? As a developer, you'd have a pretty good idea of whether the kind of operations being done by your program introduce potential for clobberage.

---

### Post by hansdown on 2009-08-30
Sounds like a great idea jacobmp92.

wILL TRY AND TEST.

Thanks.

Sorry about the caps lock thing.

---

### Post by jpeddicord on 2009-08-30
> **MaxIBoy said:**
> One thing though. Is this the kind of thing where it either works or it doesn't? Or is it the kind of thing where it either works or it destroys everything? As a developer, you'd have a pretty good idea of whether the kind of operations being done by your program introduce potential for clobberage.

I've included a lot of safety checks to make sure that it won't accidentally destroy data. Taking snapshots is a completely safe operation. Restoring snapshots should be safe as well, as long as you haven't modified the snapshots outside of Mound. When you restore a snapshot, it will also prompt you to create another snapshot "just in case."

The delete data button obviously will delete the data for the application... so be very careful with that. I may have Mound take an automatic snapshot right before you use that action.

As an example, when it takes a snapshot of Firefox (on my machine anyway), it will run:
```
tar -cvzf /home/jacob/.local/share/mound-snapshots/snapshot-name.tar.gz -C /home/jacob .mozilla/firefox
```

When it wants to restore that snapshot:
```
tar -xvz -C /home/jacob /home/jacob/.local/share/mound-snapshots/snapshot-name.tar.gz
```

One thing to note, tar will **not** follow symlinks when it takes snapshots and restores them. It is possible to do so with a flag (-h I think) but there are too many possibilities to consider there. Snapshots will contain the symlinks themselves and not the locations they point to, which should be the expected behavior.

---

### Post by jpeddicord on 2009-08-31
Added another prerelease to the downloads and PPA. It contains even more checks to ensure "anti-clobberage" of your data.

Changelog:
>     * Second preview release
    * Better error handling when locations cannot be used
    * More safety checks
    * Offer to take a snapshot before data-changing operations
    * Main window can be scrolled with the mouse
    * Display the number of snapshots in the main view
    * Prevent duplicate snapshots

[https://launchpad.net/mound/+download](https://launchpad.net/mound/+download)
[https://launchpad.net/~jpeddicord/+archive/mound](https://launchpad.net/~jpeddicord/+archive/mound)

Testing appreciated. :)

---

### Post by jesumar on 2009-09-04
I just downloaded mound-0.2.0 and put it in /usr/share. After running "sudo python setup.py install" all worked fine but when clicking under "Aplications/Accesories/Mound Data Manager" nothing happens. When running it from the command line it says:

Traceback (most recent call last):
  File "/usr/local/bin/mound-data-manager", line 25, in <module>
    ui = MainUI(m)
  File "/usr/local/lib/python2.6/dist-packages/Mound/ui/__init__.py", line 63, in __init__
    self.details_ui = DetailsUI(mound_inst, self.builder)
  File "/usr/local/lib/python2.6/dist-packages/Mound/ui/details.py", line 49, in __init__
    self.lbl_app_information.connect('activate-link', self.open_snapshots_external)
TypeError: <gtk.Label object at 0xa4b6a54 (GtkLabel at 0xa689e50)>: unknown signal name: activate-link

What is the error ?

---

### Post by jpeddicord on 2009-09-04
Sorry about that. I programmed Mound on a Karmic system, unknowingly using a GTK 2.18 feature that is not available in Jaunty. I'll release a workaround in a couple of hours when I get home.

---

### Post by jpeddicord on 2009-09-05
Updated and tested on a Jaunty install. PPA packages are building as I type. If you would rather install from source, be sure to use --prefix=/usr as an argument to setup.py.

---

### Post by jesumar on 2009-09-05
Perfectly. I downloaded the updated version (mound-0.2.1), installed with prefix=/usr and it's running ok. I proceed testing.

---

### Post by jesumar on 2009-09-06
In the case of *some* games (like lbreakout2) what i want to snapshot are scores and they are in /var/games but when putting this path in /etc/userdata Mound says "A problem occurred. This application cannot be managed".

---

### Post by jpeddicord on 2009-09-06
True, there are some writable locations outside of home. The problem there arises with how to store them -- as soon as you step outside of the home directory you need to use absolute pathnames, which means that the snapshots are not portable to other users or systems.

---

### Post by jesumar on 2009-09-07
To jacobmp92.   Excuse me for being engaged in your affair, but this is linux ...
Portable to other users: I think your data and your preferences are primarily of your personal interest and sharing it with others is a secondary goal.
Portable to other systems: Maybe, but I think most people stay in a particular distro family. This is my case; I come from Ubuntu 8.04 to 8.10 to 9.04 and go to 9.10 Others are faithful to Fedora or Suse and so on. Certainly changes may occur.
So it's worthy of exploring the feasibility to collect any of our data, be where it may be, so Mound be trully useful.
Aside this discussion I don't know how to deal with TeXmacs.

---

### Post by jesumar on 2009-09-08
TeXmacs is easy: "texmacs ~/.TeXmacs".
 Another lines I have tested are:
"mplayer ~/.mplayer"
"vlc $CONFIG/vlc"
"cinelerra ~/.bcast"
"VirtualBox ~/.VirtualBox"
and just now I'm fighting with OpenOffice, where we set many options and preferences.

---

### Post by jpeddicord on 2009-09-08
Thanks, I've added those to trunk. The next release will most likely be 0.3.1. Planned features are a new UI (already done), importing/exporting snapshots, support for local/custom applications, and a slew of bugfixes.

---

### Post by jpeddicord on 2009-09-08
Thanks, I've added those to trunk. The next release will most likely be 0.3.1. Planned features are a new UI (already done), importing/exporting snapshots, support for local/custom applications, and a slew of bugfixes.

---

### Post by jpeddicord on 2009-09-13
Following up on my last post, 0.3.1 is available for download; see the first post for information and an updated screenshot. Tested on Karmic and Jaunty.

This finally brings import/export support, and a redesigned UI with the help of others.

Enjoy. Some other features may be added before 0.4, but they'll probably be minor compared to the new functionality in 0.3.1. Give it a try. :)

---

### Post by FuturePilot on 2009-09-13
This is awesome. It will make taking my settings to other computers easier :)

Edit:
Just thought of something. Would it be possible to add a custom snapshot directory? For example so it's on an external drive or something.

---

### Post by pt123 on 2009-09-13
is it possible to ignore some folders in the settings like .cache in Firefox, this way it will reduce the size of the snap shots?

---

### Post by jpeddicord on 2009-09-13
> **pt123 said:**
> is it possible to ignore some folders in the settings like .cache in Firefox, this way it will reduce the size of the snap shots?

Planning on adding something like that soon. Currently .cache isn't listed in any UserData lines, but there will be options for it soon.

> Just thought of something. Would it be possible to add a custom snapshot directory? For example so it's on an external drive or something.Symlink ~/.local/share/mound/snapshots to a drive location, or just use snapshot exports. I suppose this could be made an option.

---

### Post by jpeddicord on 2009-10-25
Finally after a long break, 0.3.99 is out. This is a release candidate for 0.4, which should be out in about a week.

Mostly just fixes and performance improvements. The major feature is that is is now [translatable]("https://translations.launchpad.net/mound").:)

There is one known bug that prevents the UI from updating after importing a snapshot, but it's already fixed in trunk.

---

