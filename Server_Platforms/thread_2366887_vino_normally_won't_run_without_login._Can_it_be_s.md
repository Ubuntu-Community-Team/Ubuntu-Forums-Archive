---
title: "vino normally won't run without login. Can it be started through ssh cli?"
date: 2017-07-23
forum: Server Platforms
---

### Post by link626 on 2017-07-23
vino-server won't run when there's no one logged in.

However, I thought that if I logged in with ssh, I could get vino-server to run manually.
But I've failed.

I'm using windows putty to login to my linux laptop on the same network. I keep getting this error.
Is it even possible to start vino with ssh when there's no one logged in?
The laptop is just displaying the ubuntu login screen.

```
root@linux:~# export DISPLAY=:0.0 && /usr/lib/vino/vino-server
Invalid MIT-MAGIC-COOKIE-1 keyFailed to connect to Mir: Failed to connect to server socket: No such file or directory
Unable to init server: Could not connect: Connection refused
Cannot open display:



```


My goal is to boot up the computer, ssh into it and turn on vino, without locally logging in

---

### Post by wildmanne39 on 2017-07-23
*Thread moved to **Server Platforms**.*

---

