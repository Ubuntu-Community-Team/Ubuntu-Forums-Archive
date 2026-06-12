---
title: "Ubuntu 7.10 Wont Shutdown after Configuring Open Iscsi"
date: 2008-03-05
forum: Server Platforms
---

### Post by bricktop on 2008-03-05
Hi guys,

I have a bit of a problem here. I have successfully installed and mounted various Volums on my Ubuntu Servers using iSCSi. I am now having a small issue when shutting down the server.

The server successfully boots and mounts the volumes but when shutting them down the freeze on "Un mounting Local File system"

I suspect the problem is that the iSCSI initiator disconnects the volumes before Ubuntu can unmount them.

Is there any way I can set the initiator to disconnect the Volumes after Ubuntu has unmounted them?

This has happened on about 4 Ubuntu 7.10 servers all with identical configurations. It is a worry for me as we are having almost weekly power outages and my servers which house 4 Virtual servers each is not shutting down correctly with our UPS scripts.

HELP!!!

---

### Post by faulkes on 2008-03-05
look in /etc/rc6.d for the order in which the shutdown is happening.  the higher the S value 
the later in the shutdown procedure something happens.

I suspect that depending on your setup, that iscsi support is being removed prior to
the unmounting of the FS's which is causing it to hang on reboot.

The files in /etc/rc6.d will be symlinks, you can modify states and precedence by
through the update-rc.d command (man update-rc.d) although there may be a bit more
tinkering required than just that.

Faulkes

---

