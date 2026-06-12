---
title: "Stooopid Question: Does the terminal have to stay open/connected"
date: 2011-02-04
forum: Server Platforms
---

### Post by CGW on 2011-02-04
Example:  If I'm running ClamAV to scan a large directory, after the commands have been issued via the terminal does the terminal connection/screen have to remain open?  If not, where can you find the results of said scan or commands?

Hope this makes sense.

Thanks in advance.

Chris

---

### Post by arrrghhh on 2011-02-04
Yes, you would have to leave the terminal window open...

Unless of course you use [screen.](https://help.ubuntu.com/community/Screen)  Very handy tool!

---

### Post by CGW on 2011-02-04
Thanks for the help.

---

### Post by dtfinch on 2011-02-04
I use setsid to run programs in their own new session. It's simple and less to remember than other options, apart from having an odd name. It's similar to using nohup, but I've found some programs still exit on close when I've used nohup, like rsync.

For programs that are already running, in bash I think you can use ctrl-z to break from the process, "bg" to resume the process in the background, then "disown" to detach the process so it'll keep running when bash closes.

---

### Post by CharlesA on 2011-02-04
+1 for screen.

It's way easier to deal with then using bg and fg and whatnot imo.

---

