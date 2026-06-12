---
title: "is there such a thing as a terminal clock?"
date: 2013-02-19
forum: The Cafe
---

### Post by nyteshade on 2013-02-19
Previously there was [another thread with this name]("http://ubuntuforums.org/showthread.php?t=782266"). It was closed so I couldn't add to any more, but here is a simple bit that works well (even on OS X)

Create a file with these contents called something like "termclock" within your execution path.

```

#!/bin/bash
# clock in top right corner (on 80 character screens)
while true;do printf "\033[s\033[0;70H";date +"%r";printf "\033[u";sleep 1;done

```

When done, make it executable

```

chmod +x /path/to/file/termclock

```

Then, whenever you want to have the clock, do

```

termclock &

```

It will update in the top-right corner of the window (in 80 col terminals) in the background.

[[img]https://www.evernote.com/shard/s3/sh/eb9b15eb-8d1a-4c41-ab48-494209c04e3c/37d2c34530c447a15d17d75af63b9b46/deep/0/Screen%20Shot%202013-02-19%20at%203.56.44%20PM.jpg[/img]](https://www.evernote.com/shard/s3/sh/eb9b15eb-8d1a-4c41-ab48-494209c04e3c/37d2c34530c447a15d17d75af63b9b46)[Click for large view](https://www.evernote.com/shard/s3/sh/eb9b15eb-8d1a-4c41-ab48-494209c04e3c/37d2c34530c447a15d17d75af63b9b46) - [color=#A7A7A7]Uploaded with [Skitch](http://evernote.com/skitch)[/color]

---

### Post by CharlesA on 2013-02-19
Byobu does that already.

[https://help.ubuntu.com/community/Byobu](https://help.ubuntu.com/community/Byobu)

---

