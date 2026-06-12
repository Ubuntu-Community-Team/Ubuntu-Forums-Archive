---
title: "Thunderbird - Why use a different profile path?!"
date: 2008-11-04
forum: Ubuntuzilla
---

### Post by ethoms on 2008-11-04
I'm currently working on a way to synchronize (and backup) my profile (home folder) between Ubuntu and OpenSolaris. Actually I've finished, there are only a few exceptions that I need to make in grsync for it to work.... EXCEPT Thunderbird profiles will not be in common thanks to debian package maintainers changing the profile location. Everywhere else it's .thunderbird (makes sense), why has it been renamed to .mozilla-thunderbird in the debian/ubuntu packaged versions. ARGHHHH! :mad:

I don't suppose there is a way around this? Some way of changing the path setting?

---

### Post by ethoms on 2008-11-04
Got a good workaround! Link the debian profile path to the usual path, I don't know why I didn't think of this earlier.

```

#cd ~
#ln -s .thunderbird .mozilla-thunderbird

```

Of course link the other way around if .mozilla-thunderbird is the existing path.

---

### Post by nanotube on 2008-11-05
indeed, it's something quite weird and unexplainable... the only thing I found about it is this:
[http://kb.mozillazine.org/Profile_folder_-_Thunderbird#Linux_and_Unix](http://kb.mozillazine.org/Profile_folder_-_Thunderbird#Linux_and_Unix)
where mozilla guys just say that the debian/ubuntu build use .mozilla-thunderbird as default profile location. so i'm guessing that it's a compile-time option, and not changeable in any config.

your symlink idea is what i have been using in ubuntuzilla when installing the mozilla build of thunderbird. good job finding that one out on your own. :)

---

