---
title: "Themes on forwarded X sessions"
date: 2007-01-31
forum: Server Platforms
---

### Post by akadruid on 2007-01-31
Hi,

I use a few programs by forwarding the X session over SSH from a remote server.  It works well, but the forwarded programs look out of place, as they do not use my preferred theme (Industrial Tango).   I have tried logging into my gnome session on the remote machine too and setting the theme to be same, but it has no effect.

I know it seems like a silly thing but I'd really like to know if it is possible to theme the forwarded windows to look the same.

Cheers

Colin

---

### Post by akadruid on 2007-10-25
I found the answer eventually.

You need to have the exact same theme installed in /usr/share/themes on the remote server.  Having it in ~/.themes on the remote server doesn't seem to work.

more info here:
[http://ubuntuforums.org/showthread.php?t=519754#3](http://ubuntuforums.org/showthread.php?t=519754#3)

---

