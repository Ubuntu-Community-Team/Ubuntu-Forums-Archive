---
title: "Kill apache ... ?"
date: 2005-10-29
forum: Server Platforms
---

### Post by dbee on 2005-10-29
I'm trying to kill my apache processes, mainly because I keep getting this 

Address already in use: make_sock: could not bind to address [::]:80

I go to ps -aux and I kill all the processes one by one

kill -9 <process_no>

only to run ps aux again and find that all the processes are still their under a different pid ???

---

### Post by herrpoon on 2005-10-29
Try

```
ps ax | grep apache
```

Worked for me!

---

### Post by hav0x on 2005-10-29
sudo /etc/init.d/apache stop

or

sudo /etc/init.d/apache2 stop

---

### Post by LordHunter317 on 2005-10-29
You have to kill the parent apache process to stop the children.  Otherwise, they'll be respawned.

You should always use the daemon shutdown script or command, wherever possible.

Finally, kill -9 is a last resort and shouldn't be normally used.

---

