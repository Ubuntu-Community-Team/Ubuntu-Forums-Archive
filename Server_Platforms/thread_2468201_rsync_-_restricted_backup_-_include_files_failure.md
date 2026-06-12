---
title: "rsync - restricted backup - include files failure"
date: 2021-10-21
forum: Server Platforms
---

### Post by larry2311 on 2021-10-21
My use case is simple enough; to backup home dir without hidden files and without some other dirs, e.g. Downloads. But to also including a few of the hidden files.

One example of the hidden files is the firefox bookmarks directory.
So, the config includes "- .*" at the end of the list and has "+ .mozilla/firefox/xxxxxxxx.default-release/bookmarkbackups/*"
or hopefully more generically "+ .mozilla/firefox/*.default*/bookmarkbackups/*". The problem with the firefox files backup is that none of the bookmark files are backed up, nor anything else in the .mozilla directory which is the intent.

The current rsyncFiles.cfg file is show below. The logic is to exclude what I dont want, so that all else is backed up, achieved with the last line "- .*". This more recent approach to find a solution to the issue may well cause most of the lines beginning with "- " to not be needed. Anyway, thus far ... .

Tried dozens of suggestions from google searches to no avail. Please help!

The rsync command being used is:
```
rsync -navhsHm --exclude-from=$HOME/.rsync-backup/rsyncFiles.cfg  ~/  /media/backup/$HOME/
```

and the current "rsyncFiles.cfg" file contains:
```

#Directories

- /snap
- /deja-dup
- /Downloads
- /Public
- /Videos
- /dwhelper
- /efax-gtk-server
- /faxin
- /faxout
- /faxsent
- /my_docker

#Mounted filesystem
- .local/share/gvfs-metadata
- .Private
- .gvfs

#Session-specific directories and files
- .dbus
- .cache
- .Trash
- .local
- .Xauthority
- .ICEauthority
- .pulse-cookie
- .var
- .config
- .gconf
- .gnome2_private
- *.parts
+ .ssh
+ .cert
+ .bash*
+ .profile

#Recent Files
- ./local/share/recently-used.xbel

#Firefox
+ .mozilla/*
+ .mozilla/firefox/*
+ .mozilla/firefox/*.default-*/*
+ .mozilla/firefox/*.default*/bookmarkbackups/*
- .mozilla/***

#Other Applications
+ .thunderbird

- .*

```

---

### Post by sudodus on 2021-10-21
I would separate exclude and include patterns into two separate files called via

```

--exclude-from=
--include-from=

```

An alternative is to use the crude filter rules with + and -, but I think it is more difficult to manage.

```

--filter=

```

There is a lot written about filter rules in **[FONT=Courier New]man rsync[/FONT]**

---

### Post by larry2311 on 2021-11-01
Finally figured it out after much reading of the man pages and other forums with out success. I finally came across this site [https://sites.google.com/site/rsync2u/home/rsync-tutorial/the-exclude-from-option](https://sites.google.com/site/rsync2u/home/rsync-tutorial/the-exclude-from-option) which clarified what I was missing, and is arguably missed on the other pages I looked at.

so the current "homeDir.filter" file, which includes the desired files, and excludes what is not wanted, and works is:
```

#Directories

- /snap
- /deja-dup
- /Desktop
- /Downloads
- /Music
- /Pictures
- /Public
- /Videos
- /dwhelper
- /efax-gtk-server
- /faxin
- /faxout
- /faxsent
- /my_docker

#Hidden directories and files

+ /.ssh/
+ /.cert/
+ /.bash*
+ /.profile

#Firefox
+ /.mozilla/
+ /.mozilla/firefox/
+ /.mozilla/firefox/*.default*/
+ /.mozilla/firefox/*.default*/bookmarkbackups/
- /.mozilla/*
- /.mozilla/firefox/*
- /.mozilla/firefox/*.default*/*

#Other Applications
+ /.thunderbird/

- .*

```


Hope this is helpful and saves people looking to achieve something similar, a lot of time. Note, the order is important to get this to work.

---

### Post by sudodus on 2021-11-01
Thanks for sharing your solution :-)

---

