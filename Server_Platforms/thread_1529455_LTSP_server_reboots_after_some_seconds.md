---
title: "LTSP server reboots after some seconds"
date: 2010-07-12
forum: Server Platforms
---

### Post by wurzzero on 2010-07-12
Hi, i have a big problem here, i hope i can get some help!

This the scene:

I configured the LTSP server to allow a thin client to auto login (LDM_AUTOLOGIN, LDM_USERNMAE and LDM_PASSWORD). 

Then i noticed when i logout the thin client it makes a loop, exit the session and then it login  again. With this situation i could not turn off the machine, because the 'Shut Down' option do not works!

Before the auto login, i usually log out and then in the in the PREFERENCES (bottom left) in the login screen i choose Shut Down.

With this situation the only thing i thought was to turn off the LTSP server, but today when i turn it on again it shutdown! 
The server stays some seconds in the gdm screen and then shutdown, i tried to log in, but it shutdown too. Thats a big problem! 

I'll paste the last lines of my /var/log/messages


> Jul  8 17:48:34 localhost kernel: [   13.354639] r8169: eth0: link up
Jul  8 17:48:34 localhost kernel: [   13.354648] r8169: eth0: link up
Jul  8 17:48:37 localhost kernel: [   16.368909] RPC: Registered udp transport module.
Jul  8 17:48:37 localhost kernel: [   16.368912] RPC: Registered tcp transport module.
Jul  8 17:48:37 localhost kernel: [   16.368913] RPC: Registered tcp NFSv4.1 backchannel transport module.
Jul  8 17:48:37 localhost kernel: [   16.437321] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
Jul  8 17:48:37 localhost kernel: [   16.741692] svc: failed to register lockdv1 RPC service (errno 97).
Jul  8 17:48:37 localhost kernel: [   16.742525] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Jul  8 17:48:37 localhost kernel: [   16.754132] NFSD: starting 90-second grace period
Jul  8 17:48:38 localhost ltsp: # Creating dsa-hostkey for LucidLynx
Jul  8 17:48:38 localhost ltsp: # Creating rsa-hostkey for LucidLynx
Jul  8 17:48:42 localhost kernel: [   21.296440] ppdev: user-space parallel port driver
Jul  8 17:48:46 localhost pulseaudio[1803]: lock-autospawn.c: Cannot access autospawn lock.

Tanks!

**Edit:** The title is wrong, actually the serve SHUTDOWN, do not reboot.
There is a [patch]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/491940") for the reboot/shutdown problem (the loop i got in) at [Lauchpad]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/491940").

---

