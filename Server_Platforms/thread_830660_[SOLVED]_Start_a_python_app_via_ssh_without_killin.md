---
title: "[SOLVED] Start a python app via ssh without killing it when closing the session"
date: 2008-06-16
forum: Server Platforms
---

### Post by Zyzzyva100 on 2008-06-16
This may sound like a stupid question, but I have a program that I generally leave running on my server that I would like to be able to start via ssh.

The problem is that when I go into its directory and type:  python program.py, after it starts running, I can't kill the ssh session without killing the program.

Is there a way to make the python program run in the background?  or somehow start so that it isn't dependent on my ssh session being open? I tried doing this with a script and adding it to rc.d but that doesn't seem to work either.

---

### Post by windependence on 2008-06-16
Try this:

python program.py &

-Tim

---

### Post by Zyzzyva100 on 2008-06-16
Thank you much, that solved it.

---

