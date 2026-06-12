---
title: "VNC like remote connect for Command line"
date: 2011-02-05
forum: Server Platforms
---

### Post by bakegoodz on 2011-02-05
Is there a way I can shell into an local terminal of a remote machine. I'm familiar with ssh, but by default it doesn't allow me to start a script, let me close my laptop then come back to it. Or even show up a few hours later on site to see the progress. I also would like sometimes show coworkers my shell commands from a remote location. How can I do this?

---

### Post by volkswagner on 2011-02-05
I believe if you install screen you will get all or most of the functions you are after.

---

### Post by CharlesA on 2011-02-05
You won't be able to do it interactively, no. The closest you will get is using something with desktop sharing to show them whatever commands you are using.

---

### Post by bakegoodz on 2011-02-05
Awesome! you got me on the right path! I found these howtos for screen:

[http://www.linux.com/archive/feature/56443](http://www.linux.com/archive/feature/56443)
[http://forums.fedoraforum.org/showthread.php?t=212389](http://forums.fedoraforum.org/showthread.php?t=212389)

---

### Post by CharlesA on 2011-02-05
The only hitch with using screen is that it needs to be running as the current user and you need to be detached from the screen session to attach it elsewhere IIRC.

EDIT: Hmm nevermind, I didn't know you can connect to screen running under a different username.

---

