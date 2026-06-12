---
title: "Missing .deb File for bittorrent-gui"
date: 2005-10-18
forum: Repositories &amp; Backports
---

### Post by Tsuki on 2005-10-18
Just to let people know - I've just tried installing bittorrent-gui, and I get the following error:

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/b/bittorrent/bittorrent-gui_3.4.2-3ubuntu7_all.deb
  404 Not Found
```

Looking at the directory in question, the only version actually available is bittorrent-gui_3.4.2-3ubuntu4.  Anyone else had the same, or is it just something going wrong on my end?

---

### Post by ranf on 2005-10-18
[QUOTE=Tsuki]Just to let people know - I've just tried installing bittorrent-gui, and I get the following error:

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/b/bittorrent/bittorrent-gui_3.4.2-3ubuntu7_all.deb
  404 Not Found
```

Looking at the directory in question, the only version actually available is bittorrent-gui_3.4.2-3ubuntu4.  Anyone else had the same, or is it just something going wrong on my end?[/QUOTE]
Looks like the US mirror is missing the file. When you look at:
[http://archive.ubuntu.com/ubuntu/pool/universe/b/bittorrent/]("http://archive.ubuntu.com/ubuntu/pool/universe/b/bittorrent/")
it is there.

---

