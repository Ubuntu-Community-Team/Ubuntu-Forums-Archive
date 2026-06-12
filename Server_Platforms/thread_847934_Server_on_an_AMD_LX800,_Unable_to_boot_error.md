---
title: "Server on an AMD LX800, Unable to boot error"
date: 2008-07-03
forum: Server Platforms
---

### Post by Pc_Madness on 2008-07-03
"This kernel requires the following features not present on the CPU:
0:6
Unable to boot - please use a kernel appropriate for your CPU"

Hey guys, I've got abit of a tricky problem.  I have an WAFER-LX800 board which has an AMD Geode LX800 CPU, but the board seems unable to pickup CD drives.  We're installing to a CF Card, so we've just been installing it on an Core 2 Duo machine via a USB Card reader, and then plugging the card into the inbuilt card reader on the board. This approach worked fine with Debian, but we were having headaches setting up Postgresql, so we decided to try Ubuntu 8.04 Server.

The kernel is 2.6.24-16-server.

We've tried doing an apt-get install linux-image-2.6.24-16-generic, and it said it installed, but after starting up it just said the same error, so apparently thats not the solution to this problem. :p

Is there a way to fix this? :( Thanks inadvance. :)

---

### Post by Pc_Madness on 2008-07-03
*semi bump*
Whoops! Seems like it updating the kernel adds a new entry to grub, and Ubuntu was booting straight into the server entry. :)

Is there any down sides to running the generic kernel?

---

