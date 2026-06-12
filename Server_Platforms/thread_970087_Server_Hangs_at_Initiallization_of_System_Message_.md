---
title: "Server Hangs at Initiallization of System Message Bus; D-Bus"
date: 2008-11-03
forum: Server Platforms
---

### Post by blendmaster on 2008-11-03
Hello!

Well, I'm brand new to server installations (...and servers in general). I decided to use an old computer as a "practice/small" LAMP server. Anyway, after I got through some hardware issues (fun with old systems!), I got a good installation going.

I have an issue where the system gets "stuck" when initializing the system message bus. This forces me to stop the initialization by "alt-F4ing" it twice (lol, it works), which brings up another issue. The secondary issue is that the current prompt is a few too many lines off the screen... I have to hold down a key until the prompt is on the screen to see what I'm typing. I believe this is caused by the GNU license (which is pretty long) that is brought up after login, but that's just a guess.

I just want to know how to fix those two issues at the moment, so any help is greatly appreciated! Thank you!

---

### Post by cariboo on 2008-11-04
To fix your problem with motd have a look here:

[http://www.ubuntugeek.com/how-to-change-message-of-the-day-motd-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-change-message-of-the-day-motd-in-ubuntu-server.html)

I had to grab update-motd from my Intrepid desktop and transfer it to the server and install it there.

Jim

---

