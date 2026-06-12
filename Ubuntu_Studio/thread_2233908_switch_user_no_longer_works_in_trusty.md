---
title: "switch user no longer works in trusty"
date: 2014-07-11
forum: Ubuntu Studio
---

### Post by a-you on 2014-07-11
"Switch User" in the upper right hand corner is greyed out and there doesn't seem to be any way to get it working. Anybody??

I get the impression from searches that xubuntu now uses a different program to handle login(???) and that that's why. But maybe I'm way off in that interpretation too. Anyway is there any way to enable "switch user" again?

It's important to me, and I can imagine to others too, because if you're using a ~/Private dirrectory or an encrypted home then by being able to switch the user without logging out it's possible to reach an encrypted folder of a switched-from user, whereas now the folder "doesn't exist".

Thanks in advance.

---

### Post by brianmc on 2014-07-11
> **a-you said:**
> "Switch User" in the upper right hand corner is greyed out and there doesn't seem to be any way to get it working. Anybody??
I had a go at this with 14.04, found pretty-much the same as you.

A quick google? It's a known bug: [https://bugs.launchpad.net/ubuntu/+source/xfce4-whiskermenu-plugin/+bug/1285440](https://bugs.launchpad.net/ubuntu/+source/xfce4-whiskermenu-plugin/+bug/1285440)

I don't know how much of Gnome you'd end up pulling in to resolve it. Sorry can't be more help than that.

---

### Post by a-you on 2014-07-11
Thanks for that. Actually I too had come across that in one of my searches, but when I read it the first time it was clear as mud, as they say; this time, re-reading, it seemed a lot easier to understand. So thanks for bringing it to my attention again.

If I understand what's being discussed there, it looks like it's technically not problematic to use

```
 dm-tool switch-to-greeter
```

I just did that from terminal and indeed it allowed me to switch to another user and left the first user logged in. Maybe just making a launcher and putting that in the panel would be a temporary fix???

---

### Post by Toz on 2014-07-11
The "Switch User" option from the Actions Button plugin (_not_ the Whisker Menu) relies on the gdmflexiserver executable which is no longer shipped in newer versions of *buntu. You can, however, get the option to work by having it run "dm-tool switch-to-greeter" instead by creating the file **/usr/local/bin/gdmflexiserver** (as root) with the following content:
```
#!/bin/bash
dm-tool switch-to-greeter
```
...and making the file executable.

Note: the "dm-tool switch-to-greeter" command is dependent on lightdm being the DM.

---

### Post by brianmc on 2014-07-11
Nice, and simple.

Although, based on **a-you**'s actual usage here, I would've looked for a way to script a shell login to mount the encrypted user directory rather than having another X session hidden in the background. Something like an encrypted LVM partition, perhaps?

---

### Post by a-you on 2014-07-11
Thanks for the various tips. In the meantime I tried my more rudimentary idea of just making a launcher and putting it in a panel and that seems to be working just fine as well. Please tell me (any of you) if you see any reason why that's problematic for the system, because if not then I'll leave it as I have it. It's working fine and that launcher icon just sits next to the log out etc item at the far right of that panel. Not inconvenient at all.

---

### Post by brianmc on 2014-07-12
Don't see any reason for that to be a problem - as long as you remember what you did if/when you reinstall.

I've not fired up my 14.04 system yet today (putting off finishing the mix on the last set from the gig) and intend to try out what **Toz** suggests once I've had enough coffee. This machine (laptop) is running 13.10, and the missing (from 14.04) *gdmflexiserver* is under lightdm using Dbus to get you back to the greeter/login. (I.e. it's just another, slightly more-fiddly, oneliner).

---

### Post by brianmc on 2014-07-12
Here's the contents of gdmflexiserver as-provided in 13.10:
```
#!/bin/sh
#
# Copyright (C) 2011 Canonical Ltd
# Author: Michael Terry <michael.terry@canonical.com>
# 
# This program is free software: you can redistribute it and/or modify it under
# the terms of the GNU General Public License as published by the Free Software
# Foundation, version 3 of the License.
#
# See http://www.gnu.org/copyleft/gpl.html for the full text of the license.

if [ -z "$XDG_SEAT_PATH" ]; then
  # something went wrong
  exit 1
fi

dbus-send --system --type=method_call --print-reply --dest=org.freedesktop.DisplayManager $XDG_SEAT_PATH org.freedesktop.DisplayManager.Seat.SwitchToGreeter
```

I created that as-per **Toz**'s suggested location and made it executable:
```
$ sudo nano /usr/local/bin/gdmflexiserver
$ sudo chmod ogu+x /usr/local/bin/gdmflexiserver
```

This gives you back the "Switch User" option on the Action buttons as-opposed to needing to create a distinct launcher. Since it is digging into dbus to establish which display manager you're using, this might be a little more-robust than the *dm-tool* command.

---

### Post by a-you on 2014-07-13
That seems like it might be a better solution. I think I'll try that route too. Thx.

---

### Post by a-you on 2014-07-13
...hmm. I was just doing a little more searching and I get the impression that gdmflexiserver now exists as a transitional thing while gdm is being phased out in favor of lightdm. If I understood correctly that is. In which case
```
dm-tool switch-to-greeter
```
might be the better approach in the longer run. But to each their own; your method looks good too.

---

### Post by gdesilva on 2014-07-14
Thanks everyone. This is something that I wanted to do but never got around doing. Toz's suggestion worked for me.

---

