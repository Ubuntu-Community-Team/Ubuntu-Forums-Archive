---
title: "Strange happenings, sudo hash changed"
date: 2012-06-10
forum: Security
---

### Post by Park Bom on 2012-06-10
Can anyone clarify what this means?
I booted up my laptop and it was behaving peculiarly (couldn't move cursor via trackpad, when I tried to sign into my account way too many characters showed up for the amount of keys I pressed), so I ran rkhunter (full log here: [http://pastebin.com/cAJxXtmF](http://pastebin.com/cAJxXtmF)) and this part is worrying me:

```
[00:00:52]   /usr/bin/sudo                                   [ Warning ]
[00:00:52] Warning: The file properties have changed:
[00:00:52]          File: /usr/bin/sudo
[00:00:52]          Current hash: a318948a0a138d11407300753079f3ee0f00f97d
[00:00:52]          Stored hash : 0427d34b82cbfc3ff6eed5da16755b2cc40468de
[00:00:52]          Current inode: 20188947    Stored inode: 20188168
[00:00:52]          Current size: 71288    Stored size: 71280
[00:00:52]          Current file modification time: 1338522824 (31-May-2012 23:53:44)
[00:00:52]          Stored file modification time : 1337145788 (16-May-2012 01:23:08)
```

It says it was modified May 31, but I've definitely run rkhunter in the last week, and it didn't show a change.

Could anyone provide some insight? It'd be much appreciated.

---

### Post by CharlesA on 2012-06-10
sudo has had a few updates recently.

You are fine.

```
charles@Thor:~$ sha1sum /usr/bin/sudo
a318948a0a138d11407300753079f3ee0f00f97d  /usr/bin/sudo

```

---

### Post by Park Bom on 2012-06-10
> **CharlesA said:**
> sudo has had a few updates recently.

You are fine.

```
charles@Thor:~$ sha1sum /usr/bin/sudo
a318948a0a138d11407300753079f3ee0f00f97d  /usr/bin/sudo

```

Thank you so much for the quick reply. I was quite stressed, trying to think of when I could've slipped up. It's good to know I was overreacting.

Thanks again for putting my mind at ease.

---

