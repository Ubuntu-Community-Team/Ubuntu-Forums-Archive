---
title: "keep older Nautilus with trusty?"
date: 2014-06-30
forum: Ubuntu Studio
---

### Post by a-you on 2014-06-30
Anybody know if this is possible?? I'm currently using Quantal (12.10) and Nautilus 3.4.2. It works nicely *and* I can use Nautilus scripts plus Nautilus Actions. I'd like to move up to Trusty but from what I've read it looks like the newer versions of Nautilus have lost many features.

Thunar lacks tabs apparently, a feature I use a lot, and it would anyway be nice if I could use the scripts I have without having to adapt them to Thunar (if that's even possible).

Nemo apparently restores a lot of the features that were removed from Nautilus---but apparently not yet the scripting. Or maybe one can use Nautilus Actions with Nemo?? 

Anybody solved any of this? Thanks in advance.

---

### Post by ajgreeny on 2014-06-30
Thunar does have tabs available and has done for some time now, since 2012, I think.  It does not, however, have the split pane, or twin pane that older versions of nautilus had with a press of F3, which was incredibly useful.

Thunar also can and does use custom actions, similar to scripts with some ease, in fact I think it is easier to set them up than using nautilus, but that's just my opinion.

---

### Post by jejeman on 2014-06-30
I have installed Nemo instead of Nautilus. Works as expected.
Scripts in
~/.gnome2/nemo-scripts
I have more trouble adapting scripts to work with avconv instead ffmpeg.

---

### Post by a-you on 2014-07-02
Thanks for your comments. I tried Thunar again and realized that it seems to be missing one more feature that Nautilus has that I happen to use a lot: the triangle that unfolds a subdirectory within a list view. I'm not sure what to call that but you know what I mean.

I'll try Nemo and putting the scripts in ~/.gnome2/nemo-scripts, thanks.

---

### Post by a-you on 2014-07-10
Hi all. Just an update here.

I've been using nemo (and upgraded to trusty) since starting this thread and I must say that I highly recommend it. It has all the things I liked so much about nautilus, plus a few more, like eg that it has a context menu item for revealing the target of a link (I had made a nautilus script for that). Also it has an "open as root" item too; nice.

And btw the nemo actions mechanism is indeed quite simple and works nicely, and nemo supports "nemo scripts" in the same way that nautilus supported "nautilus scripts". There's a minimal example "action" that shows how to use those too. If you want to use those then look in:

/usr/share/nemo/actions
or
~/.local/share/nemo/actions

Nemo scripts go in:
~/.gnome2/nemo-scripts

Oh, one warning: I learned the hard way that nautilus had a bug where filenames with a "%" character were problematic if a script you wrote used the paths passed to it as arguments, but it worked fine if you used the variables nautilus created, eg "NAUTILUS_SCRIPT_SELECTED_FILE_PATHS". Unfortunately nemo retains this problem with filenames that have "%" and curiously file names like that are (or at least used to be; haven't checked in a while) created by ardour :-(. I have to learn how to make a bug report...

---

### Post by brianmc on 2014-07-11
Ardour still spits out files with '%' in the name - even on the latest version (3.5.358). There's quite a few things I'd change about how it names files, snapshots and so-on. Or, just make them editable masks somewhere in the preferences.

The way I've taken to working with it is to create a new user for every project that's going to take more than a few hours of work.

---

### Post by a-you on 2014-07-11
I hadn't had a chance to update my comments, but I tested this issue of file names with "%" more specifically today and it looks like if one either uses the variables (eg "NEMO_SCRIPT_SELECTED_FILE_PATHS") if running a script as a so called "nemo script" or runs the script as a nemo-action then the file names with "%" are fine. It's when running a script as a "nemo script" and using the file names that are passed to the script as args where the bug surfaces.

---

