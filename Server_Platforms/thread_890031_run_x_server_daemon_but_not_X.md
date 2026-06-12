---
title: "run x server daemon but not X"
date: 2008-08-14
forum: Server Platforms
---

### Post by ThaddeusW on 2008-08-14
Hello all, 

I would like to ssh into my home server and remotely run X applications for admin purposes. I am running 8.04 server with a very simple fluxbox based desktop. I dont have a graphical login manager but just login and "startx". How can I keep an x server running in the background so I can remotely run x apps?

---

### Post by GreenN00b on 2008-08-14
Try ```
nohup startx
```

---

