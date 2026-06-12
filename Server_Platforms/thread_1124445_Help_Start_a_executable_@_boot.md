---
title: "Help Start a executable @ boot"
date: 2009-04-13
forum: Server Platforms
---

### Post by Eirc16 on 2009-04-13
Hello,

im Currently working on a Small gaming server for my Multi gaming conumity.
The server Runs on ubuntu Server edition 8.10 and i can access it using ssh.
i'm Trying to start a Program @ ubuntu boot Its a executable.
I'm a newbie with Linux
Can someone please help me

Greetings
Eric

---

### Post by cdenley on 2009-04-13
Easiest way is to edit /etc/rc.local.

---

### Post by Eirc16 on 2009-04-13
Could you explain that please because I looked up to the file and din't understand it

---

### Post by cdenley on 2009-04-13
Let's say you want /usr/local/bin/myscript.sh to start at boot, and it runs continuously never exiting. You simply add this line before "exit 0".
```

/usr/local/bin/myscript.sh&

```

So /etc/rc.local without comments would look like
```

#!/bin/sh -e
/usr/local/bin/myscript.sh&
exit 0

```
If the executable runs then exits, you don't need the "&", which forces the command into the background so the script can continue.

---

