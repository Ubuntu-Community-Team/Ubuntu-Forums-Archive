---
title: "How to install updates?"
date: 2009-06-30
forum: Server Platforms
---

### Post by cyrus_the_virus on 2009-06-30
How can I see and install updates on ubuntu server 8.04 from the cli? I do _not_ want to upgrade ubuntu to a newer edition, but only want to install software updates. 
On the desktop edition a message will appear on the taskbar when updates are avaible but since my server doesn't a gui, I was wondering how to do this in the command line.

Thanks,
Marty

---

### Post by SunnyRabbiera on 2009-06-30
sudo apt-get update will refresh the repositories to get access to more recent packages and sudo apt-get upgrade will upgrade the software.

Apt-get is quite simple, all you see on Ubuntu like update manager, add/remove and synaptic are all graphic frontends to apt.

---

### Post by cyrus_the_virus on 2009-06-30
Thanks! :)

My server is updating now! It is going to be busy for a while since I have never installed updates :p

---

