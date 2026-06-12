---
title: "Help using Qemu to emulate application in ARM Architecture"
date: 2015-09-02
forum: Server Platforms
---

### Post by hugo29 on 2015-09-02
Hello! (this is my first post here so I apologise if i've done something wrong.

So basically I have a server running ARM architecture of Ubuntu 15.04 (Which I connect to using SSH)

The processor type is Samsung Exynos-5422 Octa-Core.

Originally I did not know anything about ARM or even any kind of architectures, but the application I planned to run on it is not compatible with ARM only x86-64.


So after copious Google'ing I found an emulator called Qemu, unfortunately I found the guide very confusing...

Regardless I managed to install it, and by simply running the command 'qemu-arm' first I could then use the program I wanted..


I think i'm doing something wrong though, since the program only utilises one of the eight cores available (I checked using htop) and therefore becomes unbearably slow...

Is there some way I can have the emulator use all eight cores?

Thanks for any assistance you can provide!

Hugo.

---

### Post by howefield on 2015-09-02
Thread moved to the "*Server Platforms* forums.

---

### Post by hugo29 on 2015-09-02
[IMG]http://i.imgur.com/zNQhA7O.png[/IMG]

Here's a picture of htop

As you can see this process is using 100% CPU of core 6 while not using any of the other cores.

You can also see the qemu command being used before my initial command (this command is compiling some code).

I think there is a way I can edit the qemu command to use all 8 cores but i'm not sure,

---

### Post by hugo29 on 2015-09-03
Nevermind, I gave up and got a different server. I think this issue was to do with the program I was using, pretty sure it actually doesn't support multi-core processing.

---

