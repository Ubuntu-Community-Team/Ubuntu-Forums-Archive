---
title: "apache localhost mixup"
date: 2006-07-07
forum: Server Platforms
---

### Post by tefflox on 2006-07-07
hello, thank you kindly for your time.  I've done something wrong setting up apache to listen only to me on port 80, I now get "forbidden access to root file directory.  Somehow it happened creating a symlink from /home/me/lh to /var/www.  I've gone through and chmod/own/grp back to my group and myself, but still i get the forbidden access message.  How is this solved?

---

### Post by adwait on 2006-07-08
I believe apache creates a user called www or something and the files should belong to that users for apache to be able to access them properly...

---

### Post by maino82 on 2006-07-08
the user apache uses is www-data as far as i know. if you set the proper permissions for that user it should work for you.

---

### Post by tefflox on 2006-07-08
thanks, the first solution worked, but I haven't learned about the www-data user.

---

