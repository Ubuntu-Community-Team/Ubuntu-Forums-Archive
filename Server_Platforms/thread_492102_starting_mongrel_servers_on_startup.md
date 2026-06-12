---
title: "starting mongrel servers on startup"
date: 2007-07-04
forum: Server Platforms
---

### Post by spaceW on 2007-07-04
I am running two **Mongrel** servers: CruiseControl.rb and a simple rails app.  I can start them in separate Terminals, but that is a little bit annoying.  I would rather have them **automatically start** up when my machine boots.

I have read a bit about rc.local, init.d, and the rc#.d folders, but quite a bit of that seemed to be rather old information.  I am running feisty fawn on xfce4.  I would greatly appreciate some simple instructions on how to start these servers.  Can I simply put a few lines in** rc.local**, and if so what should they look like?

Here are the commands that I use to start the servers in the Terminal:
```
 .../cruise$ sudo ./cruise start
```
and
```
.../myrailsproject$ ./server/script
```

I am also running Trac and svn through **Apache**, which starts automatically.  Would it be easier to have Apache somehow boot the Mongrels along with itself?

---

