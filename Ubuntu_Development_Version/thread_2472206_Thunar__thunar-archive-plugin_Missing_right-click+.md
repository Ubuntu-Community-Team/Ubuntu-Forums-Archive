---
title: "Thunar / thunar-archive-plugin: Missing right-click+drag &gt; &quot;Extract here&quot;"
date: 2022-02-20
forum: Ubuntu Development Version
---

### Post by &amp;KyT$0P# on 2022-02-20
In Xubuntu 20.04, it is possible to right-click+drag an archive file from one Thunar window to another, and select "Extract here".  In 22.04 that option is gone: Thunar only offers "Copy here", "Move here", "Link here", and "Cancel".

Other context menu items of thunar-archive-plugin are there and working in 22.04.

How to get back right-click+drag > "Extract here" in Xubuntu 22.04?

---

### Post by #&amp;thj^% on 2022-02-23
Forgive me, is it installed?
```
apt search thunar-archive-plugin

```
If I'm not mistaken it's in "xfce4-goodies".
EDIT: I've not used this method you describe rightclick+drag to extract to a location.
All is well on mine with rightclick and extract to my desired location.

---

### Post by &amp;KyT$0P# on 2022-02-23
> **1fallen said:**
> Forgive me, is it installed?

Yes
```
$ apt-cache policy thunar-archive-plugin
thunar-archive-plugin:
  Installed: 0.4.0-2
  Candidate: 0.4.0-2
  Version table:
 *** 0.4.0-2 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status

```

* Just tested compiling focal version of thunar on 22.04, keeping 22.04 version of thunar-archive-plugin.  That gets this working.  But I would prefer to be able to use the current version of thunar - if I have to compile something myself to make this work, I'd rather do thunar-archive-plugin than thunar. :-k

---

### Post by #&amp;thj^% on 2022-02-23
> **halogen2 said:**
> Yes
```
$ apt-cache policy thunar-archive-plugin
thunar-archive-plugin:
  Installed: 0.4.0-2
  Candidate: 0.4.0-2
  Version table:
 *** 0.4.0-2 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status

```
halogen2 so dose yours show as in my screenshot?

---

### Post by &amp;KyT$0P# on 2022-02-23
> **1fallen said:**
> halogen2 so dose yours show as in my screenshot?

Yes, as noted in the OP those options are there and work.  But they are so much more cumbersome to use than right-click+drag that I don't consider it a workaround.  Also I was editing previous post while you were posting

---

### Post by #&amp;thj^% on 2022-02-23
Just read it, very clever on compiling focal version of thunar on 22.04.
To be honest I have not heard of this till just now, and agreed my described way is cumbersome in comparison to the rightclick and drag you described. :)
And i mostly use CLI for that kind of stuff.

---

### Post by &amp;KyT$0P# on 2022-02-25
Ugh, Xubuntu 21.10 is affected too :(

Unfortunately I don't have enough technical knowledge to file a bug report about this.  I tried to poke around in the thunar & thunar-archive-plugin code to get the needed information, but didn't get anywhere - I am unable to even determine whether this is a thunar issue or a thunar-archive-plugin issue.  Is anyone who is more knowledgeable than me also not getting the right-click+drag > Extract here menu item?  If so could you please file a bug report?

---

### Post by #&amp;thj^% on 2022-02-25
I come in peace :D
See if there is any difference here: (This on Focal thunar 1.8.14 (Xfce 4.14))
```
**cat /usr/lib/x86_64-linux-gnu/thunar-archive-plugin/file-roller.tap**
#!/bin/sh
#
# vi:set et ai sw=2 sts=2 ts=2:
# -
# file-roller.tap - Wrapper script to create and extract archive files
#                   in Thunar, via the thunar-archive-plugin, using the
#                   file-roller archive manager.
#
# Copyright (c) 2006 Benedikt Meurer <benny@xfce.org>
# Copyright (c) 2011 Jannis Pohlmann <jannis@xfce.org>
#
# This program is free software; you can redistribute it and/or 
# modify it under the terms of the GNU General Public License as
# published by the Free Software Foundation; either version 2 of 
# the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the 
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public 
# License along with this program; if not, write to the Free 
# Software Foundation, Inc., 51 Franklin Street, Fifth Floor,
# Boston, MA 02110-1301, USA.

# determine the action and the folder, $@ then contains only the files
action=$1; shift;
folder=$1; shift;

# check the action
case $action in
create)
	exec file-roller "--default-dir=$folder" --add "$@"
	;;

extract-here)
	exec file-roller "--extract-to=$(pwd)" --extract-here --force "$@"
	;;

extract-to)
	exec file-roller "--default-dir=$folder" --extract "$@"
	;;

*)
	echo "Unsupported action '$action'" >&2
	exit 1
esac


```
You made me install 20.04 for this. :p
You can file a bug report with: "ubuntu-bug thunar-archive-plugin"

---

### Post by &amp;KyT$0P# on 2022-02-26
That file in 22.04 is the same as what you posted.

Thanks 1fallen, I filed the bug where you suggested and the link is [here]("https://bugs.launchpad.net/ubuntu/+source/thunar-archive-plugin/+bug/1962372").

---

### Post by #&amp;thj^% on 2022-02-28
Looked at it, and I think you posted a clear explanation, now *if* they will act on it. ;)

---

