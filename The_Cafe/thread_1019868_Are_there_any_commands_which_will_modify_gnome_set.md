---
title: "Are there any commands which will modify gnome settings?"
date: 2008-12-23
forum: The Cafe
---

### Post by Mazza558 on 2008-12-23
See the thread title.

Specifically, is it possible to run a command to do things like:

- Add/change/remove panel applets in specific places
- Change gtk, panel and metacity themes
- Change wallpaper/other aspects of themes
- Add programs to "sessions"

It'd be cool if I could add these to a bash script.

---

### Post by Mazza558 on 2008-12-23
Anyone know?

---

### Post by chucky chuckaluck on 2008-12-23
this could be one of those times when gui > cli.

---

### Post by Mazza558 on 2008-12-23
> **chucky chuckaluck said:**
> this could be one of those times when gui > cli.

True.

It's so that if I release a theme or setup, running a script will result in people's desktops being identical to how I envisaged it.

Potentially it would even allow for entire new distributions being shared with a tiny script - that's what I want to persue.

---

### Post by unutbu on 2008-12-23
```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename /path/to/image.jpg
gconftool-2 -t string -s /desktop/gnome/background/picture_options scaled
```

These commands will change your background to image.jpg. (scaled)

I don't know the answer to your other questions off hand, but you might be able to find the answer by experimentation:

[list]
[*]You can use gconf-editor to search for variables you can change. (e.g. /desktop/gnome/background/picture_filename).
[*]You can also do similar command line poking around using this kind of command:
```

gconftool-2 -a --all-dirs /desktop/gnome/background
```
[*]Finally, you may be able to discover what files control sessions, gtk settions, the panel, themes etc by making a pristine test user
```

sudo useradd --create-home --shell /bin/bash test
```

Make a copy of certain likely directories```


rsync -a /home/test/.gconf/ /home/test/.gconf_orig/
rsync -a /home/test/.config/ /home/test/.config_orig/
rsync -a /home/test/.gnome2/ /home/test/.gnome2_orig/
```

Then making a change to the configuration, and then using a directory diff tool to see what changed. (I use emacs M-x ediff-directories; you should be able to find others in the repos if you need one.)
[/list]

---

### Post by Polygon on 2008-12-23
yeah, the person above me already said it. the command your looking for is gconftool.

---

### Post by Mazza558 on 2008-12-23
> **unutbu said:**
> ```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename /path/to/image.jpg
gconftool-2 -t string -s /desktop/gnome/background/picture_options scaled
```

These commands will change your background to image.jpg. (scaled)

I don't know the answer to your other questions off hand, but you might be able to find the answer by experimentation:

[list]
[*]You can use gconf-editor to search for variables you can change. (e.g. /desktop/gnome/background/picture_filename).
[*]You can also do similar command line poking around using this kind of command:

gconftool-2 -a --all-dirs /desktop/gnome/background
[*]Finally, you may be able to discover what files control sessions, gtk settions, the panel, themes etc by making a pristine test user

sudo useradd --create-home --shell /bin/bash test

Make a copy of certain likely directories

rsync -a /home/test/.gconf/ /home/test/.gconf_orig/
rsync -a /home/test/.config/ /home/test/.config_orig/
rsync -a /home/test/.gnome2/ /home/test/.gnome2_orig/

Then making a change to the configuration, and then using a directory diff tool to see whach changed. (I use emacs M-x ediff-dirctories; you should be able to find others in the repos if you need one.)
[/list]

Brilliant, thanks.

---

