---
title: "LiveCD with sshd enabled ?"
date: 2008-01-21
forum: Server Platforms
---

### Post by erland on 2008-01-21
I accidently did a modification to the passwd file on my headless server. I can login to the machine as a normal user but I can't use sudo and because of this I can't change the passwd file back.

The first line of the passwd file that has been trashed looks like this now:
```

rt
oot:x:0:0:root:/root:/bin/bash

```

Is there some LiveCD which have sshd or something similar enabled by default which I can use to get into the machine as root to correct the problem ?

I suppose there is no way to correct this without rebooting with a LiveCD ? If someone sees another solution, please let me know.

The obvious workaround would be to move the server out into another room and connect a screen and keyboard to it, but I would like to avoid this if I can since I would prefer not to move it now when I have it in place.

If you have a solution but don't want to post it in the forum, please send me a private message instead.

---

