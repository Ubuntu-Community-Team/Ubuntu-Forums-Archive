---
title: "Running User Programs as Daemons"
date: 2008-09-07
forum: Server Platforms
---

### Post by GenuineXP on 2008-09-07
I'd like to run a program on my Ubuntu Hardy server. I'm not really sure if running the program as a daemon is really what I need to do though. What I'm trying to do is log into the machine via SSH, run some program, log out, and have the program continue to run (i.e., it's not "attached" the terminal I logged into).

One program I'd like to use this way is rtorrent. However, I'm not sure how I could log in, start rtorrent, log out, and log back in and interface with the currently running process again. Is this possible? Can I somehow run programs as daemons to accomplish this?

Thanks!

(Obviously, this is advantageous with rtorrent, as I'd like to start download/uploading content without needing to keep an SSH session running. This way, only the server needs to remain powered on.)

---

### Post by lswb on 2008-09-07
Take a look at the screen package. (yes, "screen" is the name) It's a kind of manager for console sessions. You can leave screen and other processes running when you log out, then later login again and reattach the same screen session and processes.

---

### Post by GenuineXP on 2008-09-07
Thanks for the tip. I actually used this package before (very briefly) and totally forgot about it!

Thanks again. This looks like exactly what I need. :-)

---

### Post by HermanAB on 2008-09-07
Another way, if you don't have permission to install screen, is to attach what you want to run to a running daemon, for example cron or at:

# at -f script now 

Cheers,

Herman

---

