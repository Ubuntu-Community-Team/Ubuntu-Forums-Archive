---
title: "Passing messages to GNU Screen"
date: 2012-01-23
forum: Server Platforms
---

### Post by galactickid2 on 2012-01-23
Let's say I created an init script to create a screen session that runs a game server. That script also has the ability to kill the screen session based on the PID. Honestly I can't make heads or tails of screen's man page. How can I create another script that allows me to send a command (simply a short string with a return at the end) to the running process within that screen?

(I want a file that lets me "./ban <username>" then passes "ban $1[ENTER]" to the running process)

---

### Post by Toz on 2012-01-27
See: [http://ubuntuforums.org/showthread.php?t=1841916&highlight=screen]("http://ubuntuforums.org/showthread.php?t=1841916&highlight=screen").

---

