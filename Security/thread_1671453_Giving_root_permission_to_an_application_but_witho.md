---
title: "Giving root permission to an application but without running it as root"
date: 2011-01-20
forum: Security
---

### Post by daniel.gross@utoronto.ca on 2011-01-20
Hello,

I want to run VirtualBox with root permissions. Trouble is that only when run as root i can access attached USB devices inside of a virtual machine, otherwise, these a greyed out).

Now running VirtualBox as a root user also changes the configuration folders, making all my virtual machines already defined disappear. I also don't want to copy all to the root configuration folders. 

Is there a way to give the VirtualBox root permissions but without actually running the application as a root user. Is it possible to do without changing the permissions of the non-root user, i.e. i don't want my user to have all root permissions, due to security considerations. 

thank you,
Daniel

---

### Post by bodhi.zazen on 2011-01-20
Add your user to the virutalbox group.

If that fails, change the ownership and permissions of the device.

---

