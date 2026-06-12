---
title: "ubuntu server 12.04 + printer"
date: 2012-09-02
forum: Server Platforms
---

### Post by anstarr on 2012-09-02
Hello all,  i am totally new to ubuntu and have decided to go for the gusto and build an amahi home server based of the ubuntu server (for headless operation). I have the system running just fine, but I would like to add a printer. All the how-to guides I found say to just plug the Canon mp240 in and it will work. This sounds like what I've seen in the desktop version of ubuntu, but it doesn't seem to work in the server version. 

I need a set of terminal commands to check what USB devices are plugged in, and what drivers are being utilized. 

Again, I'm new to ubuntu, so please be explicit

Also, it would seem that a vlc desktop might work, but I don't have that installed either, so I would need commands for that too
Thanks, JP

---

### Post by 2F4U on 2012-09-03
Did you already install the print server CUPS? If not, here is how to do that

[https://help.ubuntu.com/12.04/serverguide/cups.html](https://help.ubuntu.com/12.04/serverguide/cups.html)

CUPS has a web interface, that by default can only be used locally. However, it is possible to configure CUPS such that you are able to access it remotely. You could then configure the printer from another machine and wouldn't need to do everything on the terminal.

---

