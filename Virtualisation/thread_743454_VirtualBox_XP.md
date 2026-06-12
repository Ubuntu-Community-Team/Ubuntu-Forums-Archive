---
title: "VirtualBox XP"
date: 2008-04-02
forum: Virtualisation
---

### Post by Aloush on 2008-04-02
Hey!
I have created a new system thing and then when i start it it says

FATAL NO BOOTABLE MEDIUM FOUND

i have my windows XP CD in the drive what should i do?

---

### Post by xelapond on 2008-04-02
What is the terminal output of the command "id"?  Does it work when you run it with sudo?

I had a similar problem, it turned out to be that I had been removed from the cdrom group.

Hope that helps!

Alex

---

### Post by xelapond on 2008-04-02
Before you try that go into the settings for your Virtual Computer and go under CD ROM drives.  Make sure it is set to mount one on startup.

Good Luck!

Alex

---

