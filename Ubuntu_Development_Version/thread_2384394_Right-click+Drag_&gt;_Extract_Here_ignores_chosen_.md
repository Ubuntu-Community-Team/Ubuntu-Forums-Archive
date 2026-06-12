---
title: "Right-click+Drag &gt; Extract Here ignores chosen destination directory"
date: 2018-02-06
forum: Ubuntu Development Version
---

### Post by &amp;KyT$0P# on 2018-02-06
1) Open a Thunar window to a directory containing an archive

2) Open a second Thunar window to the home directory

3) Right-click+drag the archive into the second Thunar window, and click "Extract here".

But it extracts in the directory containing the archive, not in the home directory.

In Xubuntu 16.04, I got it working by installing Ark, and using a custom ark.tap file and a bunch of symlinks -
```
#!/bin/sh
#
# file-roller.tap - Wrapper script to create and extract archive files
#                   in Thunar, via the thunar-archive-plugin, using the
#                   KDE ark archive manager.
#
# $Id$
#
# Copyright (c) 2006 Benedikt Meurer <benny@xfce.org>.
#
# This program is free software; you can redistribute it and/or modify it
# under the terms of the GNU General Public License as published by the Free
# Software Foundation; either version 2 of the License, or (at your option)
# any later version.
#
# This program is distributed in the hope that it will be useful, but WITHOUT
# ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
# FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for
# more details.
#
# You should have received a copy of the GNU General Public License along with
# this program; if not, write to the Free Software Foundation, Inc., 59 Temple
# Place, Suite 330, Boston, MA  02111-1307  USA.
#

# determine the action and the folder, $@ then contains only the files
action=$1; shift;
folder=$1; shift;

# check the action
case $action in
create)
	exec ark --dialog --add "$@"
	;;

extract-here)
	exec ark --destination "$folder" --batch --autosubfolder "$@"
	;;

extract-to)
	exec ark --destination "$folder" --batch --dialog "$@"
	;;

*)
	echo "Unsupported action '$action'" >&2
	exit 1
esac


```
But in 18.04, this isn't a solution, because Ark is completely silent (no progress dialog like in Xubuntu 16.04).  I have no way to know how far along it is, nor do I have a way to know when it's done without looking at a system monitor.

So how to get this working with the default Xubuntu archive manager?

---

### Post by &amp;KyT$0P# on 2018-03-12
Bump

This is still a problem in Xubuntu 18.04 beta 1.  Should I file a bug report?  If so, against which package?

---

### Post by #&amp;thj^% on 2018-03-12
> **halogen2 said:**
> Bump

This is still a problem in Xubuntu 18.04 beta 1.  Should I file a bug report?  If so, against which package?

Is this just a XFCE4 install or are there other DE environments?
I'm not seeing  that on mine!

---

### Post by &amp;KyT$0P# on 2018-03-12
> **1fallen said:**
> Is this just a XFCE4 install or are there other DE environments?
It's a completely fresh install of Xubuntu 18.04 beta 1.  I didn't add or remove any software yet.

---

### Post by #&amp;thj^% on 2018-03-12
> **halogen2 said:**
> It's a completely fresh install of Xubuntu 18.04 beta 1.  I didn't add or remove any software yet.

Huum? have you tried to use just: (terminal)
```
file-roller
```
from there add the compressed folder and extract to your preference?
might give some clues.
needed "rar" && "unrar" other packages are needed for some other file-ext (7zip yada yada)
Did you install a minimal install then?

---

### Post by &amp;KyT$0P# on 2018-03-12
Maybe I wasn't clear.

Extracting from within the archive manager works fine (looks like Xubuntu uses Engrampa).  The wrong behavior happens when I right-click+drag **in Thunar**, from one Thunar window to another Thunar window.

It gives me a menu with options "Copy here", "Move here", "Link here", "Extract here", and "Cancel".  No archive manager is even open until I click "Extract Here".  And when I do click that, the archive extracts fine, **but not in the folder it's supposed to extract to.**

Clear now? :)


* Got some more information:

1) It's reproducible even in the live CD environment.  No need to install to reproduce this problem.

2) When I right-click+drag > Extract Here, Thunar runs this command -
```
engrampa --extract-to=[COLOR="#FF0000"]<correct destination directory>[/COLOR] --extract-here --force [COLOR="#FF0000"]<archive>[/COLOR]
```
Running that command manually in Terminal produces the same result.  The only terminal output is
```
Gtk-Message: xx:xx:xx.xxx: GtkDialog mapped without a transient parent. This is discouraged.
```

> **1fallen said:**
> Did you install a minimal install then?
I don't think so.  I don't know how to do a minimal install.

---

### Post by slickymaster on 2018-03-13
Yes, engrampa is replacing file-roler for 18.04. Evince -> Atril and Gnome calculator -> Mate calculator are the other 2 replacements we're doing for 18.04
> **halogen2 said:**
> 
This is still a problem in Xubuntu 18.04 beta 1.  Should I file a bug report?  If so, against which package?File it against engrampa: [https://bugs.launchpad.net/ubuntu/+source/engrampa](https://bugs.launchpad.net/ubuntu/+source/engrampa)

---

### Post by #&amp;thj^% on 2018-03-13
> **halogen2 said:**
> Maybe I wasn't clear.



Clear now? :)


Crystal :) My Fault.:( Sometimes I see only what I want to see!;)

> **slickymaster said:**
> Yes, engrampa is replacing file-roler for 18.04. Evince -> Atril and Gnome calculator -> Mate calculator are the other 2 replacements we're doing for 18.04
File it against engrampa: [https://bugs.launchpad.net/ubuntu/+source/engrampa](https://bugs.launchpad.net/ubuntu/+source/engrampa)
Understood, >>>that's why I installed file-roller.:)

---

### Post by &amp;KyT$0P# on 2018-03-13
> **slickymaster said:**
> File it against engrampa:
Done - [https://bugs.launchpad.net/ubuntu/+source/engrampa/+bug/1755556]("https://bugs.launchpad.net/ubuntu/+source/engrampa/+bug/1755556")

Thanks slickymaster & 1fallen for your help.

---

### Post by &amp;KyT$0P# on 2018-04-13
I found a workaround using xarchiver.  The 18.04 version of xarchiver added the option to auto-detect subfolder when extracting.  But thunar-archive-plugin doesn't use that option.  Easy fix though: edit [FONT=Courier New]/usr/lib/thunar-archive-plugin/xarchiver.tap[/FONT] and change this line...
```
	exec xarchiver "--extract-to=$folder" "$@"
```
... to this -
```
	exec xarchiver -d "--extract-to=$folder" "$@"
```
(The [FONT=Courier New]-d[/FONT] option is not documented in the man page.  Refer to [FONT=Courier New]xarchiver --help[/FONT] for more info.)

Not quite an ideal solution, because xarchiver's progress bar doesn't show how far along it is, but this is usable.

Thanks again to all who replied.

---

### Post by #&amp;thj^% on 2018-04-13
Thanks halogen2 for your work around very helpful as you usually are.:)
And just to add it has always been told to me "if" I'm understanding you correctly that the "-d" just lists information about the thing that follows and nothing more.

Kind regards

---

