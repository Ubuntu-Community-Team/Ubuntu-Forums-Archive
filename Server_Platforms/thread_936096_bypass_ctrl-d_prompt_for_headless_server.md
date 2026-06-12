---
title: "bypass ctrl-d prompt for headless server"
date: 2008-10-02
forum: Server Platforms
---

### Post by g.caltech on 2008-10-02
Hello,
I have a server running 7.10 headless at a remote site. Recently I had an error in my fstab file that caused fsck to fail at bootup so the server was waiting with a prompt to press ctrl-d to continue, and was thus unaccessible except from the console. Since this was just an error in the fstab, pressing ctrl-d made the system boot without issues.
My question is, how can I tell the system to automatically continue after fsck fails to avoid this problem? Basically I want the system to try as hard as it can to get to the point where I can ssh to it.
Eventually I need to set up a console over the serial port for solving problems like this, but can't do that yet.
Thanks
Glenn

---

