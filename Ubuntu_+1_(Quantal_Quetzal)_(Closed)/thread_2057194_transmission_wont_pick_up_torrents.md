---
title: "transmission wont pick up torrents"
date: 2012-09-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ELD on 2012-09-13
So now transmission will only accept a torrent if you download the file and select open from within the app itself if you double click the torrent file or open with when downloading it just loads the app without the torrent.

---

### Post by opensshd on 2012-09-13
dht option enabled? that would affect magnet links anyway...

---

### Post by ELD on 2012-09-13
They are .torrent not magnet links.

---

### Post by mips on 2012-09-13
Works fine here in xubuntu 12.10 & chromium

Don't you maybe have to specify the app to launch somewhere in your browser of system app associations?

---

### Post by opensshd on 2012-09-13
I can reproduce the problem you have.

I can find a lot of references to bugs like it, but not exactly...

I think transmission might be "just buggy", seems the consensus... have you tried deluge or anything else? Does it work any different? What browser are you using?

I also looked at mime type... didn't help here. Doesn't seem to have a problem knowing what app to use, but doesn't handle it correctly.

What window manager? gnome-shell here...

---

### Post by kansasnoob on 2012-09-13
> **opensshd said:**
> I can reproduce the problem you have.

I can find a lot of references to bugs like it, but not exactly...

I think transmission might be "just buggy", seems the consensus... have you tried deluge or anything else? Does it work any different? What browser are you using?

I also looked at mime type... didn't help here.

+1!

I'll grant you that I have a somewhat complex setup - post-install I symink separate partitions for Downloads, Documents, etc - but I can't for the life of me start a seed like I'm used to :confused:

I think I'd rather debug Transmission than just switch to Deluge so I'm looking for a reason. I may try installing an older version of Transmission and see if it works OK.

---

### Post by opensshd on 2012-09-13
Narrowing it down, I think... =]

xdg-open is the mechanism for handling torrent files between my browser and the torrent client.

when i try:

xdg-open /what/ever/file.torrent

it seems to work alright... populates the file list in transmission and everything is ok... so... that actually confuses me a bit more. ><

Could this be the woe?

[https://bugs.freedesktop.org/show_bug.cgi?id=45859](https://bugs.freedesktop.org/show_bug.cgi?id=45859)

The original line is:
eval '$browser $1'$xdg_redirect_output;

while it should be:
eval '$browser "$1"'$xdg_redirect_output;

Examining scipts/xdg-open line 445 from [https://launchpad.net/ubuntu/+archive/primary/+files/xdg-utils_1.1.0~rc1.orig.tar.gz](https://launchpad.net/ubuntu/+archive/primary/+files/xdg-utils_1.1.0~rc1.orig.tar.gz)

Yah maybe $browser $1 == $browser_with_arg... different code here than the bug I found.

Tired. Going to sleep :)

---

