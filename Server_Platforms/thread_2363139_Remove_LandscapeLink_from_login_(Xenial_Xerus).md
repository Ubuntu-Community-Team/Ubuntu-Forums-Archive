---
title: "Remove LandscapeLink from login (Xenial Xerus)"
date: 2017-06-06
forum: Server Platforms
---

### Post by jdelmoral on 2017-06-06
Hi all,

I would like to edit or remove the *Message Of The Day* ([FONT=courier new]Graph this data and manage this system at: [/FONT][FONT=courier new]https://landscape.canonical.com/[/FONT]) from login in Ubuntu Server 16.04. I know this topic was treated in the past but old methods doesn't work in Xenial Xerus.

Any help would be appreciated.

---

### Post by cariboo on 2017-06-06
The file you want to modify is /etc/update-motd.d/10-help-text. It looks like this:

```

#!/bin/sh
#
#    10-help-text - print the help text associated with the distro
#    Copyright (C) 2009-2010 Canonical Ltd.
#
#    Authors: Dustin Kirkland <kirkland@canonical.com>,
#             Brian Murray <brian@canonical.com>
#
#    This program is free software; you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation; either version 2 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License along
#    with this program; if not, write to the Free Software Foundation, Inc.,
#    51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.

printf "\n"
printf " * Documentation:  https://help.ubuntu.com\n"
printf " * Management:     https://landscape.canonical.com\n"
printf " * Support:        https://ubuntu.com/advantage\n"
```

---

### Post by jdelmoral on 2017-06-06
Thanks for your reply cariboo, I tried commenting out each lines, but the part I want to edit didn't changed:

```
Graph this data and manage this system at:
https://landscape.canonical.com/
```

I must say that I have installed **update-notifier-common** and **landscape-common**:

```
sudo apt-get install update-notifier-common landscape-common
```

---

### Post by jdelmoral on 2017-06-08
Finally I've found how to remove these **Message Of The Day** from login screen:

```
sudo nano /usr/lib/python2.7/dist-packages/landscape/sysinfo/landscapelink.py
```

Comment out this three lines:

```
self._sysinfo.add_footnote(
"Graph this data and manage this system at:\n"
"    https://landscape.canonical.com/")
```

Press **Ctrl + X** and confirm with **Y**.

```
sudo reboot now
```

Cheers.

---

